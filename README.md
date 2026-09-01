# 🐧 Linux Administration

Practical Linux administration notes, commands, troubleshooting,
and real-world DevOps scenarios.

## 📚 Topics Covered

- Linux Basics & File System
- User & Group Management
- File & Directory Permissions
- SSH & Remote Access
- Vim Editor
- Process Management
- Package Management
- Disk & Storage Management
- Networking
- System Administration
- Log Management
- Troubleshooting
- Shell Scripting

## 🛠️ Important Commands

| Category | Commands |
|---|---|
| Files & Directories | `ls`, `cd`, `pwd`, `cp`, `mv`, `rm` |
| Users | `useradd`, `usermod`, `userdel`, `passwd` |
| Groups | `groupadd`, `groupmod`, `groupdel` |
| Permissions | `chmod`, `chown`, `chgrp` |
| Processes | `ps`, `top`, `kill`, `systemctl` |
| Networking | `ip`, `ss`, `ping`, `curl` |
| Disk | `df`, `du`, `lsblk`, `mount` |
| Packages | `yum`, `dnf`, `rpm` |
| Logs | `journalctl`, `tail`, `less` |
| SSH | `ssh`, `ssh-keygen`, `scp` |

## 👤 User & Group Management

Examples:

```bash
useradd ramesh
passwd ramesh
id ramesh

groupadd devops
usermod -aG devops ramesh
