# -*- mode: ruby -*-
# vi: set ft=ruby :

# All configuration should go inside this block.
Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/trusty64"

  config.vm.network "forwarded_port", guest: 80, host: 9000
  config.vm.network "forwarded_port", guest: 8000, host: 9001

  config.ssh.forward_agent = true

  # PATH TO YOUR CODALAB DIRECTORY
  config.vm.synced_folder "/Users/flaviozhingri/work/codalab/", "/home/vagrant/codalab"


  config.vm.provider "virtualbox" do |vb|
    # Customize the amount of memory on the VM:
    # This is a shortcut. Look https://www.vagrantup.com/docs/virtualbox/configuration.html for more config
    vb.memory = "1024"
  end

  # Provisioning use shell
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get upgrade
    sudo apt-get install build-essential -y
    sudo apt-get instal python-dev -y
    sudo apt-get libmysqlclient-dev -y
    sudo apt-get install python-pip -y
    sudo pip install --upgrade pip

    # Pip installations
    pip install virtualenv
  SHELL
end
