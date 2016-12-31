# /your/project/vagrant/Vagrantfile

# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

#$gulpDir = "/var/www/html/lib/"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.ssh.insert_key = false

  config.vm.provider :virtualbox do |v|
    v.name = "yii2_test"
    v.memory = 2048
    v.cpus = 2
    v.customize ["modifyvm", :id, "--ioapic", "on"]
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
  end

  # config.vm.hostname = "site-test.loc"
  config.vm.network :private_network, ip: "192.168.33.45"
  config.vm.synced_folder ".", "/vagrant", type: "rsync",rsync__args: ["--verbose", "--archive", "--delete", "-z"], group: "www-data",owner: "www-data", mount_options: ["dmode=775,fmode=664"]

  config.hostmanager.enabled = true
  name = "site-test"
  hostname = "site-test.loc"
  
  
  # config.vm.provision "shell", path: "gulpWatch.sh"
  # config.vm.provision "shell", inline: "/vagrant/gulpWatch.sh"
  #config.vm.provision "shell", inline: "cd " + $gulpDir + " && gulp watch"

end

