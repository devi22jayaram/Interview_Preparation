# 📘 DevOps Interview Handbook
# Module 3: Users, Groups & File Permissions

> **Target Audience:** DevOps Engineers (1–2 Years Experience)
>
> **Goal:** Understand Linux user management, groups, file ownership, permissions, and access control from a production perspective.

---

# Table of Contents

1. Linux Users
2. Types of Users
3. Root User
4. User Management Commands
5. Groups
6. Group Management Commands
7. File Ownership
8. File Permissions
9. chmod
10. chown
11. umask
12. SUID, SGID & Sticky Bit
13. sudo
14. passwd File
15. shadow File
16. Production Scenarios
17. Common Interview Questions
18. Interview Tips

---

# 1. Linux Users

## What is a User?

A user is an account that can log in to the Linux system and perform operations based on the permissions assigned.

Every user has:

- Username
- UID (User ID)
- Home Directory
- Login Shell
- Password
- Primary Group

---

# Types of Users

## 1. Root User

- UID = 0
- Superuser
- Has complete control over the Linux system.

Example

```bash
sudo su
```

---

## 2. Normal User

Regular users with limited permissions.

Example

```
devi
ubuntu
administrator
```

---

## 3. System User

Created automatically for services.

Examples

```
nginx
mysql
www-data
sshd
```

These users generally cannot log in.

---

# Interview Answer

> Linux supports multiple users. Every user has a unique User ID (UID), home directory, login shell, and permissions. In production environments, we avoid using the root account directly and perform administrative tasks using sudo for better security and auditing.

---

# 2. Root User

The root user is the administrator of Linux.

Capabilities

- Install Software
- Delete Files
- Manage Users
- Configure Services
- Change Permissions
- Restart Servers

---

Check Current User

```bash
whoami
```

Check User ID

```bash
id
```

---

# 3. User Management Commands

## Create User

```bash
sudo useradd devi
```

---

Create Home Directory

```bash
sudo useradd -m devi
```

---

Set Password

```bash
sudo passwd devi
```

---

Delete User

```bash
sudo userdel devi
```

---

Delete User with Home Directory

```bash
sudo userdel -r devi
```

---

Modify User

```bash
sudo usermod
```

---

Lock User

```bash
sudo passwd -l devi
```

---

Unlock User

```bash
sudo passwd -u devi
```

---

List Current User

```bash
whoami
```

---

List Logged-in Users

```bash
who

w
```

---

# Production Example

A new developer joins the company.

Tasks:

- Create user
- Assign password
- Add to DevOps group
- Give sudo access if required

---

# 4. Groups

## What is a Group?

A group is a collection of users.

Groups simplify permission management.

Instead of assigning permissions individually, permissions are assigned to the group.

---

Example

```
DevOps Team

↓

Devi

↓

Rahul

↓

Karthik
```

---

# Types of Groups

Primary Group

Each user belongs to one primary group.

Secondary Group

A user can belong to multiple secondary groups.

---

Check User Groups

```bash
groups

id
```

---

# Group Commands

Create Group

```bash
sudo groupadd devops
```

---

Delete Group

```bash
sudo groupdel devops
```

---

Add User to Group

```bash
sudo usermod -aG devops devi
```

---

Remove User from Group

```bash
sudo gpasswd -d devi devops
```

---

# Production Example

Developers need access to deployment files.

Instead of assigning permissions individually, add them to a common group.

---

# 5. File Ownership

Every file has

- Owner
- Group

Check

```bash
ls -l
```

Example

```
-rw-r--r--

devi devops
```

Owner

↓

devi

Group

↓

devops

---

# 6. File Permissions

Linux permissions consist of

Read

Write

Execute

---

Permission Values

| Permission | Value |
|------------|------|
| Read | 4 |
| Write | 2 |
| Execute | 1 |

---

Permission Calculation

```
7 = 4+2+1 = rwx

6 = 4+2 = rw-

5 = 4+1 = r-x

4 = Read

0 = No Permission
```

---

Example

```
755

rwx

r-x

r-x
```

Owner

↓

Read Write Execute

Group

↓

Read Execute

Others

↓

Read Execute

---

644

```
rw-

r--

r--
```

---

777

```
rwx

rwx

rwx
```

---

# Interview Tip

Never recommend 777 in production.

Use least privilege principle.

---

# 7. chmod

Change file permissions.

---

Numeric Method

```bash
chmod 755 script.sh

chmod 644 file.txt
```

---

Symbolic Method

```bash
chmod +x script.sh

chmod -w file.txt
```

---

# Production Example

Deployment script is not executable.

Solution

```bash
chmod +x deploy.sh
```

---

# 8. chown

Change file owner.

---

Example

```bash
sudo chown devi file.txt
```

---

Owner + Group

```bash
sudo chown devi:devops file.txt
```

---

Recursive

```bash
sudo chown -R www-data:www-data /var/www/html
```

---

Production Example

After deploying a website, change ownership to the Nginx user so the web server can access the files.

---

# 9. umask

Default permissions assigned to new files and directories.

Check

```bash
umask
```

Example

```
022
```

Default File

```
644
```

Default Directory

```
755
```

---

# 10. SUID, SGID & Sticky Bit

## SUID

Runs with owner's permission.

Example

```
passwd
```

---

## SGID

Files created inside a directory inherit the directory's group.

Useful for shared project folders.

---

## Sticky Bit

Used on shared directories like

```
/tmp
```

Only the owner can delete their files.

Check

```bash
ls -ld /tmp
```

---

# 11. sudo

Allows a normal user to execute administrative commands.

Example

```bash
sudo systemctl restart nginx
```

---

Advantages

- Better Security
- Audit Trail
- Avoid direct root login

---

# 12. passwd File

Location

```
/etc/passwd
```

Contains

- Username
- UID
- GID
- Home Directory
- Login Shell

View

```bash
cat /etc/passwd
```

---

# 13. shadow File

Location

```
/etc/shadow
```

Contains

- Encrypted Password
- Password Expiry
- Password Policy

Only root can access.

---

# 14. Production Scenarios

## Scenario 1

Developer cannot access deployment directory.

Check

```bash
ls -l

groups username

id username
```

Solution

- Add user to correct group
- Change ownership
- Modify permissions

---

## Scenario 2

Nginx shows "Permission Denied"

Check

```bash
ls -l

chown

chmod
```

---

## Scenario 3

Script is not executable.

Solution

```bash
chmod +x deploy.sh
```

---

## Scenario 4

Developer accidentally changed ownership.

Restore

```bash
sudo chown -R www-data:www-data /var/www/html
```

---

# 15. Common Interview Questions

- What is a Linux user?
- Difference between Root User and Normal User.
- What is UID?
- What is GID?
- Difference between Primary Group and Secondary Group.
- Difference between chmod and chown.
- Explain 777, 755 and 644.
- What is umask?
- What is SUID?
- What is SGID?
- What is Sticky Bit?
- Why do we use sudo instead of root?
- Difference between /etc/passwd and /etc/shadow.

---

# 16. Interview Tips

❌ Don't Say

> chmod changes permission.

✅ Say

> chmod modifies file or directory permissions. In production, I use chmod to make deployment scripts executable or restrict access following the principle of least privilege.

---

❌ Don't Say

> chown changes owner.

✅ Say

> chown changes the ownership of files and directories. After deployments, I sometimes update ownership so that the web server user (for example, www-data or nginx) can access the application files correctly.

---

❌ Don't Recommend

```bash
chmod 777
```

Unless absolutely required for testing.

Interviewers dislike unnecessary use of 777 because it introduces security risks.

---

# Key Takeaways

✔ Every user has a UID and belongs to one or more groups.

✔ Groups simplify permission management.

✔ Every file has an owner and a group.

✔ chmod changes permissions.

✔ chown changes ownership.

✔ sudo provides secure administrative access.

✔ Follow the Principle of Least Privilege.

✔ Always relate answers to real production scenarios instead of giving textbook definitions.

---
