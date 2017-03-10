# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "OpenStackMeetUP"
  config.vm.define  :controller do |node|
    node.vm.provider "virtualbox" do |vb|
      vb.linked_clone = true
#      vb.memory = "4096"
      vb.memory = "8192"
      vb.cpus = "2"
    end
    node.vm.network "forwarded_port", guest: 80, host: 18080
    node.vm.hostname = "controller.example.local"
#    node.vm.network "public_network"
    node.vm.network "private_network", ip: "192.168.55.11", netmask: "255.255.255.0", dhcp_enabled: false, forward_mode: "none"
    node.vm.network "private_network", ip: "172.25.55.11", netmask: "255.255.255.240", dhcp_enabled: false
    node.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "playbook/2_prepare_openstack.yml"
#      ansible.verbose = true
    end
  end
end
