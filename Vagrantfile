# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

   config.vm.box = "debian/buster64"

   config.vm.provider :virtualbox do |v|
      v.name = "jarvis.local"
      v.memory = 2048
      v.cpus = 2
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
      v.default_nic_type = "82543GC"
   end

   config.vm.hostname = "jarvis.local"
   config.vm.network :private_network, ip: "192.168.4.25"

   config.vm.provision :ansible do |ansible|
      ansible.verbose = "v"
      ansible.playbook = "main.yml"
   end
end
