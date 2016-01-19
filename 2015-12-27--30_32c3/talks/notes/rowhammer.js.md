# Rowhammer.js: Root privileges for web apps?

*A tale of fault attacks on DRAM and attacks on CPU caches*

> Insanity: doing the same thing over and over again and expecting different results.
>
> -- *Albert Einstein - Who did not live long enough to see Rowhammer*
 
*Recent studies have found that repeated accesses to DRAM rows can cause random bit flips, resulting in the so called Rowhammer vulnerability. We present Rowhammer.js, the first remote software-induced hardware-fault attack, from JavaScript. We also extend our presentation with an overview of cache side-channel attacks, that use the same technique to evict data from the cache.*

 Clémentine Maurice, Daniel Gruss

- https://events.ccc.de/congress/2015/Fahrplan/events/7197.html
- https://media.ccc.de/v/32c3-7197-rowhammer_js_root_privileges_for_web_apps


## Talk notes

- History
    - 2014-06: flipping bits without accessing them, using `clflush` (cache line flush) instruction seen as a reliability issue.
    - 2015-03: first exploits published.
    - 2015-06: first exploits without `clflush` published.
- DRAM organization.
    - DRAM has banks, rows, cells.
    - Cells lose electricity and needs to be recharged periodically, or they become unstable.
    - Cells lose more electricity when nearby rows are accessed.
    - Reading neighbor rows speeds up the process, and can lead to bit flips.
    - Reading the same data over and over needs to be done without cache; done using `clflush`.
- Rowhammer with `clflush`.
    - Targets addressing rows with a flush+reload.
    - Measure timing (cache hit vs miss).
    - Run on shared libraries to spy on other processes.
    - Automated attacks reading crypto keys, creating keyloggers etcetera.
- Rowhammer without `clflush`.
    - No `clflush` outside of x86, and not accessible from javascript.
    - Access memory, fill up cache.
    - Reload data from memory.
- Rowhammer.js: the challenges.
    1. How to get physical address in javascript?
    1. Which physical addresses to access?
    1. In which order to access them?
    1. How to get accurate timings in javascript?
- Rowhammer.js solutions.
    1. Physical addresses and DRAM.
        - Fixed map from physical address to DRAM cells.
        - Undocumented by Intel.
        - Operating systems use 2MB memory pages. 2MB is 21 bits.
        - The last 21 bits of the physical addresses, are the same as the last 21 bits of the virtual address, is the same last 21 bits of JS array indices.
    1. Get physical memory addresses.
        - Assume cache uses least recently used (LRU) replacement.
        - Pages cross several rows; need to check timing to make sure to get data from page.
        - An Intel "hash" (really XOR) function maps addresses to slices; it has been reverse engineered and can be calculated.
        - This way memory addresses can be mapped to memory banks/rows/cells.
    1. Cache flush strategies.
        - Older CPU models replace oldest cache entries first (LRU).
            - Need to repeat reads to evict old cache entry.
        - Newer CPUs don't use LRU; 75% success rate on Haswell, which is too slow.
            - Using a new cache flush strategy which takes care of proper eviction; now 99.7% success rate.
    1. How to get accurate timing in javascript.
        - `window.performance.now()`
            - Timing is rounded to 5 microseconds to avoid some other attacks (cache attacks, used to track mouse movements).
            - Rounding not a problem for Rowhammer.js, as it makes millions of accesses.
        - DRAM refresh interval (microseconds) can be tweaked in BIOS.
            - Rowhammer.js requires a higher refresh interval (>25 µs) than `clflush` and native eviction strategies (>15µs).
            - Maximum number of bit flips per 15 minutes are about 10^5 for both `clflush`, native eviction and Rowhammer.js.
                - This means more than 10 bit flips per second using javascript.
                - Results are hardware dependent.
- Implementation.
    - Idea: part original root exploit.
        - Uses page table spraying.
        - Needs shared memory, which isn't available in JS.
        - Another paper shows some shared memory in JS; all zero data pages are deduplicated to a single memory address (to save memory).
    - Physical memory access exploit is similar to native code rowhammer exploits, but needs to target the write bit using the zero data page.
- Solution.
    - Dynamic row refreshing, based on number of reads.
        - Needs new hardware; can't patch legacy systems.
    - Increase the refresh rate.
        - Usually by doubling the refresh rate.
        - Needs BIOS updates -- but who does that?
    - Patch OS.
        - If a program can rowhammer only it's own process, some problems are mitigated.
        - Limit problems by not sharing memory pools across (OS) privilege levels for the pages.
- Conclusion.
    - Cache eviction is fast enough to replace `clflush`.
    - This allows for exploits in any programming language.
    - This allows attacks on any hardware (with DRAM), such as cell phones.
    - Look out for a release of Rowhammer.js.


## Links

- https://github.com/IAIK/rowhammerjs
- https://github.com/IAIK/rowhammerjs/blob/master/javascript/rowhammer.js
- https://en.wikipedia.org/wiki/Row_hammer
- http://www.rowhammer.com/
- https://github.com/google/rowhammer-test


---

Part of [Recap](https://github.com/joelpurra/recap)

