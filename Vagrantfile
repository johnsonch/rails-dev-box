# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure('2') do |config|
  config.vm.box      = 'hashicorp/precise64'
  config.vm.hostname = 'rails-dev-box'


  config.vm.provider :virtualbox do |v|
    v.customize ["modifyvm", :id,
                 "--name", 'rails-dev-box',
                 "--memory", "512",
                 "--nictype1", "Am79C973",
                 "--nictype2", "Am79C973",
                 "--natdnshostresolver1", "on"]
  end

  config.vm.network :forwarded_port, guest: 3000, host: 3000

  config.vm.synced_folder "../", "/home/vagrant/development", :nfs => true

  config.vm.provision :puppet do |puppet|
    puppet.manifests_path = 'puppet/manifests'
    puppet.module_path    = 'puppet/modules'
  end
end
