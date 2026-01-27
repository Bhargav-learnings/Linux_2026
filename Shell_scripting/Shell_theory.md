# Day 1 – Shell Scripting Fundamentals (Complete Theory Notes)

These notes cover **ALL Day-1 shell scripting concepts** required before starting hands-on practice.
This level of understanding is expected from a **4+ years experienced DevOps engineer**.

---

## 1. What is a Shell?

A shell is a **command-line interpreter** that acts as an interface between the user and the Linux kernel.
It takes user commands, interprets them, and executes them.

---

## 2. What is Bash?

Bash (Bourne Again Shell) is a **type of shell**.
It is the most widely used shell in Linux systems and supports advanced scripting features such as variables, loops, functions, and arrays.

---

## 3. Difference Between Shell and Bash

- **Shell** is a general concept (command interpreter).
- **Bash** is a specific implementation of the shell.
- Bash is more powerful and commonly used in DevOps and production environments.

---

## 4. Which One Should We Use and Why?

Bash should be used because:
- It supports advanced scripting features
- It is the industry standard
- Most DevOps tools and CI/CD pipelines rely on Bash

---

## 5. What is a Shell Script?

A shell script is a file that contains a sequence of Linux commands that are executed line by line to automate tasks.

---

## 6. What is the Shebang (`#!/bin/bash`)?

The shebang tells the operating system **which interpreter** should be used to execute the script.

Example: (`#!/bin/bash`) 
---
## 7. What Happens If the Shebang Is Missing?

If the shebang is missing:

- The OS may not know which interpreter to use  
- The script may fail when executed directly using `./script.sh`

---

## 8. What is an Executable?

An executable is a file that:

- Has execute (`x`) permission  
- Can be run as a program  

Examples:
- Binary executables (`ls`, `docker`)
- Script executables (`.sh` files with execute permission)

---

## 9. What is `$PATH`?

`$PATH` is an environment variable that contains a list of directories where the shell searches for executable commands.

---

## 10. Is `$PATH` Used for All Commands?

No.

- `$PATH` is used only for executable commands  
- Built-in commands do **NOT** use `$PATH`

---

## 11. Built-in Commands vs Executables

- Built-in commands are part of the shell itself (e.g., `cd`, `echo`)
- Executables are external programs stored as files (e.g., `ls`, `bash`)

---

## 12. Why Do We Use `./script.sh`?

The current directory (`.`) is not included in `$PATH` by default for security reasons.  
Using `./` explicitly tells the shell to execute the script from the current directory.

---

## 13. What Does `chmod +x` Do?

`chmod +x` adds execute permission for:

- User (owner)
- Group
- Others

This allows the file to be executed as a program.

---

## 14. Difference Between `chmod +x` and `chmod u+x`

- `chmod +x` → adds execute permission for all (user, group, others)
- `chmod u+x` → adds execute permission only for the owner

---

## 15. What Are User, Group, and Others?

Linux file permissions are divided into:

- **User** – file owner
- **Group** – users belonging to the same group
- **Others** – all remaining users

This helps control access securely.

---

## 16. What Are Exit Codes?

Exit codes indicate the result of command execution:

- `0` → Success
- Non-zero → Failure

Exit codes are stored in `$?`.

---

## 17. Why Are Exit Codes Important in DevOps?

Exit codes are used in:

- Shell scripts
- CI/CD pipelines
- Automation workflows

They decide whether the next step should continue or fail.

---

## 18. Relative Path vs Absolute Path

- **Relative path** depends on the current directory  
  Example: `./script.sh`

- **Absolute path** starts from root `/`  
  Example: `/home/user/script.sh`

Automation tools prefer absolute paths.

---

## 19. Why Do Scripts Fail in Cron or Jenkins?

Scripts often fail because:

- Non-interactive shells load limited environment variables
- `$PATH` is minimal
- User profiles are not sourced

Using absolute paths avoids these issues.

---

