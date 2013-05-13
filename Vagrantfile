# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "precise64"

  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.vm.network :forwarded_port, guest:80, host: 8080

  config.vm.provider "virtualbox" do |vb|
    vb.name = "Wordpress"
  end

  config.berkshelf.enabled = true

  config.vm.provision :chef_solo do |chef|
    chef.add_recipe "apt"
    chef.add_recipe "build-essential"
    chef.add_recipe "openssl"
    chef.add_recipe "apache2"
    chef.add_recipe "php"
    chef.add_recipe "mysql"
    chef.add_recipe "wordpress"

    chef.json = {
      :mysql => {
        :server_debian_password => "wordpress",
        :server_root_password => "wordpress",
        :server_repl_password => "wordpress"
      }
    }
  end

end
