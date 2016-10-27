# Memcached

*From: [memcached(https://memcached.org)*

> Free & open source, high-performance, distributed memory object caching system, generic in nature, but intended for use in speeding up dynamic web applications by alleviating database load.

> Memcached is an in-memory key-value store for small chunks of arbitrary data (strings, objects) from results of database calls, API calls, or page rendering.

> Memcached is simple yet powerful. Its simple design promotes quick deployment, ease of development, and solves many problems facing large data caches. Its API is available for most popular languages.


*From: [Wikipedia](https://en.wikipedia.org/wiki/Memcached)*

> Memcached (pronunciation: mem-cash-dee) is a general-purpose distributed memory caching system. It is often used to speed up dynamic database-driven websites by caching data and objects in RAM to reduce the number of times an external data source (such as a database or API) must be read.

> Memcached's APIs provide a very large hash table distributed across multiple machines. When the table is full, subsequent inserts cause older data to be purged in least recently used (LRU) order. Applications using Memcached typically layer requests and additions into RAM before falling back on a slower backing store, such as a database.

> The size of this hash table is often very large. It is limited to available memory across all the servers in the cluster of servers in a data centre. Where high volume, wide audience web publishing requires it, this may stretch to many gigabytes. Memcached can be equally valuable for situations where either the number of requests for content is high, or the cost of generating a particular piece of content is high.

---

## Difference with Redis

*From: [StackOverflow](http://stackoverflow.com/questions/10558465/memcached-vs-redis)*

 > They are both lightning fast as volatile caches. While that's all that memcached is, it's only the tip of the redis iceberg. Memcached is a volatile in-memory key/value store. Redis can act like one (and do that job as well as memcached), but it is a data structure server.
