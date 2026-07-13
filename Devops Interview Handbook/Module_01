# 📘 DevOps Interview Handbook
## Module 1: Operating System & Linux Fundamentals

> **Target Audience:** DevOps Engineers (1–2 Years Experience)
>
> **Goal:** Understand Linux and Operating System concepts from a production perspective instead of memorizing textbook definitions.

---

# Table of Contents

1. Operating System
2. Linux
3. Linux Architecture
4. Kernel
5. Shell
6. Process
7. Thread
8. Linux Boot Process
9. systemd
10. Daemon Process
11. Frequently Used Linux Commands
12. Production Scenario
13. Interview Tips

---

# 1. Operating System

## Definition

An **Operating System (OS)** is the core software responsible for managing computer hardware resources and providing an environment for applications to run efficiently.

Applications do not communicate directly with hardware. Instead, they communicate with the Operating System, which manages CPU, memory, storage, networking, and devices.

---

## Responsibilities

- Process Management
- Memory Management
- File System Management
- Device Management
- Networking
- Security
- User Management

---

## Real-Time Example

When restarting Nginx:

```bash
sudo systemctl restart nginx
```

The Operating System:

- Stops the existing Nginx process.
- Creates a new process.
- Allocates CPU and memory.
- Binds to ports 80 and 443.
- Starts accepting requests.

---

## Interview Answer

> An Operating System is responsible for managing hardware resources and providing an environment for applications to run. In my current DevOps role, I work with Ubuntu Linux to deploy applications, restart services, configure SSL, and troubleshoot production issues. The Operating System manages all these resources behind the scenes.

---

# 2. Linux

## Definition

Linux is an open-source, Unix-like Operating System widely used in servers, cloud computing, and enterprise environments.

---

## Why Linux?

- Open Source
- Stable
- Secure
- Lightweight
- Powerful CLI
- Automation Friendly
- Preferred for Cloud Platforms

---

## Real-Time Usage

As a DevOps Engineer, I use Linux to:

- Deploy applications
- Configure Nginx
- Manage SSL Certificates
- Troubleshoot production issues
- Monitor services
- Perform server administration

---

## Interview Answer

> Linux is an open-source Operating System preferred in production because of its stability, security, flexibility, and command-line capabilities. I use Ubuntu Linux daily for deployments, monitoring, troubleshooting, and server administration.

---

# 3. Linux Architecture

```
User
    │
Applications
    │
Shell (Bash)
    │
Kernel
    │
Hardware
```

---

## Workflow

User executes command

↓

Shell interprets command

↓

Kernel processes request

↓

Hardware executes operation

↓

Result displayed to user

---

## Example

```bash
ls
```

- Shell receives command.
- Kernel accesses filesystem.
- Hardware returns data.
- Shell displays output.

---

# 4. Kernel

## Definition

Kernel is the core component of the Operating System.

It acts as a bridge between applications and hardware.

---

## Responsibilities

- Process Management
- Memory Management
- Device Drivers
- File System Management
- Networking

---

## Real-Time Example

```bash
systemctl restart nginx
```

Kernel

↓

Stops process

↓

Allocates memory

↓

Starts new process

↓

Binds required ports

---

## Interview Answer

> Kernel is the core part of the Operating System responsible for managing system resources such as CPU, memory, devices, networking, and processes. Every application communicates with hardware through the kernel.

---

# 5. Shell

## Definition

Shell is a command-line interpreter that acts as an interface between the user and the kernel.

---

## Examples

- Bash
- Zsh
- Fish

---

## Workflow

```bash
pwd
```

Shell

↓

Kernel

↓

Filesystem

↓

Output displayed

---

## Interview Answer

> Shell accepts user commands, interprets them, and passes them to the kernel for execution.

---

# 6. Process

## Definition

A Process is a program currently executing.

Each process has

- PID
- Memory
- CPU Allocation
- State

---

## Examples

- nginx
- node
- mysql
- docker

---

## Commands

```bash
ps -ef
top
htop
pidof nginx
kill PID
kill -9 PID
```

---

## Real-Time Example

When a Node.js application becomes unresponsive:

- Check running process
- Verify logs
- Restart service

---

## Interview Answer

> A process is a running instance of a program. Every process has its own PID, memory allocation, and CPU resources.

---

# 7. Thread

## Definition

A Thread is the smallest unit of execution inside a process.

Threads share memory and resources.

---

## Process vs Thread

| Process | Thread |
|----------|----------|
| Independent | Part of Process |
| Separate Memory | Shared Memory |
| Heavyweight | Lightweight |
| Slower | Faster |

---

## Example

Chrome

↓

One Process

↓

Multiple Threads

- UI Thread
- Network Thread
- Rendering Thread

---

# 8. Linux Boot Process

```
Power ON
     │
BIOS / UEFI
     │
GRUB Bootloader
     │
Kernel
     │
systemd
     │
Services Start
     │
Login Prompt
```

---

## Explanation

### BIOS / UEFI

Checks hardware.

### GRUB

Loads Linux Kernel.

### Kernel

Initializes CPU, Memory, Devices.

### systemd

Starts services like

- nginx
- ssh
- docker

System becomes ready.

---

## Interview Answer

> During boot, BIOS/UEFI performs hardware initialization, GRUB loads the Linux kernel, the kernel initializes hardware, systemd starts background services, and finally the system presents the login prompt.

---

# 9. systemd

## Definition

systemd is the initialization system responsible for booting Linux and managing services.

---

## Commands

```bash
systemctl start nginx

systemctl stop nginx

systemctl restart nginx

systemctl status nginx

systemctl enable nginx
```

---

## Real-Time Example

Whenever deployment is completed:

```bash
sudo systemctl restart nginx
```

Then verify

```bash
sudo systemctl status nginx
```

---

# 10. Daemon Process

## Definition

Daemon is a background process running continuously without user interaction.

---

## Examples

- nginx
- docker
- sshd
- cron

---

## Check Running Daemons

```bash
ps -ef
```

---

# Frequently Used Linux Commands

| Command | Description |
|----------|-------------|
| pwd | Current Directory |
| ls -l | List Files |
| cd | Change Directory |
| mkdir | Create Directory |
| touch | Create File |
| cp | Copy Files |
| mv | Move/Rename |
| rm -rf | Delete Files |
| cat | Display File |
| head | First Lines |
| tail -f | Monitor Logs |
| grep | Search Text |
| find | Find Files |
| df -h | Disk Usage |
| du -sh | Directory Size |
| free -h | Memory Usage |
| top | Running Processes |
| ps -ef | Process List |
| kill | Stop Process |
| systemctl | Manage Services |
| journalctl | View Logs |

---

# Production Scenario

## Website is Down

Steps:

1. Check service status

```bash
systemctl status nginx
```

2. Check logs

```bash
journalctl -u nginx
```

3. Test configuration

```bash
nginx -t
```

4. Restart service

```bash
systemctl restart nginx
```

5. Verify website

---

# Common Interview Questions

- What is an Operating System?
- Why Linux?
- Explain Linux Architecture.
- What is Kernel?
- Difference between Kernel and Shell.
- What is a Process?
- Difference between Process and Thread.
- Explain Linux Boot Process.
- What is systemd?
- What is a Daemon Process?

---

# Interview Tips

✅ Don't answer with textbook definitions.

Always connect your answer with real experience.

Example:

> In my current role, I use Ubuntu Linux to deploy React and Node.js applications, configure Nginx, manage SSL certificates using Certbot, troubleshoot production issues, and monitor services using systemctl and journalctl.

This demonstrates practical DevOps experience and creates a stronger impression during interviews.

---

# Key Takeaways

✔ Understand concepts instead of memorizing definitions.

✔ Relate every answer to real production work.

✔ Explain using practical examples whenever possible.

✔ Confidence comes from understanding, not memorization.

---
