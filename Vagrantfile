# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "opscode-precise64-provisionerless"

  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.vm.network :forwarded_port, guest:80, host: 8080

  config.vm.synced_folder "./", "/var/www/wordpress",
    owner: "www-data", group: "www-data"

  config.vm.provider "virtualbox" do |vb|
    vb.name = "Wordpress"
  end

  config.berkshelf.enabled = true
  config.omnibus.chef_version = :latest

  config.vm.provision :chef_solo do |chef|
    chef.add_recipe "apt"
    chef.add_recipe "wordpress"

    chef.json = {
      :mysql => {
        :server_debian_password => "wordpress",
        :server_root_password => "wordpress",
        :server_repl_password => "wordpress"
      },
      :wordpress => {
        :owner => "www-data",
        :group => "www-data"
      }
    }
  end
end
