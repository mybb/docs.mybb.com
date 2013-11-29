---
layout: page
title:  "Install MyBB"
---

Thanks for choosing MyBB as the discussion board software for your community. You are only steps away from completing the installation of your new forum. We've broken down the installation into many smaller steps, as you can see on the navigation bar on the right. Don't worry if it looks daunting; if you need any help, just post a thread in one of our [Support Forums](http://community.mybb.com/) for the version you are running, and we will help you out.

* MyBB comes with the [features](http://www.mybb.com/features) that one would expect from a bulletin board software, as well as some unique features not found elsewhere.
* Having trouble with MyBB? The support at the [MyBB Community Forums](http://community.mybb.com/) is free and available to anyone using MyBB, supported by the [volunteer team](/developers), and other members of the community!
* MyBB is easily customizable to suit your site's needs and looks.
* Best of all, MyBB is [released under the GNU Lesser GPL licence](http://www.mybb.com/about/license), and therefore it's [entirely free](http://www.gnu.org/philosophy/free-sw.html)! No forced advertisements, no cost, no sign-ups, no forced email subscriptions!
* You will require a web host to run your forum
* Your web host must satisfy a few basic requirements for MyBB to run properly.

## Preparation

### Downloading the MyBB files

1. First, download the latest MyBB package from the [MyBB downloads page](http://www.mybb.com/downloads)
2. After downloading the zip file, unzip/decompress the file.
    * On Windows you can either use the [built in utility](http://windows.microsoft.com/en-au/windows-vista/compress-and-uncompress-files-zip-files) or an application such as [7-zip](http://www.7-zip.org/)
    * On *nix systems you can run `unzip mybb-package-name.zip`

### Uploading files

In the archive you extracted earlier there will be two directories: Documentation and Upload. The Documentation directory contains useful information, however you need not upload it to your server.

Next, you will need to upload the **contents** of the **Upload** directory to either your website root directory (sometimes called www, htdocs or httpdocs), or a subdirectory of of your root directory (such as <root>/forums or <root>/community).

The process of uploading your files will depend on your hosting configuration, but FTP is the most common method. [FIleZilla is a free FTP client](https://wiki.filezilla-project.org/FileZilla_Client_Tutorial_%28en%29) suitable for uploading MyBB.

### File permissions

Certain file permissions are required for MyBB to function correctly. Once you've uploaded your files you will need to set the permissions on certain files and directories.

** Before applying file permissions, rename config.default.php to config.php

#### *nix systems via CHMOD

On Linux, Unix and similar systems the following permissions should be applied:

* `inc/config.php` : 666
* `inc/settings.php` : 666
* `cache/` : 777
* `cache/themes/` : 777
* `uploads/` : 777
* `uploads/avatars` : 777

The following permissions may optionally be applied:

* `admin/backups` : 777
* `inc/languages/english/*` : 666
* `inc/languages/english/admin/*` : 666

If you have SSH access, these permissions can be applied via the following command, executed from your root MyBB directory:

```sh
chmod 666 inc/config.php inc/settings.php
chmod 777 cache cache/themes uploads uploads/avatars
```

And for optional permissions:

```sh
chmod 666 inc/languages/english/*.php inc/languages/english/admin/*.php
chmod 777 cache cache/themes uploads uploads/avatars admin/backups
```

If you are using FileZilla you can right click on a file or directory and click File Attributes to modify the permissions of that object.

#### Windows systems

On Windows systems you will need to follow [these instructions](http://technet.microsoft.com/en-us/library/bb727008.aspx). In general the files and directories listed above require "Full modify" permissions.

## Installer

To access the installer you must navigate to the `/install` directory of your site in your web browser. For example, if your domain is example.com and you uploaded your MyBB files to the root directory then navigate to `http://example.com/install`, or if you uploaded to a `/forums` subdirectory then navigate to `http://example.com/forums/install`.

### Welcome

If you have successfully uploaded your files and navigated to the installer you should be presented with a page like this:

[![Welcome screen](/assets/images/install/welcome.jpg)](/assets/images/install/welcome.jpg)

All you need to do is click **Next** on this page.

### License Agreement

You must read and agree to the [license agreement](http://www.mybb.com/about/license) before you can install MyBB. You must adhere to the license agreement at all times while the board is installed. After reading the agreement, click the "Next" button on this page.

If you would like more information about the GNU LGPL license and what it means for you [consult the GNU website](http://www.gnu.org/licenses/lgpl.html).

[![License screen](/assets/images/install/license.jpg)](/assets/images/install/license.jpg)

### Requirements Check

This page checks that your server meets the [requirements](/install/requirements) for running MyBB. If it does not, you will be notified on this page. If everything is working correctly, all you need to do is click on the "Next" button on this page.

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
This is the path where you want to save the SQLite file. This option is only necessary if you have selected 'SQLite 3'

#### Table Prefix
This is the prefix for the tables in the database. Unless you already have a MyBB installation in the database you entered with the prefix mybb_, you should leave this how it is. If you do already have a MyBB installation in the database, you should change it to something else.

Once you have entered the details correctly, you should click on the "Next" button on the page. If the installer cannot access the database, you will be told so, meaning you did not enter one (or more) of the details correctly.

If you are having trouble with this step, contact your web host to see what is the correct host/username/password to use. This usually can be found in your host's control panel (eg. cPanel, Ensim, DirectAdmin, Plesk) or by contacting your web host's support.

[![Database screen](/assets/images/install/database.jpg)](/assets/images/install/database.jpg)

### Table Creation

In this step, the database tables are inserted. No user input is needed on this page, so click the "Next" button when it appears. This page may take several moments to load, so please be patient while it does and inserts the database tables.

[![Table creation screen](/assets/images/install/table.jpg)](/assets/images/install/table.jpg)

### Data Insertion

In this step, the default data is inserted into the database tables created above. No user input is needed on this page, so click the "Next" button when it appears.

[![Data insertion screen](/assets/images/install/populate.jpg)](/assets/images/install/populate.jpg)

### Theme Installation

The theme data is loaded into the forum at this point. No user input is needed on this page, so click the "Next" button when it appears.

[![Theme installation screen](/assets/images/install/theme.jpg)](/assets/images/install/theme.jpg)

### Board Configuration

These are settings that are critical to running your board. MyBB tries to fill these settings with the correct value; however, you should double check to make sure these settings are set properly. These settings can be changed later if required.

#### Forum Name
This is the name of the forums that you are installing. By default, it is "Forums"

#### Forum URL
This is the URL to your forums. This should be filled in automatically, but it is always good to make sure that the URL is correct. Remember that there should not be a trailing slash

#### Website Name
This is the name of your website (if you have one). This setting is for the "Your Website" link at the bottom of the forums. The name is simply the text that you wish to use for the your website link.

#### Website URL
This is the URL to your website (if you have one). If you do not have a website, you can either leave it blank or enter your forums URL.

#### Cookie Domain
This is the domain for the cookie to be set to. In versions 1.4 and later, this field is pre-filled with the appropriate data. (See Cookies)

#### Cookie Path
This is the path for the cookie to be set to. If you have more than one MyBB installation on the domain, it is recommended that you change this to the path to your forum (for instance, /forums/). In versions 1.4 and later, this field is pre-filled with the appropriate data. (See Cookies)

#### Contact Email
This is your email address that your members can contact you by via the "Contact Us" link at the bottom of your forum. This is also the forum webmaster's email that will be used when the forum sends emails.

[![Config screen](/assets/images/install/config.jpg)](/assets/images/install/config.jpg)

### Administrator User

The administrator account is the first account on your forum (identified by the user ID #1). This account has permissions to all sections in the Admin Control Panel.

#### Username
This is the username of the administrator account that you are creating.

#### Password and Retype Password
This is the password for the administrator account. Be sure to type it in correctly in both fields.

#### Email Address
This is the email address that the administrator account will be created with.

[![Admin user screen](/assets/images/install/admin.jpg)](/assets/images/install/admin.jpg)

### Finishing Setup

**Congratulations**! If you have reached this page, then you have successfully installed your MyBB. You should remove the /install/ directory from your server now, to prevent anyone else from running the installation again. MyBB will not run unless the installer is locked, or removed.

If you simply wish to lock your MyBB install directory, simply create a new file in the install directory called **lock**, which will disallow access to the installer/upgrader while it exists.

[![Finishing screen](/assets/images/install/finish.jpg)](/assets/images/install/finish.jpg)

## Other Information

### Installation via SSH

If you have SSH access on your *nix server you may prefer to use one of the following methods which will allow you to skip the preparation steps mentioned above.

Requirements:

* access - Command Line Access to the Server
* wget, aria2 (version >= 1.9.3), curl, or lynx - Command used, depends on which you choose. These should be present or installable on any *NIX (Linux, UNIX, or Mac) based server
* unzip, mv, rm, and chmod - These are all required, and should all be present already on any *NIX based server

wget:

```sh
wget --content-disposition http://www.mybb.com/download/latest -O mybb.zip
unzip mybb.zip "Upload/*"
mv Upload/* .
rm -Rf Upload mybb.zip
mv inc/config.default.php inc/config.php
chmod -R 0777 cache uploads inc/settings.php inc/config.php
```

aria2c

```sh
aria2c http://www.mybb.com/download/latest -o mybb.zip
unzip mybb.zip "Upload/*"
mv Upload/* .
rm -Rf Upload mybb.zip
mv inc/config.default.php inc/config.php
chmod -R 0777 cache uploads inc/settings.php inc/config.php
```

curl

```sh
curl http://www.mybb.com/download/latest -o mybb.zip
unzip mybb.zip "Upload/*"
mv Upload/* .
rm -Rf Upload mybb.zip
mv inc/config.default.php inc/config.php
chmod -R 0777 cache uploads inc/settings.php inc/config.php
```

lynx

```sh
lynx -crawl -dump http://www.mybb.com/download/latest > mybb.zip
unzip mybb.zip "Upload/*"
mv Upload/* .
rm -Rf Upload mybb.zip
mv inc/config.default.php inc/config.php
chmod -R 0777 cache uploads inc/settings.php inc/config.php
```