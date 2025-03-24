# Cache Memory Simulator

A web-based interactive simulator for demonstrating and understanding cache memory concepts in computer architecture.

## Overview

This project implements a visual cache memory simulator that helps users understand how cache memory works, including different mapping techniques, replacement policies, and cache performance metrics. The simulator provides a hands-on experience with cache operations and visualizes the internal state of the cache.

## Features

- Interactive cache configuration
- Visual representation of cache blocks and sets
- Support for different cache parameters:
  - Cache size (1KB, 2KB, 4KB)
  - Block size (16, 32, 64 bytes)
  - Associativity (Direct Mapped, 2-Way, 4-Way, 8-Way)
- Real-time statistics tracking
- Visual feedback for cache hits and misses
- Support for both read and write operations

## Cache Memory Theory

### Basic Concepts

1. **Cache Memory**
   - A smaller, faster memory that stores copies of frequently accessed data from main memory
   - Reduces average memory access time
   - Located between CPU and main memory

2. **Cache Parameters**
   - **Cache Size**: Total storage capacity of the cache
   - **Block Size**: Amount of data transferred between cache and main memory
   - **Associativity**: Number of blocks that can be stored in each cache set

3. **Cache Organization**
   - **Sets**: Groups of cache blocks
   - **Ways**: Number of blocks per set
   - **Tags**: Used to identify which memory block is stored in a cache block
   - **Valid Bit**: Indicates if the cache block contains valid data
   - **Dirty Bit**: Indicates if the cache block has been modified

### Mapping Techniques

1. **Direct Mapped Cache**
   - Each memory block maps to exactly one cache block
   - Simplest but least flexible mapping technique
   - Highest potential for cache conflicts

2. **Set-Associative Cache**
   - Memory blocks can map to any block within a specific set
   - Better hit rate than direct-mapped cache
   - More complex than direct-mapped cache
   - Implemented with 2-way, 4-way, and 8-way associativity options

### Replacement Policy

The simulator implements the Least Recently Used (LRU) replacement policy:
- Tracks the last access time for each cache block
- When a cache miss occurs, replaces the least recently used block in the set
- Helps maintain frequently accessed data in the cache

### Performance Metrics

The simulator tracks several important performance metrics:
1. **Total Accesses**: Number of memory access attempts
2. **Cache Hits**: Number of successful cache accesses
3. **Cache Misses**: Number of failed cache accesses
4. **Hit Rate**: Percentage of successful cache accesses

## Technical Implementation

### Data Structures

1. **CacheBlock Class**
   ```javascript
   class CacheBlock {
       valid: boolean      // Indicates if block contains valid data
       dirty: boolean      // Indicates if block has been modified
       tag: number        // Memory block identifier
       lastUsed: number   // Last access timestamp
       data: Array        // Actual data stored in block
   }
   ```

2. **CacheSimulator Class**
   - Manages the overall cache structure
   - Handles memory access operations
   - Implements cache policies and replacement strategies
   - Tracks performance statistics

### Key Functions

1. **Address Translation**
   - `getSet(address)`: Determines which set an address maps to
   - `getTag(address)`: Extracts the tag bits from the address

2. **Cache Operations**
   - `accessMemory(address, isWrite)`: Handles read/write operations
   - `getLRUBlock(setIndex)`: Implements LRU replacement policy

3. **Visualization**
   - Real-time display of cache state
   - Visual feedback for hits and misses
   - Statistics updates

## Usage

1. Configure the cache parameters:
   - Select cache size
   - Choose block size
   - Set associativity level

2. Initialize the cache

3. Perform memory operations:
   - Enter a memory address
   - Choose read or write operation
   - Observe cache behavior and statistics

4. Monitor performance metrics and cache state

## Educational Value

This simulator helps users understand:
- Cache memory organization and operation
- Different mapping techniques and their trade-offs
- Cache performance factors
- Memory hierarchy concepts
- Cache replacement policies

## Technologies Used

- HTML5
- CSS3
- JavaScript (ES6+)
- Modern web development practices

## Future Enhancements

Potential improvements could include:
- Support for different replacement policies
- Visualization of memory hierarchy
- Cache coherence protocols
- Prefetching mechanisms
- More detailed statistics and analysis tools 