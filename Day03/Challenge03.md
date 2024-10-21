## **Day 03: Managing Files and Directories**

### **Objective**
Learn how to create, move, copy, and delete files and directories effectively.

### **Creating Files and Directories**
- **Files**: Create files using `touch`:
  ```bash
  touch filename.txt
This creates an empty file if it doesn’t exist. If the file exists, it updates the timestamp.

Directories: Create directories using mkdir:

bash
Copy code
mkdir new_directory
Use the -p flag to create parent directories if they don't exist:
bash
Copy code
mkdir -p /path/to/new_directory
Copying and Moving Files
Copying Files: Use cp to copy files:

bash
Copy code
cp source_file.txt destination_file.txt
To copy directories, use the -r flag to copy recursively:
bash
Copy code
cp -r /source_directory /destination_directory
Moving and Renaming Files: Use mv to move or rename files:

Moving:
bash
Copy code
mv file.txt /path/to/destination/
Renaming:
bash
Copy code
mv old_name.txt new_name.txt
Deleting Files and Directories
Deleting Files: Use rm to remove files:

bash
Copy code
rm file.txt
Deleting Directories: Use the -r flag to delete directories recursively:

bash
Copy code
rm -r directory_name
Add the -f flag to force deletion without confirmation.

