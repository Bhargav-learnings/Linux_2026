# Linux CPU and Memory Management

## What Is CPU and Memory Management?
Linux CPU and memory management controls **how system resources are allocated to processes** to ensure stability, performance, and fairness.

The kernel is responsible for:
- Scheduling CPU time
- Allocating and freeing memory
- Preventing a single process from exhausting system resources

---

## CPU Management Basics

### CPU Scheduling
- Linux uses a scheduler to decide **which process runs on the CPU**
- Scheduling is preemptive and time-sliced
- Each process gets CPU time based on priority

---

### CPU States
CPU time is divided into different states:

- user → time spent running user processes
- system → time spent in kernel operations
- idle → CPU doing nothing
- iowait → CPU waiting for disk or I/O
- steal → CPU time taken by hypervisor (VMs)

---

### Load Average
Load average shows **how many processes are waiting for CPU**.

Displayed as:
1 min, 5 min, 15 min average

Rule of thumb:
- Load ≤ number of CPU cores → healthy
- Load > number of CPU cores → CPU pressure

Check load:
uptime  
top

---

## Memory Management Basics

### Physical Memory (RAM)
- Used to store running programs and data
- Faster than disk
- Limited resource

---

### Virtual Memory
- Linux uses virtual memory abstraction
- Processes see continuous memory even if RAM is fragmented
- Allows use of swap space

---

### Swap Memory
- Disk space used as extension of RAM
- Much slower than RAM
- Used when RAM is exhausted

Check swap:
free -h  
swapon -s

---

## Memory Usage Metrics

### RSS (Resident Set Size)
- Actual physical memory used by a process

### VSZ (Virtual Size)
- Total memory allocated, including unused and swapped memory

---

## Buffers and Cache
Linux uses free memory for performance.

- Buffers → metadata
- Cache → file data

Important:
Free memory is NOT wasted memory.

---

## OOM Killer (Out Of Memory)

### What Is OOM Killer?
- Kernel mechanism to protect the system
- Kills processes when memory is exhausted

OOM selects process based on:
- Memory usage
- Priority
- OOM score

Check OOM score:
cat /proc/PID/oom_score

---

## High Memory Usage Scenarios

### Memory Leak
- Process continuously consumes memory
- Not released after use

Symptoms:
- Increasing RSS
- Frequent OOM kills

---

### Swap Thrashing
- Excessive swapping between RAM and disk
- System becomes very slow

---

## Monitoring CPU and Memory

### Commands
top  
htop  
free -h  
vmstat  
mpstat

---

## Real Production Scenarios

### High CPU Usage
Steps:
- Identify process using top
- Check load average
- Analyze application behavior

---

### High Memory Usage
Steps:
- Identify process with high RSS
- Check for memory leaks
- Tune application or restart service

---

## Interview Summary
Linux manages CPU through scheduling and priorities and memory through RAM, cache, and swap. Load average indicates CPU pressure, while RSS and VSZ help analyze memory usage. The OOM killer protects the system by terminating processes when memory is exhausted.

---

## Key Takeaways
- CPU time is shared using scheduling
- Load average reflects CPU pressure
- Free memory is used for cache
- Swap is slower than RAM
- OOM killer prevents system crashes
