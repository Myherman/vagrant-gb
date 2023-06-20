# -*- mode: ruby -*-
# vi: set ft=ruby :
# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.

ENV['VAGRANT_DEFAULT_PROVIDER'] = 'libvirt'
Vagrant.configure("2") do |config|
  config.vm.provider :libvirt do |vb|
    vb.driver = "qemu"
    vb.memory = 2048
    vb.cpus = 2
    vb.qemu_use_session = false
  end

  config.vm.define "haproxy_vm" do |haproxy_vm|
    haproxy_vm.vm.box = "generic/ubuntu2004"
    haproxy_vm.vm.box_check_update = false
    haproxy_vm.vm.hostname = "haproxy_vm"
    haproxy_vm.vm.network "private_network", ip: "10.100.10.30"
    config.vm.provision "file", source: "/home/valera/.ssh/id_rsa.pub", destination: "/home/vagrant/.ssh/"
    haproxy_vm.vm.provision "shell", inline: <<-SHELL
        chmod 600 /home/vagrant/.ssh/project.pub
        cat /home/vagrant/.ssh/project.pub >> /home/vagrant/.ssh/authorized_keys
    SHELL
  end
    config.vm.define "wordpress-vm1" do |wordpress-vm1|
    wordpress-vm1.vm.box = "generic/ubuntu2004"
    wordpress-vm1.vm.box_check_update = false
    wordpress-vm1.vm.hostname = "wordpress_vm"
    wordpress-vm1.vm.network "private_network", ip: "10.100.10.40"
    config.vm.provision "file", source: "/home/valera/.ssh/id_rsa.pub", destination: "/home/vagrant/.ssh/"
    wordpress-vm1.vm.provision "shell", inline: <<-SHELL
        chmod 600 /home/vagrant/.ssh/project.pub
        cat /home/vagrant/.ssh/project.pub >> /home/vagrant/.ssh/authorized_keys
    SHELL
  end
    config.vm.define "wordpress-vm2" do |wordpress-vm2|
    wordpress-vm2.vm.box = "generic/ubuntu2004"
    wordpress-vm2.vm.box_check_update = false
    wordpress-vm2.vm.hostname = "wordpress-vm2"
    wordpress-vm2.vm.network "private_network", ip: "10.100.10.50"
    config.vm.provision "file", source: "/home/valera/.ssh/id_rsa.pub", destination: "/home/vagrant/.ssh/"
    wordpress-vm2.vm.provision "shell", inline: <<-SHELL
        chmod 600 /home/vagrant/.ssh/project.pub
        cat /home/vagrant/.ssh/project.pub >> /home/vagrant/.ssh/authorized_keys
    SHELL
  end
    config.vm.define "database-vm" do |database-vm|
    database-vm.vm.box = "generic/ubuntu2004"
    database-vm.vm.box_check_update = false
    database-vm.vm.hostname = "database-vm"
    database-vm.vm.network "private_network", ip: "10.100.10.60"
    config.vm.provision "file", source: "/home/valera/.ssh/id_rsa.pub", destination: "/home/vagrant/.ssh/"
    database-vm.vm.provision "shell", inline: <<-SHELL
        chmod 600 /home/vagrant/.ssh/project.pub
        cat /home/vagrant/.ssh/project.pub >> /home/vagrant/.ssh/authorized_keys
    SHELL
  end
    config.vm.define "monitor-vm" do |monitor-vm|
    monitor-vm.vm.box = "generic/ubuntu2004"
    monitor-vm.vm.box_check_update = false
    monitor-vm.vm.hostname = "monitor-vm"
    monitor-vm.vm.network "private_network", ip: "10.10.10.7"
    config.vm.provision "file", source: "/home/set/Äîêóìåíòû/geekbrains/keys/project.pub", destination: "/home/vagrant/.ssh/"
    monitor-vm.vm.provision "shell", inline: <<-SHELL
        chmod 600 /home/vagrant/.ssh/project.pub
        cat /home/vagrant/.ssh/project.pub >> /home/vagrant/.ssh/authorized_keys
    SHELL
  end
end

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "10.58.4.20"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount tehe folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "F:/DevOps", "/home/vagrant"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL