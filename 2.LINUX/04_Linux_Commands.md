# Linux Commands

Linux commands are used to interact with the operating system through the command line. As a DevOps Engineer, these commands help manage servers, files, users, processes, networking, and deployments.

---

# 1. pwd (Print Working Directory)

## Purpose

Displays the current directory.

## Syntax

```bash
pwd
```

## Example

```bash
pwd
```

Output

```
/var/www/Rams_apartment
```

## Real-Time Example

Before deploying an application, I use `pwd` to verify that I am in the correct project directory.

---

# 2. ls (List Files)

## Purpose

Displays files and directories.

## Syntax

```bash
ls
```

## Common Options

```bash
ls -l
ls -a
ls -lh
ls -la
```

## Real-Time Example

Used to verify project files after pulling the latest code.

---

# 3. cd (Change Directory)

## Purpose

Moves from one directory to another.

## Syntax

```bash
cd directory_name
```

Examples

```bash
cd /var/www

cd ..

cd ~

cd /
```

---

# 4. mkdir (Make Directory)

## Purpose

Creates a new directory.

```bash
mkdir project
```

Multiple folders

```bash
mkdir app logs backup
```

---

# 5. touch

## Purpose

Creates an empty file.

```bash
touch app.js

touch index.html
```

---

# 6. cp (Copy)

## Purpose

Copies files or directories.

Copy file

```bash
cp file1 file2
```

Copy folder

```bash
cp -r frontend backup
```

---

# 7. mv (Move / Rename)

## Purpose

Moves or renames files.

Rename

```bash
mv old.txt new.txt
```

Move

```bash
mv file.txt /home/devi
```

---

# 8. rm (Remove)

## Purpose

Deletes files or folders.

Delete file

```bash
rm file.txt
```

Delete folder

```bash
rm -r folder
```

Force delete

```bash
rm -rf folder
```

⚠ Never run

```bash
rm -rf /
```

---

# 9. cat

## Purpose

Displays file contents.

```bash
cat nginx.conf
```

---

# 10. less

## Purpose

Views large files page by page.

```bash
less /var/log/nginx/error.log
```

Quit

```
q
```

---

# 11. head

## Purpose

Displays first 10 lines.

```bash
head file.txt
```

First 20 lines

```bash
head -20 file.txt
```

---

# 12. tail

## Purpose

Displays last lines.

```bash
tail file.txt
```

Live monitoring

```bash
tail -f /var/log/nginx/error.log
```

Real-Time Example

I use this command while troubleshooting production issues.

---

# 13. find

## Purpose

Search files.

```bash
find / -name nginx.conf
```

Find all .log files

```bash
find /var -name "*.log"
```

---

# 14. grep

## Purpose

Search text inside files.

```bash
grep "error" logfile.log
```

Ignore case

```bash
grep -i error logfile.log
```

---

# 15. which

## Purpose

Shows command location.

```bash
which nginx

which node
```

---

# 16. df

## Purpose

Displays disk usage.

```bash
df -h
```

Real-Time Example

Used to verify server disk space before deployment.

---

# 17. du

## Purpose

Shows folder size.

```bash
du -sh uploads
```

---

# 18. free

## Purpose

Displays RAM usage.

```bash
free -h
```

---

# 19. top

## Purpose

Shows running processes.

```bash
top
```

Quit

```
q
```

---

# 20. htop

## Purpose

Interactive process viewer.

```bash
htop
```

---

# 21. ps

## Purpose

Displays running processes.

```bash
ps -ef

ps aux
```

---

# 22. kill

## Purpose

Stops a process.

```bash
kill PID
```

Force stop

```bash
kill -9 PID
```

---

# 23. chmod

## Purpose

Changes file permissions.

```bash
chmod 755 app.sh

chmod 644 index.html
```

---

# 24. chown

## Purpose

Changes file ownership.

```bash
chown ubuntu:ubuntu project
```

---

# 25. systemctl

## Purpose

Manages Linux services.

Check status

```bash
systemctl status nginx
```

Restart

```bash
systemctl restart nginx
```

Start

```bash
systemctl start nginx
```

Stop

```bash
systemctl stop nginx
```

---

# 26. journalctl

## Purpose

Views system logs.

```bash
journalctl -u nginx

journalctl -xe
```

---

# 27. curl

## Purpose

Tests APIs and websites.

```bash
curl https://google.com

curl http://localhost:5000
```

---

# 28. ping

## Purpose

Checks network connectivity.

```bash
ping google.com
```

---

# 29. wget

## Purpose

Downloads files.

```bash
wget https://example.com/file.zip
```

---

# 30. ssh

## Purpose

Connects to remote Linux servers.

```bash
ssh ubuntu@192.168.1.100
```

Real-Time Example

I use SSH daily to connect to production servers for deployments.

---

# 31. scp

## Purpose

Copies files between local and remote servers.

```bash
scp file.txt ubuntu@192.168.1.100:/home/ubuntu
```

---

# 32. tar

## Purpose

Creates or extracts archives.

Create

```bash
tar -cvf backup.tar project
```

Extract

```bash
tar -xvf backup.tar
```

---

# 33. zip

Compress

```bash
zip backup.zip file.txt
```

---

# 34. unzip

Extract

```bash
unzip backup.zip
```

---

# Most Frequently Used Commands in My Daily Work

```bash
pwd
ls -la
cd
git pull
npm install
npm run build
pm2 status
pm2 restart
pm2 logs
systemctl restart nginx
systemctl status nginx
nginx -t
tail -f /var/log/nginx/error.log
journalctl -u nginx
curl
df -h
free -h
top
find
grep
chmod
chown
ssh
scp
```

---

# Top 20 Commands Every DevOps Engineer Should Know

1. pwd
2. ls
3. cd
4. cp
5. mv
6. rm
7. cat
8. tail
9. grep
10. find
11. ps
12. top
13. chmod
14. chown
15. df
16. free
17. curl
18. ssh
19. systemctl
20. journalctl

---

# Interview Questions

### What is the difference between cp and mv?

### Difference between rm and rmdir?

### Difference between cat and less?

### Why do we use tail -f?

### Difference between top and ps?

### Why do we use chmod?

### Difference between chown and chmod?

### Why do we use systemctl?

### What is the purpose of grep?

### Why do DevOps engineers use curl?

---

# Interview Tips

✅ Don't memorize commands blindly.

✅ Know what each command does.

✅ Explain where you used it in real projects.

✅ Practice every command on a Linux machine.

✅ Mention real-time production examples whenever possible.
