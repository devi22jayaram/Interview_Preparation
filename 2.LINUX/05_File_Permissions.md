# Linux File Permissions

## Interview Question

### What are Linux File Permissions?

## Answer

Linux File Permissions determine who can read, write, or execute a file or directory.

Every file and directory in Linux has permissions assigned to control access and improve system security.

There are three types of users:

- Owner (User)
- Group
- Others

Each user can have three types of permissions:

- Read (r)
- Write (w)
- Execute (x)

---

# Why are File Permissions Important?

File permissions help to:

- Protect sensitive files
- Prevent unauthorized access
- Control who can modify files
- Improve server security
- Reduce accidental deletion or modification

As a DevOps Engineer, setting correct permissions is important for applications, scripts, configuration files, and deployment directories.

---

# Types of Users

```
Owner (u)

↓

Group (g)

↓

Others (o)
```

Example

```
-rwxr-xr--
```

```
User    Group   Others
rwx     r-x     r--
```

---

# Types of Permissions

## Read (r)

Allows viewing the contents of a file.

Value

```
4
```

Example

```bash
cat file.txt
```

---

## Write (w)

Allows modifying or deleting a file.

Value

```
2
```

Example

```bash
echo "Hello" >> file.txt
```

---

## Execute (x)

Allows executing a file or entering a directory.

Value

```
1
```

Example

```bash
./deploy.sh
```

---

# Understanding Permission Format

Example

```
-rwxr-xr--
```

Breakdown

```
-

File Type

rwx

Owner Permissions

r-x

Group Permissions

r--

Others Permissions
```

Meaning

Owner

- Read
- Write
- Execute

Group

- Read
- Execute

Others

- Read Only

---

# File Types

```
-   Regular File

d   Directory

l   Symbolic Link

c   Character Device

b   Block Device
```

Example

```bash
ls -l
```

Output

```
drwxr-xr-x

-rw-r--r--

lrwxrwxrwx
```

---

# Numeric Permission Values

```
Read = 4

Write = 2

Execute = 1
```

Examples

```
rwx = 7

rw- = 6

r-x = 5

r-- = 4

--- = 0
```

---

# Common Permission Numbers

## 777

```
rwx

rwx

rwx
```

Everyone has full permission.

⚠ Not recommended in production.

---

## 755

```
Owner

rwx

Group

r-x

Others

r-x
```

Most commonly used for directories and executable files.

---

## 644

```
Owner

rw-

Group

r--

Others

r--
```

Most commonly used for normal files.

---

## 600

```
Owner

rw-

Group

---

Others

---
```

Used for sensitive files.

Example

Private SSH Keys

---

# chmod Command

## Purpose

Changes file permissions.

Syntax

```bash
chmod permission file
```

Examples

```bash
chmod 755 deploy.sh

chmod 644 index.html

chmod 600 id_rsa
```

Recursive

```bash
chmod -R 755 project
```

---

# Symbolic Mode

Add Execute Permission

```bash
chmod +x deploy.sh
```

Remove Write Permission

```bash
chmod -w file.txt
```

Add Read Permission

```bash
chmod u+r file.txt
```

---

# chown Command

## Purpose

Changes file owner.

Syntax

```bash
chown user file
```

Example

```bash
chown ubuntu app.js
```

Owner and Group

```bash
chown ubuntu:www-data project
```

---

# chgrp Command

## Purpose

Changes group ownership.

Example

```bash
chgrp developers project
```

---

# How to View Permissions

```bash
ls -l
```

Example

```
-rwxr-xr-x

index.html
```

---

# Real-Time DevOps Examples

## Example 1

A deployment script cannot execute.

Reason

No Execute Permission.

Solution

```bash
chmod +x deploy.sh
```

---

## Example 2

Nginx cannot read website files.

Reason

Incorrect permissions.

Solution

```bash
chmod -R 755 /var/www/project

chown -R www-data:www-data /var/www/project
```

---

## Example 3

SSH Private Key Error

```
Permissions 0644 are too open
```

Solution

```bash
chmod 600 ~/.ssh/id_rsa
```

---

# Best Practices

✅ Use 755 for directories.

✅ Use 644 for normal files.

✅ Use 600 for private keys.

✅ Avoid using 777.

✅ Give only required permissions.

---

# Common Interview Questions

### What are Linux file permissions?

### Explain rwxr-xr-x.

### Difference between 755 and 777.

### Difference between 644 and 600.

### Difference between chmod and chown.

### Difference between Owner, Group and Others.

### Why should we avoid 777?

### What is chmod +x?

### What happens if Execute permission is missing?

### How do you check file permissions?

---

# Sample Interview Answer

**Interviewer:** Explain Linux File Permissions.

**Answer:**

Linux File Permissions control who can access, modify, or execute files and directories.

There are three types of users: Owner, Group, and Others.

Each can have Read, Write, and Execute permissions.

Permissions can be represented symbolically (rwx) or numerically (755, 644).

As a DevOps Engineer, I frequently use `chmod` to modify permissions and `chown` to change ownership. For example, after deploying a website, I ensure that the web server has the correct ownership and permissions so that Nginx can access the files securely.

---

# Quick Revision

```
Read = 4

Write = 2

Execute = 1

rwx = 7

rw- = 6

r-x = 5

r-- = 4
```

Most Used

```
755 → Directories

644 → Files

600 → Private Keys

777 → Avoid
```

Commands

```bash
ls -l

chmod

chown

chgrp
```

---

# Interview Tips

✅ Understand the difference between permissions and ownership.

✅ Be able to explain 755, 644, and 600 confidently.

✅ Never recommend using 777 in production unless there is a very specific temporary reason.

✅ Relate your answer to real DevOps tasks such as deploying applications, configuring Nginx, or securing SSH keys.
