---
layout: page
title: "Cache Handlers"
categories: [administration]
---

## MyBB supports a number of Cache Handlers out of the box. 

**APC Cache Handler**

The Alternative PHP Cache (APC) is a free and open opcode cache for PHP. Its goal is to provide a free, open, and robust framework for caching and optimizing PHP intermediate code. 

https://www.php.net/manual/en/book.apc.php

Please note, APC Cache Handler is no longer officially supported.

**APCu Cache Handler**

APCu is APC stripped of opcode caching. 

https://www.php.net/manual/en/book.apcu.php

Please note, APCu is available in MyBB versions 1.8.23 onwards. 

**Disk Cache Handler**

Cache files are written to the filesystem within the `cache/` directory as PHP files. The `cache/` directory must be writeable for this cache handler to function.

https://httpd.apache.org/docs/2.4/mod/mod_cache.html

**eAccelerator**

eAccelerator is a free open-source PHP accelerator & optimizer. It increases the performance of PHP scripts by caching them in their compiled state, so that the overhead of compiling is almost completely eliminated. It also optimizes scripts to speed up their execution. eAccelerator typically reduces server load and increases the speed of your PHP code by 1-10 times. 

https://github.com/eaccelerator/eaccelerator/wiki

Please note, eAccelerator is no longer officially supported.

**Memcached**

Free & open source, high-performance, distributed memory object caching system, generic in nature, but intended for use in speeding up dynamic web applications by alleviating database load.

Memcached is an in-memory key-value store for small arbitrary data (strings, objects) from results of database calls, API calls, or page rendering.

https://github.com/memcached/memcached/wiki

**Memcache**

Memcache module provides handy procedural and object oriented interface to memcached, highly effective caching daemon, which was especially designed to decrease database load in dynamic web applications.

The Memcache module also provides a session handler (memcache). 

Please note, you will also need to set the Memcache hostname and port setting for this Cache Handler to work.

https://www.php.net/manual/en/book.memcache.php

**Redis**

Redis has a great article that explains in full the ins and outs of the Cache Handler - https://redis.io/topics/client-side-caching .

https://redis.io/documentation

Please note, Redis will only work with installs running MyBB version 1.8.23 or higher. You will also need to set the Redis hostname and port setting for this Cache Handler to work.

You can select which Cache Handler you would like to use on your MyBB install by logging in to your website FTP server and navigate to the MyBB root directory, then selecting /inc and edit the config.php file. Around line 38 you should find the following:

<table>
  /**
 * Data-cache configuration
 *  The data cache is a temporary cache
 *  of the most commonly accessed data in MyBB.
 *  By default, the database is used to store this data.
 *
 *  If you wish to use the file system (cache/ directory), MemCache (or MemCached), xcache, APC, APCu, eAccelerator or Redis
 *  you can change the value below to 'files', 'memcache', 'memcached', 'xcache', 'apc', 'apcu', 'eaccelerator' or 'redis' from 'db'.
 */

$config['cache_store'] = 'db';
</table>

You then need to edit the value on line 70. For example, if you wished to use Redis you change line 70 too:

<table>
  $config['cache_store'] = 'redis';
</table>

Don't forget, if you wish to use Redis or Memcache you will also need to set the Hostname and Port settings which are also set in the config.php file. The setting for Memcache can be found at line 50 and the settings for Redis can be found at line 62. You will edit the Hostname and Port number values similiar to above.
