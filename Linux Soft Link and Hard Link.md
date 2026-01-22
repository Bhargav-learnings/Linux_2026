# Linux Soft Link and Hard Link (with ln -i and ls -i)

## What Are Links in Linux?
Links allow **multiple names to reference the same file or file data**.  
Linux provides two types of links:
- Hard Link
- Soft Link (Symbolic Link)

---

## Hard Link

### What Is a Hard Link?
A hard link is **another filename pointing to the same inode** as the original file.

- Shares the same inode
- Shares the same data blocks
- File data exists as long as at least one hard link exists

---

### Create a Hard Link
ln file1 file2

---

### Key Characteristics
- Same inode number for both files
- Deleting one filename does NOT delete file data
- Works only within the same filesystem
- Cannot be created for directories (by default)

---

## Soft Link (Symbolic Link)

### What Is a Soft Link?
A soft link is a **special file that points to another filename (path)**.

- Has a different inode
- Points to the original file path
- Acts like a shortcut

---

### Create a Soft Link
ln -s file1 file2

---

### Key Characteristics
- Different inode number
- Can cross filesystems
- Can link directories
- Becomes broken if original file is deleted

---

## ln Command Options (Important for Interviews)

### ln
- Creates a hard link by default
Example:
ln file1 file2

---

### ln -s
- Creates a soft (symbolic) link
Example:
ln -s file1 file2

---

### ln -i (Very Important)
- **Interactive mode**
- Prompts before overwriting an existing file

Example:
ln -i file1 file2

Meaning:
- If file2 already exists, Linux asks for confirmation before replacing it

Use case:
- Prevents accidental overwrite of existing files

---

## ls -i (Inode Display)

### What Does ls -i Do?
- Displays the **inode number** of files

Example:
ls -i file1 file2

Output:
12345 file1  
12345 file2  

Meaning:
- Both files share the same inode
- Confirms they are hard links

---

## Hard Link vs Soft Link (Comparison)

| Feature | Hard Link | Soft Link |
|------|---------|----------|
| Inode | Same inode | Different inode |
| Data blocks | Shared | Not shared |
| Delete original | Data remains | Link breaks |
| Filesystem | Same only | Can cross |
| Directories | Not allowed | Allowed |

---

## What Happens When You Delete the Original File?

### Hard Link
- Data is NOT deleted
- Other hard links still access the data

### Soft Link
- Link becomes broken
- Points to non-existing file

---

## Real Production Use Cases

### Hard Link Use Case
- Backup systems
- Saving disk space
- Ensuring data persistence

---

### Soft Link Use Case
- Application version switching
- Configuration management
- Path redirection

Example:
ln -s /opt/app/v2/app /usr/bin/app

---

## How Links Use Inodes

- Hard link: multiple filenames → same inode
- Soft link: filename → inode → path string

---

## Interview Summary
Hard links point directly to the same inode and share data blocks, while soft links are separate files that point to another file path. The ln -i option prevents overwriting existing files, and ls -i is used to display inode numbers for verification.

---

## Key Takeaways
- ln creates hard links by default
- ln -s creates soft links
- ln -i prevents accidental overwrite
- ls -i shows inode numbers
- Same inode confirms hard links
