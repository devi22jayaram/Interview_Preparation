# Linux Process Management

## Interview Question

### What is a Process?

## Answer

A process is a program that is currently running in memory.

When we execute a program, Linux loads it into RAM, assigns it a unique Process ID (PID), allocates CPU and memory, and starts its execution. At this point, the program becomes a process.

For example:

- Running `nginx` creates an Nginx process.
- Running `node app.js` creates a Node.js process.
- Running `google-chrome` creates a Chrome process.

Every process has its own:

- Process ID (PID)
- Parent Process ID (PPID)
- Memory allocation
- CPU usage
- Process state

---

# Program vs Process

| Program | Process |
|---------|----------|
| Stored on disk | Running in memory |
| Passive | Active |
| No PID | Has PID |
| Static | Dynamic |

Example

```
Node.js Application (Program)

↓

node app.js

↓

Running Node Process
```

---

# Process Lifecycle

```
Program

↓

Ready

↓

Running

↓

Waiting

↓

Running

↓

Terminated
```

Every process follows this lifecycle until it exits.

---

# Process ID (PID)

Every running process is assigned a unique Process ID (PID).

Example

```
PID = 2546
```

To view all running processes:

```bash
ps -ef
```

---

# Parent Process (PPID)

Every process is created by another process called the Parent Process.

Example

```
systemd

↓

nginx

↓

worker process
```

View Parent Process

```bash
ps -ef
```

---

# Types of Processes

## 1. Foreground Process

Runs in the terminal.

Example

```bash
python app.py
```

The terminal remains occupied until the process finishes.

---

## 2. Background Process

Runs without blocking the terminal.

Example

```bash
python app.py &
```

View background jobs

```bash
jobs
```

Bring to foreground

```bash
fg
```

---

## 3. Daemon Process

A daemon is a background service that starts automatically and waits for requests.

Examples

- nginx
- sshd
- cron
- systemd
- docker

Check nginx

```bash
systemctl status nginx
```

---

## 4. Zombie Process

A zombie process has completed execution but still has an entry in the process table because its parent has not collected its exit status.

Characteristics

- Consumes no CPU
- Minimal memory usage
- Still occupies a PID

View

```bash
ps aux | grep Z
```

---

## 5. Orphan Process

An orphan process is a process whose parent has terminated before the child process.

Linux automatically assigns orphan processes to:

```
systemd (PID 1)
```

---

# Process States

```
R → Running

S → Sleeping

D → Waiting (Uninterruptible)

T → Stopped

Z → Zombie
```

View

```bash
ps aux
```

STAT column indicates the process state.

---

# Important Process Commands

## View Running Processes

```bash
ps
```

---

## View Detailed Processes

```bash
ps -ef
```

---

## View All Processes

```bash
ps aux
```

---

## Real-Time Process Monitoring

```bash
top
```

Quit

```
q
```

---

## Better Process Viewer

```bash
htop
```

---

## Find Process

```bash
pgrep nginx

pgrep node
```

---

## Find Process ID

```bash
pidof nginx

pidof node
```

---

## Kill Process

```bash
kill PID
```

Example

```bash
kill 2589
```

---

## Force Kill

```bash
kill -9 PID
```

Example

```bash
kill -9 2589
```

---

## Kill by Name

```bash
killall nginx
```

---

## Run in Background

```bash
command &
```

Example

```bash
node app.js &
```

---

## Background Jobs

```bash
jobs
```

---

## Bring Job to Foreground

```bash
fg
```

---

## Send Job to Background

```bash
bg
```

---

# Nice and Renice

Linux allows us to set process priority.

Priority Range

```
-20 → Highest Priority

0 → Default

19 → Lowest Priority
```

Run Process with Priority

```bash
nice -n 10 command
```

Change Existing Priority

```bash
renice 5 PID
```

---

# Signals

Linux uses signals to communicate with processes.

Common Signals

```
SIGTERM (15)

Gracefully stop process.

-------------------------

SIGKILL (9)

Forcefully terminate process.

-------------------------

SIGHUP (1)

Reload configuration.

-------------------------

SIGINT (2)

Interrupt process (Ctrl+C).
```

---

# Difference Between kill and kill -9

| kill | kill -9 |
|------|----------|
| Gracefully stops process | Forcefully kills process |
| Process can clean up resources | No cleanup |
| Preferred method | Use only if process does not respond |

---

# Difference Between ps and top

| ps | top |
|----|-----|
| Snapshot | Live monitoring |
| Static output | Dynamic output |
| Shows current state | Updates continuously |

---

# Difference Between top and htop

| top | htop |
|------|------|
| Basic | Interactive |
| Keyboard only | Easy navigation |
| Less user-friendly | More user-friendly |

---

# Real-Time DevOps Examples

## Example 1

Nginx is not responding.

Check process

```bash
ps -ef | grep nginx
```

Restart

```bash
sudo systemctl restart nginx
```

---

## Example 2

PM2 Application Crash

Check process

```bash
pm2 list

pm2 logs
```

Restart

```bash
pm2 restart app
```

---

## Example 3

High CPU Usage

Identify process

```bash
top
```

Kill process

```bash
kill PID
```

---

## Example 4

Node.js Memory Leak

Check process

```bash
ps aux | grep node

top
```

Restart

```bash
pm2 restart app
```

---

# Best Practices

✅ Use `kill` before `kill -9`.

✅ Monitor processes using `top` or `htop`.

✅ Avoid killing system processes.

✅ Restart services using `systemctl` instead of killing them directly.

✅ Use PM2 to manage Node.js applications instead of running them manually.

---

# Common Interview Questions

### What is a process?

### Difference between Program and Process?

### What is PID?

### What is PPID?

### What is a Daemon Process?

### What is a Zombie Process?

### What is an Orphan Process?

### Difference between Foreground and Background Process?

### Difference between kill and kill -9?

### Difference between ps and top?

### Difference between top and htop?

### What is nice?

### What is renice?

### How do you identify a process consuming high CPU?

### How do you identify a memory leak?

---

# Sample Interview Answer

**Interviewer:** Explain Process Management in Linux.

**Answer:**

A process is a program that is currently running in memory. Every process has a unique Process ID (PID), memory allocation, CPU usage, and a process state. Linux provides commands such as `ps`, `top`, `htop`, and `pgrep` to monitor processes. We can terminate processes using `kill` or `kill -9`, although `kill` is preferred because it allows the process to shut down gracefully. In my role as a DevOps Engineer, I frequently monitor Nginx and Node.js processes, troubleshoot high CPU or memory usage, and manage application processes using PM2 and systemctl.

---

# Quick Revision

```
Program
↓

Process

↓

PID

↓

CPU

↓

Memory

↓

Running

↓

Waiting

↓

Terminated
```

Important Commands

```bash
ps
ps -ef
ps aux
top
htop
pgrep
pidof
kill
kill -9
killall
jobs
fg
bg
nice
renice
```

---

# Interview Tips

✅ Understand the complete process lifecycle.

✅ Know the difference between a program and a process.

✅ Explain PID, PPID, and process states.

✅ Know when to use `kill` vs `kill -9`.

✅ Give real examples from your work, such as troubleshooting Nginx or PM2 processes.
