# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  # config.vm.box = "ubuntu/xenial32"
  config.vm.box = "bento/ubuntu-16.04"
  config.vm.define "nominatim-xenial" do |machine|
    # Create a private network, which allows host-only access to the machine
    # using a specific IP.
    machine.vm.hostname = "nominatim-xenial.sample.org"
    #machine.vm.network "private_network", ip: "192.168.33.34"
    #machine.vm.network "public_network"
    machine.vm.network "public_network", auto_config: false

    # manual ip
    machine.vm.provision "shell", run: "always",  inline: "ifconfig eth0 192.168.34.35 netmask 255.255.255.0 up"

    ## manual ipv6
    #config.vm.provision "shell",
    #run: "always",
    #inline: "ifconfig eth1 inet6 add fc00::17/7"

    machine.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.memory = "3072"
      vb.name = "nominatim-xenial"
    end
    #machine.vm.provision "ansible" do |ansible|
    #  ansible.verbose = "v"
    #  ansible.playbook = "provision.yml"
    #end
  end
end
