# Virtual Memory

Programs refer to the virtual memory. The compiler and the run time decides where things should be stored.

## What problem the virtual memory solves?

1. How does everything fit? Since physical memory is much smaller than the address space (in case of 64 bit machine it's 2^64). Where to put what?
2. How to manage memory for muliple processes?
3. How to protect one process's memory from the another?
4. How to share memory between multiple processes. For instance the shared memories.

## How does Virtual memory implement the above features?

Using indirection.
The CPU generated addresses in virtual memory. Thent there's a MMU (Memory Management Unit) which maps the virtual memory address to either the physical memory or the hard disk.

## VM as a tool for caching

Think of VM as a memory on disk. And think of the physical memory as the cache for VM. Here the cache is divided into pages. Just like the blocks on the cache.

Many of the pages on VM may be unallocated which are not used.
Some of the pages are cached on the physical memory. We need a mapping for that.
Some of the pages are uncached. They are being used, but not loaded on the physical memory.

## How the mapping from virtual memory address to physical memory address is done?

Using a page table. A page table contains page table entries which contain mapping from virtual pages to physical pages.

There is one page table per each process.

### Address translation with a page table

A virtual address can be divided into

1. Virtual page number
2. Virtual page offset

Virtual page number is used to index into the page table to find the correct page table entry.

The page table entry will have 2 fields
1. Valid or invalid page
2. Physical Page Number

The physical address then becomes -> Physical Page Number and the Physical Page Offset (which is actually the Virtual Page Offset)

### Where's Page Table located?

A register Page Table Base Register holds the address of the page table.

## Memory management and protection

Each Page table entry contains bits -

1. if it's valid
2. If write is permitted
3. If it can be executed

The MMU checks the these bits before every memory access. If invalid access, the OS gives a segfault.

## Address translation

Translation Lookaside Buffer - a hardware cache for MMU. MMU stores the page table entry in the TLB.

## Confusion
How stack and heap on virtual memory are organized?
