# Challenge Day 03: 

---

### Current Status
- **Day Completed**: 3
- **Total Days in Challenge**: 90

Join #TrainWithShubham Community on an exhilarating journey of learning and growth as we embark on the #90DaysofChallenge!

---

## Day 03: Managing Files and Directories

## Objective
Today’s challenge is all about mastering file and directory management in Linux. Practiced create, move, copy, and delete files and directories using various commands, with real-world DevOps use cases that demonstrate how these operations are applied in automation, system management, and deployments.

---

## **1. Creating Files and Directories**

### **Command: `touch` (Creating Files)**

The `touch` command is used to create an empty file or update the timestamp of an existing file.

#### **Syntax:**
`
touch [OPTIONS] FILE_NAME
`
#### **Common Flags:**
- `-a`: Change only the access time of the file.
- `-m`: Change only the modification time of the file.
- `-t`: Set the access and modification time explicitly.

#### **Example:**
`
touch myfile.txt
`
This creates an empty file called `myfile.txt`. If `myfile.txt` already exists, it updates its timestamp.

#### **DevOps Use Case:**
- **Log Files**: When running automated scripts, sometimes you may want to create empty log files to track errors. For example, a CI/CD pipeline might create a log file before executing a deployment script:
`
touch /var/log/deployment.log
`

---

### **Command: `mkdir` (Creating Directories)**

The `mkdir` command creates directories.

#### **Syntax:**
`
mkdir [OPTIONS] DIRECTORY_NAME
`
#### **Common Flags:**
- `-p`: Creates parent directories if they don't exist. This is useful when you need to create multiple directories at different levels.
- `-v`: Verbose mode, prints the action taken.

#### **Example:**
`
mkdir my_directory
`
This creates a directory called `my_directory`.
`
mkdir -p /home/user/logs/nginx
`
This command creates `/home/user/logs/nginx` and ensures that the entire directory path exists. If `logs` doesn't exist, it will create it too.

#### **DevOps Use Case:**
- **Directory Structure Setup**: When setting up a new environment, you may need to create directories for different logs or configurations.
`
mkdir -p /var/www/html/logs
`  
This creates a directory structure where web server logs can be stored, ensuring the right environment is in place before deploying web applications.

---

## **2. Copying Files and Directories**

### **Command: `cp` (Copying Files/Directories)**

The `cp` command copies files or directories from one location to another.

#### **Syntax:**
`
cp [OPTIONS] SOURCE DESTINATION
`

#### **Common Flags:**
- `-r` or `--recursive`: Copy directories recursively. Without this option, `cp` will not copy directories.
- `-v` or `--verbose`: Display the files being copied.
- `-i` or `--interactive`: Prompt before overwriting files.
- `-u` or `--update`: Copy only when the source file is newer than the destination file or when the destination file is missing.

#### **Example:**
`
cp file.txt /home/user/backup/
`
This copies `file.txt` to the `/home/user/backup/` directory.
`
cp -r /var/www/html/ /backup/web/
`
This command recursively copies the entire `/var/www/html/` directory to `/backup/web/`.

#### **DevOps Use Case:**
- **Backups**: Regular backups are essential in DevOps. For example, before running major updates, you might create backups of configuration files:
`
cp -r /etc/nginx /backup/nginx-config
`  
This command ensures that all Nginx configuration files are copied before any changes are made.

---

## **3. Moving and Renaming Files and Directories**

### **Command: `mv` (Move/Rename Files/Directories)**

The `mv` command moves files or directories from one location to another, or renames them.

#### **Syntax:**
`
mv [OPTIONS] SOURCE DESTINATION
`
#### **Common Flags:**
- `-i` or `--interactive`: Prompt before overwriting.
- `-u` or `--update`: Move only when the source is newer than the destination.
- `-v` or `--verbose`: Display what is being moved.

#### **Example:**
`
mv old_name.txt new_name.txt
`
This renames the file `old_name.txt` to `new_name.txt`.
`
mv /home/user/backup/* /var/www/html/
`
This moves all files from the backup folder to the web server directory.

#### **DevOps Use Case:**
- **Renaming Log Files**: As part of log rotation, you may rename old log files before archiving them.
`
mv /var/log/nginx/access.log /var/log/nginx/access.log.old
` 
This command renames the current Nginx access log so that a new log can be generated.

---

## **4. Deleting Files and Directories**

### **Command: `rm` (Remove Files/Directories)**

The `rm` command removes files or directories.

#### **Syntax:**
`
rm [OPTIONS] FILE_NAME/DIRECTORY_NAME
`
#### **Common Flags:**
- `-r` or `--recursive`: Removes directories and their contents recursively.
- `-f` or `--force`: Force removal without prompting for confirmation.
- `-i` or `--interactive`: Prompt before each file is deleted.
- `-v` or `--verbose`: Display what is being removed.

#### **Example:**
`
rm file.txt
`
This deletes the file `file.txt`.

`
rm -rf /tmp/cache/
`

This command forcefully and recursively removes the `/tmp/cache/` directory and all its contents.

#### **DevOps Use Case:**
- **Cleaning Up Build Artifacts**: In CI/CD pipelines, you may remove old build artifacts to free up space:
`
rm -rf /var/lib/jenkins/workspace/my_project/build/
`  

This ensures the workspace is clean before the next build is triggered.

---

## **5. Viewing Directory Contents**

### **Command: `ls` (List Directory Contents)**

The `ls` command lists files and directories in a given directory.

#### **Syntax:**
`
ls [OPTIONS] [DIRECTORY]
`
#### **Common Flags:**
- `-l`: Long listing format, showing file permissions, owner, size, and modification date.
- `-a`: List all files, including hidden files (files starting with a dot `.`).
- `-h`: Human-readable format, showing file sizes in KB, MB, or GB.
- `-t`: Sort by modification time, showing the most recently modified files first.
- `-R`: Recursively list subdirectories.
- `-S`: Sort files by size.

#### **Example:**
`
ls -l /home/user/
`
This lists all files in `/home/user/` in long format, showing details about each file.
`
ls -alh /var/log/
`
This lists all files, including hidden ones, in the `/var/log/` directory, in human-readable format.

#### **DevOps Use Case:**
- **Viewing Log Files**: When managing servers, you often need to check logs in directories like `/var/log/`. Using `ls` with appropriate flags helps to quickly locate the most recent or largest log files:
`
ls -lt /var/log/nginx/
`  
This command shows the Nginx log files, sorted by modification time, with the most recent logs at the top.

---

## **6. Checking File Sizes and Disk Usage**

### **Command: `du` (Disk Usage)**

The `du` command estimates file and directory space usage.

#### **Syntax:**
`
du [OPTIONS] [FILE/DIRECTORY]
`
#### **Common Flags:**
- `-h`: Human-readable format (shows sizes in KB, MB, GB).
- `-s`: Summarize the total size of a directory.
- `-a`: Show disk usage for all files, not just directories.

#### **Example:**
`
du -sh /home/user/
`
This displays the total size of the `/home/user/` directory in a human-readable format.

#### **DevOps Use Case:**
- **Monitoring Disk Usage**: Monitoring disk space is critical to ensuring that your systems don’t run out of space. For instance, before deploying a large update, you might check how much space is available in the target directory:
`
du -sh /var/www/html/
`  
---

### **7. Disk Usage Overview**

### **Command: `df` (Disk Free)**

The `df` command reports the amount of available disk space on file systems.

#### **Syntax:**
`
df [OPTIONS] [FILESYSTEM]
`
#### **Common Flags:**
- `-h`: Human-readable format (displays sizes in KB, MB, GB).
- `-T`: Show file system type.
- `-i`: Show inode usage instead of

 block usage.

#### **Example:**
`
df -h
`
This shows the disk space usage of all mounted file systems in a human-readable format.

#### **DevOps Use Case:**
- **Checking Disk Space**: Before running major installations or deployments, you need to ensure there’s enough disk space available:
`
df -h /var
`  
This checks how much disk space is available in the `/var` directory, often used for logs and temporary files.

---

## **Summary**
Day 03 has focused on building proficiency in managing files and directories in Linux, along with real-world DevOps scenarios that illustrate how these commands are used in practice. The skills you’ve learned today will help you manage file systems, automate tasks, and maintain server environments efficiently.

### **Next Steps: Day 04 Preview**
Tomorrow, we’ll dive into process management and system monitoring, covering commands like `ps`, `top`, `kill`, and more!

