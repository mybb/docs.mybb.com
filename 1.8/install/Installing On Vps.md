# Debian / Ubuntu
```
sudo su
cd /
```
Downloading Updates
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
Installing Essential Packages
```
sudo apt-get install build-essential
apt-get install libapache2-modsecurity
apt-get install unzip
```
Installing MySQL
```
sudo apt-get install mysql-server php5-mysql
```
Install PHP
```
sudo apt-get install php5 libapache2-mod-php5 php5-mcrypt
```
Configure MySQL
```
sudo mysql_install_db
```
MySQL Installation
```
sudo mysql_secure_installation
```
Database 
```
mysql -u root -p
CREATE DATABASE NAME-YOUR-DB;
CREATE USER 'YOUR-DB-USER'@'localhost' IDENTIFIED BY 'YOUR-DB-USER-PASSWORD';
GRANT ALL PRIVILEGES ON NAME-YOUR-DB.* TO 'YOUR-DB-USER'@'localhost' IDENTIFIED BY 'YOUR-DB-USER-PASSWORD';
FLUSH PRIVILEGES;
exit
```
Cleanup
```
sudo apt-get autoremove
```
Enabling Basic Stuff
```
sudo a2enmod rewrite
mv /etc/modsecurity/modsecurity.conf{-recommended,}
```
Rebooing Apache
```
service apache2 restart
```
Changing Directories
```
cd var/www/html
rm index.html
```
Downloading MyBB
```
wget https://www.mybb.com/download/latest -o mybb.zip
unzip mybb.zip
mv mybb_VERSON_NUMBER
rm -rf mybb_VERSON_NUMBER
```
# CentOS / Red Hat Enterprise Linux
soon
# Fedora
soon
