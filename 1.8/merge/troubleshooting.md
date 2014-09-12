---
layout: page
title:  "Troubleshooting"
categories: [merge]
---

# Website not reachable
This is caused by Apache's Stack Size, you can either increase the Stack Size or disable the function which causes this:

## Increasing the Stack Size
Add the following code to your `httpd.conf` and restart Apache:

```
<IfModule mpm_winnt_module>
   ThreadStackSize 8*1024*1024
</IfModule>
```

## Disabling the function
Open `merge/index.php` and search for: `define("SKIP_ENCODING_DETECTION", 0);` and replace the "0" with an "1".

# Attachment Permissions are wrong
This is most likely caused by a `.htaccess` file which denies access to the attachment directory.

-- HowTo find the file --