---
layout: page
title:  "Configuration File"
categories: [administration]
---

During the installation process of MyBB a `inc/config.php` file is created with the following content, where:
- provided database connection details are saved in `$config['database']` (_Database configuration_),
- provided Table Encoding is saved in `$config['database']['encoding']` (_Database Encoding_) &mdash; in this example: `utf8`,
- provided ACP PIN is saved in `$config['secret_pin']`.

Consult the [MyBB security guide]({{ site.baseurl }}/1.8/administration/security/protection/) to correctly configure security-related values.

```php
<?php
/**
 * Database configuration
 *
 * Please see the MyBB Docs for advanced
 * database configuration for larger installations
 * https://docs.mybb.com/
 */

$config['database']['type'] = '';
$config['database']['database'] = '';
$config['database']['table_prefix'] = '';

$config['database']['hostname'] = '';
$config['database']['username'] = '';
$config['database']['password'] = '';

/**
 * Admin CP directory
 *  For security reasons, it is recommended you
 *  rename your Admin CP directory. You then need
 *  to adjust the value below to point to the
 *  new directory.
 */

$config['admin_dir'] = 'admin';

/**
 * Hide all Admin CP links
 *  If you wish to hide all Admin CP links
 *  on the front end of the board after
 *  renaming your Admin CP directory, set this
 *  to 1.
 */

$config['hide_admin_links'] = 0;

/**
 * Data-cache configuration
 *  The data cache is a temporary cache
 *  of the most commonly accessed data in MyBB.
 *  By default, the database is used to store this data.
 *
 *  If you wish to use the file system (cache/ directory), MemCache (or MemCached), xcache, APC, or eAccelerator
 *  you can change the value below to 'files', 'memcache', 'memcached', 'xcache', 'apc' or 'eaccelerator' from 'db'.
 */

$config['cache_store'] = 'db';

/**
 * Memcache configuration
 *  If you are using memcache or memcached as your
 *  data-cache, you need to configure the hostname
 *  and port of your memcache server below.
 *
 * If not using memcache, ignore this section.
 */

$config['memcache']['host'] = 'localhost';
$config['memcache']['port'] = 11211;

/**
 * Super Administrators
 *  A comma separated list of user IDs who cannot
 *  be edited, deleted or banned in the Admin CP.
 *  The administrator permissions for these users
 *  cannot be altered either.
 */

$config['super_admins'] = '1';

/**
 * Database Encoding
 *  If you wish to set an encoding for MyBB uncomment
 *  the line below (if it isn't already) and change
 *  the current value to the mysql charset:
 *  http://dev.mysql.com/doc/refman/5.1/en/charset-mysql.html
 */

$config['database']['encoding'] = 'utf8';

/**
 * Automatic Log Pruning
 *  The MyBB task system can automatically prune
 *  various log files created by MyBB.
 *  To enable this functionality for the logs below, set the
 *  the number of days before each log should be pruned.
 *  If you set the value to 0, the logs will not be pruned.
 */

$config['log_pruning'] = array(
	'admin_logs' => 365, // Administrator logs
	'mod_logs' => 365, // Moderator logs
	'task_logs' => 30, // Scheduled task logs
	'mail_logs' => 180, // Mail error logs
	'user_mail_logs' => 180, // User mail logs
	'promotion_logs' => 180 // Promotion logs
);

/**
 * Disallowed Remote Hosts
 *  List of hosts the fetch_remote_file() function will not
 *  perform requests to.
 *  It is recommended that you enter hosts resolving to the
 *  forum server here to prevent Server Side Request
 *  Forgery attacks.
 */

$config['disallowed_remote_hosts'] = array(
	'localhost',
);

/**
 * Disallowed Remote Addresses
 *  List of IPv4 addresses the fetch_remote_file() function
 *  will not perform requests to.
 *  It is recommended that you enter addresses resolving to
 *  the forum server here to prevent Server Side Request
 *  Forgery attacks.
 *  Removing all values disables resolving hosts in that
 *  function.
 */

$config['disallowed_remote_addresses'] = array(
	'127.0.0.1',
	'10.0.0.0/8',
	'172.16.0.0/12',
	'192.168.0.0/16',
);

/**
 * Admin CP Secret PIN
 *  If you wish to request a PIN
 *  when someone tries to login
 *  on your Admin CP, enter it below.
 */

$config['secret_pin'] = '';
```
