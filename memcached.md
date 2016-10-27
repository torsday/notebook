# Memcached

*From: [memcached(https://memcached.org)*

> Free & open source, high-performance, distributed memory object caching system, generic in nature, but intended for use in speeding up dynamic web applications by alleviating database load.

> Memcached is an in-memory key-value store for small chunks of arbitrary data (strings, objects) from results of database calls, API calls, or page rendering.

> Memcached is simple yet powerful. Its simple design promotes quick deployment, ease of development, and solves many problems facing large data caches. Its API is available for most popular languages.


*From: [Wikipedia](https://en.wikipedia.org/wiki/Memcached)*

> Memcached (pronunciation: mem-cash-dee) is a general-purpose distributed memory caching system. It is often used to speed up dynamic database-driven websites by caching data and objects in RAM to reduce the number of times an external data source (such as a database or API) must be read.

> Memcached is free and open-source software, licensed under the Revised BSD license. Memcached runs on Unix-like operating systems (at least Linux and OS X) and on Microsoft Windows. It depends on the libevent library.

> Memcached's APIs provide a very large hash table distributed across multiple machines. When the table is full, subsequent inserts cause older data to be purged in least recently used (LRU) order. Applications using Memcached typically layer requests and additions into RAM before falling back on a slower backing store, such as a database.

> The size of this hash table is often very large. It is limited to available memory across all the servers in the cluster of servers in a data centre. Where high volume, wide audience web publishing requires it, this may stretch to many gigabytes. Memcached can be equally valuable for situations where either the number of requests for content is high, or the cost of generating a particular piece of content is high.

> Memcached was originally developed by Danga Interactive for LiveJournal, but is now used by many other systems, including MocoSpace, YouTube, Reddit, Survata, Zynga, Facebook, Orange, Twitter, Tumblr and Wikipedia. Engine Yard and Jelastic are using Memcached as part of their platform as a service technology stack and Heroku offers several Memcached services as part of their platform as a service. Google App Engine, AppScale, Microsoft Azure, IBM Bluemix and Amazon Web Services also offer a Memcached service through an API.
