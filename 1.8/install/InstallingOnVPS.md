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
sudo apt-get install libapache2-modsecurity
sudo apt-get install apache2
sudo apt-get install unzip
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
mv upload/* .
```
# CentOS / Fedora
```
sudo su
cd /
```
Downloading Updates
```
sudo yum update
sudo yum upgrade
sudo yum dist-upgrade
```
Installing Essential Packages
```
sudo yum install build-essential
sudo yum libapache2-modsecurity
sudo yum unzip
sudo yum httpd mod_ssl
```
Installing MySQL
```
sudo yum install mysql-server php5-mysql
```
Install PHP
```
sudo yum install php5 libapache2-mod-php5 php5-mcrypt
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
sudo yum autoremove
```
Enabling Basic Stuff
```
sudo a2enmod rewrite
mv /etc/modsecurity/modsecurity.conf{-recommended,}
```
Rebooing Apache
```
 sudo /usr/sbin/apachectl restart
```
Starting Apache
```
sudo /usr/sbin/apachectl start
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
mv upload/* .
```
---
## Installer

To access the installer you must navigate to the `install/` directory of your site in your web browser. For example, if your domain is example.com and you uploaded your MyBB files to the root directory then navigate to http://example.com/install, or if you uploaded to a `forums/` subdirectory then navigate to http://example.com/forums/install.

### Welcome

If you have successfully uploaded your files and navigated to the installer you should be presented with a page like this:

[![Welcome screen](/assets/images/install/welcome.jpg)](/assets/images/install/welcome.jpg)

All you need to do is click **Next** on this page.

### License Agreement

You must read and agree to the [license agreement](https://www.mybb.com/about/license) before you can install MyBB. You must adhere to the license agreement at all times while the board is installed. After reading the agreement, click the **Next** button on this page.

If you would like more information about the GNU LGPL license and what it means for you [consult the GNU website](https://www.gnu.org/licenses/lgpl.html).

[![License screen](/assets/images/install/license.jpg)](/assets/images/install/license.jpg)

### Requirements Check

This page checks that your server meets the [requirements](/1.8/install/requirements) for running MyBB. If it does not, you will be notified on this page. If everything is working correctly, all you need to do is click on the **Next** button on this page.

[![Requirements screen](/assets/images/install/requirements.jpg)](/assets/images/install/requirements.jpg)

### Database Configuration

This page is for the configuration of your database. If you have javascript enabled, only fields relevant to your selected engine will be displayed. Below is an explanation of each field:

#### Database Engine

This is the engine that you wish to use. At most, the options available will be MySQL, MySQL Improved, SQLite 3, or PgSQL. Most likely, there is only MySQL or something similar, so this should be the right choice for you. If you have the option between MySQL and MySQL Improved, usually the Improved is the better choice.

#### Database Host

This is the server where the database is. Unless told otherwise by your host, this should be localhost. This option is not necessary for SQLite installations.

#### Database Username

This is the username you created or you use to access your database for MyBB. This option is not necessary for SQLite installations.

#### Database Password

This is the password for the database username that you entered. This option is not necessary for SQLite installations.

#### Database Name

This is the name of the database that you would like MyBB to install to. This option is not necessary for SQLite installations.

#### Database Path

This is the path where you want to save the SQLite file. This option is only necessary if you have selected **SQLite 3**.

#### Table Prefix

This is the prefix for the tables in the database. Unless you already have a MyBB installation in the database you entered with the prefix `mybb_`, you should leave this how it is. If you do already have a MyBB installation in the database, you should change it to something else.

Once you have entered the details correctly, you should click on the **Next** button on the page. If the installer cannot access the database, you will be told so, meaning you did not enter one (or more) of the details correctly.

If you are having trouble with this step, contact your web host to see what is the correct host, username, password combination to use. This usually can be found in your host's control panel (eg. cPanel, Ensim, DirectAdmin, Plesk).

[![Database screen](/assets/images/install/database.jpg)](/assets/images/install/database.jpg)

### Table Creation

In this step, the database tables are inserted. No user input is needed on this page, so click the **Next** button when it appears. This page may take several moments to load, so please be patient while it does and inserts the database tables.

[![Table creation screen](/assets/images/install/table.jpg)](/assets/images/install/table.jpg)

### Data Insertion

In this step, the default data is inserted into the database tables created above. No user input is needed on this page, so click the **Next** button when it appears.

[![Data insertion screen](/assets/images/install/populate.jpg)](/assets/images/install/populate.jpg)

### Theme Installation

The theme data is loaded into the forum at this point. No user input is needed on this page, so click the **Next** button when it appears.

[![Theme installation screen](/assets/images/install/theme.jpg)](/assets/images/install/theme.jpg)

### Board Configuration

These are settings that are critical to running your board. MyBB tries to fill these settings with the correct value; however, you should double check to make sure these settings are set properly. These settings can be changed later if required.

#### Forum Name

This is the name of the forums that you are installing. By default, it is **Forums**.

#### Forum URL

This is the URL to your forums. This should be filled in automatically, but it is always good to make sure that the URL is correct. Remember that there should not be a trailing slash.

#### Website Name

This is the name of your website (if you have one). This setting is for the **Your Website** link at the bottom of the forums. The name is simply the text that you wish to use for the your website link.

#### Website URL

This is the URL to your website (if you have one). If you do not have a website, you can either leave it blank or enter your forums URL.

#### Cookie Domain

This is the domain for the cookie to be set to. In 1.4 and later, this field is pre-filled with the appropriate data.

#### Cookie Path

This is the path for the cookie to be set to. If you have more than one MyBB installation on the domain, it is recommended that you change this to the path to your forum (for instance, `/forums/`). In versions 1.4 and later, this field is pre-filled with the appropriate data.

#### Contact Email

This is your email address that your members can contact you by via the **Contact Us** link at the bottom of your forum. This is also the forum webmaster's email that will be used when the forum sends emails.

[![Config screen](/assets/images/install/config.jpg)](/assets/images/install/config.jpg)

### Administrator User

The administrator account is the first account on your forum (identified by the user ID #1). This account has permissions to all sections in the Admin CP.

#### Username

This is the username of the administrator account that you are creating.

#### Password and Retype Password

This is the password for the administrator account. Be sure to type it in correctly in both fields.

#### Email Address

This is the email address that the administrator account will be created with.

[![Admin user screen](/assets/images/install/admin.jpg)](/assets/images/install/admin.jpg)

### Finishing Setup

**Congratulations**! You have successfully installed your MyBB. You should remove the `install/` directory from your server now to prevent anyone else from running the installation again. MyBB will not run unless the installer is removed or locked.

If you simply wish to lock your MyBB install directory, create a new file in the install directory called `lock`, which will disallow access to the installer/upgrader while it exists.

[![Finishing screen](/assets/images/install/finish.jpg)](/assets/images/install/finish.jpg)
