# 📘 DevOps Interview Handbook
# Module 04: Process Management & Service Management

> **Target Audience:** DevOps Engineers (1–2 Years Experience)
>
> **Goal:** Understand Linux process management, signals, service management, logs, and troubleshooting from a production perspective.

---

# Table of Contents

1. What is a Process?
2. Program vs Process
3. Process States
4. Process ID (PID)
5. Parent & Child Process
6. Zombie Process
7. Orphan Process
8. Daemon Process
9. Process Management Commands
10. Signals
11. Nice & Renice
12. systemd & systemctl
13. journalctl
14. PM2 Basics
15. Production Scenarios
16. Common Interview Questions
17. Interview Tips

---

# 1. What is a Process?

## Definition

A **Process** is a program that is currently executing.

Every running application in Linux is a process.

Examples

- nginx
- node
- mysql
- docker
- sshd

Each process has:

- PID (Process ID)
- PPID (Parent Process ID)
- Memory
- CPU Allocation
- State
- Owner

---

## Interview Answer

> A process is a running instance of a program. Every process has its own PID, memory space, CPU allocation, and execution state. In production, I regularly monitor processes while troubleshooting applications and deployments.

---

# 2. Program vs Process

| Program | Process |
|----------|----------|
| Stored on Disk | Running in Memory |
| Passive | Active |
| No PID | Has PID |
| Static | Dynamic |

Example

```
node app.js

↓

Running Node Application

↓

Process
```

---

# 3. Process States

Common Linux Process States

| State | Meaning |
|--------|----------|
| R | Running |
| S | Sleeping |
| D | Waiting for I/O |
| T | Stopped |
| Z | Zombie |

Check

```bash
ps -ef
```

---

# 4. Process ID (PID)

Every running process has a unique Process ID.

Find PID

```bash
pidof nginx
```

or

```bash
ps -ef | grep nginx
```

---

# 5. Parent & Child Process

Every process is created by another process.

Example

```
systemd

↓

nginx

↓

worker process
```

Check

```bash
ps -ef
```

PPID = Parent Process ID

---

# 6. Zombie Process

## Definition

A Zombie process has completed execution but still exists in the process table because its parent process hasn't collected its exit status.

State

```
Z
```

---

## Interview Answer

> Zombie processes consume almost no CPU or memory, but many zombies indicate poor process management by the parent application.

---

Check

```bash
ps -el | grep Z
```

---

# 7. Orphan Process

A process whose parent has terminated.

Linux automatically assigns it to

```
systemd
```

---

# 8. Daemon Process

A background process running continuously.

Examples

- nginx
- sshd
- docker
- cron

Check

```bash
ps -ef
```

---

# 9. Process Management Commands

## View Processes

```bash
ps -ef
```

---

Interactive Process Viewer

```bash
top
```

---

Enhanced Viewer

```bash
htop
```

---

Search Process

```bash
ps -ef | grep nginx
```

---

Kill Process

```bash
kill PID
```

---

Force Kill

```bash
kill -9 PID
```

---

Kill by Name

```bash
pkill nginx
```

---

# 10. Linux Signals

Signals allow communication with processes.

Common Signals

| Signal | Number | Purpose |
|----------|----------|----------|
| SIGTERM | 15 | Graceful Termination |
| SIGKILL | 9 | Force Kill |
| SIGHUP | 1 | Reload Configuration |
| SIGINT | 2 | Interrupt (Ctrl+C) |

---

Examples

Graceful

```bash
kill PID
```

Force

```bash
kill -9 PID
```

---

# Interview Tip

Always try SIGTERM before SIGKILL.

---

# 11. Nice & Renice

Linux assigns priority to processes.

Check

```bash
top
```

Run Process with Low Priority

```bash
nice -n 10 command
```

Change Priority

```bash
renice 5 PID
```

---

# 12. systemd & systemctl

systemd is the service manager in modern Linux.

---

Start Service

```bash
sudo systemctl start nginx
```

---

Stop

```bash
sudo systemctl stop nginx
```

---

Restart

```bash
sudo systemctl restart nginx
```

---

Reload

```bash
sudo systemctl reload nginx
```

---

Status

```bash
sudo systemctl status nginx
```

---

Enable at Boot

```bash
sudo systemctl enable nginx
```

---

Disable

```bash
sudo systemctl disable nginx
```

---

Reload systemd

```bash
sudo systemctl daemon-reload
```

---

# 13. journalctl

View service logs.

Example

```bash
journalctl -u nginx
```

Follow Logs

```bash
journalctl -fu nginx
```

Recent Logs

```bash
journalctl -u nginx --since "1 hour ago"
```

---

# Production Example

Application failed after deployment.

Check

```bash
journalctl -u nginx
```

---

# 14. PM2 Basics

PM2 is a process manager for Node.js applications.

---

List

```bash
pm2 list
```

---

Logs

```bash
pm2 logs
```

---

Restart

```bash
pm2 restart app-name
```

---

Stop

```bash
pm2 stop app-name
```

---

Delete

```bash
pm2 delete app-name
```

---

Save

```bash
pm2 save
```

---

Startup

```bash
pm2 startup
```

---

Production Example

After deploying a backend application:

```bash
pm2 restart backend
```

Verify

```bash
pm2 logs backend
```

---

# 15. Production Scenarios

---

## Scenario 1

Website is down.

Steps

```bash
systemctl status nginx

journalctl -u nginx

ps -ef | grep nginx

nginx -t

systemctl restart nginx
```

---

## Scenario 2

Backend API not responding.

Check

```bash
pm2 list

pm2 logs

netstat -tulnp

curl localhost:3000
```

---

## Scenario 3

Server CPU usage is high.

Commands

```bash
top

htop

ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%cpu
```

---

## Scenario 4

Application consuming high memory.

Commands

```bash
free -h

top

ps aux --sort=-%mem
```

---

## Scenario 5

Service not starting.

Check

```bash
systemctl status

journalctl

nginx -t
```

---

# 16. Common Interview Questions

- What is a Process?
- Difference between Program and Process.
- What is PID?
- Explain Parent and Child Process.
- What is Zombie Process?
- What is Orphan Process?
- What is Daemon Process?
- Difference between SIGTERM and SIGKILL.
- Difference between kill and kill -9.
- What is systemd?
- Difference between restart and reload.
- What is journalctl?
- Why do we use PM2?

---

# 17. Interview Tips

❌ Don't Say

> Process is a running program.

✅ Say

> A process is a running instance of a program with its own PID, memory allocation, CPU resources, and execution state. During troubleshooting, I frequently monitor and manage processes using ps, top, systemctl, and PM2.

---

❌ Don't Say

> PM2 manages Node applications.

✅ Say

> PM2 is a production-ready process manager for Node.js applications. I use it to keep backend applications running, restart them after deployments, monitor logs, and ensure automatic startup after server reboots.

---

❌ Don't Say

> I restart Nginx.

✅ Say

> Before restarting Nginx, I validate the configuration using `nginx -t`, then restart the service using `systemctl restart nginx`, verify the status, and confirm that the application is accessible.

---

# Key Takeaways

✔ Every running application is a process.

✔ Learn process states and Linux signals.

✔ Understand the difference between SIGTERM and SIGKILL.

✔ Use systemctl to manage Linux services.

✔ Use journalctl for service logs.

✔ PM2 is commonly used for Node.js applications.

✔ Always troubleshoot before restarting a service.

✔ Relate every answer to your production experience.

---
