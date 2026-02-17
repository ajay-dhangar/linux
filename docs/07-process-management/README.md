# Process Management – Deep Engineering Guide

> Master Linux process lifecycle, scheduling, signals, priorities, and production-level debugging.

---

## Table of Contents

1. Process Architecture Overview
2. Process States
3. Process Creation & Forking
4. Foreground & Background Execution
5. Process Inspection & Monitoring
6. Signals & Process Control
7. Killing & Terminating Processes Safely
8. Process Priorities & Scheduling
9. Advanced Debugging Techniques
10. Real Production Scenarios
11. Interview & System Design Questions

---

## Process Architecture Overview

In Linux, everything runs as a process.

Each process has:

- PID (Process ID)
- PPID (Parent Process ID)
- UID / GID
- Memory space
- File descriptors
- Scheduling priority

Kernel manages processes via:

- CFS (Completely Fair Scheduler)
- Control Groups (cgroups)
- Namespaces

---

## Process States

Check states:

```bash
ps aux
```

Common states:

| State | Meaning                          |
| ----- | -------------------------------- |
| R     | Running                          |
| S     | Sleeping                         |
| D     | Uninterruptible sleep (I/O wait) |
| Z     | Zombie                           |
| T     | Stopped                          |

Example:

```bash
ps -eo pid,ppid,state,cmd
```

---

## Process Creation & Forking

Processes are created using:

* fork()
* exec()
* clone()

Visualize hierarchy:

```bash
pstree
```

Example:

```bash
bash
 ├── vim
 ├── ssh
 └── python
```

Each child inherits:

* Environment variables
* File descriptors
* Working directory

---

## Foreground & Background Execution

Run background:

```bash
sleep 100 &
```

Check jobs:

```bash
jobs
```

Bring to foreground:

```bash
fg %1
```

Suspend process:

CTRL + Z

---

## Process Inspection & Monitoring

### Basic Listing

```bash
ps aux
```

### Advanced Filtering

```bash
ps -ef | grep nginx
```

### Real-Time Monitoring

```bash
top
htop
```

### CPU/Memory Specific

```bash
top -o %MEM
```

### Open Files by Process

```bash
lsof -p <PID>
```

---

## Signals & Process Control

List signals:

```bash
kill -l
```

Important signals:

| Signal  | Number | Purpose       |
| ------- | ------ | ------------- |
| SIGTERM | 15     | Graceful stop |
| SIGKILL | 9      | Force kill    |
| SIGINT  | 2      | Interrupt     |
| SIGHUP  | 1      | Reload config |

Send signal:

```bash
kill -15 PID
kill -9 PID
```

Reload service example:

```bash
kill -HUP PID
```

---

## Killing Processes Safely

Proper order:

1. Try SIGTERM (15)
2. Wait
3. Use SIGKILL (9) only if required

Kill by name:

```bash
pkill nginx
killall node
```

---

## Process Priorities & Scheduling

### Nice Value

Range:
-20 (highest priority) → 19 (lowest)

Start process with priority:

```bash
nice -n 10 python app.py
```

Change running process:

```bash
renice 5 -p PID
```

### Check Priority

```bash
ps -o pid,ni,cmd
```

---

## Advanced Debugging Techniques

### Trace System Calls

```bash
strace -p PID
```

### Check Memory Map

```bash
pmap PID
```

### Inspect Threads

```bash
ps -eLf
```

### CPU Bottleneck Analysis

```bash
top -H
```

### Check Resource Limits

```bash
ulimit -a
```

---

## Real Production Scenarios

---

### Scenario 1: High CPU Usage

Steps:

1. Identify process

   ```bash
   top
   ```

2. Inspect threads

   ```bash
   top -H -p PID
   ```

3. Trace system calls

   ```bash
   strace -p PID
   ```

4. Check logs

---

### Scenario 2: Zombie Processes

Identify:

```bash
ps aux | grep Z
```

Fix:

* Kill parent process
* Restart service

---

### Scenario 3: Memory Leak

1. Monitor:

   ```bash
   top
   ```

2. Inspect memory:

   ```bash
   pmap PID
   ```

3. Use:

   ```bash
   valgrind
   ```

---

## Interview Questions

1. What is the difference between fork and exec?
2. Why is SIGKILL dangerous?
3. What causes zombie processes?
4. What is nice value?
5. What is context switching?
6. How does Linux scheduler work?
7. What happens when a parent dies?

---

## System Design Perspective

Linux process management affects:

* Microservices scaling
* Thread pools
* Container isolation
* CPU throttling
* High-performance systems

Understanding:

* Scheduling fairness
* Resource contention
* Process lifecycle
* Graceful shutdown handling

is critical for backend & DevOps engineers.

---

## Advanced Concepts (Research Section)

* Completely Fair Scheduler (CFS)
* CPU affinity (`taskset`)
* cgroups resource isolation
* Namespaces
* OOM killer
* Kernel preemption

## Practical Lab

### Lab 1 – Create Background Service

1. Write infinite loop script
2. Run in background
3. Monitor with top
4. Change priority
5. Kill safely

### Lab 2 – Simulate CPU Load

```bash
yes > /dev/null
```

Observe system impact.

---

## Summary

You now understand:

* Process lifecycle
* Scheduling
* Signals
* Debugging
* Production monitoring
* Resource management
* Performance tuning

This is real Linux engineering knowledge.

---

## _⭐ If this module helped you, give the repository a star!_
