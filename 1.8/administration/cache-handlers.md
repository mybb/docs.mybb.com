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

**Disk Cache Handler**

Cache file are written to the filesystem within the `cache/` directory as PHP files. The `cache/` directory must be writeable for this cache handler to function.

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

https://www.php.net/manual/en/book.memcache.php

**Redis**



https://redis.io/documentation

Please note, this will only work with installs running MyBB version 1.8.23 or higher.


