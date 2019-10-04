# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.require_version ">= 1.7.0"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

   config.vm.box = "debian/jessie64"

   config.vm.provider :virtualbox do |v|
      v.name = "jarvis.local"
      v.memory = 2048
      v.cpus = 2
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
      v.default_nic_type = "82543GC"
   end

   config.vm.hostname = "jarvis.local"
   config.vm.network :private_network, ip: "192.168.50.25"

   if defined?(VagrantPlugins::HostsUpdater)

      # Pass the found host names to the hostsupdater plugin so it can perform magic.
      config.hostsupdater.aliases = ['jarvis.local']
      config.hostsupdater.remove_on_suspend = true
   end

   config.vm.provision :ansible do |ansible|
      ansible.verbose = "v"
      ansible.playbook = "main.yml"
      ansible.compatibility_mode = "2.0"
   end
end
