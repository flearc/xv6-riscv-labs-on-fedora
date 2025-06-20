# xv6
## CH1: Operating system interfaces

### 1.1 Processes and memory

### fork

`int fork()`

1. create a new process, return child's PID
2. duplicate the parent's memory

### exec

`int exec(char *file, char *argv[])`

1. Load a file and execute it with arguments; only returns if error.

### 1.2 I/0 and File descriptors

FD(file descriptor): a small integer representing a kernel-managed object that a process may read from or write to.

xv6 kernel uses the file descriptor as an index into a **per-process** table.

1. `fork` copies parent's file descriptro tabel, so it starts with exactly the same open files as the parent, but underlying file offset is shared between parent and child.
2. `exec` replace memory but preserve file table

### 1.3 Pipes

`pipe`：a small kernel buffer exposed to processes as a pair of file descriptors, one for reading and one for writing.

### 1.4 File system

`inode` is the underlying file that holds metadata about a file, including file type, length, location of file's content on disk and the number of links to a file.
