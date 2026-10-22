# 8. Virtual Memory

## What is virtual memory?
Virtual memory gives each process a virtual address space. The OS and hardware map portions of that space to physical RAM and may keep some contents on storage when not resident in RAM.

Virtual memory is not simply the same as a disk swap file; it is an address-space abstraction that also supports protection, sharing, and demand loading.

## Demand paging
A page is brought into RAM when it is needed rather than necessarily loading every page at program startup.

### Page-fault flow
```text
Process accesses a virtual address
          |
          v
Page is not currently mapped as resident
          |
          v
Hardware raises a page fault
          |
          v
OS checks whether access is valid
     /                 \
 valid                 invalid
  |                       |
  v                       v
Find/load page        Signal/error/terminate
  |
  v
Update page table
  |
  v
Resume instruction
```
A page fault is not always an error. It can be a normal part of demand paging.

## Page replacement
If RAM frames are needed and no free frame is available, the OS may need to evict a page.

Common textbook algorithms:
- **FIFO:** evict the page that entered memory first.
- **Optimal:** evict the page whose next use is farthest in the future; theoretical benchmark, not generally implementable exactly.
- **LRU:** evict the page that has not been used for the longest time.
- **Clock/second chance:** practical approximation using reference information.

## Thrashing
Thrashing occurs when the system spends excessive time moving pages in and out of memory instead of doing useful work. It can happen when active working sets exceed available RAM.

Possible responses include reducing memory pressure, limiting concurrency, or adding RAM.

## Copy-on-write (COW)
Memory pages can initially be shared and copied only when a process attempts to modify them. This can make process creation more efficient.

## Swap
Swap space or a paging file can provide backing storage for some memory contents. Storage is much slower than RAM, so heavy paging can make a system sluggish.

## Quick comparison
- **Paging:** divides memory into fixed-size pages/frames.
- **Virtual memory:** gives processes virtual address spaces and maps them to physical resources.
- **Page fault:** an access needs OS handling, often because a page is not resident.
- **Thrashing:** excessive paging reduces useful progress.
