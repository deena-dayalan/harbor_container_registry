# -*- mode: ruby -*-
# vi: set ft=ruby :

$provision = <<-SCRIPT
grep -q "cd /var/vagrant" ~/.bashrc || echo "cd /var/vagrant" >> ~/.bashrc
/var/vagrant/bin/provision
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.box = "dhml/fedora-coreos-34.20210611.3.0-20210702"
  config.vm.provider "virtualbox" do |v|
    v.memory = 4096
    v.cpus = 2
  end
  config.vm.provision "shell", inline: $provision, privileged: false
  config.vm.network "forwarded_port", guest: 4443, host: 4443, host_ip: "127.0.0.1"
  config.vm.network "forwarded_port", guest: 8080, host: 8080, host_ip: "127.0.0.1"
  config.vm.network "forwarded_port", guest: 8443, host: 8443, host_ip: "127.0.0.1"
end
