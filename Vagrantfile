# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "centos/7"
  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.ssh.insert_key = false

  config.vm.provider "virtualbox" do |v|
    v.cpus = 1
    v.memory = 1024
    v.customize ["storageattach", :id, "--storagectl", "IDE",
		 "--port", "1", "--device", "0", "--type", "dvddrive",
		 "--medium", "/Applications/VirtualBox.app/Contents/MacOS/VBoxGuestAdditions.iso"]
    v.customize ["modifyvm", :id, "--audio", "none"]
    # If the system time falls behind, uncomment the next line
    # v.customize ["modifyvm", :id, "--paravirtprovider", "none"]
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/bootstrap.yml"
    ansible.sudo = true
  end
end
