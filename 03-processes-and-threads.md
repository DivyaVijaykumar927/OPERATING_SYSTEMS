# 3. Processes and Threads

## Program vs process
A **program** is a passive set of instructions stored in a file. A **process** is an executing instance of a program.

| Program | Process |
|---|---|
| Instructions stored on disk | Running instance |
| Passive | Has execution state and resources |
| Does not need a PID just because it exists as a file | Has a process ID (PID) |
| Example: browser executable | Example: running browser process |

## What a process contains
A process typically has:
- Virtual address space.
- One or more threads.
- PID and security credentials.
- Scheduling state.
- Open files and I/O state.
- Memory-management information.

## Process memory layout
```text
Higher addresses
+-----------------------------+
| Stack: calls, local data    |
+-----------------------------+
| Memory mappings/libraries   |
+-----------------------------+
| Heap: dynamic allocations   |
+-----------------------------+
| Data/BSS: global/static data|
+-----------------------------+
| Text/code: instructions     |
+-----------------------------+
Lower addresses
```
This is conceptual; actual layouts vary by OS and program.

- **Text/code:** executable instructions, commonly read-only.
- **Data:** initialized global/static variables.
- **BSS:** typically zero-initialized or uninitialized global/static variables.
- **Heap:** runtime dynamic allocations.
- **Stack:** function calls, return addresses, and many local variables.
- **Mappings:** shared libraries, mapped files, and other regions.

## Process Control Block (PCB)
The PCB is an OS data structure that stores information needed to manage a process.

| Field | Meaning |
|---|---|
| PID | Process identifier |
| State | Ready, running, waiting, etc. |
| Scheduling info | Priority and queue details |
| CPU context | Registers and instruction position needed to resume |
| Memory info | Address-space details |
| I/O and open files | Resources associated with process |
| Accounting | CPU usage and other statistics |
| Credentials | Identity and permissions |

## Process states
```text
New -> Ready -> Running -> Terminated
          ^       |
          |       | waits for I/O/event
          |       v
          +---- Waiting
Running -> Ready when preempted/time slice ends
Waiting -> Ready when event completes
```
- **New:** being created.
- **Ready:** can run but waits for CPU.
- **Running:** currently executing on a CPU core.
- **Waiting/Blocked:** waiting for I/O or another event.
- **Terminated:** finished or stopped.

## What is a thread?
A **thread** is a unit of execution within a process. Threads in one process commonly share its address space and resources, while each thread has its own execution state and stack.

### Process vs thread

| Process | Thread |
|---|---|
| Own process identity and address space | Executes within a process |
| Stronger isolation from other processes | Threads in same process share memory |
| Communication often needs IPC | Can share data directly, requiring synchronization |
| More isolation overhead | Often cheaper to create/switch, depending on OS |

## Context switch
When switching from one task to another, the OS saves the current execution context and restores the next task's context.

## Real-life example: downloading a file
1. Browser runs on the CPU.
2. It requests network data.
3. It may block while waiting for data.
4. The scheduler runs another ready task.
5. When data arrives, the browser becomes ready.
6. It resumes processing the data.

## Process creation on Unix-like systems
- `fork()` creates a child process.
- `exec()` family replaces the current process program with a new one.
- `wait()`-family calls can let a parent wait for child status.
Exact behavior and APIs vary by OS.
