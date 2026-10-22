# 7. Memory Management

## What is memory management?
Memory management is the OS function that allocates, tracks, protects, and releases memory for processes.

## Why it matters
- Multiple programs need RAM.
- One process should not freely overwrite another process's memory.
- Programs need a convenient memory abstraction.
- The OS must manage memory pressure and reclaim unused resources.

## Logical/virtual vs physical address
- **Virtual address:** address used by a process.
- **Physical address:** location in RAM.
- The memory-management hardware (often an MMU) and OS cooperate to translate virtual addresses to physical addresses.

```text
Process uses virtual address
          |
          v
MMU + page tables translate/check
          |
          v
Physical memory (RAM)
```

## Contiguous allocation
A process receives one continuous region of physical memory in simple allocation models.
- **Fixed partitions:** memory divided into fixed-size regions.
- **Variable partitions:** regions sized for processes.
- **External fragmentation:** free memory exists but is split into small separated holes.
- **Internal fragmentation:** allocated region contains unused space inside it.

## Paging
Memory is divided into fixed-size units:
- Virtual memory units: **pages**.
- Physical memory units: **frames**.
- A page table maps virtual pages to physical frames.

Advantages:
- Avoids external fragmentation in physical frame allocation.
- Supports virtual memory and protection.

Costs:
- Page tables consume memory.
- Address translation and page faults add overhead.

## Segmentation
A process is divided into logical variable-sized segments, such as code, data, and stack. Segmentation can reflect program structure but may suffer external fragmentation in systems using contiguous segment allocation.

Some systems combine concepts, and modern mainstream systems commonly rely heavily on paging.

## Memory protection and sharing
The OS and hardware restrict what a process can access. Shared memory can allow processes to share selected pages when configured deliberately.

## Memory allocation example
When an application opens:
1. OS creates a process address space.
2. Memory regions are mapped for code, data, stack, libraries, and other needs.
3. Physical frames are assigned as required.
4. Protection rules restrict access.
5. When the process exits, its resources can be reclaimed.

## Revision terms
Virtual address, physical address, MMU, page, frame, page table, internal fragmentation, external fragmentation, protection, sharing.
