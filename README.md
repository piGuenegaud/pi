# Raspberry PI 3 install and configuration procedures

## First configuration
* modifying background
* modifying appearance
* modifying keyboard and mouse settings
* adding .bash_aliases and aliases
* modifying pi password and hostname in /etc/hostname
* enabling ssh with raspi-config
* creating a google account pi.guenegaud@gmail.com (15gb on google drive)
* sudo apt-get -y update && sudo apt-get -y upgrade
* added github account as piGuenegaud

## Installing LAMP (Apache2, MySQL, PHP5)
Instructions from [StewRight blog](https://www.stewright.me/2012/09/tutorial-install-apache-php-and-mysql-on-raspberry-pi/)
'''bash
sudo apt-get install apache2 apache2-utils apache2-doc
sudo apt-get install libapache2-mod-php5 php5 php-pear php5-xcache
sudo apt-get install php5-mysql
sudo apt-get install mysql-server mysql-client
'''
* setting admin password for mysql as the one on the PI

## Installing phpmyadmin
Instructions from [StewRight blog](https://www.stewright.me/2012/09/tutorial-install-phpmyadmin-on-your-raspberry-pi/)
'''bash
sudo apt-get install phpmyadmin
nano /etc/apache2/apache2.conf add at the end Include /etc/phpmyadmin/apache.conf
'''
* access the web interface with ipadress/phpmyadmin as root

## Installing wordpress
Instructions from [Raspberry PI official website](https://www.raspberrypi.org/learning/lamp-web-server-with-wordpress/worksheet/)
'''bash
sudo wget http://wordpress.org/latest.tar.gz
sudo tar xzf latest.tar.gz
cd wordpress
sudo mysql -uroot -pmyPassword
mysql> create database wordpress;
cd /var/www/html/wordpress
sudo su
chown www-data *
chown www-data */*
chown www-data */*/*
'''
* access the web interface with ipadress/wordpress as root
* copy the file in wp-config.php
* click on "Run the install"
* log as pi, pi.guenegaud@gmail.com

## Installing mediawiki
Instructions from [Trevor Appleton blog](http://trevorappleton.blogspot.fr/2013/04/installing-mediawiki-on-raspberry-pi.html)
'''bash
sudo apt-get install mediawiki
sudo apt-get install php-apc imagemagick
sudo nano /etc/mediawiki/apache.conf and add the alias
sudo apache2ctl restart
'''
* user pi_wiki
* navigate to ipadress/mediawiki, and fill the informations

## Installing phpbb3

## Installig gitlab
'''bash
sudo apt-get install curl openssh-server ca-certificates postfix apt-transport-https
curl https://packages.gitlab.com/gpg.key | sudo apt-key add -
sudo curl -sS https://packages.gitlab.com/install/repositories/gitlab/raspberry-pi2/script.deb.sh | sudo bash
sudo apt-get install gitlab-ce
'''

## Installing owncloud
Instructions from [Raspbian](http://raspbian-france.fr/owncloud-cloud-raspberry-pi/)
sudo apt-get install owncloud
sudo nano /etc/php5/apache2/php.ini
sudo nano /etc/apache2/apache2.conf
sudo /etc/init.d/apache2 restart
mysql -u root -p<votre_password>
create database owncloud;
GRANT ALL PRIVILEGES ON owncloud.* TO pi_cloud@localhost IDENTIFIED BY 'Lolopolo29**';
'''
* connect via ipadress/owncloud

## Troubleshooting
* sudo /etc/init.d/apache2 reload
* sudo /etc/init.d/apache2 restart