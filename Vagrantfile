# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.

VAGRANT_USER_NAME = "#{ENV['USERNAME']}"
VAGRANT_INSTANCE_NAME = "devbox-#{VAGRANT_USER_NAME}-1804"

Vagrant.configure("2") do |config|
  # config.vm.define VAGRANT_INSTANCE_NAME
  # config.vm.hostname = VAGRANT_INSTANCE_NAME
  machine = {
    :define   => VAGRANT_INSTANCE_NAME,
    # :hostname => "sandbox",
    :hostname => VAGRANT_INSTANCE_NAME,
    :box      => "ubuntu/bionic64",
    # :ip       => "192.168.56.10",
    :memory   => "4096",
    :cpu      => "2"
  }
  forwarded_ports = [
    { :guest => "8080", :host  => "8080" }, # jenkins
    { :guest => "8888", :host  => "8888" }, # chronograf
    { :guest => "3000", :host  => "3000" }, # grafana
    # { :guest => "8181", :host  => "8181" }, # rancher
    # { :guest => "4566", :host  => "4566" }, # localstack
  ]
  config.vm.define machine[:define]
  config.vm.box = machine[:box]
  config.vm.box_check_update = false
  # config.vm.synced_folder "projects", "/home/vagrant/projects"
  config.vm.synced_folder "~/OneDrive/playground/projects", "/home/vagrant/projects"
  config.vm.synced_folder "E:/vagrant-data", "/home/vagrant/vagrant-data"
  config.vm.hostname = machine[:hostname]
  # config.ssh.username = 'root'
  # config.ssh.password = 'root'
  # config.ssh.insert_key = 'true'
  # config.vm.network "public_network"
  # config.vm.synced_folder ".", "/vagrant", disabled: false
  # config.vm.network "private_network", ip: machine[:ip]
  forwarded_ports.each do |fp|
    # config.vm.network "forwarded_port", guest: fp[:guest], host: fp[:host], host_ip: machine[:ip], id: machine[:id]
    config.vm.network "forwarded_port", guest: fp[:guest], host: fp[:host]
  end

  config.vm.provider "virtualbox" do |vb|
    vb.memory = machine[:memory]
    vb.cpus = machine[:cpu]
    vb.name = VAGRANT_INSTANCE_NAME
  end
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
  # config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/id_rsa.pub"
  # config.vm.provision "file", source: "~/.ssh/id_rsa", destination: "~/.ssh/id_rsa"
  
  config.vm.provision "file", source: "~/.aws/", destination: "/tmp/aws_config"
  config.vm.provision "file", source: "~/.ssh/", destination: "/tmp/ssh_config"
  config.vm.provision "file", source: "./ansible", destination: "/tmp/ansible"
  config.vm.provision "ansible_local" do |ansible|
    ansible.provisioning_path = "/tmp/ansible"
    ansible.playbook = "devbox-1804.yml"
  end
  # config.vm.provision "shell", path: "ansible/ohmyposh.sh"
end
