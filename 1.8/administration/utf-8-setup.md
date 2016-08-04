---
layout: page
title: "UTF-8 Setup"
categories: [administration]
---

MyBB **1.2.10** and above feature a new set of UTF-8 tools. These tools allow users to convert their current encodings over to 
UTF-8 which is rapidly becoming the Unicode standard for many webmasters. However, before you can use these tools we need to make some changes to the config.php.

The following changes are to be made in `inc/config.php`. At this time you should download that file and open it in an appropriate text editor.

1. Look for the following lines in `inc/config.php`: 

```
/**
 * Database Encoding
 *  If you wish to set an encoding for MyBB uncomment
 *  the line below (if it isn't already) and change
 *  the current value to the mysql charset:
 *  http://dev.mysql.com/doc/refman/5.1/en/charset-mysql.html
 */
 ```

```$config['database']['encoding'] = 'utf8';```

2. Find the following line

``// $config['database']['encoding'] = 'utf8';``

And replace it with

```$config['database']['encoding'] = 'utf8';```

Save the file and upload it to your server, replacing the old `inc/config.php`. Now that's done, you can continue to run the UTF-8 tools in the ACP.


**Please note that once you've converted to UTF-8 there is no supported way to undo this process.** 
