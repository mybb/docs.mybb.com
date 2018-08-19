---
layout: page
title: "Database Restore"
categories: [install]

redirect_from:
- /Database-Restore.html
---

To restore a database to your forum, you will first need to know what database engine your forum is using in order to determine which instructions to follow. MyBB supports the following database engines:

* MySQL (In this demonstration, [PhpMyAdmin](https://www.phpmyadmin.net/) will be used)

* SQLite (In this demonstration, [PhpLiteAdmin](https://www.phpliteadmin.org/) will be used)

* PostgreSQL (In this demonstration, [PhpPgAdmin](http://phppgadmin.sourceforge.net) will be used)

In the following instructions Linux CentOS 7 will be used, so commands may differ.

## MySQL Database Restore

1. Once logged into PhpMyAdmin, select your database from the side-menu on the left. 

[![database screen](/assets/images/1.8/database-restore/phpmyadmin_1.png)](/assets/images/1.8/database-restore/phpmyadmin_1.png)

2. From here, select "Import" from the top menu. You will be presented with a page like this:

[![import screen](/assets/images/1.8/database-restore/phpmyadmin_2.png)](/assets/images/1.8/database-restore/phpmyadmin_2.png)

3. Select "Choose File", browse to your backup, and click "Open" on the Windows Prompt. 

4. Generally, the settings on this page can be left as is, but you may alter where appropriate.

5. Click "Go". If successful, a message saying so will be presented as well as your tables in the side-menu on the left.

## SQLite Database Restore

1. Login to PhpLiteAdmin and select your database from the side-menu on the left. 

[![phpliteadmin screen](/assets/images/1.8/database-restore/sqlite_1.png)](/assets/images/1.8/database-restore/sqlite_1.png)

2. Select "Import" from the top menu and you will be presented with a page like this:

[![phpliteadmin import](/assets/images/1.8/database-restore/sqlite_2.png)](/assets/images/1.8/database-restore/sqlite_2.png)

3. Select "Choose File", browse to your backup, and click "Open" on the Windows Prompt.

4. Generally, the settings on this page can be left as is, but you may alter where appropriate.

5. Click "Import". If successful, you will see your tables in the side-menu on the left, as well as a message letting you know the import was successful.

[![phpliteadmin success](/assets/images/1.8/database-restore/sqlite_3.png)](/assets/images/1.8/database-restore/sqlite_3.png)

## PostgreSQL Database Restore

1. Login to PhpPgAdmin and select your database from the side-menu on the left.

[![phppgadmin screen](/assets/images/1.8/database-restore/phppgadmin_1.png)](/assets/images/1.8/database-restore/phppgadmin_1.png)

2. Select "SQL" from the top menu and you will be presented with a page like this:

[![phppgadmin import](/assets/images/1.8/database-restore/phppgadmin_2.png)](/assets/images/1.8/database-restore/phppgadmin_2.png)

3. Select "Choose File", browse to your backup, and click "Open" on the Windows Prompt.

4. Click "Execute". Allow the SQL to run. If successful, you will be able to scroll down to the bottom of the page and it will look something like this:

[![phppgadmin successful](/assets/images/1.8/database-restore/phppgadmin_3.png)](/assets/images/1.8/database-restore/phppgadmin_3.png)

## Database Restore using SSH

### MySQL

1. After logging into your server via SSH, run the following:

```
mysql -u YOUR_MYBB_DB_USER -p YOUR_MYBB_DBNAME < /PATH/TO/DUMP.SQL
```

2. You will be prompted for your password. If successful, your SSH window will look something like this:

[![importssh screen](/assets/images/1.8/database-restore/ssh_mysql_1.png)](/assets/images/1.8/database-restore/ssh_mysql_1.png)

3. To be sure, log back into MySQL by running the following (When prompted, enter password):

```
mysql -u YOUR_MYBB_DB_USER -p
```

4. Now run the following to select your database and show existing tables:

```
USE database_name_here; SHOW TABLES;
```

5. If successful, your SSH window will look something like this:

[![ssh mysqltables](/assets/images/1.8/database-restore/ssh_mysql_2.png)](/assets/images/1.8/database-restore/ssh_mysql_2.png)

### SQLite

1. After logging into your server via SSH, run the following to import your database:

```
sqlite3 database_name < /PATH/TO/DUMP.SQL 
```

2. Now login to your database and check to see if your tables exist by running the following:

```
sqlite3 database_name.db
```

3. Once you have entered SQLite, you will be greeted with a simlar message to the following:

[![ssh sqlitegreeting](/assets/images/1.8/database-restore/ssh_sqlite_1.png)](/assets/images/1.8/database-restore/ssh_sqlite_1.png)

3. Proceed to run the following:

``` 
.tables
```

4. Your SSH window should now look something like this:

[![ssh sqlitetables](/assets/images/1.8/database-restore/ssh_sqlite_2.png)](/assets/images/1.8/database-restore/ssh_sqlite_2.png)


### PostgreSQL

1. After logging into your server via SSH, you will now need to enter PostgreSQL. Your method may slightly differ when logging in. Run the following to login:

``` 
su - postgres
```

[![ssh postgres](/assets/images/1.8/database-restore/ssh_postgresql_1.png)](/assets/images/1.8/database-restore/ssh_postgresql_1.png)

2. To restore your database, you will need to run the following:

``` 
psql database_name < /PATH/TO/DUMP.SQL
```

3. You can now proceed to run the following to output your tables:

``` 
psql database_name
```

4. Followed by:

``` 
\dt
```

[![ssh postgrestables](/assets/images/1.8/database-restore/ssh_postgresql_2.png)](/assets/images/1.8/database-restore/ssh_postgresql_2.png)

## Optional

1. Now that you have restored your database, we are not quite done yet. You may now need to configure your database settings in ```./inc/config.php``` :

```
$config['database']['table_prefix'] = 'mybb_'; - The Table Prefix from the database should be placed here.
```

**Note: If you are restoring a database from IcyBoards, you will need to replace your current prefix in ```./inc/config.php``` with your new prefix (in PhpMyAdmin). Additionally, you will need correct the ```Uploads Path``` and ```Avatar Upload Path``` in the Admin CP:**

``` 
Uploads Path - By default, MyBB's Upload Path is ./uploads
Avatar Upload Path - By default, MyBB's Avatar Upload Path is ./uploads/avatars
``` 

### Useful links
- [How to perform a backup](https://docs.mybb.com/1.8/administration/backups/)
- [How to use PuTTY on Windows](https://www.ssh.com/ssh/putty/windows/)
