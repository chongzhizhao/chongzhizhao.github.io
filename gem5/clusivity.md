## What does "mostly inclusive/exclusive" mean?

In mem/cache/base.cc, allocOnFill() suggest that "mostly inclusive" ensures allocation upon fill.
This is called when a miss happens and marks the MSHR entry so it will be allocated. Thus, for
block allocation, the cache is strictly inclusive.

The more important question here is whether the same cache line in upper level caches are evicted
upon an eviction.

## Upon replacement eviction, is a cache line evicted from all cache levels?

The type of eviction I'm looking at is replacement eviction. It is triggered in this sequence:
BaseCache::access() or BaseCache::handleFill() >> BaseCache::allocateBlock() >> BaseCache::handleEvictions()
>> evictBlock(). The final function is virtually implemented in BaseCache but overriden in Cache.
After taking over, Cache::evictBlock() decides if the block shall be handled with BaseCache::writebackBlk()
or Cache::cleanEvictBlk(). In our case, my guess is that cleanEvictBlk() should be used to make a
packet before the invalidation. The packet is added to the writeback packet list that is then passed back
up the chain. In any event, Cache::doWritebacks() does not ask the same block to be evicted from upper
level caches.

BaseSetAssoc::findVictim() is responsible for returning a pointer to a potential victim by
consulting the replacement policy.

## What does it take to implement strict clusivity?

## How is clflush instruction implemented?


