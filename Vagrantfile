# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" refers to the version of Vagrantfile
Vagrant.configure("2") do |config|
  # See the full documentation https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. This is Ubuntu official box from https://vagrantcloud.com/search.
  config.vm.box = "ubuntu/focal64"

  config.vm.provision :docker
  # install golang
  config.vm.provision :shell, :path => "setup/install-golang.sh"
  # install fabric binaries
  config.vm.provision :shell, :path => "setup/install-compose.sh"
  # install fabric binaries
  config.vm.provision :shell, :path => "setup/install-fabric.sh"
  
  # deploy network
  config.vm.provision :shell, :path => "setup/test-network.sh"

  # Create a forwarded port mapping which allows access to a specific port:
  config.vm.network "forwarded_port", guest: 9443, host: 9443
  config.vm.network "forwarded_port", guest: 8005, host: 8005

  # Share a folder to the guest VM.
  config.vm.synced_folder "code", "/home/vagrant/code"

  config.vm.provider "virtualbox" do |vb|
    # Set Virtual Machine name
    vb.name = "vagrant_fabric"
    # Display or not the VirtualBox GUI when booting the machine
    vb.gui = false
    # Customize the amount of memory on the VM:
    vb.memory = "2048"
    # Set number of CPUs
    vb.cpus = 2
   end
  #
  # Enable provisioning with a shell script. Additional provisioners such as
  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
end
