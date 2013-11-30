---
layout: page
title:  "Cannot login"
---

# Unable to login

So every day we have people reporting that logins don't work on their forum. Let's fix this once and for all!

Most of the time this is a problem with your cookie settings being incorrect or inadequate. For more information about MyBB's cookies, read [Cookies](../miscellaneous/cookies).

Your cookie settings can be found in: **Admin CP** > **Configuration** > **Settings** > **General Configuration**. The two settings are *Cookie Domain* and *Cookie Path*.

By default, MyBB suggests Cookie Domain to be blank, and Cookie Path to be **/**. Although this theoretically will work, in many cases it is inadequate.

First a few examples of what your cookie settings should look like:

If your URL is **http://www.example.com**, your settings should be:

    Cookie Domain: .example.com
    Cookie Path: / 

If your URL is **http://www.example.com/myforum**, your settings should be:

    Cookie Domain: .example.com
    Cookie Path: /myforum/ 

If your URL is **http://subdomain.example.com/wow**, your settings should be:

    Cookie Domain: .subdomain.example.com OR .example.com
    Cookie Path: /wow/ 

Alternatively you can use [this tool](http://www.dennistt.net/mybb/cookiesettings.php) to provide your cookie settings based on your forum's URL.

These cookie settings should work on all MyBB installations. If you have site-integration, your cookie settings may need to be more generalized.

After you change your cookie settings, please advise your users to log out and [clear their cookies from their browser](/faq/clear_board_cookies), so that the new cookies can take effect. 
