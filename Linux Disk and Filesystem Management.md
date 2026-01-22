# Linux Disk and Filesystem Management

## What Is Disk and Filesystem Management?
Disk and filesystem management in Linux deals with **how storage devices are organized, mounted, monitored, and maintained** so that data can be stored and accessed reliably.

---

## Disk vs Filesystem
- Disk → physical or virtual storage device
- Filesystem → structure used to store files on a disk

Example:
- Disk: /dev/sda
- Partition: /dev/sda1
- Filesystem: ext4, xfs

---

## Block Devices
Linux represents disks as block devices.

Common examples:
- /dev/sda → first disk
- /dev/sdb → second disk
- /dev/nvme0n1 → NVMe disk

List block devices:
lsblk

---

## Disk Partitions
Partitions divide a disk into logical sections.

Common partition types:
- Primary
- Extended
- Logical

View partitions:
lsblk  
fdisk -l

---

## Filesystems
A filesystem defines how data is stored and retrieved.

Common Linux filesystems:
- ext4 → most common
- xfs → high performance
- vfat → USB drives

Check filesystem type:
df -T

---

## Mounting Filesystems

### What Is Mounting?
Mounting attaches a filesystem to a directory so it can be accessed.

Syntax:
mount <device> <directory>

Example:
mount /dev/sdb1 /mnt/data

---

### Unmounting
Unmount a filesystem safely:

umount /mnt/data

---

## Persistent Mounts (/etc/fstab)

### What Is /etc/fstab?
- Configuration file for automatic mounting at boot

Example entry:
/dev/sdb1  /mnt/data  ext4  defaults  0  0

Check fstab without reboot:
mount -a

---

## Disk Usage Monitoring

### Disk Space Usage
df -h

Shows:
- Total space
- Used space
- Available space

---

### Directory Size
du -sh /var/log

---

## Inode Usage (Very Important)

### What Is Inode Exhaustion?
- Disk may show free space
- System still cannot create files
- Reason: inodes are exhausted

Check inode usage:
df -i

---

## Disk Full Troubleshooting (Production Scenario)

### Common Causes
- Large log files
- Too many small files
- Application writing endlessly

Steps:
1. Check disk usage (df -h)
2. Check inode usage (df -i)
3. Identify large directories (du -sh *)
4. Clean logs or rotate

---

## Logical Volume Manager (LVM)

### What Is LVM?
LVM allows **flexible disk management** without downtime.

Components:
- PV (Physical Volume)
- VG (Volume Group)
- LV (Logical Volume)

---

### Why LVM Is Used
- Resize disks online
- Combine multiple disks
- Better storage flexibility

---

## Swap Space

### What Is Swap?
- Disk space used as virtual memory
- Helps when RAM is exhausted

Check swap:
free -h  
swapon -s

---

## Real Production Scenarios

### Disk Full but Space Available
Cause:
- Inode exhaustion
- Deleted file still used by process

Check:
df -i  
lsof | grep deleted

---

### System Not Booting Due to Disk Issue
Common reason:
- / filesystem full
- /var full due to logs

---

## Interview Summary
Linux disk management involves handling block devices, partitions, filesystems, mounts, inode usage, and logical volumes. Disk full issues often relate to log growth or inode exhaustion, and LVM is widely used in production for flexible storage management.

---

## Key Takeaways
- Disk stores data, filesystem organizes it
- Mounting makes storage accessible
- /etc/fstab controls boot-time mounts
- Inode exhaustion can cause disk issues
- LVM provides flexibility in production
