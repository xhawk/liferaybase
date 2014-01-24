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

  config.vm.network "forwarded_port", guest: 8080, host: 8080

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "2048"]
    vb.customize ["modifyvm", :id, "--cpus", "2"]
  end
 
  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = ["cookbooks", "sitecookbooks"]
    chef.json = {
        "postgresql" => {
            "password" => {
              "postgres" => "proot"
            }
        },
        "liferay" => {
          "download_version" => "liferay-portal-6.1.2-ce-ga3",
          "download_filename" => "liferay-portal-tomcat-6.1.2-ce-ga3-20130816114619181.zip",
          "download_url" => "http://downloads.sourceforge.net/project/lportal/Liferay%20Portal/6.1.2%20GA3/liferay-portal-tomcat-6.1.2-ce-ga3-20130816114619181.zip",
          "tomcat_version" => "tomcat-7.0.40"
        }
    }
    # You may also specify custom JSON attributes:
    # chef.add_recipe "apt"
    # chef.add_recipe "liferayupdate"
    chef.add_recipe "liferay::postgresql"
    chef.add_recipe "liferay"
  end
  
end
