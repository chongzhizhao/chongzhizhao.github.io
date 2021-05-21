Find an official explanation of the classic memory coherence
[here](https://www.gem5.org/documentation/general_docs/memory_system/classic-coherence-protocol/).

## What does "mostly inclusive/exclusive" mean?

In mem/cache/base.cc, allocOnFill() suggest that "mostly inclusive" ensures allocation upon fill.
This is called when a miss happens and marks the MSHR entry so it will be allocated. Thus, for
block allocation, the cache is strictly inclusive.

The more important question here is whether the same cache line in upper level caches are evicted
upon an eviction.

## Upon replacement eviction, is a cache line evicted from all cache levels?

The type of eviction I'm looking at is replacement eviction. It is triggered in this sequence:
BaseCache::access() or BaseCache::handleFill() >> BaseCache::allocateBlock() >> BaseCache::handleEvictions() >>
evictBlock(). The final function is virtually implemented in BaseCache but overriden in Cache.
After taking over, Cache::evictBlock() decides if the block shall be handled with BaseCache::writebackBlk()
or Cache::cleanEvictBlk(). In our case, my guess is that cleanEvictBlk() should be used to make a
packet before the invalidation. The packet is added to the writeback packet list that is then passed back
up the chain. In any event, Cache::doWritebacks() does not ask the same block to be evicted from upper
level caches.

BaseSetAssoc::findVictim() is responsible for returning a pointer to a potential victim by
consulting the replacement policy.

## What does it take to implement strict clusivity?

The basic idea should be sending a snoop to the upper level cache to see if the block is present.
If it is present, it must be invalidated. The problem with this idea is: can the upper level copy
have a more up-to-date version of data? If yes, it has to be written back.

My current idea is to let Cache::doWritebacks() prepared a packet in the event when the block
is found in any higher level cache. If the block is clean, just invalidate it. If dirty, write
back that block instead. The packet may be sent through ResponsePort::sendTimingSnoopReq() in the
cpuSidePort. The upstream cache, on the other hand, has to handle it in memSidePort with recvTimingSnoopReq().

Alternatively, BaseCache::memInvalidate() and memWriteback() seem to be good examples of using
BaseCache::invalidateVisitor(). However, the input argument is a pointer to the block to be invalidated,
which may be useless if we are initiating the invalidation from another cache. We probably need the
physical address.

## What is my current solution?

For now, I insert a block of code in BaseCache::handleEvictions() where an express snoop packet is made.
The packet contains a request that commands invalidation.
