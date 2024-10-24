# 📅 Day 05: Advanced Linux Shell Scripting for DevOps Engineers with User Management

## 🚀 **Tasks Completed:**

### 1. **Create Multiple Directories Using Shell Script:**

In this task, I created a shell script that takes multiple directory names as input from the user and creates them all at once. This is useful for quickly setting up multiple project directories.

#### Example Script:
```bash
#!/bin/bash

# Prompt the user for the base directory name

echo "Enter the base name for the directories:"
read base_name

# Prompt the user for the number of directories to create

echo "How many directories do you want to create?"
read number_of_dirs

# Create the specified number of directories

for i in $(seq -f "%02g" 1 $number_of_dirs); do
    
    # Create directory name in the format "base_name01", "base_name02", etc.
    
    dir_name="${base_name}${i}"  
    mkdir -p "$dir_name"
    echo "Directory '$dir_name' created successfully!"
done

```
- This script takes multiple directory names from the user, creates each directory, and confirms their creation.

---

### 2. **Create a Script to Backup All Your Work:**

This task involved creating a shell script to back up a source directory into a destination folder provided as arguments. It automates the backup process for important work files.

#### Example Backup Script:
```bash
#!/bin/bash

# Backup Script
src=$1
dest=$2

if [ -d "$src" ]; then
    echo "Starting backup of $src to $dest..."
    cp -r "$src" "$dest"
    echo "Backup completed."
else
    echo "Source directory does not exist."
fi
```
- This script takes the source and destination directories as arguments, making it a reusable tool for performing backups.

---

### 3. **Read About User Management:**

For this task, I explored essential user management commands in Linux. Additionally, I created a shell script to automate adding a user, setting their full name, and setting their password with masked input (showing `*` for each character typed).

#### User Management Script:
```bash
#!/bin/bash

echo "Enter the username:"
read username

echo "Enter the full name of the user:"
read fullname

echo "Creating the user $username..."
useradd -m -s /bin/bash -c "$fullname" "$username"

echo "Enter password for $username:"
while IFS= read -p "Password: " -r -s -n 1 char; do
    if [[ $char == $'\0' ]]; then
        break
    fi
    password+="$char"
    printf "*"
done
echo

echo "$username:$password" | chpasswd

echo "User $username created with full name '$fullname' and a password has been set."
```
- This script asks for the username, full name, and password, ensuring the password input is hidden by showing `*` for each entered character.

### Breakdown of the Command

1. **`IFS=`**:
   - **What it is**: IFS stands for "Internal Field Separator."
   - **Why we use it**: By setting `IFS=` to an empty value, we're telling the shell not to treat spaces, tabs, or newlines as special characters. This is particularly important here because it lets us handle spaces within the password input without any issues. Essentially, it ensures that the whole input is treated as one continuous string.

2. **`read`**:
   - **What it does**: The `read` command is used to capture input from the user in a shell script.
   - **How it’s used**: In this case, it’s set up to read the input character by character, which is perfect for password entry.

3. **`-p "*"`**:
   - **What it means**: The `-p` option allows us to display a prompt before the user types anything.
   - **How it works**: Here, we use `*` as the prompt. So, for every character the user types, the script will display a `*` instead of showing the actual character. This helps to mask the input, which is essential for keeping passwords secure.

4. **`-r`**:
   - **What it does**: The `-r` option tells the `read` command to avoid interpreting backslashes (`\`) as escape characters.
   - **Why it matters**: This ensures that if a user types a backslash, it’s treated just like any other character, not a special command or symbol.

5. **`-s`**:
   - **What it means**: The `-s` option puts `read` into "silent mode."
   - **Why it's important**: In this mode, anything the user types won't be displayed on the screen. This is crucial for password inputs, so the actual password remains hidden while the user is typing.

6. **`-n 1`**:
   - **What it does**: The `-n 1` option tells `read` to capture only one character at a time.
   - **Why we use it**: This is key for our password input, allowing us to read each character individually and display a `*` after every keypress, mimicking the behavior of password fields in login forms.

7. **`char`**:
   - **What it is**: `char` is the variable where we store the single character that the user just typed.
   - **How it works**: During each iteration of the loop, we read one character, store it in `char`, and then append it to our password string. This way, we can build the complete password while keeping everything private.


#### Common User Management Commands:
1. **Add a User:**
   ```bash
   sudo useradd -m -s /bin/bash username
   ```
   - `-m`: Creates a home directory for the user.
   - `-s /bin/bash`: Specifies the default shell for the user.

2. **Set or Change a User's Password:**
   ```bash
   sudo passwd username
   ```

3. **Modify a User Account:**
   ```bash
   sudo usermod -l new_username old_username
   ```

4. **Delete a User:**
   ```bash
   sudo userdel -r username
   ```

---

### 4. **Read About Cron and Crontab to Automate the Backup Script:**

I explored `cron` and `crontab`, which are used for scheduling repetitive tasks like daily backups. I scheduled my backup script to run automatically every day at midnight using `crontab`.

#### Example Cron Job:
```bash
crontab -e
```
- To run the backup script every day at midnight, I added this line in the crontab file:
```bash
0 0 * * * /path/to/backup_script.sh /source/dir /destination/dir
```
This ensures regular backups of my work without manual intervention.

---

## 🔍 **What I Learned:**
- **Shell scripting** is an efficient way to automate tasks like creating multiple directories and backing up work files.
- **User management** in Linux is a critical skill for managing users and system security.
- **Cron jobs** are an excellent way to automate tasks on a schedule, such as daily backups.
