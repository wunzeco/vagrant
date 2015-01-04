# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "ubuntu/trusty64"

  config.vm.define "n1" do |n1|
    n1.vm.hostname = "n1"
    n1.vm.network "private_network", ip: "172.20.10.10"
  end

  config.vm.define "gocd" do |gocd|
    gocd.vm.hostname = "gocd"
    gocd.vm.network "private_network", ip: "172.20.10.50"
    config.vm.network "forwarded_port", guest: 8153, host: 8153
    config.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
    end
    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "gocd.yml"
    end
  end
end
