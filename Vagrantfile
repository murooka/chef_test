# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "chef/centos-6.5"
  config.omnibus.chef_version = :latest
  config.berkshelf.enabled = true

  # config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", "2048"]
  end

  config.vm.define "db1" do |c|
    c.vm.network "private_network", ip: "192.168.10.10"
    c.vm.provision "chef_solo" do |chef|
      chef.run_list = [
        "hello",
        "mysql::server",
        "mysql::client",
      ]
      chef.json = {
        mysql: {
          server_root_password:   "iloverandompasswordsbutthiswilldo",
          server_repl_password:   "iloverandompasswordsbutthiswilldo",
          server_debian_password: "iloverandompasswordsbutthiswilldo",
          bind_address:           "127.0.0.1",
        }
      }
    end
  end

  config.vm.define "db2" do |c|
    c.vm.network "private_network", ip: "192.168.10.11"
    c.vm.provision "chef_solo" do |chef|
      chef.run_list = [
        "hello",
        "mysql::server",
        "mysql::client",
      ]
      chef.json = {
        mysql: {
          server_root_password:   "iloverandompasswordsbutthiswilldo",
          server_repl_password:   "iloverandompasswordsbutthiswilldo",
          server_debian_password: "iloverandompasswordsbutthiswilldo",
          bind_address:           "127.0.0.1",
        }
      }
    end
  end

end
