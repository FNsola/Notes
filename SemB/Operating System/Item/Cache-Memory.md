# Cache Memory
> https://www.geeksforgeeks.org/cache-memory-in-computer-organization/  
> https://www.gatevidyalay.com/direct-mapping-cache-mapping/
## Overview
- Holds frequently requested data and instructions
- Reduce the average time to access data from the Main memory
- Checks for a corresponding entry in the cache first
- Allocates a new entry and copies in data from main memory for a cache miss  
  **Hit ratio = hit / (hit + miss) = no. of hits/total accesses**
- Higher cache block size, higher associativity to reduce miss rate
## Mapping
- Direct Mapping
  - Address space is split into index field(main memory) and tag field(cache)
  - Maps each block of main memory into one possible cache line  
    **Cache line number = (Main memory block number) Modulo (Number of lines in the cache)**
  - Trashed a old block if a new block needs to be loaded
  - Performance is directly proportional to the Hit ratio
  ![Direct Mapping](Image/direct_mapping.png)
- Fully Associative Mapping
  - A block of main memory can be mapped to any freely available cache line
  - Replacement algorithm is needed if the cache is full
    - Least Recently Used (LRU) - probably the most effective  
      **Replace the cache line that has been in the cache the longest with no references to it**
    - First-in First-out (FIFO)  
      **Replace the cache line that has been in the cache the longest**
    - Least Frequently Used (LFU)  
      **Replace the cache line that has experienced the fewest references**
    - Random  
      **Pick a line at random from the candidate lines**
  - More flexible than direct mapping
- K-way Set Associative Mapping
  - Cache lines are grouped into sets, each set contains k number of lines
  - A block of main memory can map to one set of the cache
  - Memory block can map to any freely available cache line  
    **Number of line in the in the cache number of sets = (Number of sets in cache) * (Number of liness in each set)
    **Cache set number = (Main memory block number) Modulo (Number of sets in cache)**
  ![Set Associative Mapping](Image/set_associative_mapping.png)
