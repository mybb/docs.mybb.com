---
layout: page
title:  "Upgrade"
categories: [install]

redirect_from:
- /Upgrading.html
---

## Preparing for your Upgrade

Before you upgrade, you should always read the announcement blog post properly before starting. The new version's changes will clearly be explained and provide an insight into how difficult the upgrade will be.

1. First, you may want to shut down your forum. Doing this means that no one will interrupt the upgrade process accidentally. Please remember that switching the forum off by using the **Board Online/Offline** setting is **not** recommended. The best method is to use a `.htaccess` restriction on your forum's root folder so that no one can access the front-end. 

To restrict access to your forum except from your IP address, you need to place the following code in your root `.htaccess` file if you're using apache or in the server block of your site's config file if you're using nginx. Replace `127.0.0.1` with [your IP address](https://icanhazip.com/).

Apache 2.2:

```
Order deny,allow
Deny from all
Allow from 127.0.0.1
```

Apache 2.4:

```
Require all denied
Require ip 127.0.0.1
```

Nginx:

```
location / {
    allow 127.0.0.1;
    deny  all;
}
```

If you find yourself unable to access your website during this process, it is possible that you have a dynamic IP, in which case you will have to repeat the above procedure whenever your IP changes.

2. Secondly, you should back up your files and database and store them in a safe place. Just in case something goes wrong, you can restore the backup and start again. You can back up the database using the [MyBB Admin CP or your database management software](/1.8/administration/backups).

3. You must deactivate (or disable) all of your plugins. This is because it is likely they will need to be updated to work on the new version and can cause problems if they are left active.  You can deactivate (or disable) your plugins by going to  **Admin CP > Board Settings > General Configuration** and changing "Disable All Plugins" to Yes.

### Downloading the Correct Upgrade Package

There are two different methods of upgrading your forum: full upgrades and a changed files upgrade.

#### Full Upgrade

If your current version is more than one point below the newest version, you need to make a full upgrade. For example, if you're using 1.6.1 and the newest version is 1.6.4, then you need a full upgrade. The same applies if you're using 1.6.x and you're upgrading to 1.8.x. You need to use the latest version of the software.

[Download the latest version](https://www.mybb.com/download/).

#### Changed Files Upgrade

If you're just one point behind the newest version - for example, if you're using 1.6.3 and the newest version is 1.6.4 - then you can use the changed files package. This is available in the blog post announcement. If a changed files package is not available then the latest version of the software should be used.

## Beginning the Upgrade

Once you've downloaded the correct upgrade package for you, it's time to do the upgrade. Please follow these steps carefully.

1. Upload **all** of the files and folders inside the package (from inside the `Upload/` folder if using the full package), including the `install/` folder (if it exists), overwriting the existing copies of the files in your file system.

2. If the blog post announcement mentions that the upgrade script **is** required, then perform the following:

	1. Open your forum's home page in your web browser and add `/install/` to the URL. For example, `www.yourdomain.com/install/` or `www.yourdomain.com/forum/install/`.

	2. It might ask you to remove a file called `lock` in this folder. Use an FTP Client or a File Manager to remove the `install/lock` file.

	3. You should see a drop down list asking what version of MyBB you're upgrading from. Remember to select the correct version - the one you're currently using - or else the upgrade will not work correctly.

	4. Follow the instructions to run the upgrade.

	5. After the upgrade has finished, check that the file called `lock` was created in the `install/` folder. If it is missing, create it yourself or delete the `install/` folder from your server. For extra protection, `chmod 644 inc/config.php`.

3. If the blog post announcement mentions that there are theme changes, then perform the following:

	1. Go to **Admin CP > Templates & Style > Templates > Find Updated Templates**. This will show you a list of all the templates that have changed during the upgrade.

	2. You can either revert these templates to their default - meaning all the changes you've made to it will be removed - or you can see a **Diff Report** which will show you exactly what's changed. If you have a custom theme installed, it is probably best that you look at the Diff Report and apply the changes you need.

4. If the blog post announcement mentions that there are language changes and you've either customised your English language pack (the default pack) or installed a custom language pack, then perform the following:

	1. Check to see if the language pack you're using has already been updated in the [Translation Releases Forum](https://community.mybb.com/forum-169.html). Download and install any updates you need.

	2. If you have made customisations to the packs yourself, or you manage a language pack for MyBB, then read through the blog post announcement for a list of changes to the language packs and apply the changes as necessary.

5. The upgrade process should now be complete! You may want to re-open your forum by removing the `.htaccess` block or turning your forum on again. Before you do this, ensure that your forum functions correct and it looks the way it's supposed to look! Take your time don't rush it.

## Conclusion

If you run into any problems at any point of the upgrade process, visit the [Community Forum](https://community.mybb.com/) for help.

Otherwise, *congratulations*! You've just upgraded your forum!
