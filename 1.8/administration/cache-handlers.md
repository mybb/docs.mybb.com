---
layout: page
title: "Cache Handlers"
categories: [administration]
---

MyBB's [Datacache](/1.8/development/datacache/), fetched from the database by default, can be stored using different cache handlers to improve performance.

You can select which Cache Handler you would like to use on your MyBB installation by editing the [configuration file](/1.8/administration/configuration-file/) (`inc/config.php`) and changing the value of `$config['cache_store']`.

For example, to use the APCu cache store, change the line to:
```php
$config['cache_store'] = 'apcu';
```


## Supported Cache Handlers
- ### Database
  `db`
  
  The default cache handler.

- ### [APC](https://www.php.net/manual/en/book.apc.php)
  `apc`

  Please note, APC Cache Handler is no longer officially supported.

- ### [APCu](https://www.php.net/manual/en/book.apcu.php)
  `apcu`

  Please note, APCu is available in MyBB 1.8.23 or higher.

- ### Files
  `files`

  Cache files are written to the filesystem within the `cache/` directory as PHP files. The `cache/` directory must be writeable for this cache handler to function.

- ### [eAccelerator](https://github.com/eaccelerator/eaccelerator/wiki)
  `eaccelerator`

  Please note, eAccelerator is no longer officially supported.

- ### [Memcache](https://www.php.net/manual/en/book.memcache.php)
  `memcache`
  
- ### [Memcached](https://github.com/memcached/memcached/wiki)
  `memcached`

  Please note, you will also need to set the Memcache hostname and port setting for this Cache Handler to work.

- ### [Redis](https://redis.io/documentation)
 `redis`

  Please note, you will need to set the Redis hostname (`$config['redis']['host']`) and port (`$config['redis']['port']`) setting for this Cache Handler to work.
  
  This handler is available in MyBB 1.8.23 or higher.
