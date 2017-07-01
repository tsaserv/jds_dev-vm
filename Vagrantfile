# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.

Vagrant.configure("2") do |config|
  config.vm.define "dev1" do |dev1|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  #config.vm.box = "base"
    dev1.vm.box = "ubuntu/xenial64"
    dev1.vm.host_name = "jdsdev1VM"
    dev1.ssh.shell = "bash -c 'BASH_ENV=/etc/profile exec bash'"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
    dev1.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
    dev1.vm.network "public_network", bridge: "en0: Wi-Fi (AirPort)"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
    dev1.vm.synced_folder "/Users/jamesstorr/GitHub", "/host/GitHub"
    dev1.vm.synced_folder "/Users/jamesstorr/DevData", "/host/DevData"


  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #
    dev1.vm.provider :virtualbox do |virtualbox|
      virtualbox.gui    = false
      virtualbox.memory = 2048
      virtualbox.cpus   = 1
      virtualbox.name   = "jdsdev1VM"
    end
  # View the documentation for the provider you are using for more
  # information on available options.

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  # config.push.define "atlas" do |push|
  #   push.app = "YOUR_ATLAS_USERNAME/YOUR_APPLICATION_NAME"
  # end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
  #config.vm.provision :shell, :inline => "sudo /vagrant/bootstrap.sh"
    config.vm.provision :shell, :inline => "sudo /vagrant/bootstrap.sh"
  end
    # Second VM before commnd line args
    config.vm.define "dev2" do |dev2|
      dev2.vm.box = "ubuntu/xenial64"
      dev2.vm.host_name = "jdsdev2VM"
      dev2.ssh.shell = "bash -c 'BASH_ENV=/etc/profile exec bash'"
      dev2.vm.network "forwarded_port", guest: 80, host: 8081
      dev2.vm.synced_folder "/Users/jamesstorr/GitHub", "/host/GitHub"
      dev2.vm.synced_folder "/Users/jamesstorr/DevData", "/host/DevData"

      config.vm.provider :virtualbox do |virtualbox|
        virtualbox.gui    = false
        virtualbox.memory = 1024
        virtualbox.cpus   = 1
        virtualbox.name   = "jdsdev2VM"
      end
      config.vm.provision :shell, :inline => "sudo /vagrant/bootstrap.sh"
    end
end
