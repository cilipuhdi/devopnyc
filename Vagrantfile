# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.box_url = "https://vagrantcloud.com/ubuntu/boxes/trusty64"
  config.vm.hostname = "devop.nyc" #attempt to provision vm with puppet "vagrant-centos64.vagrantup.com"
  config.ssh.forward_agent = true
  config.vm.network :private_network, ip: "192.168.86.1"

  config.vm.provision "shell", path: "provisioning/rvm.sh"
  config.vm.provision "shell", path: "provisioning/nvm.sh"

  config.vm.provider :virtualbox do |vb|
    vb.gui = false
    vb.customize ["modifyvm", :id, "--memory", "4096"]
    vb.customize ["modifyvm", :id, "--cpus", "1"] # 2
    vb.auto_nat_dns_proxy = false
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
  end

end
