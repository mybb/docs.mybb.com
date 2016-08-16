---
layout: page
title:  "Broken Styles"
categories: [faq]
description: "Fixes for when the styles are not working on your forum or your Admin CP."
---

# My site has no styles / looks broken

If your site looks like the following then your site URL probably wasn't entered correctly:

[![Broken installation](/assets/images/faq/broken.jpg)](/assets/images/faq/broken.jpg)

To fix this edit the `inc/settings.php` file and find the `$settings['bburl']` line.

Change the value to the correct URL, such as `$settings['bburl'] = "http://notmysite.com";` to `$settings['bburl'] = "http://mysite.com";`.

Next, log into your Admin Control Panel > Configuration > Site Details and update your Board URL here too.

# My Admin CP has no styles / looks broken

If it is only your AdminCP that looks like such and you have changed the directory name for it (from /admin to something else, for example /panel) then you should also apply the change in the `inc/config.php` file.

To fix this edit the `inc/config.php` file and find the `$config['admin_dir']` line and change the value to the directory name of the admin directory, such as `$config['admin_dir'] = 'admin';` to `$config['admin_dir'] = 'panel';`
