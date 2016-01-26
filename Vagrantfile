# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrant file for DevOps Playground #2

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64 "

  # Share current directory with VM so we have the playbooks
  config.vm.synced_folder ".", "/devops-playground-2"

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
    sudo apt-get install -y docker-engine docker-compose
    sudo usermod -aG docker vagrant
  SHELL
end
