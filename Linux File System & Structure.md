# Linux File System & Structure

## What is the Linux File System?
Linux uses a single-root directory structure.

- Everything starts from the root directory `/`
- There are no drive letters like Windows (C:, D:)
- Files, directories, devices, and processes are treated as files

---

## Root Directory `/`
- `/` is the top-level directory
- All other directories exist under `/`
- If `/` fails, the system cannot boot

Example directory structure:
/
├── bin
├── etc
├── home
├── var
└── tmp

---

## Important Linux Directories

### /bin
- Essential user commands
- Required for basic system operation and recovery mode

Examples:
- ls
- cp
- mv
- cat

---

### /sbin
- System administration commands
- Mostly used by root user

Examples:
- reboot
- fsck
- iptables

---

### /etc
- Configuration files for system and applications
- Contains only text-based configuration files

Examples:
- /etc/passwd → user details
- /etc/shadow → encrypted passwords
- /etc/ssh/sshd_config → SSH configuration

Interview note:
If you want to change system behavior, you check /etc.

---

### /var
- Variable data that changes frequently
- Data grows over time

Examples:
- /var/log → system and application logs
- /var/cache → cached files

Production note:
Most disk full issues occur due to /var/log.

---

### /home
- Home directories for normal users
- Each user has a separate directory

Examples:
- /home/devops
- /home/admin

---

### /opt
- Optional or third-party software
- Commonly used in enterprise environments

Examples:
- /opt/jenkins
- /opt/tomcat

---

### /tmp
- Temporary files
- Files are cleared automatically (reboot or cleanup jobs)
- Uses sticky bit so users cannot delete others’ files

---

### /proc
- Virtual filesystem
- Does not consume disk space
- Provides real-time kernel and process information

Examples:
- /proc/cpuinfo
- /proc/meminfo

---

### /sys
- Virtual filesystem for hardware and kernel information
- Used for advanced system and device control

---

### /dev
- Device files representing hardware
- Hardware is treated as files

Examples:
- /dev/sda → hard disk
- /dev/null → discards output
- /dev/random → random data generator

---

## Absolute vs Relative Path

Absolute Path:
- Starts from the root `/`
Example:
/etc/passwd

Relative Path:
- Based on current directory
Example:
../logs/app.log

---

## Inode Concept
Inode stands for index node. When a file is created in Linux, the system allocates an inode that stores metadata like permissions, owner, size, and pointers to the actual data blocks. 
The directory maps the filename to the inode number, which is how Linux locates the file.
- Every file has an inode
- Inode stores:
  - File size
  - Owner
  - Permissions
  - Disk block location
- Filename is NOT stored in inode

Directory maps:
filename → inode

---

## File Types in Linux
- Regular file (-)
- Directory (d)
- Symbolic link (l)
- Block device (b)
- Character device (c)

---

## Virtual File Systems
- Exist only in memory
- Created dynamically by the kernel

Examples:
- /proc
- /sys

---

## Interview Summary
Linux follows a single-root filesystem starting from `/`. Configuration files are stored in `/etc`, logs and variable data in `/var`, user data in `/home`, and real-time kernel information is exposed through virtual filesystems like `/proc`.

---

## Key Takeaways
- Everything starts from `/`
- /etc → configuration
- /var → logs and variable data
- /home → user data
- /proc → live system information
