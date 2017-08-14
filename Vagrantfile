# -*- mode: ruby -*-
# vi: set ft=ruby :
# credits:  https://github.com/geerlingguy/packer-debian-9

Vagrant.configure("2") do |config|
  config.ssh.insert_key = false
  #config.ssh.insert_key = true
  #config.vm.synced_folder '.', '/vagrant', type: 'nfs'

  # VirtualBox.
  # `vagrant up debian9
  config.vm.define "debian9" do |virtualbox|
    virtualbox.vm.hostname = "virtualbox-debian9"
    virtualbox.vm.box = "file://builds/virtualbox-debian9.box"
    virtualbox.vm.network :private_network, ip: "172.16.3.2"

    config.vm.provider :virtualbox do |v|
      v.gui = false
      v.memory = 1024
      v.cpus = 1
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--ioapic", "on"]
    end
  end

  config.vm.define "debian8" do |virtualbox|
    virtualbox.vm.hostname = "virtualbox-debian8"
    virtualbox.vm.box = "file://builds/virtualbox-debian8.box"
    virtualbox.vm.network :private_network, ip: "172.16.3.2"

    config.vm.provider :virtualbox do |v|
      v.gui = false
      v.memory = 1024
      v.cpus = 1
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--ioapic", "on"]
    end
  end

#  config.vm.define "ubuntu1604" do |virtualbox|
#    virtualbox.vm.hostname = "virtualbox-debian8"
#    virtualbox.vm.box = "file://builds/virtualbox-debian8.box"
#    virtualbox.vm.network :private_network, ip: "172.16.3.2"
#
#    config.vm.provider :virtualbox do |v|
#      v.gui = false
#      v.memory = 1024
#      v.cpus = 1
#      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
#      v.customize ["modifyvm", :id, "--ioapic", "on"]
#    end
#  end

end
