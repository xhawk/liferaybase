# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'rubygems'
#require 'bundler'

#Bundler.require
require 'json'

Vagrant.configure("2") do |config|
  config.vm.box = "gtkliferay"

  config.vm.box_url="http://files.vagrantup.com/lucid64.box"
  config.ssh.forward_agent=true

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "2048"]
    vb.customize ["modifyvm", :id, "--cpus", "2"]
  end
 
 
  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = "cookbooks"
    chef.json = {
        "postgresql" => {
            "password" => {
              "postgres" => "proot"
            }
        }
    }
    # You may also specify custom JSON attributes:
    chef.add_recipe "apt"
    chef.add_recipe "postgresql::server"
    chef.add_recipe "liferay"
  end
  
end
