# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.box = "rails-dev-box"
    config.vm.box_url   = 'http://files.vagrantup.com/precise32.box'
    config.vm.hostname = 'rails-dev-box'
    config.vm.network :private_network, ip: "192.168.33.11"
    config.vm.network :forwarded_port, guest: 3000, host: 3000
    config.vm.synced_folder "/Users/jkendall/dev/sinatra", "/home/vagrant/sinatra"
    
    config.vm.provider :virtualbox do |vb|
        vb.customize ["modifyvm", :id, "--memory", "512"]
        vb.customize ["modifyvm", :id, "--natnet1", "10.0.28.0/24"]
    end

    config.vm.provision :puppet do |puppet|
        puppet.manifests_path = "puppet/manifests"
        puppet.module_path = "puppet/modules"
    end
end
