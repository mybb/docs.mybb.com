---
layout: page
title: "Database Restore"
categories: [install]

redirect_from:
- /Database-Restore.html
---

To restore a database to your forum, you will first need to know what database type your forum is using in order to determine which instructions to follow. MyBB supports the following database types:

* MySQL

* SQLite

* PostgreSQL

## MySQL Database Restore

1. Once logged into PhpMyAdmin, select your database from the side-menu on the left. 

[![database screen](https://i.gyazo.com/f4376fa46113a79a691d023ee07bf430.png)](https://i.gyazo.com/f4376fa46113a79a691d023ee07bf430.png)

2. From here, select "Import" from the top menu. You will be presented with a page like this:

[![import screen](https://i.gyazo.com/d460da5ba195ecc8f6b0056a8d01b0f0.png)](https://i.gyazo.com/d460da5ba195ecc8f6b0056a8d01b0f0.png)

3. Select "Choose File", browse to your backup, and click "Open" on the Windows Prompt. 

4. Generally, the settings on this page can be left as is, but you may alter where appropriate.

5. Click "Go". If successful, a message saying so will be presented as well as your tables in the side-menu on the left.

### Optional

6. We are not quite done yet. You may now need to configure your database settings (.../inc/config.php).

**Note: If you are restoring a database from IcyBoards, you will need to replace your current prefix (in ../inc/config.php) with your new prefix (in PhpMyAdmin).**

## SQLite Database Restore


## PostgreSQL Database Restore


## Database Restore using SSH

