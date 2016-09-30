# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "/opt/sbeliakou-vagrant-centos-6.7-x86_64.box"
  config.vm.network "private_network", ip: "192.168.33.14"
  config.vm.hostname = "yauhen.com"
  config.vm.provider "virtualbox" do |vb|
    vb.cpus = 1
    vb.memory = 4096
end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = 'ansible/provision.yml'
    ansible.verbose = 'vv'
  end
end
