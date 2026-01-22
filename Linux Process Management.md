# Linux Process Management

## What Is a Process?
A process is a **running instance of a program**.

- Every command you run creates a process
- Linux manages processes using the kernel
- Each process has a unique Process ID (PID)

---

## Process Identification

### PID (Process ID)
- Unique number assigned to each process
- Used to track and control processes

### PPID (Parent Process ID)
- PID of the process that started the current process

Example:
ps -ef

---

## Types of Processes

### Foreground Process
- Runs in the terminal
- Blocks the terminal until completion

Example:
ls

---

### Background Process
- Runs in the background
- Terminal remains free

Example:
command &

---

### Daemon Process
- Runs in background continuously
- Usually started at boot

Examples:
- sshd
- docker
- kubelet

---

## Process States
Common process states in Linux:

- R → Running
- S → Sleeping
- D → Uninterruptible sleep
- T → Stopped
- Z → Zombie

---

## Zombie Process

### What Is a Zombie Process?
- Process that has completed execution
- Still has an entry in process table
- Parent process has not collected exit status

Key point:
- Zombie uses NO CPU or memory
- Too many zombies can exhaust PID table

---

## Orphan Process

### What Is an Orphan Process?
- Parent process is terminated
- Child process is still running
- Adopted by init/systemd (PID 1)

---

## Viewing Processes

### ps Command
Shows snapshot of current processes.

ps -ef  
ps aux  

---

### top / htop
- Real-time process monitoring
- Shows CPU and memory usage

top  
htop  

---

## Killing Processes

### kill Command
Sends a signal to a process.

kill PID

---

### Common Signals
- SIGTERM (15) → Graceful stop
- SIGKILL (9) → Force stop
- SIGSTOP (19) → Pause process

Example:
kill -9 PID

Important:
SIGKILL cannot be ignored by a process.

---

## Process Priority (nice & renice)

### nice
- Sets priority at process start
- Range: -20 (highest) to 19 (lowest)

nice -n 10 command

---

### renice
- Changes priority of running process

renice -5 PID

---

## Process Resource Usage

### CPU Usage
- User
- System
- Idle
- I/O wait

---

### Memory Usage
- RSS → Actual memory used
- VSZ → Virtual memory size

---

## Real Production Scenarios

### High CPU Usage
Steps:
- Identify process using top
- Check logs
- Restart or tune process

---

### Application Hung
Steps:
- Try SIGTERM
- If not responding, use SIGKILL

---

## Interview Summary
A process is a running program identified by a PID. Linux supports foreground, background, daemon, zombie, and orphan processes. Processes are managed using tools like ps, top, kill, and systemd, with priorities controlled by nice and renice.

---

## Key Takeaways
- Every running program is a process
- PID uniquely identifies a process
- Zombie processes are not fully cleaned up
- kill -9 is forceful and unsafe if misused
- nice controls CPU priority
