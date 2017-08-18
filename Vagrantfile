# -*- mode: ruby -*-
# vi: set ft=ruby :

#SERÁ GERADO PELO SELENIUM_PROC

VAGRANT_FILE_VERSION = 2

Vagrant.configure(VAGRANT_FILE_VERSION) do |config|

  config.vm.box        = 'ebrc/centos-7-64-puppet'

  config.ssh.username  = 'vagrant'
  config.ssh.password  = 'vagrant'
  config.ssh.insert_key = 'true'

  config.vm.provider :virtualbox do |virtualbox|
    virtualbox.customize ["modifyvm", :id, "--cpus", "1"]
    virtualbox.customize ["modifyvm", :id, "--memory", "1096"]
  end

  config.vm.define :selenium_gocd do |selenium_gocd|
	  selenium_gocd.vm.network "private_network", ip: "192.168.70.107"
	  selenium_gocd.vm.network "forwarded_port", guest:8153, host: 8153
  end

  config.vm.provision "puppet" do |puppet|
  	puppet.environment_path = "environments"
  	puppet.environment 	= "development"
 	  puppet.module_path      = "puppet/modules"
  end
end
