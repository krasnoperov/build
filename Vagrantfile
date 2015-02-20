# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"
DOMAIN                  = "build.krasnoperov.me"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.box = "ubuntu/trusty64"
    config.ssh.forward_agent = true

    config.vm.provider :virtualbox do |v|
        v.customize ["modifyvm", :id, "--name", DOMAIN]
        v.customize ["modifyvm", :id, "--memory", 1024]
        v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    end

    config.vm.define DOMAIN do |host|
        host.vm.hostname = DOMAIN
    end
end

load "Vagrantfile.local" if File.exists?("Vagrantfile.local")
