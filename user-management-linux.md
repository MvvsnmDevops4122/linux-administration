
# 🐧 Linux User Management 

## 1. What is Linux User Management?

Linux User Management means **creating, modifying, deleting, and managing users and groups and controlling their access on Linux system.**

### Main Components

- User
- Group
- Role
- Permissions
- Sudo / Privileged Access

---

## 2. 👤 User

A **user** is an individual account used to access and work on a Linux system.

### Example

```bash
useradd ramesh
````

Here:

```text
ramesh → Linux user
```

### Important User Information

A user has information such as:

* Username
* UID
* Primary Group
* Secondary Groups
* Home Directory
* Login Shell

### Verify User

```bash
id ramesh
```

Example:

```text
uid=1001(ramesh) gid=1001(ramesh) groups=1001(ramesh)
```

Meaning:

```text
uid    → User ID
gid    → Primary Group ID
groups → Group memberships
```

---

## 3. 👥 Group

A **group** is a collection of users.

Instead of assigning permissions to every user individually, we can assign permissions to a group.

### Example

```text
             devops group
                  |
        ┌─────────┼─────────┐
        ↓         ↓         ↓
     Ramesh     Suresh    Krishna
```

### Why Groups?

Groups make permission and access management easier when multiple users need the same access.

### Create Group

```bash
groupadd devops
```

### Verify Group

```bash
getent group devops
```

or:

```bash
cat /etc/group
```

`getent group` is useful when querying the system's configured group database.

---

## 4. 🎯 Role

A **role** represents the responsibility or level of access assigned to a user.

### Examples

```text
devops-trainee → Read access

devops-juniors → Specific Write/Update access

devops-seniors → Write + Update access

devops-leads   → Write + Update + Delete access
```

### Important Clarification

In basic Linux, **role is a logical concept**. There is no standard `roleadd` command for creating roles.

Roles can be implemented using:

```text
Groups
   +
Permissions
   +
Sudo rules
```

### Example

```text
Ramesh
   ↓
devops-trainee group
   ↓
Required permissions
```

---

## 5. 🔹 Why is User Management Required?

User management is required to:

* Control access to servers
* Prevent unauthorized access
* Give users only the required permissions
* Provide administrative access when required
* Manage teams using groups
* Follow the Principle of Least Privilege

### Principle of Least Privilege

> Give a user only the permissions required to perform their job.

---

## 6. 📍 Where is User Management Used?

User management is commonly used in:

* Linux servers
* AWS EC2
* Production servers
* Development servers
* Testing / QA servers
* DevOps environments
* Application servers

---

# 7. 🛠️ Creating a User — `useradd`

Used to create a user.

### Syntax

```bash
useradd <username>
```

### Example

```bash
useradd ramesh
```

### Verify

```bash
id ramesh
```

---

# 8. 🔑 Set User Password — `passwd`

Used to set or change a user's password.

### Syntax

```bash
passwd <username>
```

### Example

```bash
passwd ramesh
```

The system will ask you to enter the password.

---

# 9. 🔗 Adding a User to a Group

There are different ways to modify a user's group membership.

## Change Primary Group

```bash
usermod -g <group-name> <user-name>
```

Example:

```bash
usermod -g devops ramesh
```

```text
-g → Change primary group
```

---

## Set Secondary Groups

```bash
usermod -G <group-name> <user-name>
```

Example:

```bash
usermod -G developers ramesh
```

```text
-G → Supplementary / secondary groups
```

> ⚠️ `-G` sets the user's supplementary group list. If used without `-a`, existing supplementary group memberships can be replaced.

---

## Append a Secondary Group

```bash
usermod -aG <group-name> <user-name>
```

Example:

```bash
usermod -aG testing ramesh
```

Meaning:

```text
-a → Append
-G → Supplementary / secondary group
```

### ⭐ Remember

```text
-g
 ↓
Primary Group

-aG
 ↓
Add Secondary Group
```

---

# 10. 🗑️ Delete User and Group

## Delete User

```bash
userdel ramesh
```

Deletes the user account.

## Delete User + Home Directory

```bash
userdel -r ramesh
```

Deletes the user account and the user's home directory.

⚠️ Be careful with `-r`, especially on production systems.

## Delete Group

```bash
groupdel devops
```

A group cannot normally be deleted while it is the **primary group of an existing user**.

If `devops` is Ramesh's primary group:

```text
Ramesh
  ↓
Primary Group
  ↓
devops
  ↓
❌ groupdel devops
```

Change Ramesh's primary group first:

```bash
usermod -g users ramesh
```

Then:

```bash
groupdel devops
```

---

# 11. 📂 Important User Management Files

## `/etc/passwd`

Contains basic user account information.

```text
/etc/passwd
      ↓
User account information
```

## `/etc/shadow`

Contains password-related and password-aging information.

```text
/etc/shadow
      ↓
Password + aging information
```

## `/etc/group`

Contains group information.

```text
/etc/group
      ↓
Group information
```

## `/etc/gshadow`

Contains secure group-related information.

```text
/etc/gshadow
      ↓
Secure group information
```

## `/etc/sudoers`

Main sudo configuration file.

```text
/etc/sudoers
      ↓
Main sudo policy
```

## `/etc/sudoers.d/`

Directory containing additional sudo configuration files.

```text
/etc/sudoers.d/
      ↓
Additional sudo policies
```

---

# 12. 🔐 SSH Access

SSH (**Secure Shell**) provides secure remote access to a Linux server.

### Connect to a Server

```bash
ssh ramesh@<server-ip>
```

Meaning:

```text
ssh          → SSH client/command
ramesh       → Remote username
<server-ip>  → Remote server IP address
```

### SSH Configuration

The SSH server configuration is commonly maintained in:

```text
/etc/ssh/sshd_config
```

One relevant setting is:

```text
PasswordAuthentication
```

### Password Authentication Disabled

```text
PasswordAuthentication no
```

→ Password-based authentication is disabled.

### Password Authentication Enabled

```text
PasswordAuthentication yes
```

→ Password-based authentication is enabled, assuming other authentication and account policies permit it.

### Validate SSH Configuration

```bash
sshd -t
```

This checks whether the SSH server configuration has valid syntax.

If there is no output, the configuration syntax is valid.

### Restart SSH Service

After changing the configuration:

```bash
systemctl restart sshd
```

### Production Tip

When changing SSH configuration remotely, keep your existing SSH session open until you confirm that the new configuration works.

> SSH authentication depends on the server configuration. Cloud Linux instances such as AWS EC2 commonly use key-based authentication.

---

# 13. 🔑 Sudo Access

## What is `sudo`?

`sudo` allows an authorized user to execute a command with elevated privileges.

Example:

```bash
sudo systemctl restart nginx
```

---

# 14. Full Sudo Access for Ramesh

There are different ways to provide broad administrative access.

## Method 1 — `wheel` Group

On RHEL-family systems, including many RHEL/Amazon Linux configurations, the `wheel` group is commonly used.

```bash
usermod -aG wheel ramesh
```

### Verify

```bash
id ramesh
```

Then start a new login session and check:

```bash
sudo -l
```

### Important

The actual sudo configuration determines what members of the `wheel` group can do.

> `wheel` does not automatically mean full sudo access on every Linux distribution.

---

# 15. Full Sudo Access Using Sudoers

Use:

```bash
visudo
```

Add:

```text
ramesh ALL=(ALL) ALL
```

This gives Ramesh broad sudo access according to this rule.

For example:

```bash
sudo systemctl restart nginx
```

### Why `visudo`?

Prefer:

```bash
visudo
```

instead of directly editing:

```bash
vim /etc/sudoers
```

`visudo` validates the sudoers syntax and helps prevent configuration mistakes.

---

# 16. 🔒 Limited Sudo Access — Real-Time

Suppose Ramesh needs to:

* Create users
* Modify users

But should **not** receive unrestricted administrative access.

## Step 1 — Create Sudoers File

```bash
visudo -f /etc/sudoers.d/ramesh
```

## Step 2 — Add the Rule

```text
ramesh ALL=(ALL) /usr/sbin/useradd, /usr/sbin/usermod
```

Meaning:

```text
Ramesh
   ↓
Specific sudo permission
   ↓
useradd + usermod
```

## Step 3 — Verify

As Ramesh:

```bash
sudo -l
```

## Step 4 — Allowed Commands

```bash
sudo /usr/sbin/useradd john
```

and:

```bash
sudo /usr/sbin/usermod -aG devops john
```

But:

```bash
sudo systemctl restart nginx
```

will not be allowed by this rule unless another sudo rule grants that permission.

---

# 17. 👥 Limited Sudo Access for a Group

If several users require the same permissions, group-based sudo is better than creating individual rules for each user.

## Step 1 — Create Group

```bash
groupadd devops-user-managers
```

## Step 2 — Add Ramesh

```bash
usermod -aG devops-user-managers ramesh
```

## Step 3 — Create Sudo Rule

```bash
visudo -f /etc/sudoers.d/devops-user-managers
```

Add:

```text
%devops-user-managers ALL=(ALL) /usr/sbin/useradd, /usr/sbin/usermod
```

## Step 4 — Verify

```bash
id ramesh
```

Then start a new login session and check:

```bash
sudo -l
```

---

# 18. ⭐ Why Group-Based Sudo is Better for Teams

Suppose:

```text
Ramesh
Suresh
Krishna
```

All need the same permissions.

Instead of:

```text
Ramesh  → sudo rule
Suresh  → sudo rule
Krishna → sudo rule
```

Use:

```text
             devops-user-managers
                      |
          ┌───────────┼───────────┐
          ↓           ↓           ↓
       Ramesh       Suresh      Krishna
                      |
                      ↓
              Limited sudo access
                      |
                useradd + usermod
```

If a new administrator joins:

```bash
usermod -aG devops-user-managers newuser
```

The group-based sudo rule applies to the new member.

---

# 19. ⭐ Real-Time Best Practice

If a user needs only specific administrative commands, provide **limited sudo access** through a dedicated group and a separate file under `/etc/sudoers.d/`, instead of giving unrestricted administrative access.

This follows the **Principle of Least Privilege**.

### Production Flow

```text
User
 ↓
Team / Role
 ↓
Group
 ↓
Required Permissions
 ↓
Limited Sudo
 ↓
Required Administrative Commands
```

---

# 20. 📍 Verify Sudo Command Paths

Before adding commands to a sudoers rule, verify their actual locations on the server.

```bash
command -v useradd
command -v usermod
```

Example:

```text
/usr/sbin/useradd
/usr/sbin/usermod
```

Use the actual paths returned by your system.

### Why?

Sudo rules should reference the command path that actually exists on that system.

---

# 21. 🔍 `/etc/sudoers` vs `visudo` vs `/etc/sudoers.d/`

This is an important interview topic.

### `/etc/sudoers`

```text
/etc/sudoers
      ↓
     FILE
      ↓
Main sudo configuration
```

### `/etc/sudoers.d/`

```text
/etc/sudoers.d/
      ↓
  DIRECTORY
      ↓
Additional sudo configuration files
```

### `visudo`

```text
visudo
   ↓
 COMMAND
   ↓
Safely edit / validate sudo configuration
```

### `sudo`

```text
sudo
   ↓
 COMMAND
   ↓
Execute an allowed command with elevated privileges
```

---

# 🧠 Quick Revision

## User Management Flow

```text
USER
 ↓
GROUP
 ↓
ROLE / RESPONSIBILITY
 ↓
PERMISSIONS
 ↓
SUDO
 ↓
CONTROLLED ADMINISTRATIVE ACCESS
```

## ⭐ Core Commands

```bash
useradd
passwd
id
groupadd
usermod
userdel
groupdel

sshd -t
systemctl restart sshd

visudo
sudo
```

## 🔐 Core Files

```text
/etc/passwd
/etc/shadow
/etc/group
/etc/gshadow
/etc/sudoers
/etc/sudoers.d/
/etc/ssh/sshd_config
```

> **Golden Rule:** In production, give users only the permissions they need — no more, no less.

```
```
