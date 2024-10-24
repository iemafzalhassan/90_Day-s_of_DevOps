# Challenge Day 11:

---

### Current Status
- **Day Completed**: 11
- **Total Days in Challenge**: 90

---

## Day 10 Challenge: Error Handling in Shell Scripting

## Learning Objectives
Today, I focused on understanding how to handle errors in shell scripts to create robust and reliable code. The key objectives were:


### Understanding Exit Status

1. **What is Exit Status?**
   - When you run a command in a shell script (like a little program), it finishes its job and gives you a number back. This number is called the **exit status**.
   - If the exit status is **0**, it means everything went well (the command was successful).
   - If the exit status is **not 0** (like 1, 2, etc.), it means something went wrong (the command failed).
  
2. **How to Check Exit Status?**
   - After you run a command, you can check its exit status using `$?`. This is like asking, "Did my last command succeed?"

   **Example:**
   ```bash
   mkdir myfolder
   if [ $? -ne 0 ]; then
       echo "Oops! Couldn't create the folder."
   fi
   ```

### Using if Statements for Error Checking

- You can use **if statements** to check the exit status and handle errors.
- Think of it like this: if the command failed, you can say, "Hey, let’s do something different" instead of just letting it fail without saying anything.

**Example:**
```bash
mkdir myfolder
if [ $? -ne 0 ]; then
    echo "Couldn't create the folder! Check if it already exists."
else
    echo "Folder created successfully!"
fi
```

### Using trap for Cleanup

- Sometimes, you might create temporary files or resources that need to be cleaned up later (like a messy room after a party!).
- The **trap** command helps you tell the script, "If I’m about to exit, please do this cleanup for me."

**Example:**
```bash
trap "rm -f tempfile.txt" EXIT
```
This means that when the script exits (for any reason), it will delete `tempfile.txt`.

### Redirecting Errors

- When a command doesn’t work, it usually shows an error message on the screen. You can **redirect** these error messages to a file instead.
- This is like writing down the mistakes instead of shouting them out loud!

**Example:**
```bash
cat nonexistentfile.txt 2> error.log
```
This command tries to read a file that doesn't exist and writes the error message into `error.log` instead of showing it on the screen.

### Creating Custom Error Messages

- Sometimes, the default error messages aren't very helpful. You can create your own messages to make it clearer what went wrong.
- This helps users (or yourself) understand the problem better.

**Example:**
```bash
mkdir myfolder
if [ $? -ne 0 ]; then
    echo "Error: Couldn't create 'myfolder'. Make sure you have the right permissions!"
fi
```


## Tasks and Scripts

### Task 1: Checking Exit Status

**Script:**

```bash
#!/bin/bash

mkdir /tmp/mydir
if [ $? -ne 0 ]; then
  echo "Failed to create directory /tmp/mydir"
fi
```

**Explanation**: This script attempts to create a directory called `mydir` in the `/tmp` folder. If the command fails, it prints an error message.

---

### Task 2: Using if Statements for Error Checking

**Script:**

```bash
#!/bin/bash

mkdir /tmp/mydir
if [ $? -ne 0 ]; then
  echo "Failed to create directory /tmp/mydir"
  exit 1
fi

touch /tmp/mydir/myfile.txt
if [ $? -ne 0 ]; then
  echo "Failed to create file /tmp/mydir/myfile.txt"
  exit 1
fi

echo "Directory and file created successfully."
```

**Explanation**: This script checks for errors while creating a directory and a file. It exits if any command fails.

---

### Task 3: Using trap for Cleanup

**Script:**

```bash
#!/bin/bash

tempfile=$(mktemp)
trap "rm -f $tempfile" EXIT

echo "This is a temporary file." > $tempfile
cat $tempfile

# Simulate an error
exit 1
```

**Explanation**: This script creates a temporary file and sets a trap to delete it upon script exit, whether normal or due to an error.

---

### Task 4: Redirecting Errors

**Script:**

```bash
#!/bin/bash

cat non_existent_file.txt 2> error.log
echo "Error message has been redirected to error.log"
```

**Explanation**: This script tries to read a non-existent file, redirecting the error message to `error.log`.

---

### Task 5: Creating Custom Error Messages

**Script:**

```bash
#!/bin/bash

mkdir /tmp/mydir
if [ $? -ne 0 ]; then
  echo "Error: Directory /tmp/mydir could not be created. Check if you have the necessary permissions."
  exit 1
fi

touch /tmp/mydir/myfile.txt
if [ $? -ne 0 ]; then
  echo "Error: Could not create file in /tmp/mydir. Ensure the directory exists."
  exit 1
fi

echo "Directory and file created successfully."
```

**Explanation**: This script includes custom error messages that give more context about what went wrong.