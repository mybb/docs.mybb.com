---
layout: page
title:  "FAQ"
categories: [faq]
---

## My site has no styles / looks broken

If your site looks like the following then your site URL probably wasn't entered correctly:

[![Broken installation](/assets/images/faq/broken.jpg)](/assets/images/faq/broken.jpg)

To fix this edit the `inc/settings.php` file and find the `$settings['bburl']` line.

Change the value to the correct URL, such as `$settings['bburl'] = "http://notmysite.com";` to `$settings['bburl'] = "http://mysite.com";`.

Next, log into your Admin Control Panel > Configuration > General Configuration and update your Board URL here too.