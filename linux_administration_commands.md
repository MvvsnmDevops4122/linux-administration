

# 📘 Linux Commands & Administration

> Practical Linux reference for DevOps, Cloud, CI/CD, troubleshooting, and system administration.

---

## 1. Linux Command Syntax

### General Syntax

```bash
command <options> <inputs>
```

* `command` → Action to perform
* `options` → Modify command behavior
* `inputs/arguments` → Target on which the command operates

### Example

```bash
ls -l /home
```

```text
ls      → command
-l      → option
/home   → input
```

---

## 2. `uname` — System Information

Displays information about the Linux system.

```bash
uname
```

### Display all available information

```bash
uname -a
```

`-a` → Display all available system information.

---

## 3. Absolute Path vs Relative Path

### Absolute Path

A complete path that starts from the root.

```text
/home/ec2-user
/opt/application/logs
```

### Relative Path

A path based on the current working directory.

```text
repos/
../logs/
```

### Remember

```text
Absolute Path → starts from root
Relative Path → starts from current directory
```

---

## 4. CRUD

```text
C → Create
R → Read
U → Update
D → Delete
```

CRUD represents the four basic operations commonly performed on data, files, and resources.

---

# 📂 Linux Filesystem

## 5. Linux Root Directory

```text
/
```

`/` → Root directory and top-level directory of the Linux filesystem.

---

## 6. Important Linux Directories

| Directory | Purpose                                     |
| --------- | ------------------------------------------- |
| `/`       | Root directory                              |
| `/home`   | Home directories of users                   |
| `/etc`    | Configuration files                         |
| `/tmp`    | Temporary files                             |
| `/bin`    | Traditional location for essential commands |

Examples:

```text
/home/satya
/home/ec2-user
```

> On modern Linux distributions, `/bin` may be linked to `/usr/bin`.

---

# 📁 File & Directory Management

## 7. `pwd`

Displays the current working directory.

```bash
pwd
```

Example:

```text
/home/ec2-user
```

---

## 8. `ls`

Lists files and directories.

```bash
ls
```

### Long listing

```bash
ls -l
```

Displays:

* Permissions
* Owner
* Group
* Size
* Modification time
* File/directory name

### Useful options

```bash
ls -a
ls -lh
ls -lt
ls -lr
ls -ltr
ls -i
```

```text
-a → all files, including hidden
-l → long format
-h → human-readable sizes
-t → sort by modification time
-r → reverse order
-i → inode number
```

---

## 9. Hidden Files

Linux hidden files/directories normally start with:

```text
.
```

Examples:

```text
.bashrc
.ssh
```

Display hidden files:

```bash
ls -la
```

---

## 10. `cd`

Change directory.

```bash
cd /path
```

Go to home directory:

```bash
cd
```

Previous directory:

```bash
cd -
```

One directory back:

```bash
cd ..
```

Two directories back:

```bash
cd ../..
```

---

## 11. `tree`

Displays files and directories in tree format.

```bash
tree
```

---

## 12. `touch`

Creates an empty file if it does not exist.

```bash
touch devops.txt
```

Create multiple files:

```bash
touch one.txt two.txt three.txt
```

> If the file already exists, `touch` updates its timestamps.

---

## 13. `mkdir`

Creates a directory.

```bash
mkdir devops
```

Create multiple directories:

```bash
mkdir linux aws devops
```

### `-p`

Creates parent directories when required.

```bash
mkdir -p parent/child1/child2
```

### `-v`

Displays what was created.

```bash
mkdir -v devops
```

---

## 14. `rmdir`

Removes an **empty directory**.

```bash
rmdir devops
```

> `rmdir` cannot remove a directory containing files.

---

## 15. `rm`

Remove a file:

```bash
rm file.txt
```

Remove multiple files:

```bash
rm file1.txt file2.txt
```

Remove directory recursively:

```bash
rm -r devops
```

Force recursive removal:

```bash
rm -rf devops
```

```text
-r → recursive
-f → force
```

⚠️ Always verify the path before using `rm -rf`.

---

# 📋 Copy, Move & Rename

## 16. `cp`

### Syntax

```bash
cp <source> <destination>
```

Copy file to directory:

```bash
cp devops.txt DevOps/
```

Copy file:

```bash
cp file1.txt file2.txt
```

Copy directory:

```bash
cp -r Python DevOps/
```

Copy all Java files:

```bash
cp *.java destination_dir/
```

---

## 17. `mv`

### Move

```bash
mv file.txt /tmp/
```

### Rename

```bash
mv old.txt new.txt
```

### Move directory

```bash
mv DevOps/ Python/
```

> `mv` is used for both **moving and renaming**.

---

# 📄 File Content & Redirection

## 18. `cat`

Display file content:

```bash
cat devops.txt
```

Display multiple files:

```bash
cat file1.txt file2.txt
```

Display line numbers:

```bash
cat -n file.txt
```

### Create a file using `cat`

```bash
cat > devops.txt
```

Enter content and press:

```text
Ctrl + D
```

`>` → Overwrites existing content.

### Append content

```bash
cat >> devops.txt
```

`>>` → Appends content.

### Merge files

```bash
cat file1 file2 > merge.txt
```

```text
file1 + file2
      ↓
  merge.txt
```

### Reverse content

```bash
tac file.txt
```

---

## 19. Output Redirection

### Overwrite

```bash
command > file.txt
```

### Append

```bash
command >> file.txt
```

### Clear a file without deleting it

```bash
> file.txt
```

```text
>  → overwrite
>> → append
```

---

# 📖 File Viewing

## 20. `head`

Displays the first 10 lines by default.

```bash
head file.txt
```

First 3 lines:

```bash
head -n 3 file.txt
```

Alternative:

```bash
head -3 file.txt
```

### Display lines 35–50

```bash
head -50 file.txt | tail -15
```

---

## 21. `tail`

Displays the last 10 lines by default.

```bash
tail file.txt
```

Last 3 lines:

```bash
tail -n 3 file.txt
```

### Follow live logs

```bash
tail -f app.log
```

This is especially useful for monitoring application logs.

---

## 22. `more`

Displays file content page by page.

```bash
more file.txt
```

---

## 23. `diff`

Compare files line by line:

```bash
diff file1 file2
```

Side-by-side comparison:

```bash
diff -y file1 file2
```

---

# 🔍 Search & Text Processing

## 24. `grep`

Searches for text or patterns.

```bash
grep "linux" file.txt
```

Linux is case-sensitive by default:

```text
linux
Linux
LINUX
```

### Important options

```bash
grep -i "linux" file.txt
```

`-i` → Case-insensitive

```bash
grep -n "linux" file.txt
```

`-n` → Show line numbers

```bash
grep -c "linux" file.txt
```

`-c` → Count matching lines

```bash
grep -v "linux" file.txt
```

`-v` → Show non-matching lines

```bash
grep -l "linux" *
```

`-l` → Show filenames containing the match

```bash
grep -w "linux" file.txt
```

`-w` → Match whole words

```bash
grep -o "linux" file.txt
```

`-o` → Show only matching text

### Context search

```bash
grep -B5 "error" demo.txt
```

5 lines before.

```bash
grep -A5 "error" demo.txt
```

5 lines after.

```bash
grep -C5 "error" demo.txt
```

5 lines before and after.

### Multiple patterns

```bash
grep -iE "error|error1" demo.txt
```

### Quick reference

```text
-i → ignore case
-n → line number
-c → count
-v → inverse match
-l → matching filenames
-w → whole word
-o → matching text only
-A → after
-B → before
-C → before + after
```

---

## 25. `wc`

Counts lines, words, and bytes.

```bash
wc file.txt
```

Count lines:

```bash
wc -l file.txt
```

Count words:

```bash
wc -w file.txt
```

Count bytes:

```bash
wc -c file.txt
```

---

## 26. `sort`

Alphabetical sort:

```bash
sort file.txt
```

Reverse sort:

```bash
sort -r file.txt
```

Sort by second field:

```bash
sort -k 2 data.txt
```

Remove duplicates:

```bash
sort -u file.txt
```

---

## 27. `cut`

Extracts specific fields from text.

### Syntax

```bash
cut -d "<delimiter>" -f <field-number> file
```

```text
-d → delimiter
-f → field
```

Example:

```text
name:password:1001:user
```

Extract first field:

```bash
cut -d ":" -f1 file
```

Multiple fields:

```bash
cut -d ":" -f1,3 /etc/passwd
```

---

# 👤 Users & Groups

## 28. `/etc/passwd`

Contains information about Linux user accounts.

```bash
cat /etc/passwd
```

Example:

```text
root:x:0:0:root:/root:/bin/bash
```

### Extract usernames

```bash
cut -d ":" -f1 /etc/passwd
```

### Extract UIDs

```bash
cut -d ":" -f3 /etc/passwd
```

### Extract username + UID

```bash
cut -d ":" -f1,3 /etc/passwd
```

---

## 29. `id`

Displays user information such as:

* UID
* GID
* Groups

```bash
id
```

```bash
id username
```

---

## 30. `groups`

Displays the groups a user belongs to.

```bash
groups
```

```bash
groups username
```

---

# ⚙️ Advanced Text Processing

## 31. `awk`

`awk` is used for text processing, field extraction, and conditional filtering.

### Extract username

```bash
awk -F ":" '{print $1}' /etc/passwd
```

```text
-F ":" → field separator
$1     → first field
```

### Find users with UID greater than 999

```bash
awk -F ":" '$3 > 999 {print $1}' /etc/passwd
```

```text
$3     → UID field
> 999  → condition
$1     → username
```

---

## 32. `tr`

Translates or replaces characters.

### Lowercase → Uppercase

```bash
cat demo.txt | sort | tr 'a-z' 'A-Z'
```

### Uppercase → Lowercase

```bash
cat demo.txt | sort | tr 'A-Z' 'a-z'
```

---

## 33. Pipe `|`

A pipe sends the output of one command as the input of another command.

```bash
command1 | command2
```

Example:

```bash
curl -s <URL> | grep "linux"
```

Flow:

```text
curl
 ↓
Output
 ↓
grep
 ↓
Matching lines
```

> Pipe allows multiple commands to work together.

---

# 🌐 Network Utilities

## 34. `wget`

Downloads files from a URL.

```bash
wget <URL>
```

Example:

```bash
wget https://example.com/file.txt
```

---

## 35. `curl`

Transfers data to or from a URL.

```bash
curl <URL>
```

Common DevOps uses:

* API testing
* Endpoint testing
* Data transfer
* Shell scripting
* Downloading resources

Example:

```bash
curl https://example.com
```

Silent mode:

```bash
curl -s https://example.com
```

---

# 🔎 File Search

## 36. `find`

Searches for files and directories based on conditions such as name, type, permissions, and modification time.

### Search by name

Case-sensitive:

```bash
find . -name "filename"
```

Case-insensitive:

```bash
find . -iname "filename"
```

### Find files

```bash
find . -type f
```

### Find directories

```bash
find . -type d
```

### Find empty files

```bash
find . -type f -empty
```

### Find non-empty files

```bash
find . -type f ! -empty
```

### Find empty directories

```bash
find . -type d -empty
```

### Search by permission

```bash
find . -perm 777
```

### Search by modification time

```bash
find . -mtime -1
```

Modified within approximately the last 24 hours.

```bash
find . -mtime +1
```

Modified more than approximately 24 hours ago.

### Delete empty files

```bash
find . -type f -empty -delete
```

⚠️ Always verify the search condition before using `-delete`.

### Modify file timestamp for testing

```bash
touch -d "2 days ago" filename
```

---

# ✏️ Stream Editing

## 37. `sed`

`sed` is a stream editor used to replace, delete, and print selected text.

### Replace first occurrence on each line

```bash
sed 's/unix/linux/' abc.txt
```

### Replace second occurrence

```bash
sed 's/unix/linux/2' abc.txt
```

### Replace all occurrences

```bash
sed 's/unix/linux/g' abc.txt
```

### Replace on line 3

```bash
sed '3 s/unix/linux/' abc.txt
```

### Replace within line range

```bash
sed '1,3 s/unix/linux/' abc.txt
```

### Delete line 5

```bash
sed '5d' filename.txt
```

### Delete lines 3–6

```bash
sed '3,6d' filename.txt
```

### Display lines 60–80

```bash
sed -n '60,80p' filename.txt
```

```text
-n → suppress automatic output
p  → print selected lines
```

### Replace and print only line 2

```bash
sed -n '2 s/am/was/p' sample.txt
```

### Replace all occurrences on line 1 and print

```bash
sed -n '1 s/unix/linux/gp' sample.txt
```


---

## 39. Nano

`nano` is a beginner-friendly command-line text editor.

```bash
nano demo.txt
```

Install on RPM-based systems when required:

```bash
sudo yum install nano -y
```

Common shortcuts:

```text
Ctrl + O → Save
Ctrl + X → Exit
```

---

# 1. TAR Command

## What is TAR?

`tar` is used to **create and extract archive files**.

An archive is a single file that contains multiple files and/or directories.

### Common Formats

| Format | Description |
|---|---|
| `.tar` | TAR archive |
| `.tar.gz` | TAR archive compressed using gzip |
| `.tgz` | Same as `.tar.gz` |
| `.zip` | ZIP archive with compression |

> `.tar.gz` is commonly used in Linux environments.

---

## Create a `.tar.gz` Archive

### Syntax

```bash
tar -czvf <file-name>.tar.gz <files/folders>
````

### Example

```bash
tar -czvf aws.tar.gz devops aws
```

This creates:

```text
aws.tar.gz
```

containing:

```text
devops/
aws/
```

---

## Meaning of `tar -czvf`

```text
tar
 │
 ├── c → Create
 ├── z → gzip compression
 ├── v → Verbose output
 └── f → Archive file name
```

### `c` → Create

Creates a new TAR archive.

```bash
tar -c ...
```

### `z` → gzip

Compresses the TAR archive using gzip.

```bash
tar -cz ...
```

### `v` → Verbose

Displays the files/directories being processed.

```bash
tar -czv ...
```

### `f` → File

Specifies the archive file name.

```bash
-f backup.tar.gz
```

### Complete Meaning

```bash
tar -czvf backup.tar.gz devops aws
```

> Create a TAR archive, compress it using gzip, display the files being processed, and save the archive as `backup.tar.gz`.

---

## Extract a `.tar.gz` Archive

### Syntax

```bash
tar -xzvf <file-name>.tar.gz
```

### Example

```bash
tar -xzvf aws.tar.gz
```

### Options

```text
x → Extract
z → gzip
v → Verbose
f → File
```

---

## List Archive Contents

To view the contents without extracting:

```bash
tar -tzvf backup.tar.gz
```

```text
t → List contents
z → gzip
v → Verbose
f → File
```

---

## TAR Quick Revision

### Create

```bash
tar -czvf backup.tar.gz directory/
```

### Extract

```bash
tar -xzvf backup.tar.gz
```

### List

```bash
tar -tzvf backup.tar.gz
```

### Easy Memory

```text
C → Create
X → Extract
T → List

Z → gzip
V → Verbose
F → File
```

---

# ZIP and UNZIP

ZIP is commonly used to archive and compress files/directories.

## Create ZIP

```bash
zip -r ansible.zip Ansible/
```

`-r` means recursively include the directory and its contents.

## Extract ZIP

```bash
unzip ansible.zip
```

---

# Working with Compressed Files

## Search inside a `.gz` file

```bash
zgrep "<pattern>" file.gz
```

Example:

```bash
zgrep "ERROR" application.log.gz
```

## Display a compressed file

```bash
zcat file.gz
```

This displays the contents without manually extracting the file.

---

# 2. FIND Command

## What is `find`?

`find` is used to **search for files and directories based on conditions**.

### Syntax

```bash
find <where-to-search> <conditions>
```

---

## Find `.log` Files

```bash
find / -iname "*.log"
```

### Meaning

```text
/          → Search from root
-iname     → Case-insensitive name search
"*.log"    → Files ending with .log
```

---

## Find a Directory by Name

```bash
find / -type d -name "devops"
```

```text
-type d → Search for directories
-name   → Match the name
```

---

## Find Files Owned by a User

```bash
find / -user ramesh
```

This searches for files/directories owned by `ramesh`.

---

## Exclude a User's Home Directory

```bash
find / -user ramesh -not -path "/home/ramesh/*"
```

This excludes:

```text
/home/ramesh/
```

---

## Search by Name

### Case-sensitive

```bash
find . -name "filename"
```

### Case-insensitive

```bash
find . -iname "filename"
```

---

## Find Files

```bash
find . -type f
```

## Find Directories

```bash
find . -type d
```

---

## Find Empty Files

```bash
find . -type f -empty
```

## Find Non-Empty Files

```bash
find . -type f ! -empty
```

## Find Empty Directories

```bash
find . -type d -empty
```

---

## Search by Permission

```bash
find . -perm 777
```

This finds files/directories with the specified permission mode.

---

## Search by Modification Time

### Modified within approximately the last 24 hours

```bash
find . -mtime -1
```

### Modified more than approximately 24 hours ago

```bash
find . -mtime +1
```

---

## Delete Empty Files

```bash
find . -type f -empty -delete
```

> Always verify the search condition before using `-delete`.

---

## Modify File Timestamp for Testing

```bash
touch -d "2 days ago" filename
```

---

## FIND Quick Revision

```bash
find . -type f
find . -type d
find . -name "filename"
find . -iname "*.log"
find . -user ramesh
find . -empty
find . -mtime -1
find . -mtime +1
```

---

# 3. Linux User Management

User management is an important Linux administration task.

Typical organization scenario:

```text
Employee joins organization
        ↓
Create Linux account
        ↓
Assign required groups/access
        ↓
Employee works
        ↓
Employee leaves organization
        ↓
Remove access safely
```

---

# Part A — Creating a User

## Scenario

A new employee named `ramesh` joins the organization.

### Requirements

* Create user `ramesh`
* Create groups `devops` and `testing`
* Set a password
* Make `devops` the primary group
* Add `testing` as a supplementary group

---

## Step 1: Create the User

```bash
useradd ramesh
```

Verify:

```bash
id ramesh
```

---

## Step 2: Create Groups

```bash
groupadd devops
groupadd testing
```

Verify:

```bash
getent group devops
getent group testing
```

---

## Step 3: Set User Password

```bash
passwd ramesh
```

Enter the password when prompted.

---

## Step 4: Set Primary Group

```bash
usermod -g devops ramesh
```

Verify:

```bash
id ramesh
```

Example:

```text
uid=1001(ramesh) gid=1002(devops) groups=1002(devops)
```

### Important

```text
-g → Primary group
```

---

## Step 5: Add Supplementary Group

```bash
usermod -aG testing ramesh
```

Verify:

```bash
id ramesh
```

Example:

```text
uid=1001(ramesh) gid=1002(devops) groups=1002(devops),1003(testing)
```

### Important

```text
-g  → Primary group
-aG → Add supplementary group
```

The `-a` is important because it appends the new group instead of replacing the user's existing supplementary groups.

---

## User Creation Flow

```text
Create User
    ↓
useradd ramesh
    ↓
Create Groups
    ↓
groupadd devops
groupadd testing
    ↓
Set Password
    ↓
passwd ramesh
    ↓
Set Primary Group
    ↓
usermod -g devops ramesh
    ↓
Add Supplementary Group
    ↓
usermod -aG testing ramesh
    ↓
Verify
    ↓
id ramesh
```

---

## All User Creation Commands

```bash
useradd ramesh
groupadd devops
groupadd testing
passwd ramesh
usermod -g devops ramesh
usermod -aG testing ramesh
id ramesh
```

---

# Part B — Removing a User

## Scenario

Ramesh leaves the organization.

We need to:

1. Check whether he is logged in
2. Check his running processes
3. Terminate processes if required
4. Check his groups
5. Take a backup of his home directory
6. Check sudo access
7. Delete the user and home directory
8. Verify removal

---

## Step 1: Check Whether User Is Logged In

```bash
who | grep ramesh
```

Alternative:

```bash
w | grep ramesh
```

If Ramesh is logged in, identify his processes before removing the account.

---

## Step 2: Check User Processes

```bash
ps -u ramesh
```

This shows processes owned by Ramesh.

If necessary:

```bash
pkill -u ramesh
```

> Check the processes first. `pkill -u` terminates processes owned by that user.

---

## Step 3: Check User Groups

```bash
id ramesh
```

Example:

```text
uid=1001(ramesh) gid=1002(devops) groups=1002(devops),1003(testing)
```

This shows:

```text
Primary group       → devops
Supplementary group → testing
```

---

## Remove Supplementary Group Membership

If required:

```bash
gpasswd -d ramesh testing
```

Verify:

```bash
id ramesh
```

### Important

```bash
gpasswd -d ramesh testing
```

removes Ramesh from the `testing` group.

It does **not** delete the `testing` group.

---

## Step 4: Take Backup of Home Directory

Before deleting the account, take a backup if the files may be required later.

Create backup directory:

```bash
mkdir -p /backup
```

Create compressed backup:

```bash
tar -czvf /backup/ramesh_homedir.tar.gz /home/ramesh
```

This creates:

```text
/backup/ramesh_homedir.tar.gz
```

The backup includes files under:

```text
/home/ramesh/
```

including hidden files such as:

```text
.bashrc
.bash_profile
.bash_logout
```

Verify:

```bash
ls -lh /backup
```

---

## Step 5: Check Sudo Access

Check:

```bash
grep ramesh /etc/sudoers
```

Also:

```bash
grep -R ramesh /etc/sudoers.d/
```

Why?

A user may have administrative privileges configured through sudo.

Also check group membership because sudo access can be granted through groups.

---

## Step 6: Remove the User

```bash
userdel -r ramesh
```

### Meaning

```text
userdel → Delete the user account
-r       → Remove home directory and mail spool
```

This removes:

```text
User account
     +
Home directory
     +
User's mail spool
```

Because we created:

```text
/backup/ramesh_homedir.tar.gz
```

the home-directory data can be recovered later if required.

---

## Step 7: Verify User Removal

```bash
id ramesh
```

Expected:

```text
id: ‘ramesh’: no such user
```

You can also check:

```bash
getent passwd ramesh
```

If there is no output, the account is no longer present in the passwd database.

---

## Complete User Removal Flow

```text
Ramesh leaves organization
          ↓
Check login
          ↓
who | grep ramesh
          ↓
Check processes
          ↓
ps -u ramesh
          ↓
Terminate if required
          ↓
pkill -u ramesh
          ↓
Check groups
          ↓
id ramesh
          ↓
Remove supplementary access if required
          ↓
gpasswd -d ramesh testing
          ↓
Take backup
          ↓
tar -czvf /backup/ramesh_homedir.tar.gz /home/ramesh
          ↓
Check sudo access
          ↓
Delete user
          ↓
userdel -r ramesh
          ↓
Verify
          ↓
id ramesh
```

---

# 4. Linux Package Management

## What is Package Management?

Package management is the process of:

* Installing software
* Removing software
* Updating software
* Searching for packages
* Checking package information
* Managing installed packages

A **package** is a collection of files required to install and run software.

---

## Common Package Managers

| Linux Distribution | Package Manager |
| ------------------ | --------------- |
| Amazon Linux       | `dnf`           |
| RHEL               | `dnf`           |
| Fedora             | `dnf`           |
| Ubuntu             | `apt`           |
| Debian             | `apt`           |

> Older RHEL/Amazon Linux systems may also use `yum`. Modern systems commonly use `dnf`.

---

# A. DNF Package Manager

`dnf` stands for **Dandified YUM**.

It is used for package management on RPM-based distributions.

Common examples:

* Amazon Linux
* RHEL
* Fedora

---

## 1. Search for a Package

```bash
dnf search <package-name>
```

Example:

```bash
dnf search nginx
```

---

## 2. Check Package Information

```bash
dnf info <package-name>
```

Example:

```bash
dnf info nginx
```

Information may include:

```text
Name
Version
Release
Architecture
Size
Repository
Summary
Description
```

---

## 3. Install a Package

```bash
dnf install <package-name>
```

Example:

```bash
dnf install nginx
```

### Non-Interactive Installation

```bash
dnf install -y nginx
```

`-y` automatically answers yes to confirmation prompts.

---

## 4. Check Installed Packages

```bash
dnf list installed
```

Specific package:

```bash
dnf list installed | grep nginx
```

Another useful command:

```bash
rpm -q nginx
```

---

## 5. Remove a Package

```bash
dnf remove <package-name>
```

Example:

```bash
dnf remove nginx
```

Non-interactive:

```bash
dnf remove -y nginx
```

> Before removing an important production package, check its dependencies and impact.

---

## 6. Update a Specific Package

```bash
dnf update <package-name>
```

Example:

```bash
dnf update nginx
```

---

## 7. Update All Packages

```bash
dnf update
```

> In production, review available updates and their impact before performing a full system update.

---

## 8. List Available Packages

```bash
dnf list available
```

Specific package:

```bash
dnf list available nginx
```

---

## 9. Check Configured Repositories

```bash
dnf repolist
```

For all repositories:

```bash
dnf repolist all
```

---

# DNF Practical Example — Install NGINX

Suppose you are working on an Amazon Linux EC2 server and need to install NGINX.

### Step 1 — Search

```bash
dnf search nginx
```

### Step 2 — Check Information

```bash
dnf info nginx
```

### Step 3 — Install

```bash
dnf install -y nginx
```

### Step 4 — Verify Package

```bash
dnf list installed | grep nginx
```

### Step 5 — Check Service

```bash
systemctl status nginx
```

### Step 6 — Start and Enable

```bash
systemctl enable --now nginx
```

### Complete Flow

```text
Search
  ↓
dnf search nginx
  ↓
Check information
  ↓
dnf info nginx
  ↓
Install
  ↓
dnf install -y nginx
  ↓
Verify package
  ↓
dnf list installed | grep nginx
  ↓
Start + Enable
  ↓
systemctl enable --now nginx
  ↓
Verify service
  ↓
systemctl status nginx
```

---

# B. APT Package Manager

`apt` is commonly used on:

* Ubuntu
* Debian

You may also see `apt-get`, especially in scripts and older documentation.

---

## 1. Update Package Index

```bash
apt update
```

This refreshes the local package index from configured repositories.

### Important

```text
apt update
    ↓
Refresh package information
```

It does **not** upgrade installed packages.

---

## 2. Install a Package

```bash
apt install <package-name>
```

Example:

```bash
apt install nginx
```

Non-interactive:

```bash
apt install -y nginx
```

Using `apt-get`:

```bash
apt-get install nginx
```

---

## 3. Remove a Package

```bash
apt remove <package-name>
```

Example:

```bash
apt remove nginx
```

Using `apt-get`:

```bash
apt-get remove nginx
```

---

## `remove` vs `purge`

### Remove

```bash
apt remove nginx
```

Removes the package but may leave configuration files.

### Purge

```bash
apt purge nginx
```

Removes the package and its configuration files.

---

## 4. Search for a Package

```bash
apt search <package-name>
```

Example:

```bash
apt search nginx
```

Another common command:

```bash
apt-cache search nginx
```

---

## 5. Check Package Information

```bash
apt show <package-name>
```

Example:

```bash
apt show nginx
```

Another command:

```bash
apt-cache show nginx
```

---

## 6. List Installed Packages

```bash
apt list --installed
```

Specific package:

```bash
apt list --installed | grep nginx
```

Another common command:

```bash
dpkg -l nginx
```

---

## 7. Upgrade Packages

```bash
apt upgrade
```

Remember:

```text
apt update
    ↓
Refresh package information

apt upgrade
    ↓
Upgrade installed packages
```

---

# DNF vs APT

| Task               | DNF                  | APT                      |
| ------------------ | -------------------- | ------------------------ |
| Search             | `dnf search nginx`   | `apt search nginx`       |
| Information        | `dnf info nginx`     | `apt show nginx`         |
| Install            | `dnf install nginx`  | `apt install nginx`      |
| Remove             | `dnf remove nginx`   | `apt remove nginx`       |
| Upgrade packages   | `dnf update`         | `apt upgrade`            |
| Installed packages | `dnf list installed` | `apt list --installed`   |
| Repositories       | `dnf repolist`       | `/etc/apt/sources.list*` |

---

## Easy Memory

```text
DNF → Amazon Linux / RHEL / Fedora

APT → Ubuntu / Debian
```

Installation:

```bash
dnf install nginx
apt install nginx
```

---

# 5. Service Management

## What is a Service?

A **service** is a background program that performs a specific function.

Examples:

```text
sshd   → SSH service
nginx  → Web server
docker → Container runtime
jenkins → CI/CD server
```

---

# `systemctl`

`systemctl` is used to manage services on systems using `systemd`.

---

## Start a Service

```bash
systemctl start <service-name>
```

Example:

```bash
systemctl start nginx
```

This starts the service immediately.

---

## Stop a Service

```bash
systemctl stop nginx
```

---

## Check Service Status

```bash
systemctl status nginx
```

---

## Restart a Service

```bash
systemctl restart nginx
```

---

## Enable Service at Boot

```bash
systemctl enable nginx
```

This configures the service to start automatically when the system boots.

---

## Disable Service at Boot

```bash
systemctl disable nginx
```

---

## Start + Enable

```bash
systemctl enable --now nginx
```

This:

```text
Starts the service now
       +
Enables it at boot
```

---

## Important Difference

```bash
systemctl start nginx
```

→ Start now.

```bash
systemctl enable nginx
```

→ Start automatically after reboot.

```bash
systemctl enable --now nginx
```

→ Start now + enable at boot.

---

## Useful Commands

```bash
systemctl status nginx
systemctl start nginx
systemctl stop nginx
systemctl restart nginx
systemctl enable nginx
systemctl disable nginx
```

---

# 6. Process Management

## What is a Process?

A **process is a running instance of a program**.

Example:

```text
Program
  ↓
Running Program
  ↓
Process
  ↓
PID
```

Every running process has a unique **PID**.

---

# PID — Process ID

PID stands for **Process ID**.

It uniquely identifies a running process.

Example:

```text
PID
1012 → nginx
1250 → sshd
1432 → java
```

---

# PPID — Parent Process ID

PPID stands for **Parent Process ID**.

A process can create another process.

```text
Parent Process
      ↓
Child Process
```

Example:

```text
PID     PPID    Process
2000    1000    java
2001    2000    worker
```

Here:

```text
2000 → PID of Java process
1000 → Parent PID

2001 → PID of worker process
2000 → Parent PID
```

---

# Process Hierarchy

Linux processes form a parent-child hierarchy.

```text
systemd
   │
   ├── sshd
   │    └── bash
   │         └── commands
   │
   └── nginx
        └── nginx worker
```

---

# `ps` Command

`ps` stands for **Process Status**.

It is used to view running processes.

---

## Current User's Processes

```bash
ps
```

---

## Detailed Process Information

```bash
ps aux
```

Shows information such as:

* User
* PID
* CPU
* Memory
* Process
* Start time

---

## Process Information with Parent

```bash
ps -ef
```

Useful columns:

```text
UID
PID
PPID
CMD
```

---

## Search for a Process

```bash
ps -ef | grep <process-name>
```

Example:

```bash
ps -ef | grep nginx
```

---

## Processes for a Specific User

```bash
ps -u <username>
```

Example:

```bash
ps -u ramesh
```

---

# Foreground Process

A foreground process runs directly in the terminal.

Example:

```bash
ping google.com
```

The terminal remains occupied by the command.

Stop it using:

```text
Ctrl + C
```

---

# Background Process

A background process runs without occupying the terminal.

Example:

```bash
ping google.com &
```

The `&` sends the command to the background.

---

# Killing a Process

## Normal Termination

```bash
kill <PID>
```

Example:

```bash
kill 1234
```

By default, `kill` sends:

```text
SIGTERM = 15
```

SIGTERM requests the process to terminate gracefully.

This gives the application an opportunity to:

* Finish current work
* Close files
* Release resources
* Perform cleanup
* Exit normally

---

## Force Kill

```bash
kill -9 <PID>
```

Example:

```bash
kill -9 1234
```

This sends:

```text
SIGKILL = 9
```

The process is forcefully terminated.

### Important

Prefer:

```bash
kill <PID>
```

before:

```bash
kill -9 <PID>
```

because `SIGKILL` does not allow the application to perform normal cleanup.

---

# `pkill`

Terminate a process using its name:

```bash
pkill <processname>
```

Example:

```bash
pkill nginx
```

Forcefully:

```bash
pkill -9 nginx
```

For all processes owned by a user:

```bash
pkill -u ramesh
```

---

# Process Management Quick Revision

```text
Process → Running instance of a program

PID  → Process ID
PPID → Parent Process ID

ps      → Process information
ps aux  → Detailed process information
ps -ef  → PID + PPID + command
top     → Real-time process monitoring

kill PID     → SIGTERM / graceful termination
kill -9 PID  → SIGKILL / forceful termination

pkill name   → Kill by process name
```

---

# 7. Network Management

Network management is used to check:

* Network connections
* Listening ports
* Running network services
* Processes associated with ports

---

# Check Listening Ports

## `netstat`

```bash
netstat -lntp
```

### Options

| Option | Meaning                   |
| ------ | ------------------------- |
| `l`    | Listening                 |
| `n`    | Numerical addresses/ports |
| `t`    | TCP                       |
| `p`    | Process/PID               |

Example:

```bash
netstat -lntp
```

Possible output:

```text
Proto  Local Address     PID/Program name
tcp    0.0.0.0:22       sshd
tcp    0.0.0.0:80       nginx
```

This tells us:

```text
Port 22 → SSH
Port 80 → HTTP / NGINX
```

---

# Modern Alternative — `ss`

On modern Linux systems, `ss` is commonly preferred over `netstat`.

```bash
ss -lntp
```

Useful options:

```text
l → Listening
n → Numerical
t → TCP
p → Process/PID
```

---

# Useful Network Commands

## Check listening TCP ports

```bash
ss -lntp
```

## Check all TCP/UDP connections

```bash
ss -an
```

## Test HTTP service

```bash
curl http://localhost
```

## Test connectivity

```bash
ping <IP-address>
```

## DNS lookup

```bash
nslookup example.com
```

or:

```bash
dig example.com
```

---

# Practical Example

Suppose NGINX is running but the application is not accessible.

### Step 1 — Check service

```bash
systemctl status nginx
```

### Step 2 — Check port

```bash
ss -lntp
```

Look for:

```text
:80
```

### Step 3 — Test locally

```bash
curl http://localhost
```

### Step 4 — Check process

```bash
ps -ef | grep nginx
```

This helps determine whether NGINX is running and listening on the expected port.

---

# Network Management Quick Revision

```bash
ss -lntp
netstat -lntp
curl http://localhost
ping <IP>
nslookup example.com
dig example.com
```

---

# 8. 3-Tier Architecture

## What is 3-Tier Architecture?

3-Tier Architecture divides an application into three separate tiers:

```text
User
  ↓
Web / Presentation Tier
  ↓
Application / Backend Tier
  ↓
Database Tier
```

Each tier has a specific responsibility.

---

# 1. Web Tier / Frontend Tier

The Web Tier is the **user-facing layer**.

## Restaurant Example — Captain

The captain interacts directly with the customer.

```text
Captain
   ↓
Welcome customer
   ↓
Check table availability
   ↓
Assign table
```

## Application Example

```text
User
  ↓
Load Balancer
  ↓
Frontend
```

Common technologies:

```text
HTML
CSS
JavaScript
React
Angular
```

### Responsibility

The Web Tier handles:

* User interface
* User interaction
* Receiving user requests
* Sending requests to the backend
* Displaying responses

---

# 2. Application Tier / Backend Tier

The Application Tier contains the **business logic**.

## Restaurant Example — Waiter

```text
Waiter
   ↓
Take order
   ↓
Send order to kitchen
   ↓
Receive food
   ↓
Serve customer
```

## Application Example

```text
Frontend
   ↓
Backend
```

Common technologies:

```text
Java
Spring Boot
Python
.NET
Node.js
Go
```

### Responsibility

The Application Tier handles:

* Business logic
* Request processing
* Validation
* Authentication
* Application operations
* Communication with the database

---

# 3. Database Tier

The Database Tier stores application data.

## Restaurant Example — Records

A restaurant may maintain:

```text
Customer Details
Orders
Payments
Inventory
```

## Application Example

```text
Backend
   ↓
Database
```

Common databases:

```text
MySQL
Oracle
PostgreSQL
MS SQL Server
```

Example data:

```json
{
  "user": "satya",
  "email": "satya@example.com"
}
```

---

# Complete 3-Tier Architecture

```text
                    USER
                      ↓
               LOAD BALANCER
                      ↓
              ┌───────────────┐
              │   WEB TIER    │
              │   FRONTEND    │
              │ HTML/CSS/JS   │
              └───────┬───────┘
                      ↓
              ┌───────────────┐
              │ APPLICATION   │
              │     TIER      │
              │    BACKEND    │
              │ Java/Spring   │
              └───────┬───────┘
                      ↓
              ┌───────────────┐
              │ DATABASE TIER │
              │ MySQL/Oracle/ │
              │ PostgreSQL    │
              └───────────────┘
```

---

# Real-Time Example — Online Shopping Application

Consider an online shopping application.

```text
User
 ↓
Frontend
 ↓
Backend
 ↓
Database
```

## User

The user searches for a mobile phone.

```text
User
 ↓
Search for mobile phone
```

## Frontend

The frontend displays:

```text
Product
Price
Image
Add to Cart
```

## Backend

The backend processes:

```text
Login
Product Availability
Cart
Order
Payment
```

## Database

The database stores:

```text
Users
Products
Orders
Payments
```

---

# Request Flow

When the user performs an operation:

```text
User
 ↓
Frontend
 ↓
Backend
 ↓
Database
 ↓
Backend
 ↓
Frontend
 ↓
User
```

---

# Restaurant Analogy

```text
Captain  → Web / Frontend Tier
Waiter   → Application / Backend Tier
Records  → Database Tier
```

The restaurant analogy is only used to understand the **separation of responsibilities**.

---

# Easy Way to Remember

```text
WEB → What the user sees
APP → What the application does
DB  → What the application stores
```

Or:

```text
WEB
 ↓
APP
 ↓
DB
```

---

# Quick Revision

| Tier             | Purpose        | Examples                                     |
| ---------------- | -------------- | -------------------------------------------- |
| Web Tier         | User Interface | HTML, CSS, JavaScript, React, Angular        |
| Application Tier | Business Logic | Java, Spring Boot, Python, .NET, Node.js, Go |
| Database Tier    | Data Storage   | MySQL, Oracle, PostgreSQL, MS SQL Server     |

---

# Interview Answer

> **3-Tier Architecture divides an application into three separate tiers: Web Tier, Application Tier, and Database Tier. The Web Tier handles the user interface, the Application Tier handles business logic and request processing, and the Database Tier stores application data.**

## Real-World Example

> **For example, in an online shopping application, the frontend displays products and accepts user actions, the backend processes login, product availability, cart, orders and payments, and the database stores users, products, orders and payment-related data.**

---
