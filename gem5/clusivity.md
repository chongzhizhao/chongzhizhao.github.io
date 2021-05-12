##What does "mostly inclusive/exclusive" mean?

In mem/cache/base.cc, allocOnFill() suggest that "mostly inclusive" ensures allocation upon fill.
This is called when a miss happens and marks the MSHR entry so it will be allocated. Thus, for
block allocation, the cache is strictly inclusive.

##Upon eviction, is a cache line evicted from all cache levels?

##How is clflush instruction implemented?

##How is a replacement eviction implemented?

