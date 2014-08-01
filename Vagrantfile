# -*- mode: ruby -*-
# vi: set ft=ruby :
$script = <<SCRIPT
# download required packages
sudo apt-get update && sudo apt-get -y install git vim-gtk libxml2-dev libxslt1-dev libpq-dev python-pip libsqlite3-dev && sudo apt-get -y build-dep python-mysqldb && sudo pip install --upgrade pip && sudo pip install --upgrade setuptools && sudo pip install git-review tox && git clone git://git.openstack.org/openstack-dev/devstack -b stable/icehouse  && chown -R vagrant:vagrant devstack && cd devstack
SCRIPT

## Vagrant config
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "heat"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  #config.vm.box_url = "../precise64.box"
  # Change memory of our VM to 4096MB
  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "4096"]
  end
  #config.proxy.http  = "http://www-proxy.ericsson.se:8080"
  #config.proxy.https = "http://www-proxy.ericsson.se:8080"

  # Forward port for Horizon
  config.vm.network :forwarded_port, guest: 80, host: 8080

  # Private network IP, needed for NFS
  config.vm.network :private_network, ip: "192.168.55.10"

  # /opt/stack is synced with vagrant project dir over NFS
  #config.vm.synced_folder "share/", "/opt/stack", :nfs => { :mount_options => ["dmode=777","fmode=777"] }
  config.vm.synced_folder ".", "/vagrant", disabled:true
  config.vm.synced_folder "src/", "/opt/stack", nfs:true
	#, :owner=> 'vagrant', :mount_options => ['dmode=777', 'fmode=777']
  #config.bindfs.bind_folder "/opt/shared", "/opt/stack", perms:"u=rwx:g=rx:o=rx"

  config.vm.provision "shell", inline: $script
end
