# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrant file for DevOps Playground #2
# Author: Angus Williams <angus@forest-technologies.co.uk>

Vagrant.configure(2) do |config|
  # Ubuntu 14.04
  config.vm.box = "ubuntu/trusty64"

  # Foward elastic service ports to localhost
  config.vm.network "forwarded_port", guest: 9200, host: 9200 # elasticsearch
  config.vm.network "forwarded_port", guest: 5601, host: 5601 # kibana4

  config.vm.provider "virtualbox" do |vb|
    # Add another CPU
    vb.cpus = "2"
    # Customize the amount of memory on the VM
    vb.memory = "2048"
  end

  # Install docker & docker-compose
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
    echo "deb https://apt.dockerproject.org/repo ubuntu-trusty main" | sudo tee /etc/apt/sources.list.d/docker.list
    sudo apt-get update
    sudo apt-get install -y docker-engine python-pip
    sudo usermod -aG docker vagrant
    sudo pip install docker-compose
    cd /vagrant && docker-compose build && docker-compose pull
  SHELL
end
