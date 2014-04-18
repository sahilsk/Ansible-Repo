# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.provision "shell", inline: "echo Hello"
	
	config.vm.define "master" do |instance|
		instance.vm.box = "precise32"
		instance.vm.network "private_network", ip: "192.168.50.21", mac: "macMaster210031307"
		instance.vm.hostname = "master.vmcluster.com"
		instance.vm.synced_folder "../repo", "/vagrant_data"
	end	
	
	(1..3).each do |id|
		config.vm.define "slave"+id.to_s do |instance|
			instance.vm.box = "precise32"
			instance.vm.network "private_network", ip: "192.168.50.1"+id.to_s, mac: "macSlave#{id}0023431"
			instance.vm.hostname = "slave#{id}.vmcluster.com"
			instance.customize ["modifyvm", :id, "--memory", "256"]
		end
	end
  
end
