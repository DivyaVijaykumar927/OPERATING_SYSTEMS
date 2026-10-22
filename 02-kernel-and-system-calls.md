# 2. Kernel and System Calls

## Kernel
The kernel is the core of the OS. It remains active while the system runs and manages critical resources.

### Main functions
1. **Process management:** Create, schedule, and terminate processes/threads.
2. **Memory management:** Allocate memory, manage virtual memory, and enforce protection.
3. **Device management:** Coordinate hardware through drivers.
4. **File-system support:** Provide interfaces for file operations.
5. **Resource management:** Share CPU time and other resources.
6. **Security:** Enforce access control and isolation.
7. **Inter-process communication (IPC):** Support communication between processes.

## Kernel types

| Type | Design | Trade-off / example |
|---|---|---|
| Monolithic | Many OS services run in kernel space | Often efficient; faults in kernel code can have broad impact. Linux is commonly described as modular monolithic. |
| Microkernel | Small kernel; many services run in user space | Better separation may improve fault isolation, with communication overhead. MINIX 3 is an example. |
| Hybrid | Combines monolithic and microkernel ideas | Windows NT-family kernels and Apple's XNU are often described as hybrid. |
| Nanokernel | Term for a very small low-level kernel layer | Meaning varies by system. |
| Exokernel | Securely multiplexes hardware while allowing applications/libraries more direct control | Research design; MIT Exokernel/Xok. |

## What is a system call?
A **system call** is a controlled interface through which a program requests a service from the OS kernel.

Examples on Unix-like systems:
- `open()` — request access to a file.
- `read()` — read data.
- `write()` — write data.
- `fork()` — create a process.
- `execve()` — execute a program in the current process.
- `mmap()` — create a memory mapping.

A library function such as C `fopen()` is not itself necessarily a system call; it usually uses lower-level OS interfaces.

## System-call flow: read a file
```text
Application requests file data
 -> System-call interface
 -> CPU enters kernel mode
 -> Kernel validates request and permissions
 -> File system / driver retrieves data
 -> Kernel returns result or error
 -> Application continues
```

## Common categories

| Category | Purpose | Examples |
|---|---|---|
| Process control | Create/execute/terminate processes | `fork()`, `execve()`, `exit()` |
| File management | Open/read/write/close files | `open()`, `read()`, `write()`, `close()` |
| Memory management | Map or unmap memory | `mmap()`, `munmap()` |
| Communication | Exchange data | `pipe()`, `socket()` |
| Information/protection | Get IDs or change permissions | `getpid()`, `chmod()` |
| Device access | Interact with device interfaces | OS/device-specific interfaces |

## Mode switch vs context switch
- **Mode switch:** CPU changes privilege level, for example user mode to kernel mode.
- **Context switch:** CPU stops executing one process/thread and resumes another.
- A system call usually causes a mode switch, but not necessarily a context switch. A context switch may happen if the caller blocks or scheduling selects another task.

## Real-life analogy
A system call is like submitting a request at a service counter. The application asks for a service; the OS checks the request and performs the protected operation.
