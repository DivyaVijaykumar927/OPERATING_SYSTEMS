# 11. Linux Commands and Booting

## Useful Linux commands

| Command | Purpose |
|---|---|
| `uname -a` | Kernel/system information |
| `whoami` | Current username |
| `pwd` | Current directory |
| `ls -la` | List files, including hidden entries |
| `cd /path` | Change directory |
| `ps` | Show processes (default view varies) |
| `ps aux` | Broad process listing on many Linux systems |
| `top` | Live process/resource view |
| `free -h` | Memory usage |
| `df -h` | File-system disk usage |
| `du -sh folder` | Approximate space used by a folder |
| `uptime` | Uptime and load averages |
| `cat /proc/cpuinfo` | CPU details on Linux |
| `cat /proc/meminfo` | Memory details on Linux |
| `ip addr` | Network interfaces/addresses on many Linux distributions |
| `dmesg` | Kernel messages, subject to permissions/configuration |
| `kill PID` | Request termination of a process |
| `man command` | Open manual for a command |

**Safety:** Inspect a process before stopping it. Avoid killing system processes unless you understand the consequences. Some commands or paths differ by distribution.

## Process inspection example
```bash
ps aux
top
```
Find the PID of a process you own, understand what it does, and only then decide whether to stop it.

## File permissions
```bash
ls -l
chmod 640 notes.txt
```
On typical Unix permissions, `640` means owner read/write, group read, others no access. Apply permissions carefully.

## Boot sequence
```text
Power on
 -> BIOS/UEFI firmware initializes hardware
 -> Bootloader selected
 -> Kernel loaded into memory
 -> Kernel initializes memory, drivers, and core facilities
 -> User-space services start
 -> Login manager / user interface appears
```
Actual boot flow varies by OS and hardware. Embedded devices may include additional boot stages.

## What happens after login?
The system starts or connects to a user session, launches a desktop shell or command shell, and applications can be started. Background services may continue running independently of the logged-in user.

## Useful practice tasks
1. Run `uname -a` and identify the kernel/system information.
2. Run `free -h` and note total and available memory.
3. Run `df -h` and identify the file system mounted at `/`.
4. Run `ps aux` and find a process name and PID.
5. Run `pwd`, `ls`, and `cd` to navigate directories.
