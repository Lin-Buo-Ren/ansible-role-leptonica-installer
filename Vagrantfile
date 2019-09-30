# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrant configuration template for ITZXA
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  # The bento boxes supports synced folders
  #config.vm.box = "ubuntu/bionic64"
  config.vm.box = "bento/ubuntu-18.04"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  # https://www.vagrantup.com/docs/virtualbox/configuration.html
  config.vm.provider "virtualbox" do |v|
    # Customize the amount of memory on the VM
    # Use too much may causes host system thrashing
    # Acer: 8GiB
    # Dell: 16GiB
    v.memory = "1024"

    # The sane value is how many physical cores your system has
    v.cpus = 4

    # Use VirtIO NIC for better performance
    # https://www.virtualbox.org/manual/ch08.html#vboxmanage-modifyvm-networking
    v.default_nic_type = "virtio"
  end

  config.vm.define "default" do |vm_default|
    # Uncomment if you need bridged network instead of default NAT
    #vm_default.vm.network "public_network"

    # Uncomment if you need private network interconnecting between multiple vagrant VMs
    #vm_default.vm.network "private_network", ip: "192.168.50.11"

    # Port forwarding configuration
    vm_default.vm.network "forwarded_port", guest: 22, host: 2222, host_ip: "127.0.0.1", id: "ssh", auto_correct: true
    #vm_default.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
    #vm_default.vm.network "forwarded_port", guest: 443, host: 8443, host_ip: "127.0.0.1"

    #vm_default.vm.provision "shell", inline: <<-EOF
      #apt install --yes rsync
    #EOF
    vm_default.vm.provision "ansible" do |ansible|
      ansible.playbook = "tests/test-vagrant.yml"
    end
  end
end
