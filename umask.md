# Linux umask

## What is umask?
umask (User File Creation Mask) defines which permissions are removed from the default permissions when a new file or directory is created.  
umask does NOT give permissions. It only removes (masks) permissions.

## Default Permissions in Linux
Before umask is applied, Linux uses default permissions:
- Files: 666 (rw-rw-rw-)
- Directories: 777 (rwxrwxrwx)

Important: Files never get execute (x) permission by default for security reasons.

## How umask Works
Final Permission = Default Permission − umask  
umask specifies which permission bits must be removed.

## Common umask Values and Results

umask 022 (most common on servers)
- Files: 666 - 022 = 644 (rw-r--r--)
- Directories: 777 - 022 = 755 (rwxr-xr-x)

umask 002
- Files: 664 (rw-rw-r--)
- Directories: 775 (rwxrwxr-x)
Used when group members need write access.

umask 027
- Files: 640 (rw-r-----)
- Directories: 750 (rwxr-x---)
Used for stricter security.

## How to Check Current umask

Check numeric value:
umask

Example output:
0022

Check symbolic format:
umask -S

Example output:
u=rwx,g=rx,o=rx

## How to Set umask

Temporary (current shell session only):
umask 027

Permanent (user level):
Add the value in one of these files:
~/.bashrc
~/.profile

Example:
umask 022

Permanent (system-wide):
Configure in:
 /etc/profile
 /etc/login.defs
Used to enforce organization-wide security policies.

## Real-Time Example

umask 027
touch testfile
mkdir testdir
ls -l

Result:
-rw-r----- testfile
drwxr-x--- testdir

## Important Interview Points
- umask does NOT change existing files
- umask does NOT add permissions
- umask applies only at file or directory creation time
- umask is mainly used for security hardening

## Interview One-Liner (Must Remember)
umask defines which permission bits are removed from default permissions when a file or directory is created.

## Common Interview Questions

Why don’t files get execute permission by default?
Because of security reasons. Execute permission must be explicitly granted.

Why is umask important in servers?
To prevent accidental creation of world-writable files and to enforce security standards.

Does umask affect existing files?
No. It only applies at the time of file or directory creation.

## Summary
- umask = permissions to remove
- Default file permission = 666
- Default directory permission = 777
- Most common umask = 022
- Used for security and access control
