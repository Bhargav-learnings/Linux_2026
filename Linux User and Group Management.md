# Linux User and Group Management

## What Are Users and Groups in Linux?
Linux uses **users and groups** to control access to files, directories, and system resources.

- Every process runs as a user
- Permissions are evaluated based on:
  - User
  - Group
  - Others

---

## Types of Users

### Root User
- Superuser with full access
- UID = 0
- Can read, write, and execute anything

---

### Normal Users
- Created for human users
- UID usually starts from 1000
- Limited access based on permissions

---

### System Users
- Created for services and applications
- Usually have no login shell
- Examples: nginx, docker, mysql

---

## User Identification (UID)
- Every user has a unique UID
- Linux internally identifies users by UID, not username

Check UID:
id username

---

## Group Identification (GID)
- Every group has a unique GID
- Users belong to:
  - One primary group
  - Zero or more secondary groups

---

## Important User & Group Files

### /etc/passwd
- Stores user account information
- Does NOT store passwords

Fields:
username:x:UID:GID:comment:home:shell

---

### /etc/shadow
- Stores encrypted passwords
- Accessible only by root

---

### /etc/group
- Stores group information
- Lists group members

---

## Creating and Deleting Users

### Create User
useradd devops

Create user with home directory:
useradd -m devops

---

### Set Password
passwd devops

---

### Delete User
userdel devops

Delete user and home directory:
userdel -r devops

---

## Creating and Deleting Groups

### Create Group
groupadd admins

---

### Delete Group
groupdel admins

---

## Modifying Users

### Add User to Group
usermod -aG admins devops

Important:
- Use -a (append) to avoid removing existing groups

---

### Change User Shell
usermod -s /bin/bash devops

---

## Primary vs Secondary Group

- Primary group:
  - Assigned at user creation
  - New files inherit this group

- Secondary group:
  - Additional access permissions

Check groups:
groups devops

---

## Sudo Access

### What is sudo?
- Allows normal users to run commands as root
- Controlled via /etc/sudoers

---

### Grant Sudo Access
Add user to sudo group:
usermod -aG sudo devops

Or (RHEL-based):
usermod -aG wheel devops

---

### Check Sudo Access
sudo -l

---

## Password Aging Policies
Control password expiry and security.

Check password policy:
chage -l devops

---

## File Ownership and Users

- Every file has:
  - Owner (user)
  - Group

Change ownership:
chown user file.txt  
chown user:group file.txt

---

## Real Production Scenarios

### Application Permission Issue
Problem:
- App cannot read/write files

Fix:
- Ensure correct user ownership
- Ensure correct group membership

---

### Shared Directory for Team
Solution:
- Create group
- Add users to group
- Use setgid on directory

---

## Interview Summary
Linux uses users and groups to manage access control. Each user has a UID and belongs to one primary group and multiple secondary groups. Access is controlled through ownership, permissions, and sudo privileges.

---

## Key Takeaways
- Root user has UID 0
- UID and GID are what Linux actually uses
- Users and groups control access to resources
- Sudo allows controlled root access
- Incorrect user or group setup causes permission issues
