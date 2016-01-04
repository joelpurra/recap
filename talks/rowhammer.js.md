# Rowhammer.js: Root privileges for web apps?

> Insanity: doing the same thing over and over again and expecting different results.

-- *Albert Einstein - Who did not live long enough to see Rowhammer*
 
 *Recent studies have found that repeated accesses to DRAM rows can cause random bit flips, resulting in the so called Rowhammer vulnerability. We present Rowhammer.js, the first remote software-induced hardware-fault attack, from JavaScript. We also extend our presentation with an overview of cache side-channel attacks, that use the same technique to evict data from the cache.*

 Clémentine Maurice, Daniel Gruss

- History
  - 2014-06: flipping bits without accessing them, using `clflush` instruction seen as a reliability issue.
  - 2015-03: first exploits published.
- DRAM organization.
  - DRAM has ranks, rows, cells.
  - Cells lose electricity and needs to be recharged periodically, or they become unstable.
  - Cells lose more electricty when nearby rows are accessed.
  - Reading neighbor rows speeds up the process, and can lead to bit flips.
  - Reading the same data over and over needs to be done without cache; done using `clflush`.
- Rowhammer with `clflush`.
  - Targets addressing rows with a flush+reload.
  - Measure timing (cache hit vs miss).
  - Run on shared libraries to spy on other processes.
  - Automated attackes reading crypto keys, creating keyloggers etcetera.
- Rowhammer without `clflush`.
  - No `clflush` outside of x86, and not accessible from javascript.
  - Access memory, fill up cache.
  - Reload data from memory.
  - How to get physical address in javascript?
  - How to ...
  - How to ...
  - How to ...
- Physical addresses and DRAM.
  - Fixed map from physical address to DRAM cells.
  - Undocumented by Intel.
  - Operating systems use 2MB memory pages.
  - The last 21 bits of the physical addresses, are the same as the 21 bit virtual address, is the same 21 bits of JS array indices.
  - Pages cross several rows; need to check timing to make sure to get data from page.
  - An Intel hash function maps addresses to slices; reverse engineered.
  - Older CPUs replace older cache entries first.
    - Need to repeate reads to evict old cache entry.
  - Newer CPUs don't use LRU; 75% success rate on Haswell, which is too slow.
    - Using a new cache flush strategy which takes care of proper eviction; now 99.7% success rate.
- How to get accurate timing in javascript.
  - Timing is rounded to 5 microseconds to avoid some other attacks.
  - Refresh interval can be tweaked.
  - Can get more than 10 bit flips per second using javascript.
- Implementation.
  - Idea: part original root exploint.
    - Uses pge table spraying.
    - Needs shared memory, which isn't available in JS.
    - Another paper shows some shared memory in JS.
  - Physical memory acces exploit in native code:
    - 

Out of battery.
