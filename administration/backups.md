---
layout:   page
category: Admin CP
title:    "Backups"
---

From the database backups page, you can easily create backups that are either stored on your server or downloaded to your computer. The database backups listing page shows you all backups that are currently stored on your server, the size of the backup, the time and day of creation, and allows you to download or delete the backup.

For automatically scheduled backups, see the Database Backup Task section.

## Database Tables

Select the tables you wish to back up. Holding down CTRL lets you select multiple databases, or you can choose to **Select All Tables** **Deselect All Tables** or **Select Forum Tables** (those with the prefix your forum was installed under).

## File Type

You can choose to have the backup compressed in a GZIP file (`.gz`), or as a plain text file (`.txt`).

## Save Method

Would you like to have the backup stored on your server (Backup Directory) or downloaded to your computer (Download)?

## Backup Contents

You can choose to backup the structure and data, just the structure, or just the data. Backing up the structure and data allows you to recreate the database completely, as it is right now. Backing up the structure lets you recreate the structure of your current database, but without any data. Backing up the data lets you insert data into an existing database with the same structure of your current database.

## Analyze and Optimize Selected Tables

While performing the backup, would you like to have the selected tables optimized (as if you were running the **Optimize Database** tool)?
Once you have made your selections, click on "Perform Backup." If you have selected to store it to your server, you will be provided a link to the backup, while if you have selected to download it, you will be offered to download the backup.