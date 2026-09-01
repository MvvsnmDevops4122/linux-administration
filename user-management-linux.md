````md
# 🐧 Linux User Management — DevOps Notes

## 1. What is Linux User Management?

Linux User Management is the process of creating, modifying, deleting, and managing user accounts and groups while controlling their access to system resources.

### Main Components

- User
- Group
- Role
- Permissions
- Sudo / Privileged Access

---

## 2. 👤 USER

A user is an individual account used to access and work on a Linux system.

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

---

## 3. 👥 GROUP

A group is a collection of users.

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

---

## 4. 🎯 ROLE

A role represents the responsibility or level of access assigned to a user.

### Examples

```text
devops-trainee → Read access

devops-juniors → Specific write/update access

devops-seniors → Write + Update access

devops-leads   → Write + Update + Delete access
```

### Important Clarification

In basic Linux, **role is a logical concept**, not a separate object that you create with a `roleadd` command.

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

## 5. 🔹 WHY IS USER MANAGEMENT REQUIRED?

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

## 6. 📍 WHERE IS USER MANAGEMENT USED?

User management is commonly used in:

* Linux servers
* AWS EC2
* Production servers
* Development servers
* Testing / QA servers
* DevOps environments
* Application servers

---

# 7. 🛠️ CREATING A USER — `useradd`

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

### Example Output

```text
uid=1001(ramesh) gid=1001(ramesh) groups=1001(ramesh)
```

### Important

```text
uid    → User ID
gid    → Primary Group ID
groups → Group memberships
```

---

# 8. 👥 CREATE GROUP — `groupadd`

Used to create a group.

### Syntax

```bash
groupadd <group-name>
```

### Example

```bash
groupadd devops
```

### Verify

```bash
getent group devops
```

or:

```bash
cat /etc/group
```

### Better Practice

Use:

```bash
getent group devops
```

when you want to query the system's configured group database.

---

# 9. 🔗 ADDING A USER TO A GROUP

There are different ways to modify a user's group membership.

## Change Primary Group

### Syntax

```bash
usermod -g <group-name> <user-name>
```

### Example

```bash
usermod -g devops ramesh
```

Here:

```text
-g → Primary group
```

---

## Set Secondary Groups

### Syntax

```bash
usermod -G <group-name> <user-name>
```

### Example

```bash
usermod -G developers ramesh
```

Here:

```text
-G → Supplementary / secondary groups
```

> ⚠️ `-G` specifies the user's supplementary group list. If used without `-a`, existing supplementary group memberships can be replaced.

---

## Append a Secondary Group

### Syntax

```bash
usermod -aG <group-name> <user-name>
```

### Example

```bash
usermod -aG testing ramesh
```

Here:

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

> This is one of the important points for Linux interviews.

---

# 10. 🔑 SET USER PASSWORD

Use:

```bash
passwd <username>
```

### Example

```bash
passwd ramesh
```

The system will ask you to enter the password.

---

# 11. 📂 IMPORTANT USER MANAGEMENT FILES

## `/etc/passwd`

Contains basic user account information.

```text
/etc/passwd
      ↓
User account information
```

---

## `/etc/shadow`

Contains password-related and password-aging information.

```text
/etc/shadow
      ↓
Password + aging information
```

---

## `/etc/group`

Contains group information.

```text
/etc/group
      ↓
Group information
```

---

## `/etc/sudoers`

Main sudo configuration file.

```text
/etc/sudoers
      ↓
Main sudo policy
```

---

## `/etc/sudoers.d/`

Directory containing additional sudo configuration files.

```text
/etc/sudoers.d/
      ↓
Additional sudo policies
```

---

# 12. 🔐 USER LOGIN TO SERVER USING SSH PASSWORD

Whether SSH allows password authentication or public-key authentication depends on the SSH server configuration and the authentication methods configured on the system.

Check the SSH configuration:

```text
/etc/ssh/sshd_config
```

The relevant setting is:

```text
PasswordAuthentication
```

### Password Authentication Disabled

```text
PasswordAuthentication no
```

Means password authentication is disabled.

### Password Authentication Enabled

```text
PasswordAuthentication yes
```

Password authentication is enabled, assuming other authentication and account policies also permit it.

### Check SSH Configuration

```bash
sshd -t
```

This checks whether the SSH server configuration has valid syntax.

If there is no output, the configuration syntax is valid.

If you changed the configuration, restart or reload the SSH service as appropriate:

```bash
systemctl restart sshd
```

### ⚠️ Production Tip

When changing SSH configuration remotely, keep your existing SSH session open until you confirm that the new configuration works.

---

# 13. 🔑 SUDO ACCESS

## What is `sudo`?

`sudo` allows an authorized user to execute a command with elevated privileges.

### Example

```bash
sudo systemctl restart nginx
```

---

# 14. FULL SUDO ACCESS FOR RAMESH

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

Then start a new login session and test:

```bash
sudo -l
```

### Important

This gives Ramesh the privileges configured for the `wheel` group.

> `wheel` does not automatically mean full sudo access on every Linux distribution. The actual sudo configuration determines what the group can do.

---

# 15. FULL SUDO ACCESS USING SUDOERS

You can also configure Ramesh directly.

Use:

```bash
visudo
```

Add:

```text
ramesh ALL=(ALL) ALL
```

This allows Ramesh to use `sudo` according to this rule.

For example:

```bash
sudo systemctl restart nginx
```

would be allowed by this rule.

### ⚠️ Important

Don't normally edit the main sudoers file directly with:

```bash
vim /etc/sudoers
```

Prefer:

```bash
visudo
```

because it validates the sudoers syntax.

---

# 16. 🔐 LIMITED SUDO ACCESS — REAL-TIME

This is an important real-world approach when Ramesh needs only specific administrative commands.

### Requirement

Ramesh should be able to:

* Create users
* Modify users

But he should **not** receive unrestricted administrative access.

## Step 1 — Create Sudoers File

```bash
visudo -f /etc/sudoers.d/ramesh
```

## Step 2 — Add the Rule

```text
ramesh ALL=(ALL) /usr/sbin/useradd, /usr/sbin/usermod
```

### Meaning

```text
ramesh
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

# 17. 👥 LIMITED SUDO ACCESS FOR A GROUP

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

Then start a new login session for Ramesh and check:

```bash
sudo -l
```

---

# 18. ⭐ WHY GROUP-BASED SUDO IS BETTER FOR TEAMS

Suppose you have:

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

The group-based sudo rule applies to them.

---

# 19. ⭐ REAL-TIME BEST PRACTICE

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

# 20. 📍 IMPORTANT COMMAND PATH POINT

Before putting commands into a sudoers rule, verify their actual locations on your server.

For example:

```bash
command -v useradd
command -v usermod
```

You may get:

```text
/usr/sbin/useradd
/usr/sbin/usermod
```

Use the actual paths returned by your system.

### Why?

Because sudo rules should reference the command path that actually exists on that system.

---

# 21. 🔍 `sudoers` vs `visudo` vs `sudoers.d`

This is an important interview topic.

```text
/etc/sudoers
      ↓
     FILE
      ↓
Main sudo configuration
```

```text
/etc/sudoers.d/
      ↓
  DIRECTORY
      ↓
Additional sudo configuration files
```

```text
visudo
   ↓
 COMMAND
   ↓
Safely edit / validate sudo configuration
```

```text
sudo
   ↓
 COMMAND
   ↓
Execute an allowed command with elevated privileges
```

---

# 🧠 Quick Revision

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

### ⭐ Core Commands to Remember

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

### 🔐 Core Files to Remember

```text
/etc/passwd
/etc/shadow
/etc/group
/etc/sudoers
/etc/sudoers.d/
/etc/ssh/sshd_config
```

> **Golden Rule:** In production, give users only the permissions they need — no more, no less.
