---
layout:   page
title:    "Backups"
categories: [administration]
---

# Database

From the database backups page, you can easily create backups that are either stored on your server or downloaded to your computer. The database backups listing page shows you all backups that are currently stored on your server, the size of the backup, the time and day of creation, and allows you to download or delete the backup.


- **Database Tables**

  Select the tables you wish to back up. Holding down CTRL lets you select multiple databases, or you can choose to **Select All Tables** **Deselect All Tables** or **Select Forum Tables** (those with the prefix your forum was installed under).

- **File Type**

  You can choose to have the backup compressed in a GZIP file (`.gz`), or as a plain text file (`.txt`).

- **Save Method**

  Would you like to have the backup stored on your server (Backup Directory) or downloaded to your computer (Download)?

- **Backup Contents**

  You can choose to backup the structure and data, just the structure, or just the data. Backing up the structure and data allows you to recreate the database completely, as it is right now. Backing up the structure lets you recreate the structure of your current database, but without any data. Backing up the data lets you insert data into an existing database with the same structure of your current database.

- **Analyze and Optimize Selected Tables**

  While performing the backup, would you like to have the selected tables optimized (as if you were running the **Optimize Database** tool)?

  Once you have made your selections, click on "Perform Backup." If you have selected to store it to your server, you will be provided a link to the backup, while if you have selected to download it, you will be offered to download the backup.


For automatically scheduled backups, see [Task Manager]({{ site.baseurl }}/1.8/administration/task-manager/#weekly-backups).


# Files

The [Directory Structure]({{ site.baseurl }}/1.8/development/directory-structure/), besides MyBB's source code, also contains user-generated content and files related to installed extensions (like themes, plugins, language packs). In most use cases, backups of the following locations should be created for easier recovery.

Whenever the board's functionality is changed (e.g. by MyBB upgrade, installation of a plugin, theme, language pack):
- **images/** (if any extensions added their files),
- **inc/languages/** (if any additional language packs are used),
- **inc/plugins/** (if any plugins are used),
- **inc/config.php** (MyBB configuration file),
- **jscripts/** (if any extensions added their files),

Regularly, for files uploaded by users:
- **uploads/** (user avatars and attachment contents).

MyBB's core files for each version are [available on MyBB.com](https://mybb.com/versions/), and extensions on the [Extend site](https://community.mybb.com/mods.php), code repositories, or other download sources, and thus are not a critical component of backups (unless they contain important custom modifications).
