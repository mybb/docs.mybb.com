---
layout: page
title: "Fixing Database errors"
categories: [faq]
---

MyBB set-up is made to be as simple as possible, however sadly sometimes there are a few issues that can occur. Including, it seems, database connection issues.
With this FAQ tutorial, we will go over how to fix common database issues.

Note: Please find the set-up installation guide for MyBB here: http://docs.mybb.com/1.8/install/

# Access denied for user
Getting an error like this?:
![alt text](http://puu.sh/qmmNw/60de3ed946.png "Access Denied database")

This means that your configuration is wrong! Don't worry though, this is easy to fix. 
First - lets find out our username and password.

If you're on a webhost environment, login to your CPanel and select your database configuration. 
![alt text](http://puu.sh/qmkpY/2c24c1ec6f.png "CPanel database account")

Create a username and password, and then assign this user to your database:
![alt text](http://puu.sh/qmkvf/d9763cebab.png "Assign user to database")

Now that you have assigned your user to your database, we need to change our MyBB configuration to reflect this.
Open your preferred FTP software and navigate to '/inc/config.php'
Enter the details that you made earlier like so:

![alt text](http://puu.sh/qmkK7/8ca656a3a5.png "Database settings")

# Access denied cont.
Another cause for the above issue is if your database is hosted seperately to your website. In this case, you will need to enable remote database connection.
On a Unix environment, you will want to login via SSH and enter your MySQL configuration

Ubuntu:
```
mysql -u (YOUR USER) -p
```
You will then need to enter your password

You can then grant permissions for a user on a specific IP address, or % for wildcard (all IP addresses)
For example:
```
CREATE USER 'USERNAME HERE'@'IP ADDRESS HERE' IDENTIFIED BY 'PASSWORD HERE';
```

```
GRANT ALL PRIVILEGES ON * . * TO 'USERNAME HERE'@'IP ADDRESS HERE';
```
The asterisks in this command refer to the database and table (respectively) that they can access—this specific command allows to the user to read, edit, execute and perform all tasks across all the databases and tables.

Once you have finalized the permissions that you want to set up for your new users, always be sure to reload all the privileges.
```
FLUSH PRIVILEGES;
```

#Table <table> doesn't exist!
Missing a table? First, you need to think about key things here:
- Is this table a core table that ships with MyBB?
- Is this table from a plugin / extension?
- What were you doing before this error appeared?

## If the table is a core table
If the missing table is a core table, you should be asking yourself what you were doing. If you were installing a clean copy of MyBB, then try to drop your database and rebuild it with the provided installer.
If you were updating, you should follow the: http://docs.mybb.com/1.8/install/upgrade/ <-- upgrade guide.
If you were merging an old database to yours, then you can check the troubleshooting guide here: http://docs.mybb.com/1.8/merge/troubleshooting/

## If the table is from a plugin
Disable the plugin, and uninstall it.
You can then reinstall it later if needed, but ensure that the plugin is compatible with your version of MyBB.
HINT: You can **sometimes** change the compatibility within the plugin file like so:
```
return array(
		"name"			=> "Example Plugin",
		"description"	=> "This is an example Plugin.",
		"website"		=> "Authorwebsite.com/plugin/",
		"author"		=> "Katos",
		"authorsite"	=> "authorsite.com",
		"version"		=> "1.1.8",
		"guid" 			=> "2418077c65561fe2bd0ac601bdb0c889",
		**"compatibility" => "18*"**
```

Change the compatibility to your version. For example from 16* to 18* to upgrade it to 1.8.x
**PLEASE NOTE** this does **not** always work.

_Contribute to this guide here: https://github.com/mybb/docs.mybb.com/blob/gh-pages/1.8/faq/database-errors.md_
