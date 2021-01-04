## Basics of cache

- A cache is a hardware or software component that stores data so that future requests for that data can be served faster.

## Why use cache?

- Reduce network calls.
- Avoid computations. Pre-compute and store results in cache.
- Reduce load on the database.

## Why not dump all data on cache?

- Hardware (SSD's) on which cache runs is expensive than the one on which a normal database runs.

- If we store a lot of data on cache then the search times will increase.

- Cache needs to have most relevant information according to requests that will come in the future.

- Loading and evicting data in a cache is called cache policy. Cache performance mainly depends on cache policy. Eg. LRU (Least Recently Used) where the latest/frequently needed entries are on top and the old ones are in the bottom and are removed eventually.

## Problems with poor eviction policy

- Extra network calls.
- Very small cache. The concept of constantly loading and deleting data in the cache without ever using the results is called thrashing.
- Consistency issues due to outdated data in the cache. Eg. One server updates some data in the database but another server serves the old data from cache.

## Where to place the cache?

- Cache can be placed in memory itself. It is fast and simple to implement. If a server fails then the data in the in memory cache is also lost. Consistency issue in caches in different servers. (model not suitable if data is sensitive)

- Cache can also be placed between the servers and the database as a global cache which is a bit slower but gives high accuracy (if a server crashes the data is not lost as in case of in memory cache). It can also be scaled independently.

In write through cache, data is simultaneously updated to cache and memory. This is simple and reliable and is used when there are no frequent write operations. It solves inconsistency problem. A data write will experience latency as we have to write to two locations.

In write back cache, data is updated only in the cache and updated into the memory in later time. The modified data is written to the memory only when it is removed from the cache. This mode has fast data write speed but data will be lost if a power failure occurs before the updated data is written to the memory.

## Cache Invalidation

Cache invalidation is a process where entries in a cache are replaced or removed.

Cache invalidation can be used to push new content to a client.

Some methods to invalidate a cache are:-

- Purge: Removes content from caching proxy immediately. When the client requests the data again, it is fetched from the application and stored in the caching proxy.

- Refresh: Fetches requested content from the application, even if cached content is available. The content previously stored in the cache is replaced with a new version from the application.

- Ban: A reference to the cached content is added to a blacklist. Client requests are then checked against this blacklist, and if a request matches, new content is fetched from the application, returned to the client, and added to the cache.