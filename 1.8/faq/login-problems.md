---
layout: page
title:  "Login Problems"
categories: [faq]
description: "Resolve issues with logging in to your forum."

redirect_from:
- /Help-Cannot_login.html
---

# Cookie Settings
Most of the time this is a problem with your [cookie](/1.8/development/cookies/) settings being incorrect or inadequate.

By default, MyBB suggests Cookie Domain to be blank, and Cookie Path to be `/`. Although this theoretically will work, in many cases it is inadequate.

You can use [this tool](/tools/cookie-settings) to generate appropriate cookie settings, but here are some examples of what valid cookie settings look like:

Forum URL | Cookie Domain | Cookie Path | Cookie Secure Flag
-|-|-|:-:
http**s**://www.example.com | `.example.com` | `/` | Yes
http**s**://www.example.com/directory/ | `.example.com` | `/directory/` | Yes
http**s**://www.subdomain.example.com | `subdomain.example.com`| `/` | Yes
http**s**://www.subdomain.example.com/directory/ | `subdomain.example.com`| `/directory/` | Yes
http://www.example.com | `.example.com`| `/`| No

These cookie settings should work on all MyBB installations. If you have site-integration, your cookie settings may need to be more generalized.

## Updating Cookie Settings

- ### Using the ACP  
  The board's cookie settings can be found in the Admin CP's **Configuration → Settings → Site Details**.

- ### Using the Cached Settings File
  When not able to log into the Admin CP, the cookie settings can be temporarily changed by modifying the `inc/settings.php` file.
  
  Locate the values `cookiedomain`, `cookiepath`, and `cookiesecureflag` that may look like this:
  ```php
  $settings['cookiedomain'] = ".example.com";
  ```
  ```php
  $settings['cookiepath'] = "/directory/";
  ```
  ```php
  $settings['cookiesecureflag'] = "1";
  ```

  Apply the necessary changes (`1` for _Yes_, or `0` for _No_), save the file on the server and try logging in.
  
  Once you are able to login into the Admin CP, re-apply the change in Settings to make it permanent.


After you change your cookie settings, you may have to advise your users to log out and clear cookies stored by their browser, so that the new cookies can take effect.

# Password Change
It's possible to change a user's password by executing an SQL query &mdash; replace `RANDOM_VALUE` with desired password, and `USER_ID` with targeted user's ID:
```sql
UPDATE mybb_users SET `password` = md5(CONCAT(md5('temp-salt'), md5('RANDOM_VALUE'))), salt = 'temp-salt' WHERE uid = USER_ID;
```
After this operation, you should change the password again using MyBB's interface.

### Useful links
- [Login/Logout problems? PLEASE READ](https://community.mybb.com/thread-42123.html)
- [Authorization code mismatch? PLEASE READ](https://community.mybb.com/thread-218862.html)
