---
layout: page
title: "Moving to a New Web Host"
categories: [faq]
description: "Guide on moving your MyBB installation to a new web host."
---

This guide will explain the general process to move your MyBB installation to a new web host with minimal complications or downtime. Thank you to [Inferno](https://community.mybb.com/user-12365.html) of the MyBB Community Forums for creating [the thread](https://community.mybb.com/thread-27771.html) that aided in the creation of this guide.

There are three main "sections" of the migration process: backups/export of data, uploading of data to the new host, and domain transfer.

If you encounter issues with following this transfer process, [create a support thread in the MyBB Community Forums](https://community.mybb.com/newthread.php?fid=176) or contact your new web host for assistance (and link them to this documentation!).

# Backup/Export Data

1. Log into your MyBB Admin Control Panel, and disable all plugins by navigating to `Configuration` and setting `Disable All Plugins` to `Yes`.

2. Close your forum by navigating to `Configuration`, `Board Online / Offline`, and setting the board to closed. This will ensure that the data you export in the next step is the latest and that no activity is lost in the transfer to the new host.

3. Export your database by navigating to the `Tools & Maintenance` section, `Backup Database`, `New Backup`. `Select All` tables, check `GZIP Compressed`, `Download`, `Structure and Data`, and `Analyze and Optimize Selected Tables`. Save the resulting file to a location on your computer. See the below image for reference.

	![Exporting database backup from MyBB Admin Control Panel](/assets/images/faq/backupdb-export.png)

4. Using an FTP client, such as [FileZilla](https://filezilla-project.org/download.php?show_all=1), download **ALL** of your forum's files to a location on your computer.

# Uploading Data to the New Host

5. Create a new database and user on the new host. Change the database configuration variables in `./inc/config.php` to the values appropriate for your new host.

6. Using a tool such as phpMyAdmin, browse to the blank database on your new host, and import the data exported in Step 3 of [Backup/Export Data](#backup-export-data).

7. Using an FTP client, upload **ALL** of your forum's files to the new web host.

# Domain Transfer

In many cases, your new web host will help transfer your domain and point it to their systems. If not, please contact them for assistance with changing the settings for your domain at your registrar, as the settings differ between hosts. Also, keep in mind that DNS propagation (the time it takes for computers to learn that your domain points somewhere new) can often take up to a few hours, so if it doesn't update immediately, there is no cause for concern.

# Completing the Transfer

8. Your domain should hopefully be pointed to the new host at this point, and your forum should behave exactly as it did on your old host. If it doesn't, [create a support thread in the MyBB Community Forums](https://community.mybb.com/newthread.php?fid=176), or contact your new web host for assistance, providing them with a link to this documentation.

9. Re-open your board by following Steps 1-2 of [Backup/Export Data](#backup-export-data), but opening the board instead of closing it.
