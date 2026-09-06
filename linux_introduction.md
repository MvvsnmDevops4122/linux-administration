# 📘 LINUX INTRODUCTION

---

## 1. AWS REGION

### What is an AWS Region?

An **AWS Region** is a geographical location where AWS has multiple data centers.

### Examples

```text
us-east-1    → N. Virginia
ap-south-1  → Mumbai
```

---

# 2. AVAILABILITY ZONE (AZ)

### What is an Availability Zone?

An **Availability Zone (AZ)** is an isolated infrastructure/data-center location inside an AWS Region.

```text
             Region
                │
       ┌────────┼────────┐
       ↓        ↓        ↓
     AZ-1     AZ-2     AZ-3
```

### Purpose

* **High Availability**
* **Fault Tolerance**

If one AZ has a problem, the application can continue running in another AZ.

---

# 3. LATENCY

### What is Latency?

**Latency = Delay in communication between systems.**

```text
User → AWS Region → Application
```

### Remember

```text
Nearby Region → Usually lower latency
Far Region    → Usually higher latency
```

---

# 4. TRADITIONAL DATA CENTER

Before cloud computing, organizations maintained their own physical data centers.

### A Data Center contains:

* Servers
* Storage
* Networking equipment
* Power supply
* Cooling systems
* Physical security
* Operating systems
* Backup systems

### Simple Flow

```text
Company
   ↓
Own Data Center
   ↓
Servers + Storage + Network
   ↓
Application
```

The company is responsible for maintaining the infrastructure.

---

# 5. MIGRATION TO CLOUD

Organizations can move their applications and infrastructure from a traditional data center to a cloud platform such as AWS.

```text
Traditional Data Center
          ↓
       Migration
          ↓
          AWS
          ↓
EC2 / S3 / RDS / VPC
```
 
# 6. IP-ENABLED DEVICE

### What is an IP-Enabled Device?

An **IP-enabled device** is a device that can communicate over a network using an IP address.

### Examples

* Mobile
* Laptop
* Server
* TV
* Washing Machine
* Refrigerator

### It may contain:

* **OS** → Helps applications/users interact with hardware
* **RAM** → Temporary memory
* **HD/SSD** → Storage
* **Processor** → Performs processing

### Hardware

```text
RAM
HD / SSD
Processor
```

### Simple Flow

```text
IP-Enabled Device
       ↓
      OS
       ↓
   Hardware
```

---

# 7. WINDOWS vs LINUX

| Windows                           | Linux                                     |
| --------------------------------- | ----------------------------------------- |
| GUI is generally heavier          | Lightweight                               |
| Can require more RAM/CPU          | Can work efficiently with lower resources |
| Commonly used on desktops/laptops | Widely used on servers/cloud              |
| Proprietary software              | Open source                               |

### Why is Linux popular?

* Low resource usage
* Can work with lower RAM
* Suitable for long-running servers
* Open source
* Secure
* Stable

**Linux is lightweight, secure, stable, and widely used for servers.**

---

# 8. WHAT IS LINUX?

**Linux is a kernel.**

The **kernel is the core part of an operating system**.

### Flow

```text
User
 ↓
Application
 ↓
Linux Kernel
 ↓
Hardware
```
---

### Remember

> **Linux = Kernel**

---

# 9. LINUS TORVALDS

**Linus Torvalds → Created Linux Kernel and Git**

### Remember

> **Linus Torvalds → Linux + Git**

---

# 10. LINUX AND C LANGUAGE

The **Linux Kernel was developed mainly using the C programming language**.

### Remember

```text
Linux Kernel
      ↓
 Mainly C
```

---

# 11. WHAT IS UNIX?

### Definition

> **Unix is an operating system family.**

Linux follows many Unix concepts/principles, so Linux is called a **Unix-like operating system**.

```text
Unix
 ↓
Unix principles
 ↓
Linux
```

### Important

> **Linux is not Unix. Linux is Unix-like.**

### Examples of Unix-like systems

* Linux
* Ubuntu
* Red Hat
* Debian

---

# 12. HARDWARE + SOFTWARE

A computer system consists of **hardware and software**.

## Hardware

Physical parts of a computer.

Examples:

* CPU / Processor
* RAM
* Hard Disk / SSD

## Software

Programs that run on the hardware.

Examples:

* Linux
* Windows
* Applications

### Simple Diagram

```text
Computer
   │
   ├── Hardware
   │     ├── CPU
   │     ├── RAM
   │     └── Disk
   │
   └── Software
         ├── Operating System
         └── Applications
```

---

# 13. WHAT IS KERNEL?

### Definition

> **Kernel is the core part of the operating system.**

It connects **software and hardware**.

```text
Applications
      ↓
    Kernel
      ↓
   Hardware
```

### Kernel Responsibilities

* **Memory Management**
* **CPU Management**
* **Process Management**
* **Device Management**
* **File System Management**

### Easy Remember

> **Kernel → Software ↔ Hardware**

---

# 14. LINUX DISTRIBUTIONS / FLAVOURS

### What is a Linux Distribution?

A Linux distribution is a complete operating system built around the **Linux Kernel** and includes system tools, libraries, package management, and other software.

```text
Linux Kernel
     +
System Tools
     +
Libraries
     +
Package Manager
     ↓
Linux Distribution
```

### Examples

* RHEL / Red Hat
* Debian
* Oracle Linux
* Ubuntu
* Fedora
* Amazon Linux

### Remember

> **Linux = Kernel**
> **Ubuntu/RHEL/Debian = Linux Distributions**

---

# 15. OPEN SOURCE vs ENTERPRISE

## Open Source

> Source code is available and the software can be used according to its license.

Support can come from:

* Community
* Documentation
* Forums

```text
Open Source
     ↓
Community Support
```

## Enterprise

Organizations can purchase **commercial support** from the vendor.

```text
Enterprise
     ↓
Vendor Support
     ↓
Technical Assistance
```

### Remember

> **Open Source → Community Support**
> **Enterprise → Vendor/Commercial Support**

---

# 16. AUTHENTICATION

### What is Authentication?

> **Authentication means verifying who you are.**

There are three common authentication factors:

### 1. What you know

* Username
* Password
* PIN

### 2. What you have

* RSA Token
* Authenticator
* Security Key

### 3. What you are

* Fingerprint
* Retina
* Palm
* Other biometrics

### Remember

```text
Know → Password
Have → Token
Are  → Fingerprint
```

---

# 17. SSH KEY

### Generate SSH Key

```bash
ssh-keygen -f <file-name>
```

It generates a key pair:

```text
Public Key
Private Key
```

### Important

> **Private Key → Keep Secret**

> **Public Key → Can be shared**

---

# 18. SSH

### SSH = Secure Shell

SSH is a protocol used to **securely connect to a remote system**.

### Example

```bash
ssh -i <private-key> ec2-user@<IP-address>
```

### Connection

```text
Your Computer
      ↓
     SSH
      ↓
EC2 Instance
```

### Default SSH Port

> **SSH → TCP 22**

---

# 19. AWS SECURITY GROUP / FIREWALL

### Firewall

> A firewall controls network traffic based on rules.

### AWS Security Group

> A Security Group acts as a **virtual firewall** for resources such as EC2 instances.

```text
Internet
    ↓
Security Group
    ↓
EC2 Instance
```

---

# 20. INBOUND TRAFFIC

> **Inbound = Incoming traffic**

```text
Internet → EC2
```

### Examples

```text
SSH    → TCP 22
HTTP   → TCP 80
HTTPS  → TCP 443
```

---

# 21. OUTBOUND TRAFFIC

> **Outbound = Outgoing traffic**

```text
EC2 → Internet
```

---

# 22. ACCESSING AN EC2 SERVER

Suppose:

```text
Public IP  → <public-ip>
SSH Port   → 22
User       → ec2-user
Key        → mykey.pem
```

### Command

```bash
ssh -i mykey.pem ec2-user@<public-ip>
```

The Security Group must allow SSH traffic from your source IP.

### Better Security Practice

Avoid:

```text
SSH 22 → 0.0.0.0/0
```

when it isn't necessary.

Prefer:

```text
SSH 22 → Your Trusted IP
```

### Remember

> **Allow only the traffic that is actually required.**

---

# 23. NETWORK PORTS

TCP and UDP port numbers range from:

```text
0 – 65535
```

Total:

```text
65,536 ports
```

A **port** helps identify a network service/application on a device.

### Common Ports

| Service | Port |
| ------- | ---: |
| SSH     |   22 |
| HTTP    |   80 |
| HTTPS   |  443 |
| FTP     |   21 |
| SMTP    |   25 |
| DNS     |   53 |

---

# 24. PROTOCOL + IP + PORT

For network communication, we commonly identify:

```text
Protocol + IP Address + Port
```

### Example

```text
https://example.com:443
```

Means:

```text
Protocol → HTTPS
Port     → 443
```

The hostname `example.com` is resolved to an IP address through DNS.

### Another Example

```text
http://example.com:80
```

```text
HTTP → Port 80
```

---

# 25. COMMON NETWORK PROTOCOLS

Examples:

* HTTP
* HTTPS
* SSH
* FTP
* SMTP
* DNS
* TCP
* UDP
* DHCP

### Important

> **TCP and UDP → Transport-layer protocols**

> **HTTP, HTTPS, SSH, FTP, SMTP, DNS, DHCP → Application-layer protocols**

---

# 26. `pwd` — PRESENT WORKING DIRECTORY

```bash
pwd
```

→ Shows the **current directory/location**.

### Example

```text
/c/Users/siva
/c/Users/ramesh
```

---

# 27. WINDOWS vs LINUX PATH FORMAT

### Windows

```text
C:\devops\daws-90s
```

### Linux

```text
/c/devops/daws-90s
```

**Note:** `/c/...` is commonly seen in Git Bash on Windows. A native Linux path would normally look like `/home/user/...`.

---

# 28. `cd` — CHANGE DIRECTORY

```bash
cd <directory>
```

→ Used to **move from one directory to another**.

Example:

```bash
cd /home/ec2-user
```

---

# 29. LINUX DIRECTORY PATHS

## Absolute Path

> An absolute path starts from the root directory `/`.

### Example

```text
/home/ec2-user
```

Another example:

```text
/opt/application/logs
```

### Remember

> **Absolute Path → Starts from `/`**

---

## Relative Path

> A relative path is based on your **current directory**.

Example:

```text
daws-90s/daws-90s
```

### Remember

```text
Absolute → Starts from /
Relative → Starts from current location
```

---

# 30. LINUX USERS

Linux has different users and privilege levels.

## Normal User

Prompt commonly looks like:

```text
$
```

Example:

```text
[ec2-user@server ~]$
```

## Root User

Prompt commonly looks like:

```text
#
```

Example:

```text
[root@server ~]#
```

### Root User

Root has **extensive administrative privileges**.

---

# 31. `sudo`

```bash
sudo command
```

`sudo` allows an authorized user to execute a command with **elevated privileges**.

Example:

```bash
sudo yum install nginx
```

### Remember

```text
$ → Usually normal user
# → Usually root user

sudo → Execute command with elevated privileges
```

---
