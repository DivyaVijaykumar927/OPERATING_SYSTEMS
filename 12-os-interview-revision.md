# 12. OS Interview Revision

## One-line definitions
- **Operating system:** Manages resources and provides services to applications.
- **Kernel:** Core privileged component of the OS.
- **Shell:** Command interpreter used to issue commands.
- **System call:** Controlled request from a program to the OS kernel.
- **Program:** Passive instructions stored as a file.
- **Process:** Running instance of a program.
- **Thread:** Unit of execution within a process.
- **PCB:** Data structure containing process-management information.
- **Scheduler:** Chooses a ready process/thread to execute.
- **Context switch:** Saves one execution context and restores another.
- **Race condition:** Result depends on timing/order of concurrent operations.
- **Mutex:** Lock used to provide mutual exclusion.
- **Semaphore:** Counter-based synchronization primitive.
- **Deadlock:** Processes are stuck waiting on resources/events held by one another.
- **Paging:** Divides virtual memory into pages and physical memory into frames.
- **Virtual memory:** Gives processes virtual address spaces mapped to physical resources.
- **Page fault:** OS handling triggered by a memory access needing resolution.
- **File system:** Organizes files, directories, metadata, and storage allocation.
- **Driver:** Software that helps OS communicate with hardware.
- **Interrupt:** Event signal requiring CPU/OS attention.
- **DMA:** Device-supported memory transfer with less CPU involvement in copying data.

## Common comparisons

### Program vs process
Program = stored instructions; process = executing instance with state and resources.

### Process vs thread
A process has its own address space and resources. Threads execute within a process and commonly share its memory/resources while keeping their own execution state and stack.

### User mode vs kernel mode
User mode restricts application privileges. Kernel mode permits protected OS operations.

### Mode switch vs context switch
Mode switch changes privilege level. Context switch changes the executing process/thread.

### Multiprogramming vs multitasking
Multiprogramming keeps several jobs available so the CPU can work while another waits for I/O. Multitasking emphasizes switching among tasks for concurrent progress and responsiveness.

### Multiprocessing vs multitasking
Multiprocessing uses multiple CPU cores/processors for parallel execution. Multitasking lets tasks share CPU time; it can occur even on one core.

### Deadlock vs starvation
Deadlock: a set of tasks cannot progress due to mutual resource waits. Starvation: one task waits indefinitely while other tasks may continue.

### Paging vs segmentation
Paging uses fixed-size pages/frames. Segmentation divides a program into logical variable-sized units.

### Cache vs buffer
A cache retains data to speed future access. A buffer temporarily holds data during transfer or processing.

## Practice questions
1. What does an OS do?
2. Explain kernel, shell, and device driver.
3. Walk through the steps when a camera app captures a photo.
4. What is a system call? Name common categories.
5. Explain a process's memory layout.
6. What information is stored in a PCB?
7. Explain process states.
8. Compare FCFS, SJF, Priority, and Round Robin scheduling.
9. What is a race condition? How does a mutex help?
10. Name the four necessary conditions for deadlock.
11. Compare paging and segmentation.
12. What is a page fault? Is every page fault an error?
13. Explain the role of a file system.
14. Explain interrupts and DMA.
15. Describe the boot sequence.

## Short answers
1. An OS manages CPU, memory, storage, devices, and security, while providing services for applications.
2. Kernel manages protected resources; shell interprets commands; drivers communicate with devices.
3. App requests camera access; OS checks permissions; driver/framework coordinates with hardware; app processes data; storage services help save it.
4. A system call requests a kernel service; categories include process, file, memory, communication, and device operations.
5. Common regions include text/code, data/BSS, heap, stack, and mappings.
6. PID, state, scheduling, CPU context, memory details, I/O/open files, accounting, and credentials.
7. New, Ready, Running, Waiting/Blocked, Terminated.
8. FCFS follows arrival order; SJF favors short bursts; Priority favors priority; RR gives each task a time quantum.
9. A race condition depends on operation timing; a mutex allows one participant into a protected region at a time.
10. Mutual exclusion, hold and wait, no preemption, circular wait.
11. Paging uses fixed-size units; segmentation uses logical variable-sized units.
12. A page fault requests OS handling when an access cannot be completed directly; it can be a normal demand-paging event.
13. A file system manages names, directories, metadata, permissions, and storage mapping.
14. Interrupts signal events; DMA lets a device transfer data with less CPU involvement in copying.
15. Firmware initializes hardware, bootloader starts kernel, kernel initializes core facilities, then user-space services and interface start.

## Study plan
- Day 1: OS basics, kernel, system calls.
- Day 2: Processes, threads, process states.
- Day 3: CPU scheduling; solve Gantt-chart questions.
- Day 4: Synchronization and deadlocks.
- Day 5: Memory management and virtual memory.
- Day 6: File systems, I/O, drivers, interrupts, DMA.
- Day 7: Linux commands and interview revision.
