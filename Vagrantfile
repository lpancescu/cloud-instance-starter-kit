# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "centos/7"
  config.vm.network "private_network", ip:"192.168.56.3"
  config.vm.synced_folder ".", "/home/vagrant/sync", disabled: true

  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.customize ["storageattach", :id, "--storagectl", "IDE Controller",
		 "--port", "1", "--device", "0", "--type", "dvddrive",
		 "--medium", "/Applications/VirtualBox.app/Contents/MacOS/VBoxGuestAdditions.iso"]
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/bootstrap.yml"
    ansible.sudo = true
  end
end
