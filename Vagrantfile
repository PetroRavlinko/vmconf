# -*- mode: ruby -*-
# vi: set ft=ruby :
require 'berkshelf/vagrant'

Vagrant.configure("2") do |config|
  
  config.vm.define :masternode  do |masternode| 
    # Every Vagrant virtual environment requires a box to build off of.
    masternode.vm.box = "ubuntu12.04.2"
    masternode.vm.box_url = "http://d1owbwdg5aiwzw.cloudfront.net/ubuntu12.04.2.box"
  
    # Setup Network
    # Set private network
    # Setup internal network 
    masternode.vm.network :private_network, ip: "192.168.1.11"
 
    # Set provider related settings 
    masternode.vm.provider :virtualbox do | vb | 
      vb.customize ["modifyvm", :id, "--memory", "1024"]
      vb.customize ["modifyvm", :id, "--name", "masternode"]
    end

    # Enable provisioning with chef solo, specifying a cookbooks path, roles
    # path, and data_bags path (all relative to this Vagrantfile), and adding
    # some recipes and/or roles.
    #
    masternode.vm.provision :chef_solo do |chef|
       chef.cookbooks_path = "cookbooks"
       chef.roles_path = "roles"
       chef.data_bags_path = "data_bags"
    #    chef.add_recipe "mysql"
       chef.add_role "base"
    #
    #   # You may also specify custom JSON attributes:
    #   chef.json = { :mysql_password => "foo" }
    end
  end
end
