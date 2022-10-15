# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # gateway
  config.vm.define "gateway" do |gateway|
    gateway.vm.box = "bento/ubuntu-22.04"

    # VB configs
    gateway.vm.provider "virtualbox" do |vb|
      # Display the VirtualBox GUI when booting the machine
      vb.gui = false

      # Customize the amount of memory on the VM:
      vb.memory = "1024"
    end

    # Create NIC for LAN
    gateway.vm.network "private_network",
      virtualbox__intnet: "intnet",
      ip: "172.16.0.1"

    # Run provision with Ansible
    gateway.vm.provision :ansible do |ansible|
      ansible.playbook = "gateway/playbook.yml"
    end
  end


  # HostA (nginx)
  config.vm.define "hostA" do |hostA|
    hostA.vm.box = "bento/ubuntu-22.04"
    hostA.vm.hostname = "mysite.com"

    # VB configs
    hostA.vm.provider "virtualbox" do |vb|
      # Display the VirtualBox GUI when booting the machine
      vb.gui = false

      # Customize the amount of memory on the VM:
      vb.memory = "1024"
    end

    # Create NIC for WAN
    hostA.vm.network "private_network",
      virtualbox__intnet: "intnet",
      ip: "172.16.0.2"

    # Create NIC for LAN
    hostA.vm.network "private_network",
      virtualbox__intnet: "intnet100",
      ip: "192.168.100.1"

    # Run provision with Ansible
    hostA.vm.provision :ansible do |ansible|
      ansible.playbook = "hostA/playbook.yml"
    end
  end


  # HostB (mysql)
  config.vm.define "hostB" do |hostB|
    hostB.vm.box = "bento/ubuntu-22.04"

    # VB configs
    hostB.vm.provider "virtualbox" do |vb|
      # Display the VirtualBox GUI when booting the machine
      vb.gui = false

      # Customize the amount of memory on the VM:
      vb.memory = "1024"
    end

    # Create NIC for LAN
    hostB.vm.network "private_network",
      virtualbox__intnet: "intnet100",
      ip: "192.168.100.2"

    # Create NIC for MySQL
    hostB.vm.network "private_network",
      virtualbox__intnet: "intnet101",
      ip: "192.168.101.1"

    # Run provision with Ansible
    hostB.vm.provision :ansible do |ansible|
      ansible.playbook = "hostB/playbook.yml"
    end
  end


  # HostC (Apache2)
  config.vm.define "hostC" do |hostC|
    hostC.vm.box = "bento/ubuntu-22.04"

    # VB configs
    hostC.vm.provider "virtualbox" do |vb|
      # Display the VirtualBox GUI when booting the machine
      vb.gui = false

      # Customize the amount of memory on the VM:
      vb.memory = "1024"
    end

    # Share html folder
    #hostC.vm.synced_folder "./hostC/html", "/var/www/html/"

    # Create NIC for LAN
    hostC.vm.network "private_network",
      virtualbox__intnet: "intnet100",
      ip: "192.168.100.3"

    # Create NIC for Apache
    hostC.vm.network "private_network",
      virtualbox__intnet: "intnet102",
      ip: "192.168.102.1"

    # Run provision with Ansible
    hostC.vm.provision :ansible do |ansible|
      ansible.playbook = "hostC/playbook.yml"
    end
  end
end