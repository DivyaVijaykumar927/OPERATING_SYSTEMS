# 1. Introduction to Operating Systems

## What is an OS?
An **Operating System (OS)** is system software that manages hardware and software resources and provides common services to applications. Examples include Windows, Linux, macOS, Android, and iOS.

```text
User
  |
Applications (browser, camera, music player)
  |
Operating System (kernel, drivers, system services)
  |
Hardware (CPU, RAM, storage, camera, display, network)
```

## Real-life example: Take a photo
1. You tap Capture in the camera app.
2. The app requests camera access through OS camera services.
3. The OS checks permissions and coordinates with the driver.
4. The camera hardware captures data.
5. The app processes the image.
6. OS file/storage services help save the image.
7. The image appears in Gallery.

## Why do we need an OS?
- Run programs.
- Share CPU time.
- Allocate and protect memory.
- Manage files and storage.
- Coordinate input/output devices.
- Enforce security and permissions.
- Handle errors and support networking.

## Goals and functions

| Function | Meaning | Example |
|---|---|---|
| Program execution | Provide the environment to run programs | Launch a browser |
| CPU management | Schedule processes/threads | Share CPU between apps |
| Memory management | Allocate and protect RAM | Isolate app memory |
| File management | Create/read/write files | Save a photo |
| I/O management | Coordinate devices | Read keyboard input |
| Security | Check identity and permissions | Screen lock and file access |
| Reliability | Handle faults and errors | Report an app crash |
| Communication | Let processes exchange data | Browser and helper process |

## Components
- **Kernel:** Core privileged part of the OS; manages processes, memory, and protected resources.
- **Shell:** Command interpreter, such as Bash or PowerShell.
- **GUI:** Windows, icons, menus, and buttons.
- **Device driver:** Software that helps the OS communicate with hardware.
- **System services:** Background facilities such as networking, logging, and updates.

The shell and GUI are ways to interact with an OS; neither is the kernel.

## Types of operating systems

| Type | Main idea | Example use |
|---|---|---|
| Batch | Run grouped jobs with little interaction | Payroll processing |
| Multiprogramming | Keep multiple jobs in memory to use CPU efficiently | Run another job while one waits for I/O |
| Multitasking/time-sharing | Share CPU time among tasks/users | Browser, music, editor |
| Multiprocessing | Use multiple CPU cores/processors | Parallel workloads |
| Distributed computing/OS | Coordinate multiple computers | Compute cluster |
| Network OS | Provide shared network services | Office file server |
| Real-time OS | Meet predictable timing requirements | Embedded control |
| Mobile OS | Manage phone/tablet hardware and apps | Android, iOS |

These categories can overlap; modern systems may support several properties.

## User mode and kernel mode
- **User mode:** Restricted mode for most applications.
- **Kernel mode:** Privileged mode used for protected OS operations.

Applications request protected services through OS interfaces instead of freely accessing hardware.

## Boot sequence
```text
Power on
 -> Firmware (BIOS/UEFI) initializes hardware
 -> Bootloader starts
 -> Kernel loads and initializes core facilities
 -> System services start
 -> Login screen / user interface appears
```

## Quick revision
- OS = resource manager and service provider.
- Kernel = core of the OS.
- Shell = command interpreter.
- Driver = helps OS communicate with a device.
- Multitasking = tasks make progress by sharing CPU time.
- Multiprocessing = multiple CPU cores/processors execute work.
