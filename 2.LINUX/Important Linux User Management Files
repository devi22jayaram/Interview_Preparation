# Important Linux User Management Files

Linux stores user, password, and group information in three important files:

```
/etc/passwd
/etc/shadow
/etc/group
```

Every Linux administrator and DevOps Engineer should understand these files because they are used for authentication, authorization, and user management.

---

# 1. /etc/passwd

## What is /etc/passwd?

The `/etc/passwd` file contains basic information about every user account on the Linux system.

It **does not store the actual password**. Instead, it stores details such as:

- Username
- User ID (UID)
- Group ID (GID)
- User Description
- Home Directory
- Default Shell

Every user created on Linux will have an entry in this file.

---

## View the File

```bash
cat /etc/passwd
```

Example Output

```
devi:x:1001:1001:Devi Jayaram:/home/devi:/bin/bash
```

---

## Understanding Each Field

```
devi:x:1001:1001:Devi Jayaram:/home/devi:/bin/bash
```

| Field | Meaning |
|--------|---------|
| devi | Username |
| x | Password stored in `/etc/shadow` |
| 1001 | User ID (UID) |
| 1001 | Group ID (GID) |
| Devi Jayaram | User description (GECOS) |
| /home/devi | Home directory |
| /bin/bash | Default login shell |

---

## UID (User ID)

Every Linux user has a unique number called a UID.

Example

```
Root User

UID = 0
```

Normal Users

```
1000+

1001

1002

1003
```

System Users

```
1-999
```

---

## Real-Time Example

When a new employee joins,

```bash
sudo useradd -m ramesh
```

Linux automatically adds an entry into

```
/etc/passwd
```

---

# 2. /etc/shadow

## What is /etc/shadow?

The `/etc/shadow` file stores encrypted passwords and password-related information.

Unlike `/etc/passwd`, this file is **highly secure** and can only be accessed by the root user.

---

## View

```bash
sudo cat /etc/shadow
```

Example

```
devi:$6$Abcdxyz....:20210:0:99999:7:::
```

---

## Understanding the Fields

```
Username

Encrypted Password

Last Password Change

Minimum Days

Maximum Days

Warning Days

Inactive Days

Expiry Date
```

---

## Why Passwords Are Not Stored in /etc/passwd?

Earlier versions of Linux stored passwords in `/etc/passwd`.

Since every user can read `/etc/passwd`, it became a security risk.

To improve security, encrypted passwords were moved to:

```
/etc/shadow
```

Only the root user can access this file.

---

## Real-Time Example

When you run:

```bash
sudo passwd devi
```

Linux updates the encrypted password inside

```
/etc/shadow
```

---

# 3. /etc/group

## What is /etc/group?

The `/etc/group` file stores information about all groups on the system.

Each group contains:

- Group Name
- Group Password (usually unused)
- Group ID (GID)
- Members

---

## View

```bash
cat /etc/group
```

Example

```
developers:x:1010:devi,ramesh,arun
```

---

## Understanding Each Field

```
developers:x:1010:devi,ramesh,arun
```

| Field | Meaning |
|--------|---------|
| developers | Group Name |
| x | Group Password |
| 1010 | Group ID |
| devi,ramesh,arun | Group Members |

---

## Real-Time Example

Suppose a company has five developers.

Instead of assigning permissions individually,

Create one group

```
developers
```

Add everyone

```bash
sudo usermod -aG developers devi

sudo usermod -aG developers arun
```

Now all developers inherit the same permissions.

---

# Relationship Between These Files

```
                User Login

                     │

          Username Entered

                     │

          Check /etc/passwd

                     │

Find UID, GID and Home Directory

                     │

Check Password in

/etc/shadow

                     │

Authentication Successful

                     │

Load Group Information

/etc/group

                     │

User Logged In
```

---

# Commands Every DevOps Engineer Should Know

View Current User

```bash
whoami
```

View User ID

```bash
id
```

View Current User Details

```bash
id devi
```

View User Entry

```bash
grep devi /etc/passwd
```

View Group Entry

```bash
grep developers /etc/group
```

View Shadow Entry (Root)

```bash
sudo grep devi /etc/shadow
```

---

# Interview Questions

### What is the purpose of `/etc/passwd`?

Stores user account information such as username, UID, GID, home directory, and login shell.

---

### What is the purpose of `/etc/shadow`?

Stores encrypted passwords and password policies securely.

---

### What is the purpose of `/etc/group`?

Stores group information and group memberships.

---

### Why are passwords stored in `/etc/shadow` instead of `/etc/passwd`?

Because `/etc/passwd` is readable by all users. Storing passwords there would create a security risk. `/etc/shadow` is accessible only by the root user.

---

### Can a normal user read `/etc/passwd`?

✅ Yes.

---

### Can a normal user read `/etc/shadow`?

❌ No.

Only the root user can access it.

---

### Which command changes the password?

```bash
passwd
```

---

### Which command creates a new user?

```bash
useradd
```

---

### Which command adds a user to a group?

```bash
usermod -aG group_name username
```

---

# Quick Revision

```
/etc/passwd

↓

User Information

Username

UID

GID

Home Directory

Shell

-----------------------------------

/etc/shadow

↓

Encrypted Passwords

Password Policies

Root Access Only

-----------------------------------

/etc/group

↓

Group Information

Group Members

Group ID
```

---

# Best Practices

✅ Never edit these files manually unless necessary (use commands like `useradd`, `usermod`, `passwd`, `groupadd`).

✅ Restrict access to `/etc/shadow`.

✅ Follow the principle of least privilege.

✅ Use groups to simplify permission management.

---

# Real-Time DevOps Scenario

A new developer joins the team.

Steps:

1. Create the user.

```bash
sudo useradd -m arun
```

2. Set the password.

```bash
sudo passwd arun
```

3. Add the user to the developers group.

```bash
sudo usermod -aG developers arun
```

Linux automatically updates:

- `/etc/passwd` → User details
- `/etc/shadow` → Encrypted password
- `/etc/group` → Group membership

This is exactly how user management is performed on production Linux servers.
