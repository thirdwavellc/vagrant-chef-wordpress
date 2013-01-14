# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|

  config.vm.box = "precise64"

  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.vm.forward_port 80, 8080

  config.vm.provision :chef_client do |chef|

    user = ENV["USER"]
    dir = File.basename(Dir.getwd)
    
    chef.chef_server_url = "http://10.120.50.16:4000"
    chef.validation_key_path = "~/.chef/validation.pem"
    chef.node_name = "#{user}-wordpress-#{dir}"
    chef.environment = "vagrant"
    chef.add_role "wordpress"

  end

end
