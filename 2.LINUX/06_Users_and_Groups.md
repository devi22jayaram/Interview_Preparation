# Linux Users and Groups

## Interview Question

### What are Users and Groups in Linux?

## Answer

Linux is a multi-user operating system, which means multiple users can access and work on the same system simultaneously.

To ensure security and proper access control, Linux organizes users into groups and assigns permissions based on user ownership and group membership.

Every file and directory belongs to:

- A User (Owner)
- A Group

Users and Groups help administrators manage permissions efficiently.

---

# Why are Users and Groups Important?

Users and Groups help to:

- Secure the system
- Restrict unauthorized access
- Manage file ownership
- Share resources among team members
- Control administrative privileges

As a DevOps Engineer, managing users and groups is essential when multiple developers, testers, and administrators work on the same Linux server.

---

# Types of Users

## 1. Root User

The root user is the superuser of Linux.

Characteristics:

- Full administrative privileges
- Can access all files
- Can install software
- Can create and delete users
- Can modify system configuration

Home Directory

```
/root
```

Prompt

```
#
```

---

## 2. Normal User

A normal user has limited permissions.

Characteristics:

- Cannot modify system files
- Cannot install software without sudo
- Has a personal home directory

Example

```
/home/devi
```

Prompt

```
$
```

---

## 3. System Users

System users are created automatically by Linux or installed services.

Examples:

- nginx
- www-data
- mysql
- nobody

These users run services securely without using the root account.

---

# What is a Group?

A group is a collection of users who share the same permissions.

Instead of assigning permissions to each user individually, permissions can be assigned to a group.

Example

```
Developers

↓

Devi

Ramesh

Arun
```

All members inherit the group's permissions.

---

# Important Files

## User Information

```
/etc/passwd
```

View

```bash
cat /etc/passwd
```

---

## Password Information

```
/etc/shadow
```

View (Root only)

```bash
sudo cat /etc/shadow
```

---

## Group Information

```
/etc/group
```

View

```bash
cat /etc/group
```

---

# Common User Commands

## Display Current User

```bash
whoami
```

---

## Display User ID

```bash
id
```

Example

```bash
id devi
```

Output

```
uid=1001(devi)

gid=1001(devi)

groups=1001(devi),27(sudo)
```

---

## Create User

```bash
sudo useradd devi
```

Create Home Directory

```bash
sudo useradd -m devi
```

---

## Set Password

```bash
sudo passwd devi
```

---

## Delete User

```bash
sudo userdel devi
```

Delete User with Home Directory

```bash
sudo userdel -r devi
```

---

## Modify User

```bash
sudo usermod
```

Example

Add user to sudo group

```bash
sudo usermod -aG sudo devi
```

---

# Group Commands

Create Group

```bash
sudo groupadd developers
```

Delete Group

```bash
sudo groupdel developers
```

Add User to Group

```bash
sudo usermod -aG developers devi
```

Display Groups

```bash
groups

groups devi
```

---

# Sudo

## What is sudo?

sudo allows a normal user to execute commands with administrative (root) privileges.

Example

```bash
sudo systemctl restart nginx
```

Without sudo

Permission Denied

With sudo

Command executes successfully.

---

# Switching Users

Become Root

```bash
sudo su
```

Switch User

```bash
su username
```

Example

```bash
su devi
```

Exit

```bash
exit
```

---

# Lock User

```bash
sudo passwd -l devi
```

Unlock User

```bash
sudo passwd -u devi
```

---

# Real-Time DevOps Examples

## Example 1

A new developer joins the team.

Tasks:

- Create user
- Set password
- Add to developers group
- Give required permissions

Commands

```bash
sudo useradd -m arun

sudo passwd arun

sudo usermod -aG developers arun
```

---

## Example 2

Allow deployment without using the root account.

Instead of logging in as root, assign sudo privileges.

```bash
sudo usermod -aG sudo devi
```

---

## Example 3

Nginx Ownership

After deploying a website, ownership should belong to the web server.

```bash
sudo chown -R www-data:www-data /var/www/project
```

This allows Nginx to read application files.

---

# Best Practices

✅ Never log in as root for daily work.

✅ Use sudo instead of the root account.

✅ Give users only the permissions they need.

✅ Remove inactive users.

✅ Review group memberships regularly.

---

# Common Interview Questions

### What is the difference between a Root User and a Normal User?

### What is sudo?

### What is the purpose of /etc/passwd?

### What is stored in /etc/shadow?

### What is stored in /etc/group?

### Difference between useradd and usermod?

### Difference between su and sudo?

### Why do we create groups?

### How do you add a user to a group?

### Why should we avoid using the root account?

---

# Sample Interview Answer

**Interviewer:** Explain Users and Groups in Linux.

**Answer:**

Linux is a multi-user operating system where multiple users can work on the same system.

Each file belongs to a user and a group.

Users and groups help manage access permissions securely.

In my role as a DevOps Engineer, I use users and groups to provide developers with appropriate access, assign ownership to application files, and securely manage production servers.

I also use sudo to perform administrative tasks without logging in directly as the root user.

---

# Quick Revision

Users

- Root
- Normal
- System

Important Files

```
/etc/passwd

/etc/shadow

/etc/group
```

Commands

```bash
whoami

id

useradd

usermod

userdel

groupadd

groupdel

passwd

groups

sudo

su
```

---

# Interview Tips

✅ Explain why Linux is called a multi-user operating system.

✅ Know the difference between Root, Normal, and System users.

✅ Remember the purpose of `/etc/passwd`, `/etc/shadow`, and `/etc/group`.

✅ Explain the difference between `su` and `sudo`.

✅ Use real-time examples such as adding developers to a group or assigning ownership to Nginx files.
