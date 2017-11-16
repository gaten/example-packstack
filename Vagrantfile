# -*- mode: ruby -*-
# vi: set ft=ruby :
#
# Install vagrant hostmanager plugin!
# vagrant plugin install vagrant-hostmanager
#

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.

Vagrant.configure(2) do |config|

  ## Manage /etc/hosts
  ## Plugin vagrant-hostmanager 
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
  config.hostmanager.ignore_private_ip = false
  config.hostmanager.include_offline = true

  ## PackStack machine
  config.vm.define "packstack" do |ostack|
    ostack.vm.box = "centos/7"
    ostack.vm.hostname = "packstack"

    ostack.vm.network :private_network, ip: "192.168.199.120", :netmask => "255.255.255.0"

    ostack.vm.synced_folder ".", "/vagrant", disabled: true

    ostack.vm.provider "virtualbox" do |vb|
      vb.memory = "8192"
    end

    ostack.vm.provision "ansible" do |ansible|
       ansible.playbook = "packstack.yml"
    end
  end


end
