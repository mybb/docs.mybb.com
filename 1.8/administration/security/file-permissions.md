---
layout: page
title: "File Permissions"
categories: [security]
---

Certain file permissions are required for MyBB to function correctly. Once you've uploaded your files, you will need to set the permissions on certain files and directories to allow PHP to write to and execute from them.

These files need a chmod of 666:

*  `./inc/settings.php`
*  `./inc/config.php (you must rename config.default.php to config.php first)`
*  `./inc/languages/your_language/all files (optional)`
*  `./inc/languages/your_language/admin/all files (optional)`

These files need a chmod of 777:

*  `./cache/`
*  `./cache/themes/`
*  `./uploads/`
*  `./uploads/avatars/`
*  `./admin/backups/ (optional)`

For increased security, you can change the file permissions of the `./inc/config.php` file to 644 or 444 after mybb is installed and configured correctly.


## Chmod with *nix systems

If you have SSH access, you can apply the necessary permissions via the following command, executed from your root MyBB directory:

```sh
chmod 666 inc/config.php inc/settings.php
chmod 777 cache/ cache/themes/ uploads/ uploads/avatars/
```

Optionally, you can also apply the following permissions:

```sh
chmod 666 inc/languages/english/*.php inc/languages/english/admin/*.php
chmod 777 cache/ cache/themes/ uploads/ uploads/avatars/ admin/backups/
```

## Chmod with Windows systems

If you are using [FileZilla](https://filezilla-project.org/), you can right click on a file or directory and click file permissions to modify the permissions of that file or directory.

If you prefer to modify permissions through Windows explorer, you can follow [these instructions](https://technet.microsoft.com/en-us/library/bb727008.aspx) to help you out. In general, the files and directories listed above require Full Modify permissions.
