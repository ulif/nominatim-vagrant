# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  # Apache webserver
  # config.vm.network "forwarded_port", guest: 80, host: 8089

  # If true, then any SSH connections made will enable agent forwarding.
  config.ssh.forward_agent = true

  checkout = "yes"
  #if ENV['CHECKOUT'] != 'y' then
  #    config.vm.synced_folder "./Nominatim", "/home/vagrant/Nominatim"
  #    checkout = "no"
  #end

  config.vm.define "ubuntu", primary: true do |sub|
      sub.vm.box = "bento/ubuntu-16.04"
      #sub.vm.provision :shell do |s|
      #  s.path = "Nominatim/vagrant/install-on-ubuntu-16.sh"
      #  s.privileged = false
      #  s.args = [checkout]
      #end
      #sub.vm.provision "ansible" do |ansible|
      #  ansible.verbose = "v"
      #  ansible.playbook = "provision.yml"
      #end
  end

  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory = "3072"
  end

end
