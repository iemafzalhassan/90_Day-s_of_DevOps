# Challenge Day 09:

---

### Current Status
- **Day Completed**: 9
- **Total Days in Challenge**: 90

Join #TrainWithShubham Community on an exhilarating journey of learning and growth as we embark on the #90DaysofChallenge!

---

## Day 9: Bash Scripting Challenge
### Backup Script: `backup_with_rotation.sh`

```bash
#!/bin/bash

# Check if a directory path is provided

if [ $# -ne 1 ]; then
  echo "Usage: $0 Path of source Directory which is needed to be backedup."
  exit 1
fi

# Source path from argument 1.
SRC_DIR="$1"

# Check if the provided path is a valid directory

if [ ! -d "$SRC_DIR" ]; then
  echo "Error: $SRC_DIR is not a valid directory."
  exit 1
fi

# Create a timestamp for the backup folder

TIMESTAMP=$(date +"%Y-%m-%d_%H-%M-%S")
BACKUP_DIR="$SRC_DIR/backup_$TIMESTAMP"

# Create the backup directory
mkdir "$BACKUP_DIR"

# Copy all files from the specified directory to the backup folder

cp -r "$SRC_DIR/"* "$BACKUP_DIR"

# Inform the user that the backup was created
echo "Backup created: $BACKUP_DIR"

# Implement backup rotation to keep only the last 3 backups
cd "$SRC_DIR" || exit

# Find and sort the backup folders, keeping the last 3
BACKUPS=($(ls -d backup_* 2>/dev/null | sort))

# Check if there are more than 3 backups
if [ ${#BACKUPS[@]} -gt 3 ]; then
  # Remove the oldest backups
  for ((i=0; i<${#BACKUPS[@]}-3; i++)); do
    echo "Removing old backup: ${BACKUPS[i]}"
    rm -rf "${BACKUPS[i]}"
  done
fi
```

### Explanation of the Script

1. **Input Validation**: 
   - The script first checks if a directory path is provided as a command-line argument.
   - It then checks if the provided path is a valid directory.

2. **Backup Directory Creation**:
   - A timestamp is generated using the current date and time.
   - A backup directory is created with the format `backup_YYYY-MM-DD_HH-MM-SS`.

3. **Copying Files**:
   - All files from the specified directory are copied to the newly created backup directory using `cp -r`.

4. **Backup Rotation**:
   - The script navigates to the specified directory and lists all backup folders sorted by name.
   - If the number of backups exceeds 3, it removes the oldest backups, ensuring that only the most recent 3 backups are retained.

### Example Usage

1. **Make the Script Executable**:
   ```bash
   chmod +x backup_with_rotation.sh
   ```

2. **Run the Script**:
   ```bash
   ./backup_with_rotation.sh /path/to/your/directory
   ```