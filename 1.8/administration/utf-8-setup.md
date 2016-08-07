---
layout: page
title: "UTF-8 Setup"
categories: [administration]
---

UTF-8 has rapidly become the web standard for character encoding, supporting the character sets of many languages, emojis, and more. MyBB features a set of UTF-8 tools to help administrators convert their current encodings over to UTF-8. However, before you can use these tools we need to make a change to `./inc/config.php`.

**Please note that once you've converted to UTF-8 there is no supported way to undo this process.** 

The following change needs to be made in `inc/config.php`. Download the file from the server and open it in an appropriate text editor, or you edit it on-server if you have the means to do so.

1. Look for the following lines in `inc/config.php`:

   ```php
   /**
   * Database Encoding
   *  If you wish to set an encoding for MyBB uncomment
   *  the line below (if it isn't already) and change
   *  the current value to the mysql charset:
   *  http://dev.mysql.com/doc/refman/5.1/en/charset-mysql.html
   */
   
   // $config['database']['encoding'] = 'utf8';
   ```

2. Replace the following:

   ```php
   // $config['database']['encoding'] = 'utf8';
   ```

   with:

   ```php
   $config['database']['encoding'] = 'utf8';
   ```

Save the file and upload it to your server, replacing the old `inc/config.php`. Now that's done, you can continue to run the UTF-8 tools in the ACP.
