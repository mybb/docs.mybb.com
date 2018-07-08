---
layout: page
title: "Database Restore"
categories: [install]

redirect_from:
- /Database-Restore.html
---

To restore a database to your forum, you will first need to know what database type your forum is using in order to determine which instructions to follow. MyBB supports the following database types:

* MySQL (In this demonstration, PhpMyAdmin will be used)

* SQLite (In this demonstration, PhpLiteAdmin will be used)

* PostgreSQL (In this demonstration, PhpPgAdmin will be used)

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

1. 

## PostgreSQL Database Restore


## Database Restore using SSH

### MySQL

1. After logging into your server via SSH, run the following:

``` mysql -u YOUR_MYBB_DB_USER -p YOUR_MYBB_DBNAME < /PATH/TO/DUMP.SQL ``` 

2. You will be prompted for your password. If successful, your SSH window will look something like this:

[![importssh screen](https://i.gyazo.com/7c06e62e690921ba9efecf130fddc1ec.png)](https://i.gyazo.com/7c06e62e690921ba9efecf130fddc1ec.png)

3. To be sure, log back into MySQL by running the following (When prompted, enter password):

```mysql -u YOUR_MYBB_DB_USER -p```

4. Now run the following to select your database and show existing tables:

```USE database_name_here; SHOW TABLES;```

5. If successful, your SSH window will look something like this:

[![ssh mysqltables](https://i.gyazo.com/b4bf33214eca3d8458c6aa34dae81026.png)](https://i.gyazo.com/b4bf33214eca3d8458c6aa34dae81026.png)

### SQLite

1. After logging into your server via SSH, run the following to import your database:

``` sqlite3 database_name < /PATH/TO/DUMP.SQL ```

2. Now login to your database and check to see if your tables exist by running the following:

``` sqlite3 database_name.db ```

3. Once you have entered SQLite, you will be greeted with a simlar message to the following:

[![ssh sqlitegreeting](https://i.gyazo.com/1ff04ce7c6e643ca3ddcd242c832b0f7.png)](https://i.gyazo.com/1ff04ce7c6e643ca3ddcd242c832b0f7.png)

3. Proceed to run the following:

``` .tables ```

4. Your SSH window should now look something like this:

[![ssh sqlitetables](https://i.gyazo.com/bbb6839e815b8e403f5347baab622030.png)](https://i.gyazo.com/bbb6839e815b8e403f5347baab622030.png)


### PostgreSQL
