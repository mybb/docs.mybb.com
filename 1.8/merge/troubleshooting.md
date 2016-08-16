---
layout: page
title:  "Troubleshooting"
categories: [merge]
order: 2
---

# Website not reachable
This is caused by Apache's Stack Size, you can either increase the Stack Size or disable the function which causes this.

## Increasing the Stack Size
Add the following code to your `httpd.conf` and restart Apache:

```apacheconf
<IfModule mpm_winnt_module>
   ThreadStackSize 8*1024*1024
</IfModule>
```

## Disabling the Function
Open `merge/index.php` and search for:
```php
define("SKIP_ENCODING_DETECTION", 0);
```
Replace the `0` with a `1`.

# Attachment Permissions are Wrong
This is most likely caused by a `.htaccess` file that denies access to the attachment directory.

Normally the `.htaccess` is located either directly in the attachment directory or in the root of your old board. After you rename the `.htaccess` file to something else, you can reload the merge system.
