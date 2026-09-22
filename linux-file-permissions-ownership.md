
### File Permissions and Ownership in Linux

---

## umask (User Mask)

| User Type  | umask | Default File | Default Dir |
| ---------- | ----- | ------------ | ----------- |
| **root**   | 0022  | 644          | 755         |
| **normal** | 0022  | 644          | 755         |

📌 **Note:** In **RHEL 9.x**, the umask value is the same.

---

### Base Permissions Calculation

**Base permissions for file:**

```
0666
(-)0022
---------
0644
```

**Base permissions for directory:**

```
0777
(-)0022
---------
0755
```

---

###  Permission Values

| Symbol | Meaning | Value |
| ------ | ------- | ----- |
| **r**  | read    | 4     |
| **w**  | write   | 2     |
| **x**  | execute | 1     |

🧠 *Create one dir and file —> explain the permissions.*

---

###  How to Change umask Value?

Only **root user** can change umask value.

```bash
umask          # Display umask value
umask 222      # Set new umask value
```

> **NOTE:** Permissions are **not changed** for previously created files and directories.

---

##  Understanding File Permissions

In Linux, each file and directory has **three types of permissions**:

| Permission      | Meaning                                                        |
| --------------- | -------------------------------------------------------------- |
| **Read (r)**    | Permission to read the file or list directory contents.        |
| **Write (w)**   | Permission to modify files or add/remove files in a directory. |
| **Execute (x)** | Permission to execute a file or access a directory.            |

---

###  Types of Users

| User Type      | Description                         |
| -------------- | ----------------------------------- |
| **User (u)**   | The owner of the file.              |
| **Group (g)**  | The group associated with the file. |
| **Others (o)** | All other users.                    |

---

##  Permission Representation

###  Symbolic Notation

| Symbol | Meaning       |
| ------ | ------------- |
| **r**  | Read          |
| **w**  | Write         |
| **x**  | Execute       |
| **-**  | No permission |

**Example:**
`-rwxr-xr--` means:

* User → read, write, execute
* Group → read, execute
* Others → read

---

###  Numeric (Octal) Notation

Each permission is represented by a number:

| Permission | Binary | Value |
| ---------- | ------ | ----- |
| **r**      | 100    | 4     |
| **w**      | 010    | 2     |
| **x**      | 001    | 1     |

**Example Calculations:**

```
rwx = 4 + 2 + 1 = 7
r-x = 4 + 0 + 1 = 5
r-- = 4 + 0 + 0 = 4
```

---

##  CHANGE PERMISSIONS OF FILES AND FOLDERS

> The **chmod** command changes permissions of files and directories.
> It stands for **"change mode"** and allows defining who can read, write, or execute a file.

---

###  Common chmod Commands

| Command                                          | Description                                              |
| ------------------------------------------------ | -------------------------------------------------------- |
| `umask`                                          | Display umask value                                      |
| `chmod 777 filename` OR `chmod ugo+rwx filename` | Change full permissions of a file                        |
| `chmod 777 filename1 filename2`                  | Change full permissions of multiple files                |
| `chmod 777 *`                                    | Change full permissions of all files                     |
| `chmod 777 foldername`                           | Change full permissions of a folder                      |
| `chmod 777 foldername -R`                        | Change full permissions of a folder and all files inside |
| `chmod 777 foldername/*`                         | Change full permissions of files inside a folder         |
| `chmod u+x file.txt`                             | Add execute permission for the user                      |
| `chmod g+w file.txt`                             | Add write permission for the group                       |
| `chmod o-r file.txt`                             | Remove read permission for others                        |
| `chmod u-w file.txt`                             | Remove write permission for the user                     |
| `chmod -v 644 file.txt`                          | Show what changes were made                              |
| `chmod ugo+x DevOps/`                            | Change only parent directory permissions                 |

---

##  CHANGE OWNERS OF FILES AND FOLDERS

*(Only root user can use these commands)*

> The **chown** command changes file or directory ownership.
> The name stands for **"change owner"**.
> It can assign a new owner and optionally a new group.

---

###  Common chown Commands

| Command                                        | Description                               |
| ---------------------------------------------- | ----------------------------------------- |
| `chown username:groupname filename`            | Change owner of a file                    |
| `chown username:groupname filename1 filename2` | Change owners of multiple files           |
| `chown username:groupname *`                   | Change owners of all files                |
| `chown username:groupname foldername`          | Change owner of a folder                  |
| `chown username:groupname foldername -R`       | Change owner recursively (folder + files) |
| `chown username:groupname foldername/*`        | Change owners of files inside a folder    |
| `chown ownername filename`                     | Change user owner only                    |
| `chgrp groupname filename`                     | Change group owner only                   |



