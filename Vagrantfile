# -*- mode: ruby -*-
# vi: set ft=ruby :





# Requirements
Vagrant.require_version ">= 1.8.0"





#
# Configuration
#
Vagrant.configure(2) do |config|





  #
  # Machine Settings
  #
  config.vm.boot_timeout = 180
  config.vm.box = "ubuntu/trusty64"





  #
  # Provider
  #
  config.vm.provider "virtualbox" do |vb|

    vb.name = "craft"
    vb.memory = 2048
    vb.cpus = 2

  end





  #
  # Networking
  #
  # Forward the Rails server default port to the host
  # config.vm.network "forwarded_port", guest: 3000, host: 3000, auto_correct: true

  # Forward the Nginx server default port to the host
  # config.vm.network "forwarded_port", guest: 80, host: 8080, auto_correct: true
  config.vm.network "private_network", type: "dhcp"





  #
  # Synced Folders
  #
  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.synced_folder "src/", "/srv/www/app", owner: "deploy", group: "deploy", mount_options: ["dmode=777", "fmode=777"]





  #
  # Provisioner
  #
  config.vm.provision "ansible" do |ansible|

    # Config
    ansible.host_key_checking = false
    ansible.ask_vault_pass = false
    # ansible.verbose = 'vvvv'

    # Playbooks
    ansible.playbook = "ansible/site.yml"

    # Roles
    # ansible.tags = [ 'common', 'users' ]
    ansible.tags = [ 'common', 'users', 'fish', 'nginx', 'php', 'php-mysql', 'mysql' ]

  end





end
