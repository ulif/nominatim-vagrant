# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  # Apache webserver
  config.vm.network "forwarded_port", guest: 80, host: 8089

  # In case you want to share something
  config.vm.synced_folder "./shared", "/home/vagrant/shared"

  # If true, then any SSH connections made will enable agent forwarding.
  config.ssh.forward_agent = true

  config.vm.define "ubuntu", primary: true do |sub|
    sub.vm.box = "bento/ubuntu-16.04"
    sub.vm.provision "ansible" do |ansible|
      ansible.verbose = "v"
      ansible.playbook = "provision.yml"
    end
    # Enable the following if you want maps automatically installed.
    #sub.vm.provision "ansible" do |ansible|
    #  ansible.verbose = "v"
    #  ansible.playbook = "installmaps.yml"
    #end
  end

  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory = "3072"
  end

end
