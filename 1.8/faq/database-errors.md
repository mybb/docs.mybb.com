---
layout: page
title: "Fixing Database Errors"
categories: [faq]
description: "Explains some of the most common database connection errors and suggests ways to resolve the issue causing them."
---

MyBB setup is made to be as simple as possible. However, database connection issues may arise during installation, or later after installation. This article will explain some of the most common database connection errors and suggest ways to resolve the issue causing them.

**Note: If needed, the MyBB installation guide for MyBB can be found here: https://docs.mybb.com/1.8/install/**

# Access denied for user
Getting an error like this?:
![MySQL Error 1045 - Access denied for user with password](/assets/images/faq/dberrors-1045-MySQL-access-denied.png "Access Denied database")

This means that your configuration is wrong! Don't worry though, this is easy to fix.
First - lets find out our username and password.

If you're on a shared hosting environment that uses cPanel, log in to cPanel and select your database configuration.
![cPanel UI to create new database user](/assets/images/faq/dberrors-cpanel-create-db-user.png "cPanel database account")

Create a username and password, and then assign this user to the database MyBB will use:
![cPanel UI to add user to database](/assets/images/faq/dberrors-cpanel-add-user-to-db.png "Assign user to database")

Now that you have assigned a user to your database, we need to change the MyBB configuration to reflect this.

Open your preferred FTP software and navigate to `./inc/config.php`.

Enter the details that you made earlier like so:

```php
$config['database']['hostname'] = 'localhost';
```

**Note: If you are running a local installation on macOS, you may need to set the database host to `127.0.0.1` instead of `localhost`. `127.0.0.1` is known as the "loopback" address that always points to your system.**

## Using a Remote MySQL Database Connection

Another cause for the above issue is if your database is hosted seperately from your MyBB installation. In this case, you will need to enable remote database connection.

On a Unix environment, you will want to login via SSH and enter your database command line.

**Note: If you are using a different DBMS, such as PostgreSQL, the process will be different than the steps outlined below. If you're using SQLite, none of the below steps apply.**

```
mysql -u root -p
```
**Tip: Don't ever use the MySQL `root` user for your MyBB database. If something happens and an attacker is able to exploit your forum, they will be able to cause far more damage with the `root` user than with a user constrained to only your MyBB database. It is only being used here so that you can be certain you'll have the necessary privileges to run potential `GRANT` statements to give a MyBB database user access to the MyBB database.**

You will then need to enter the password for the root database user.

You can then grant permissions for a user on a specific database hostname, or `%` for "wildcard" (all hostnames and IPs that route to the server):

For example:

```sql
CREATE USER 'USERNAME HERE'@'DATABASE HOSTNAME HERE' IDENTIFIED BY 'PASSWORD HERE';
```

**Tip: You can use an IP address OR a domain/subdomain for the `DATABASE HOSTNAME HERE` value.**

```sql
GRANT ALL PRIVILEGES ON MYBB_DATABASE_NAME.* TO 'USERNAME HERE'@'DATABASE HOSTNAME HERE';
```

The asterisk in this command means **all tables on the `MYBB_DATABASE_NAME` database**, which the user can read, edit, execute and perform all tasks on.

Once you have set the permissions for your new user, be sure to reload the privileges.

```sql
FLUSH PRIVILEGES;
```

# Table <table> doesn't exist

Missing a table? First, consider a few key things:

- Is this table a core table that ships with MyBB?
- Is this table from a plugin / extension?
- What were you doing before this error appeared?

## If the table is a core table

If the missing table is a core table, you should be asking yourself what you were doing. If you were installing a clean copy of MyBB, then try to drop your database and rebuild it with the provided installer.

If you were updating, you should follow the guidance in the [upgrade guide](https://docs.mybb.com/1.8/install/upgrade/).

If you were merging an old database to yours, then you can check the [merge troubleshooting](https://docs.mybb.com/1.8/merge/troubleshooting/) document for troubleshooting steps.

## If the table is from a plugin

Disable the plugin, and uninstall it. You can then reinstall it later if needed, but ensure that the plugin is compatible with your version of MyBB.

**Tip: You can sometimes change the compatibility within the plugin file like so:**

```php
return array(
		"name"			=> "Example Plugin",
		"description"	=> "This is an example Plugin.",
		"website"		=> "Authorwebsite.com/plugin/",
		"author"		=> "Katos",
		"authorsite"	=> "authorsite.com",
		"version"		=> "1.1.8",
		"guid" 			=> "2418077c65561fe2bd0ac601bdb0c889",
		"compatibility" => "18*"
```

**Change the `compatibility` value to your version. For example from 16* to 18* to try and run a former MyBB 1.6.x plugin on 1.8.x. Note that this doesn't always work, as some plugins may depend on deprecated functionality from the MyBB 1.6 series.**
