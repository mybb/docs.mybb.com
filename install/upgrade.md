---
layout: page
title:  "Ugrade MyBB"
---

## Upgrading

### The Upgrade Process

As with any software, there are various different types of upgrades. They vary in size, difficulty and the type of changes being made.

With MyBB, we follow a sequenced-based version scheme to describe the changes we've made.

##### Major Point Upgrades

A major upgrade is where the version number changes. For example, going from version 1.x to 2.x. This type of change means that plugins, themes and language packs will need major changes to work on the new version.

##### Minor Point Upgrades

This type of updates means the minor number of the version changes. For example, going from version 1.4.x to 1.6.x. This type of change might require some changes to plugins, themes and language packs.

##### Maintenance Point Upgrades

The maintenance upgrade makes small changes, mostly bug fixes, to the minor point versions. These can also be security upgrades. As an example, going from version 1.6.2 to 1.6.3 or 1.6.1 to 1.6.4 is a maintenance point upgrade. These changes are meant to make the new version more stable than the last. It is very unlikely that any changes to plugins are needed, but language packs or themes may need to be updated.

### Preparing for your Upgrade

Before you upgrade, you should always read the announcement blog post properly before starting. The new version's changes will clearly be explained and provide an insight into how difficult the upgrade will be.

1. First, you may want to shut down your forum. Doing this means that no one will interrupt the upgrade process accidentally. Please remember that switching the forum by using the **Board Online/Offline** setting **IS NOT** recommended. The best method is to use a `.htaccess` restriction on your forum's root folder so that no one can access the front end. There are various tutorials on search engines that help you do this and some hosts (especially ones that give you cPanel) provide simple tools to do this.

2. Secondly, you should back up your files and database and store them in a safe place. Just in case something goes wrong, you can restore the backup and start again. You can back up the database using the [MyBB Admin CP or your database management software](../administration/backups).

3. If you are upgrading to a major or minor point, you must deactivate (or disable) all of your plugins. This is because it is likely they will need to be updated to work on the new version and can cause problems if they are left active. You may also want to deactivate or disable all of your plugins for maintenance upgrades too, but it is not usually required.
      
##### Downloading the correct upgrade package

There are two different methods of upgrading your forum, full upgrades and a changed files upgrade.

#### Full Upgrade

If your current version is more than one point below the newest version, you need to make a full upgrade. For example, if you're using 1.6.1 and the newest version is 1.6.4, then you need a full upgrade. The same applies if you're using 1.4.x and you're upgrading to 1.6. You need use the latest version of the software.

[Download the latest version](http://mybb.com/download/latest)

**Changed Files Upgrade**

If you're just one point behind the newest version - for example, you're using 1.6.3 and the newest version is 1.6.4 - then you can use the changed files package. This is available in the blog post announcement. If a changed files package is not available then the latest version of the software should be used.

##### Beginning the Upgrade

Once you've downloaded the correct upgrade package for you, it's time to do the upgrade. Please follow these steps carefully.

1. Upload **all** of the files and folders inside the package (from inside the `Upload/` folder if using the latest version/full package), including the `install/` folder (if it exists), overwriting the existing copies of the files in your file system.

2. If the blog post announcement mentions that the upgrade script **is** required, then perform the following:

	1. Open your forum's home page in your web browser and add /install/ to the URL. For example, `www.yourdomain.com/install/` or `www.yourdomain.com/forum/install/`.

	2. It might ask you to remove a file called `lock` in this folder. Use an [FTP Client](ftp) or a File Manager to remove the `install/lock` file.

	3. You should see a drop down list asking what version of MyBB you're upgrading from. Remember to select the correct version - the one you're currently using - or else the upgrade will not work correctly.

	4. Follow the instructions to run the upgrade.

	5. After the upgrade has finished, check that the file called `lock` was created in the `install/` folder. If it is missing, create it yourself or delete the `install/` folder from your server. For extra protection, CHMOD `inc/config.php` to 644 if it isn't already.

3. If the blog post announcement mentions that there are theme changes, then perform the following:

	1. Visit your Admin Control Panel, then go to **Templates & Style > Templates > Find Updated Templates**. This will show you a list of all the templates that have changed during the upgrade.

	2. You can either revert these templates to their default - meaning all the changes you've made to it will be removed - or you can see a Diff Report which will show you exactly what's changed. If you have a **custom theme** installed, it is probably best that you look at the **Diff Report** and apply the changes you need.

4. If the blog post announcement mentions that there are language changes and you've either customised your English language pack (the default pack) or installed a custom language pack, then perform the following:

	1. Check to see if the language pack you're using has already been updated in the [Translation Releases Forum](http://community.mybb.com/forum-169.html). Download and install any updates you need.

	2. If you have made customisations to the packs yourself, or you manage a language pack for MyBB, then read through the blog post announcement for a list of changes to the language packs and apply the changes as necessary.

5. The upgrade process should now be complete! You may want to re-open your forum by removing the `.htaccess` block or turning your forum on again. Before you do this, ensure that your forum functions correct and it looks the way it's supposed to look! Take your time don't rush it.

### Help and Support

If you run into any problems at any point of the upgrade process, visit the [Community Forum](http://community.mybb.com/) and post a thread in the [Support area](http://community.mybb.com/forum-124.html). Our Support Team will try their best to provide help as fast as they can, but please note they are extremely busy when there is a new release. Remember to take screenshots if you can and include them in your new thread, and be as detailed as possible when writing your post.

Otherwise, *congratulations*! You've just upgraded your forum!