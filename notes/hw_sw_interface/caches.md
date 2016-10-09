# Yay, Caches!

Processor-Memory bottleneck - CPU growing faster and faster. But memory didn't evelove as fast as the processor. The memory latency and the bandwidth of data transfer is not fast enough.

Caches are memory closer to the processor. They are small.

Cache hit and miss. When a miss happens, the new block of data is loaded from the memory into the cache. There are two decisions to be made -

1. Placement policy - where to store this new block
2. Replacement policy - which block gets evicted from the cache now.

## Cache locality

Programs tend to use data or instructions which have been accessed recently or which are close by.

Temporal locality and spatial locality.

## Cost of cache misses

1. Miss rate: Fraction of memory references that are not found in the cache.

miss rate = 1 - hit rate

2. Hit time: time required to deliver a cache line to the processor. It includes the time to determine if the line is in the cache or not. For L1 it's 1-2 clock cycles.

3. Miss penalty: Time required to fetch the data in case of cache miss.

## Memory hierarchy

Each level in the hierarchy serves as a cache for the level below. The idea is to create an illusion that data is being served at the rate of the memory at the highest level.

1. Registers
2. On chip L1 Cache
3. On or off chip L2 Cache
3. Main memory DRAM
4. Local disks
5. Remote secondary storage - distributed file systems

Intel I7 memory hierarchy -

Each core has
1. 1 L1 cache for data - 32 KB, Access 4 cycles
2. 1 L1 cache for instruction - 32 KB, Access 4 cycles
3. 1 unified L2 cache - 256 KB, Access 11 cycles

1 L3 unified cache shared by all the cores - 8 MB, Access 30-40 cycles

## Cache organization

Cache block/ cache line - size of memory that are loaded

### Direct mapped access
Way of mapping data from memory to the cache. For each memory location there's a single location in the cache.

### Associativity

Set associative caches - 2 places in a set where data could go.

Let's consider a cache of size 8 blocks.

1 way associativity - 8 sets, 1 block each. data can go to only a single location in the cache. direct mapping
8 way associativity - 1 set, 8 blocks. data can go anywhere in the cache. But lookup is expensive
2 way associativity - 4 sets, 2 blocks each. data can go to 2 locations in a set
4 way associativity - 2 sets, 4 blocks each. data can go to 4 locations in a set.


Where does the data go in a set associative cache?

m-bit address divided into 3 components

1. n-bit block offset - where inside the block
2. k bit index - which set in the cache
3. m - n - k bits tag - what data is stored in the cache

For instance, if the block size is 16 bytes, then we need 4 bits for the block offset.

In case of 2 way associativity, 4 sets of 2 blocks each, you need 2 bits for the index.

### General cache organization
<TODO>



## Notes to self

Okay. Each block in the cache can be n bytes. That means n bytes from memory are loaded into the cache together even if only 1 byte is needed. There can be m blocks in the cache. If it's a set associative cache, a cache can be divided into k sets. Now if k == m, then it's a directly mapped cache. Otherwise each of those k sets can contain (m / k) blocks.
