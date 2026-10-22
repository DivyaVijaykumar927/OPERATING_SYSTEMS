# 9. File Systems

## What is a file system?
A file system organizes and manages files and directories on a storage device or another storage-backed resource.

## Common responsibilities
- Create/delete files and directories.
- Read and write file contents.
- Track metadata such as size, timestamps, and permissions.
- Map file data to storage.
- Enforce access permissions.
- Manage free space and consistency.

## File path example
`/home/divya/notes/os.md`
- `/` is the root directory on a Unix-like system.
- `home` is a directory beneath root.
- `divya` is a subdirectory.
- `notes` contains the file.
- `os.md` is the file name.

Windows often uses paths such as `C:\Users\Student\Documents\os.txt`.

## File operations
- Create
- Open
- Read
- Write
- Seek
- Close
- Rename
- Delete

## Metadata and permissions
Metadata can include file size, owner, timestamps, and access permissions. Permissions help control who can read, write, or execute a file.

On Unix-like systems, a simple permissions example is:
```bash
ls -l
chmod 640 notes.txt
```
`chmod 640` sets owner read/write, group read, and no permissions for others on typical Unix permission models. Use care when changing permissions.

## Directories
A directory maps names to file-system objects. Paths let users and applications locate files.

## File allocation concepts
- **Contiguous allocation:** file occupies consecutive storage blocks; access can be fast but growth can be difficult.
- **Linked allocation:** blocks link to the next block; sequential access is natural, random access may be costly.
- **Indexed allocation:** an index maps file data blocks; supports more flexible access but uses index storage.

Real file systems use more sophisticated structures, metadata, caching, journaling or copy-on-write techniques.

## Caching and buffering
- **Cache:** keeps copies of frequently used data to speed up later access.
- **Buffer:** temporarily holds data while it moves between components or operates at different speeds.

## File read flow
```text
Application requests read
 -> OS validates access
 -> File system finds file data
 -> Cache or storage driver supplies data
 -> OS returns bytes to application
```

## Revision questions
1. What is a file system?
2. What is file metadata?
3. Compare contiguous, linked, and indexed allocation.
4. What is the difference between caching and buffering?
5. Why do permissions matter?
