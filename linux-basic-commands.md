# LINUX

## 1. System Information Commands

### User Switching & Session

```bash
1. sudo su -                # Switch to root user (root's home: /root)
2. sudo su                  # Switch to root but stay in current user’s home directory
3. su - username            # Switch to another normal user
4. exit                     # Exit current shell/session
5. clear                    # Clear terminal screen
```

✅ **Use Case**: Switching between application users (e.g., `tomcat`, `jenkins`, `root`) during deployments or troubleshooting.

### Kernel & OS Info

```bash
1. uname                   # Show OS details (e.g., Linux)
2. uname -r                # Show kernel version
3. uname -a                # Full system info (kernel, OS, arch, build time)
4. uname -m                # Architecture (32/64-bit)
```

✅ **Use Case**: Checking kernel version before installing Docker/Kubernetes.

### Hostname & Network

```bash
1. hostname                         # Show hostname
2. hostname -i                      # Show system IP
3. hostnamectl set-hostname <name>  # Change hostname
```

✅ **Use Case**: Updating hostname to meaningful names like `jenkins-server`, `prod-db`.

### Uptime & Boot Time

```bash
1. uptime                  # Display system running time, users, load average
2. uptime -p               # Display running time only (e.g., up 2 hours)
3. uptime -s               # Show exact boot time
```

✅ **Use Case**: Checking server uptime after patching or unexpected reboot.

### History

```bash
1. history                 # Show executed commands
2. history -c              # Clear all history
3. history -d 500          # Delete entry #500
4. !35                     # Run command #35 from history
5. !!                      # Re-run the last executed command
```

✅ **Use Case**: Re-running long commands quickly during builds or troubleshooting.
⚠️ **Caution**: Avoid `history -c` on shared servers (audit trail loss).

### Manual & Help

The `man` command is used to view the manual pages for Linux commands and programs.

```bash
1. man <cmd>               # Manual page for command
2. whatis ls               # One-line description of the command
```

✅ **Use Case**: Quick help for unfamiliar commands.

### Date & Time

```bash
1. date                                      # Show system date/time
2. sudo date -s "2025-08-30 09:00:00"        # Set date/time
3. timedatectl                               # Show timezone & clock info
4. timedatectl set-timezone Asia/Kolkata     # Set timezone
```

✅ **Use Case**: Fixing incorrect timezone on Jenkins build servers.

### Date Format Examples

```bash
1. date +"%d"            # Display date only
2. date +"%m"            # Display month only
3. date +"%y"            # Display year only
4. date +%D              # MM/DD/YY
5. date +"%F"            # YYYY-MM-DD
6. date +"%A"            # Weekday name
7. date +"%B"            # Month name
8. date +%H:%M:%S        # Display Hours:Minutes:Seconds
```

✅ **Use Case**: Creating daily log files, e.g., `backup_$(date +"%F").log`

### Calendar

```bash
cal                    # Display current month calendar
```

✅ **Use Case**: Checking calendar while scheduling cron jobs.

## 2. Hardware Information Commands

### Basic CPU & Memory Commands

```bash
1. lscpu                  # Show CPU architecture details (cores, threads, vendor)
2. cat /proc/cpuinfo      # CPU hardware info
3. nproc                  # Number of CPU cores available
4. free                   # Show memory usage
5. free -h                # Show memory in human-readable format
6. free -m                # Show memory in MB
7. vmstat                 # Show CPU, memory, swap, and I/O statistics
8. top                    # Display real-time process & resource monitor
```

### vmstat Example Output

```bash
ubuntu@ip-172-31-6-93:~$ vmstat
procs -----------memory---------- ---swap-- -----io---- -system-- -------cpu-------
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st gu
 2  0      0 185280  22120 536036    0    0     9    15   43    0  0  0 100  0  0  0
```

✅ **Use Case**:
Check **CPU, RAM**, and **system load** before deploying heavy applications like **Jenkins**, **MySQL**, or other services.

## 3. User Information Commands

### Basic User Info & Session Tracking

```bash
1. whoami / logname       # Show current username
2. users                  # List all logged-in users (names only)
3. who                    # Show usernames + login time + terminal info
4. who -H                 # Same as 'who' but with headers
5. w                      # Display usernames, login time, idle time, actions, and system load
6. last                   # Show login history
7. last -R username       # Show login history for a specific user
8. last -F                # Show login/logout timestamps
9. whereis mkdir          # Find binary, source, and man page locations of a command
```

✅ **Use Case**:
Useful for **security audits**, to check **who logged in recently**, what they’re doing, and when.
