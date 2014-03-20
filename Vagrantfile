-- mode: ruby --
vi: set ft=ruby :
Vagrant config

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
config.vm.box = "heat"
config.vm.box_url = "http://files.vagrantup.com/precise32.box"
# Change memory of our VM to 2048MB
config.vm.provider :virtualbox do |vb|
vb.customize ["modifyvm", :id, "--memory", "2048"]
end

# Forward port for Horizon
config.vm.network :forwarded_port, guest: 80, host: 8080

# Private network IP, needed for NFS
config.vm.network :private_network, ip: "192.168.55.10"

# /opt/stack is synced with vagrant project dir over NFS
config.vm.synced_folder ".", "/opt/stack", :owner=> 'vagrant', :group=>'vagrant', :mount_options => ['dmode=775', 'fmode=775']
end
