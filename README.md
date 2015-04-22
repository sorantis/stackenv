stackenv
========

Vagrant and Devstack based development and testing environment for OpenStack.
Tested with Vagrant 1.7.2 and VirtualBox 4.3.26.

Installation
===
1. Install Vagrant and VirtualBox
2. Create a folder where you want to host your devstack 
3. Copy Vagrantfile to that folder
4. Create a shared folder (in the configuration it is src/)
5. sudo chown root:0 -R src/
6. vagrant up
7. vagrant ssh
8. cd devstack
9. copy localrc
10. ./stack.sh
