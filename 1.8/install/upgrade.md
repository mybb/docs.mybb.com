---
layout: page
title:  "Upgrade"
categories: [install]

redirect_from:
- /Upgrading.html
---

Before you upgrade, you should always read the Release Notes, where the new version's changes will be explained and provide an insight into what additional steps you may need to take.

## Prepare for the Upgrade
### Restrict Access to the Forum
First, you may want to temporarily disable public access to your forum. Doing this means that no one will interrupt the upgrade process accidentally.

This can be achieved by modifying the server configuration:

- **Apache 2.4 servers**

  Add the following code in the `.htaccess` file in the MyBB root directory:

   ```apache
   Require all denied
   Require ip 127.0.0.1
   ```

- **Apache 2.2 servers**

  Add the following code in the `.htaccess` file in the MyBB root directory

   ```apache
   Order deny,allow
   Deny from all
   Allow from 127.0.0.1
   ```

- **Nginx servers**

   Add the following code to server block configuration for the forum:
 
   ```nginx
   location / {
     allow 127.0.0.1;
     deny all;
   }
   ```

Replace `127.0.0.1` with [your IP address](https://icanhazip.com/); if you find yourself unable to access your website during this process, it is possible that you have a dynamic IP, in which case you will have to repeat the above procedure whenever your IP changes.

While you can disable forum access using the _Board Online/Offline_ setting, it is generally recommended to use the method above instead, so that neither the forum nor the installer can be accessed by other people.

### Create a Backup
You should back up your files and database and store them in a safe place. Just in case something goes wrong, you can restore the backup and start again. You can back up the database using the [MyBB Admin CP or your database management software](/1.8/administration/backups).

### Disable Plugins
It's recommended to temporarily disable all plugins for the duration of the upgrade. This is because they may need to be updated to work on the new version, and can cause problems if left active during the process. You can disable your plugins by going to the Admin CP's _Configuration → Settings → Board Settings → General Configuration_ and changing **Disable All Plugins** to _Yes_.

## Apply the New Version
### Download the Package
Whichever version your forum is running on, you should always use [the latest version](https://www.mybb.com/download/) to upgrade.

The Release Notes accompanying the release may include two packages:
- **Full Package** — upgrading from older versions

  This is the main package that allows users to either install or upgrade their board from any previous version.
  
  If your current version is more than one point below the newest version, you need to use the _Full Package_. For example, if you're using 1.6.1 and the newest version is 1.6.4, then you need a full upgrade. The same applies if you're using 1.6.x and you're upgrading to the new series 1.8.x.

  Files intended for upload are located in the `Upload/` directory.

- **Changed Files** — upgrading from the previous version

  Alternatively, if you're just one point behind the newest version — for example, if you're using 1.6.3 and the newest version is 1.6.4 — then you can use the _Changed Files_ package. This package does not include files that were left unchanged, and thus may be faster to upload.
  
  All files in the archive are intended for upload.
  
### Upload New Files
Select all files and directories intended for upload from the new package, and copy them to the main forum directory, overwriting existing files.

For added security, if the package includes an `install/` directory, you may choose to upload its content to a directory with an unguessable random name instead, and use that name in the following steps. This applies especially if you chose not to add an IP address restriction.

### Run the Installation
After uploading and overwriting the files, MyBB may ask you to run the upgrade, or remove the unnecessary installation directory, depending on whether running the upgrade script is required.

- If the Release Notes mention that running the **upgrade script** is required:

  1. Open the upgrade system by appending `/install/upgrade.php` to your forum's URL in your browser (`example.com/install/upgrade.php`).
  
     - You may be asked to remove the `install/lock` file, which can be done using an FTP client or a File Manager.

     - You may be asked to log in again as an administrator in order to run the upgrade.

  3. Select your _old version_ of MyBB version in the drop down list and proceed.
  
     If your MyBB version is higher than all versions on the list, you might not need to run the upgrade system.

  4. Follow the instructions to run the upgrade.

  5. After the upgrade has finished successfully, you can safely delete the `install/` directory.

- If you're upgrading from the previous version, and the Release Notes instruct to **copy and overwrite files** only, you can safely delete the `install/` directory (if it exists).

After this process, your forum should be running on the new version of MyBB.

### Run File Verification
To make sure that all files have been copied correctly, run the Admin CP's _Tools & Maintenance → File Verification_ tool. Missing or modified files can be replaced by overwriting them using the original package.

### Update & Restore Extensions
Some plugins, themes, language packs may be incompatible with the new version and may need to be updated. It's recommended to check for related announcements from their authors.

- #### Plugins
  To check for plugin updates using the Admin CP, go to _Configuration → Plugins → Plugin Updates_.

  If you deactivated plugins prior to the update, you can reactivate them again. If you used the setting, go to the Admin CP's _Configuration → Settings → Board Settings → General Configuration_ and change **Disable All Plugins** to _No_ and make sure they work correctly.

- #### Themes
  If the Release Notes mention that there are theme changes, go to _Admin CP → Templates & Style → Templates → Find Updated Templates_. This will show you a list of all the templates that have changed during the upgrade, but require manual intervention.

  The _Diff Report_ which will show you exactly what's changed. You can also use the [GitHub compare tool](https://github.com/mybb/mybb/compare/mybb_1820...mybb_1821) to show changes to the _Default_ theme file (`install/resources/mybb_theme.xml`) between chosen MyBB versions, and apply similar changes to your themes.

  The _Revert to Original_ option will replace the template content with the MyBB Default theme's version. This may break custom themes and remove manual changes that were previously made.

  If you have a custom theme installed, you can check for its update announcements, or attempt to apply required changes using the Diff Report.

- #### Translations
  If the Release Notes that there are language changes: and you've installed a custom language pack, check to see if the language pack you're using has already been updated on [Extend MyBB](https://community.mybb.com/mods.php) or in the [Translation Releases Forum](https://community.mybb.com/forum-169.html). Download and install any updates you need.

  If you have made customisations to the packs yourself, or you manage a language pack for MyBB, then read through the Release Notes for a list of changes to the language packs and apply the changes as necessary. You can use the [GitHub compare tool](https://github.com/mybb/mybb/compare/mybb_1820...mybb_1821) to show changes to English language files (`inc/languages/english/`) between chosen MyBB versions, and apply similar changes to your languages.

## Finish the Upgrade
### Verify Forum Functionality
Ensure that your forum functions correct and it looks the way it's supposed to look! Take your time don't rush it.

### Restore Access to the Forum
If you added IP address restrictions or closed the board earlier using the _Board Online/Offline_ setting, you can now revert these changes to restore public access. 

### Conclusion
If you run into any problems at any point of the upgrade process, visit the Community Forums' [Installation and Upgrades Support](https://community.mybb.com/forum-182.html) for help.

Otherwise, *congratulations*! You've just upgraded your forum!

### Useful links
- [How to use File Manager in cPanel](https://documentation.cpanel.net/display/74Docs/File+Manager)
- [Subscribe for new version notifications](https://mybb.com/download/verifying/)
