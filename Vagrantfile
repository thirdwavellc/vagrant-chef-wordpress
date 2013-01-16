# -*- mode: ruby -*-
# vi: set ft=ruby :

chefserver = "http://chef.thirdwave.local:4000"
home = File.expand_path("~")
user = ENV["USER"]
dir = File.basename(Dir.getwd)
node = "#{user}-wordpress-#{dir}"

Vagrant::Config.run do |config|

  config.vm.box = "precise64"

  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.vm.forward_port 80, 8080

  config.vm.provision :chef_client do |chef|

    chef.chef_server_url = chefserver
    chef.validation_key_path = "#{home}/.chef/validation.pem"
    chef.node_name = node
    chef.environment = "vagrant"
    chef.add_role "wordpress"

  end

end
