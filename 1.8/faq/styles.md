---
layout: page
title:  "Broken Styles"
categories: [faq]
description: "Fixes for when the styles are not working on your forum or your Admin CP."
---

# Forum Front-End

Problems with loading web resources, like stylesheets and images, may make the site to look visually broken:

[![Broken installation](/assets/images/faq/broken.jpg)](/assets/images/faq/broken.jpg)

This may be accompanied by more detailed errors displayed in the browser's [Console](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_are_browser_developer_tools#how_to_open_the_devtools_in_your_browser).

The problem is usually caused by an incorrect value of the **Board URL** setting (_Configuration → Site Details_ in the Admin CP).

Make sure that the setting contains the right [URL](https://en.wikipedia.org/wiki/URL), and is in the correct format (e.g. `https://example.com/forum` &mdash; contains the scheme, domain, path if such exists, and does not include a slash `/` at the end).

Common problems to look for are:
- incorrect scheme (e.g. `http://` when the forum is accessed using `https://`),
- incorrect domain,
- missing subdomain (e.g. when the forum was installed on `forum.example.com`, the subdomain must be included),
- missing or incorrect path (e.g. when the forum was installed on `example.com/forum`, the directory must be included),
- incorrectly included trailing slash (there should be no `/` character at the end).

<!--
To fix this edit the `inc/settings.php` file and find the `$settings['bburl']` line.

Change the value to the correct URL, such as `$settings['bburl'] = "http://notmysite.com";` to `$settings['bburl'] = "http://mysite.com";`.

Next, log into your Admin Control Panel > Configuration > Site Details and update your Board URL here too.
-->

# Admin CP

If it is only your Admin CP that looks broken, and you have changed the directory name for it (from `admin/` to something else), you should also apply the change in the [Configuration File](/1.8/administration/configuration-file/).

To fix this, edit the `inc/config.php` file and find the `$config['admin_dir']` line and change the value to the directory name of the admin directory:
```php
$config['admin_dir'] = 'admin';
```
