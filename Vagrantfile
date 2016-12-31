# /your/project/vagrant/Vagrantfile

# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

#Gulp dir
$gulpDir = "/var/www/html/templates/protostar/"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.ssh.insert_key = false

  config.vm.provider :virtualbox do |v|
    v.name = "yii2_test"
    v.memory = 2048
    v.cpus = 2
    # v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--ioapic", "on"]
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
  end

  # config.vm.hostname = "yii2_test.loc"
  config.vm.network :private_network, ip: "192.168.33.45"
  config.vm.synced_folder ".", "/vagrant", type: "rsync",rsync__args: ["--verbose", "--archive", "--delete", "-z"], group: "www-data",owner: "www-data", mount_options: ["dmode=775,fmode=664"]

  # Set the name of the VM. See: http://stackoverflow.com/a/17864388/100134
  config.hostmanager.enabled = true
  name = "yii2_test"
  hostname = "joomla-test.loc"
  
  # config.vm.define name do |yii2_test|
  #   yii2_test.vm.hostname = hostname
  #   yii2_test.vm.provision :shell, inline: "sed -i'' '/^127.0.0.1\\t#{hostname}\\t#{name}$/d' /etc/hosts"
  # end
  

  # Ansible provisioner.
  # config.vm.provision "ansible" do |ansible|
  #   ansible.playbook = "provisioning/playbook.yml"
  #   ansible.inventory_path = "provisioning/inventory"
  #   ansible.sudo = true
  # end
  
  # config.vm.provision "shell", path: "gulpWatch.sh"
  # config.vm.provision "shell", inline: "/vagrant/gulpWatch.sh"
  #config.vm.provision "shell", inline: "cd " + $gulpDir + " && gulp watch"

end

