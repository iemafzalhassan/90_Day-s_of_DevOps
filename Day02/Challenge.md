# Challenge Day 02: 

---

### Current Status
- **Day Completed**: 2
- **Total Days in Challenge**: 90

Join #TrainWithShubham Community on an exhilarating journey of learning and growth as we embark on the #90DaysofChallenge!

---

## Day 02: Understanding the Linux File System Hierarchy


### **Objective**
Today, we will explore the Linux file system, understanding its directory structure and purpose. This is foundational knowledge for any DevOps professional, as you need to know where files are stored and how to navigate the file system.

### **File System Hierarchy Standard (FHS)**
The **FHS** defines the directory structure and directory contents in Linux. Here’s a breakdown of key directories:

- **`/` (Root Directory)**:  
  - The base of the file system. All files and directories start here.
  - Only the system administrator (root user) has access to make changes here.

- **`/home`**:  
  - Contains user directories. Each user has a separate folder (e.g., `/home/user1`, `/home/user2`).
  - Stores user-specific files and settings.

- **`/etc`**:  
  - Configuration files for the system.
  - Examples include network settings, service configurations (like Apache), and startup scripts.

- **`/var`**:  
  - Stores variable data like logs, caches, and temporary files.
  - **Important subdirectories**:
    - `/var/log`: Log files.
    - `/var/spool`: Email queues, print queues, etc.

- **`/bin` and `/sbin`**:  
  - **`/bin`**: Essential command binaries like `ls`, `cp`, `mv`, and `cat`.
  - **`/sbin`**: System binaries used for administrative tasks like `ifconfig`, `reboot`, `shutdown`.

- **`/dev`**:  
  - Contains device files, which represent hardware components.
  - Example: `/dev/sda` for your hard disk, `/dev/tty` for your terminal.

- **`/tmp`**:  
  - Stores temporary files.
  - These files are automatically deleted after a reboot.

- **`/opt`**:  
  - Optional software that you might install manually. For example, custom applications or third-party packages go here.

- **`/usr`**:  
  - User binaries and libraries, documentation, and source code.
  - Subdirectories include `/usr/bin` for user commands and `/usr/lib` for libraries.

### **Commands to Explore the File System**
- `pwd` (Print Working Directory): Displays your current directory.
- `ls` (List Directory Contents): Shows files and directories. Use options like:
  - `-l` for a detailed list with permissions and sizes.
  - `-a` to include hidden files (files starting with a dot).
  - `-h` for human-readable file sizes.

- `cd` (Change Directory): Navigates through directories. Use `cd ..` to move up one directory level.

- **Examples:**
  - Print your current directory:
    ```bash
    pwd
    ```
  - List the contents of `/etc` in long format:
    ```bash
    ls -l /etc
    ```
  - Navigate to `/home`:
    ```bash
    cd /home
    ```

