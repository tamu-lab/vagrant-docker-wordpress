# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "ubuntu/trusty64"
  config.vm.box_check_update = false

  config.vbguest.auto_update = false

  config.vm.define "wordpress" do |atomic|
    atomic.vm.hostname = "wordpress.local"
    atomic.vm.synced_folder "./", "/vagrant"
    atomic.vm.network "private_network", ip: "192.168.33.11"

    atomic.vm.provider "virtualbox" do |vb|
      # Customize the amount of memory on the VM:
      vb.memory = "2048"
      vb.cpus = 1
      vb.customize ["modifyvm", :id, "--name", "ubuntu-docker-wordpress"]
    end

    # port forward
    atomic.vm.network :forwarded_port, guest: 80, host: 8080
  end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get dist-upgrade -y
    sudo apt-get install -y python-dev python-pip build-essential libffi-dev libssl-dev libYAML-dev git
    sudo python -m pip install -U pip
    sudo pip install --upgrade packaging appdirs setuptools ansible markupsafe passlib ndg-httpsclient
  SHELL
end
