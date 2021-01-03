## Basics of Cache

- A cache is a hardware or software component that stores data so that future requests for that data can be served faster.

## Why use Cache?

- Reduce network calls.
- Avoid computations. Pre-compute and store results in cache.
- Reduce load on the database.

## Why not dump all data on Cache?

- Hardware (SSD's) on which cache runs is expensive than the one on which a normal database runs.
- If we store a lot of data on cache then the search times will increase.

- Cache needs to have most relevant information according to requests that will come in the future.

- Loading and evicting data in a cache is called cache policy. Cache performance mainly depends on cache policy. Eg. LRU (Least Recently Used) where the latest/frequently needed entries are on top and the old ones are in the bottom and are removed eventually.

## Problems with poor eviction policy

- Extra network calls.
- Very small cache. The concept of constantly loading and deleting data in the cache without ever using the results is called thrashing.
- Consistency issues due to outdated data in the cache. Suppose 1 server updates some data in the database but another server serves the old data from cache 

