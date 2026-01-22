# Linux File Permissions

## What Are File Permissions?
Linux file permissions define **who can access a file or directory and what actions they can perform**.  
Permissions are enforced by the kernel to ensure security and controlled access.

Permissions apply to three entities:
- Owner (user)
- Group
- Others (everyone else)

---

## Permission Types
Linux has three basic permission types:

- Read (r)
  - File: allows reading file content
  - Directory: allows listing files inside the directory

- Write (w)
  - File: allows modifying file content
  - Directory: allows creating, deleting, or renaming files

- Execute (x)
  - File: allows executing the file as a program or script
  - Directory: allows entering the directory (`cd`)

---

## Permission Display Format
Permissions are displayed using a 10-character string.

Example:
-rwxr-xr--

Breakdown:
- First character: file type (`-` file, `d` directory, `l` link)
- Next 3: owner permissions
- Next 3: group permissions
- Last 3: others permissions

---

## Numeric Permission Values
Each permission has a numeric value:
- Read (r) = 4
- Write (w) = 2
- Execute (x) = 1

Permission combinations:
- 7 = rwx
- 6 = rw-
- 5 = r-x
- 4 = r--

Common examples:
- 777 → rwxrwxrwx
- 755 → rwxr-xr-x
- 644 → rw-r--r--
- 600 → rw-------

---

## chmod (Change File Permissions)

### Numeric Method
chmod 755 script.sh

### Symbolic Method
chmod u+x script.sh  
chmod g-w file.txt  
chmod o+r file.txt  

Symbols:
- u → user
- g → group
- o → others
- a → all

---

## chown (Change Ownership)
Changes file owner and group.

chown user file.txt  
chown user:group file.txt  

Example:
chown devops:admins app.log

---

## chgrp (Change Group Ownership)
Changes only the group.

chgrp admins file.txt

---

## umask (Default Permission Control)
umask defines which permissions are **removed by default** when a file or directory is created.

Check current umask:
umask

Common umask values:
- 022 → files: 644, directories: 755
- 027 → files: 640, directories: 750

---

## Special Permissions

### SetUID (s)
- Applied to executable files
- Program runs with the file owner's privileges

Example:
chmod u+s binary

Use case:
- passwd command runs with root privileges

---

### SetGID (s)
- Applied to files or directories
- New files inherit the group ownership

Example:
chmod g+s shared_dir

Use case:
- Team-shared directories

---

### Sticky Bit (t)
- Applied to directories
- Users can delete only their own files

Example:
chmod +t /tmp

Use case:
- /tmp directory

---

## File vs Directory Permissions

### File
- r → read file content
- w → modify file content
- x → execute file

### Directory
- r → list directory contents
- w → create or delete files
- x → access files inside directory

Important note:
Without execute permission on a directory, files inside cannot be accessed even if file permissions allow it.

---

## Common Permission Issues in Production

### Permission Denied Error
Troubleshooting steps:
- Check file permissions
- Check directory permissions
- Verify ownership
- Check SELinux status if enabled

---

### Application Cannot Write Logs
Typical fix:
chown appuser:appgroup /var/log/app  
chmod 755 /var/log/app

---

## Interview Summary
Linux file permissions control access using read, write, and execute bits for owner, group, and others. Permissions are managed using chmod, chown, umask, and special permission bits like setuid, setgid, and sticky bit.

---

## Key Takeaways
- Permissions define access control
- Directories require execute permission to access files
- Numeric and symbolic permission modes exist
- Special permissions are widely used in production systems
- Incorrect permissions are a common cause of application failures
