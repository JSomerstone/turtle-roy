# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu-trusty-64"
      config.vm.box_url = "https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box"

      config.vm.hostname = "turtleroy.dev"
      #config.vm.network :private_network, ip: "192.168.111.222"
      config.vm.network "forwarded_port", guest: 8070, host: 8000
      config.vm.synced_folder "./", "/vagrant", owner: "vagrant"

      config.vm.provision "ansible" do |ansible|
          ansible.playbook = "ansible/playbook.yml"
          ansible.host_key_checking = false
          ansible.sudo = true
      end

      config.vm.provider "virtualbox" do |v|
          v.name = "turtle-roy-dev"
          v.memory = 2048
          v.customize ["modifyvm", :id, "--cpus", 2]
      end
  end
