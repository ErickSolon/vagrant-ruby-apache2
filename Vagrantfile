# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "vm1" do |vm1|
    vm1.vm.box = "ubuntu/trusty64"
    vm1.vm.box_version = "20191107.0.0"
    vm1.vm.network "forwarded_port", guest: 80, host: 8181, host_ip: "127.0.0.1"
    vm1.vm.synced_folder ".", "/vagrant_data"
    vm1.vm.provider "virtualbox" do |vb1|
      vb1.gui = false
      vb1.memory = "1024"
    end

    vm1.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y apache2

      ruby /vagrant_data/main.rb

      cp -v /vagrant_data/index.html /var/www/html/index.html
    SHELL
  end

  config.vm.define "vm2" do |vm2|
      vm2.vm.box = "ubuntu/trusty64"
      vm2.vm.box_version = "20191107.0.0"
      vm2.vm.network "forwarded_port", guest: 80, host: 8182, host_ip: "127.0.0.1"
      vm2.vm.synced_folder ".", "/vagrant_data"
      vm2.vm.provider "virtualbox" do |vb2|
        vb2.gui = false
        vb2.memory = "1024"
      end

      vm2.vm.provision "shell", inline: <<-SHELL
        apt-get update
        apt-get install -y apache2

        ruby /vagrant_data/main.rb

        cp -v /vagrant_data/index.html /var/www/html/index.html
      SHELL
  end
end
