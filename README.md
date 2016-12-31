# Vagrant Host: Archlinux, Guest: Ubuntu

Host:

	1. yaourt -S virtualbox
		#(virtualbox-host-modules-arch)
	
	2. yaourt -S vagrant openssh rsync

	3. vagrant plugin install vagrant-hostmanager

	4. vim Vagrantfile
	
	5. vagrant up && vagrant ssh

Guest:

	1. install LAMP

		Server:

			Apache
			    sudo apt-get install apache2 libapache2-mod-php5

			(or)

			NGINX
			    sudo apt-get install nginx

			NGINX doesn’t start on its own, so:
			    sudo service nginx start

		MySQL:
			  sudo apt-get install mysql-server mysql-client

		PHP:

			PHP 5
			    sudo apt-get install python-software-properties
			    sudo add-apt-repository ppa:ondrej/php5-oldstable
			    sudo apt-get update
			    sudo apt-get install php5 php5-gd php5-mysql php5-curl php5-cli php5-cgi php5-dev php5-fpm

			(or)

			PHP 7.0 (prior to Ubuntu 16.04)
			    sudo apt-get install python-software-properties
			    sudo LC_ALL=en_US.UTF-8 add-apt-repository ppa:ondrej/php
			    sudo apt-get update
			    sudo apt-get install php7.0 php7.0-fpm php7.0-mysql -y

		phpMyAdmin:
		  	  sudo apt-get install phpmyadmin

	2. Config system

		www symlink:
			  sudo mv /var/www/html /var/www/html_default
			  sudo ln -s /vagrant/www/html /var/www/html

		phpMyAdmin:
			  sudo ln -s /usr/share/phpmyadmin/ /var/www/html

		apache & mod_rewrite
			  sudo vim /etc/apache2/apache2.conf

			  #change
			    AllowOverride All

			  #<Directory /var/www/>
			  #  Options Indexes FollowSymLinks
			  #  AllowOverride All
			  #  Require all granted
			  #</Directory>

			  sudo a2enmod rewrite

		restart apache
			  sudo service apache2 restart
