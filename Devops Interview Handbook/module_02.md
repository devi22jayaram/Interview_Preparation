# 📘 DevOps Interview Handbook
## Module 2: Linux File System & Essential Linux Commands

> **Target Audience:** DevOps Engineers (1–2 Years Experience)
>
> **Goal:** Understand the Linux file system hierarchy, important directories, and frequently used Linux commands from a production perspective.

---

# Table of Contents

1. Linux File System
2. Important Directories
3. Inode
4. Absolute vs Relative Path
5. File Types
6. Essential Linux Commands
7. Search & Filter Commands
8. Disk & Memory Commands
9. Log Monitoring
10. Production Scenarios
11. Common Interview Questions
12. Interview Tips

---

# 1. Linux File System

## What is a File System?

A **File System** is the method used by the Operating System to organize, store, retrieve, and manage files and directories on a storage device.

Everything in Linux is treated as a file:

- Regular Files
- Directories
- Devices
- Processes
- Sockets

Linux follows a **hierarchical tree structure** starting from the root directory (`/`).

---

# Linux File System Structure

```
                /
                |
    -------------------------
    |    |    |    |    |
  /bin /etc /home /var /usr
                 |
              /home/devi
```

---

# 2. Important Linux Directories

## /

Root directory.

All files and directories start from here.

Example:

```bash
cd /
```

---

## /home

Stores home directories of normal users.

Example

```bash
/home/devi
```

---

## /root

Home directory of the root user.

Normal users cannot access it without permission.

---

## /etc

Contains system configuration files.

Examples

```
/etc/nginx/

/etc/passwd

/etc/hosts

/etc/fstab
```

**Real-Time Example**

Whenever we configure Nginx:

```
/etc/nginx/sites-available
```

---

## /var

Stores variable data.

Examples

```
/var/log/

/var/www/

/var/lib/
```

---

### Why is /var important?

Because application logs are stored here.

Example

```
/var/log/nginx/

/var/log/syslog
```

---

## /tmp

Temporary files.

Files may be removed automatically after reboot.

---

## /usr

Contains installed applications and binaries.

Examples

```
/usr/bin

/usr/lib

/usr/share
```

---

## /bin

Essential Linux commands.

Examples

```
ls

cp

mv

cat
```

---

## /opt

Third-party applications.

Example

```
Google Chrome

Custom Software
```

---

## /proc

Virtual filesystem.

Contains process information.

Example

```
cat /proc/cpuinfo

cat /proc/meminfo
```

---

## /dev

Contains device files.

Example

```
/dev/sda

/dev/null
```

---

# 3. Inode

## What is Inode?

An inode is a data structure that stores metadata about a file.

It stores

- Owner
- Permissions
- Size
- Timestamp
- Disk Block Location

It **does not store the filename**.

---

## Check inode

```bash
ls -i
```

---

# 4. Absolute vs Relative Path

## Absolute Path

Starts from root.

Example

```bash
/home/devi/Documents/file.txt
```

---

## Relative Path

Starts from current directory.

Example

```bash
Documents/file.txt
```

---

# 5. Linux File Types

Regular File

```
-
```

Directory

```
d
```

Symbolic Link

```
l
```

Block Device

```
b
```

Character Device

```
c
```

Socket

```
s
```

Pipe

```
p
```

Check

```bash
ls -l
```

---

# 6. Essential Linux Commands

## pwd

Current directory

```bash
pwd
```

---

## ls

List files

```bash
ls

ls -l

ls -la
```

---

## cd

Change directory

```bash
cd

cd ..

cd /
```

---

## mkdir

Create directory

```bash
mkdir project
```

---

## touch

Create file

```bash
touch index.html
```

---

## cp

Copy

```bash
cp file1 file2

cp -r folder backup
```

---

## mv

Move or Rename

```bash
mv old.txt new.txt

mv file folder/
```

---

## rm

Delete

```bash
rm file

rm -r folder

rm -rf folder
```

---

## cat

Display file

```bash
cat file.txt
```

---

## less

Read large file

```bash
less log.txt
```

---

## head

First 10 lines

```bash
head log.txt
```

---

## tail

Last lines

```bash
tail log.txt

tail -f log.txt
```

**Production Example**

Monitor Nginx logs

```bash
tail -f /var/log/nginx/access.log
```

---

# 7. Search & Filter Commands

## grep

Search text

```bash
grep "error" app.log
```

Ignore case

```bash
grep -i "error" app.log
```

---

## find

Find files

```bash
find /home -name "*.log"
```

---

## locate

Find quickly

```bash
locate nginx.conf
```

---

## which

Find command path

```bash
which nginx
```

---

# 8. Disk & Memory Commands

## df

Disk usage

```bash
df -h
```

---

## du

Folder size

```bash
du -sh folder/
```

---

## free

Memory usage

```bash
free -h
```

---

## uptime

System uptime

```bash
uptime
```

---

## top

CPU and Memory

```bash
top
```

---

## htop

Interactive process viewer

```bash
htop
```

---

# 9. Log Monitoring

## journalctl

View service logs

```bash
journalctl -u nginx
```

---

## tail

Monitor logs

```bash
tail -f /var/log/nginx/error.log
```

---

## grep

Search logs

```bash
grep ERROR app.log
```

---

# 10. Production Scenarios

## Scenario 1

Website is down.

First steps:

```bash
systemctl status nginx

journalctl -u nginx

tail -f /var/log/nginx/error.log
```

---

## Scenario 2

Disk full.

Commands

```bash
df -h

du -sh *

find / -size +500M
```

---

## Scenario 3

Application consuming high memory.

Commands

```bash
top

htop

ps -ef
```

---

## Scenario 4

Find configuration file

```bash
find / -name nginx.conf
```

---

# 11. Common Interview Questions

### What is Linux File System?

### Explain Root Directory.

### Difference between /home and /root.

### Why is /etc important?

### Why is /var important?

### What is inode?

### Difference between Absolute Path and Relative Path?

### Difference between cp and mv?

### Difference between cat and less?

### Difference between df and du?

### Difference between grep and find?

### Difference between top and ps?

### What is tail -f?

### How do you monitor logs?

---

# 12. Interview Tips

❌ Don't say

> /etc stores files.

✅ Say

> /etc stores system configuration files. In my current role, I frequently work inside `/etc/nginx` to configure virtual hosts and reverse proxy settings.

---

❌ Don't say

> /var contains logs.

✅ Say

> During production troubleshooting, I usually check logs under `/var/log`, especially Nginx logs, to identify configuration or application errors.

---

## Key Takeaways

✔ Linux follows a hierarchical directory structure.

✔ Every DevOps engineer should know the purpose of important directories.

✔ Learn commands with real production use cases.

✔ Interviewers expect practical examples, not only definitions.

✔ Always connect Linux commands to troubleshooting or deployment scenarios.

---
