# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|

  config.vm.box = "precise64"

  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.vm.forward_port 80, 8080

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = "cookbooks"

    chef.add_recipe "apt"
    chef.add_recipe "build-essential"
    chef.add_recipe "openssl"
    chef.add_recipe "wordpress"

    chef.json = {
      "mysql" => {
        "server_debian_password" => "wordpress",
        "server_root_password" => "wordpress",
        "server_repl_password" => "wordpress"
      }
    }

  end

end
