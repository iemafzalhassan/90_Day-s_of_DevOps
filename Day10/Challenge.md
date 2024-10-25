# Challenge Day 10:

---

### Current Status
- **Day Completed**: 10
- **Total Days in Challenge**: 90

Join #TrainWithShubham Community on an exhilarating journey of learning and growth as we embark on the #90DaysofChallenge!

---

## Day 10 Challenge: Log Analysis Script

## Challenge Description
As a system administrator responsible for managing a network of servers, I needed to analyze log files generated daily on each server. The goal was to automate the process of analyzing these log files, identifying specific events, and generating a summary report.

## Tasks Completed
I created a Bash script to perform the following tasks:

1. **Input Validation**:
   - The script takes the path to the log file as a command-line argument.
   - It checks if the specified log file exists and handles errors appropriately.

2. **Error Count**:
   - The script analyzes the log file to count the number of error messages, specifically looking for keywords like "ERROR" and "Failed".

3. **Critical Events**:
   - It searches for lines containing the keyword "CRITICAL" and prints those lines along with their line numbers.

4. **Top Error Messages**:
   - The script identifies the top 5 most common error messages and displays them along with their occurrence counts.

5. **Summary Report**:
   - A summary report is generated in a separate text file, which includes:
     - Date of analysis
     - Log file name
     - Total lines processed
     - Total error count
     - Top 5 error messages with their occurrence counts
     - List of critical events with line numbers

6. **Optional Enhancement**:
   - The script moves processed log files to a designated archive directory for better organization.

## Script Code

```bash
#!/bin/bash

# Check if the log file path is provided
if [ $# -ne 1 ]; then
    echo "Usage: $0 <log_file_path>"
    exit 1
fi

# Get the log file path
LOG_FILE="$1"

# Check if the log file exists
if [ ! -f "$LOG_FILE" ]; then
    echo "Error: Log file '$LOG_FILE' not found."
    exit 1
fi

# Initialize variables
ERROR_COUNT=0
declare -A ERROR_MESSAGES
CRITICAL_EVENTS=()
TOTAL_LINES=0

# Analyze the log file
while IFS= read -r line; do
    ((TOTAL_LINES++))

    # Count error messages
    if [[ "$line" == *"ERROR"* || "$line" == *"Failed"* ]]; then
        ((ERROR_COUNT++))
        
        # Count specific error messages
        ERROR_MESSAGES["$line"]=$((ERROR_MESSAGES["$line"] + 1))
    fi

    # Collect critical events
    if [[ "$line" == *"CRITICAL"* ]]; then
        CRITICAL_EVENTS+=("$line")
    fi
done < "$LOG_FILE"

# Sort the error messages by occurrence and get the top 5
TOP_ERRORS=$(printf "%s\n" "${!ERROR_MESSAGES[@]}" | sort -nr -k2 | head -n 5)

# Generate the summary report
REPORT_FILE="summary_report_$(date +%Y-%m-%d).txt"
{
    echo "Date of Analysis: $(date)"
    echo "Log File Name: $LOG_FILE"
    echo "Total Lines Processed: $TOTAL_LINES"
    echo "Total Error Count: $ERROR_COUNT"
    echo "Top 5 Error Messages:"
    for error in "${!ERROR_MESSAGES[@]}"; do
        echo " - $error: ${ERROR_MESSAGES[$error]}"
    done | sort -k2 -nr | head -n 5
    echo "Critical Events:"
    for i in "${!CRITICAL_EVENTS[@]}"; do
        echo " - Line $((i + 1)): ${CRITICAL_EVENTS[$i]}"
    done
} > "$REPORT_FILE"

# Print the report location
echo "Summary report generated: $REPORT_FILE"

# Optional Enhancement: Archive the processed log file
ARCHIVE_DIR="./archive"
mkdir -p "$ARCHIVE_DIR"
mv "$LOG_FILE" "$ARCHIVE_DIR/"
echo "Moved log file to archive: $ARCHIVE_DIR/$(basename "$LOG_FILE")"
```

### Bash Script Breakdown

```bash
#!/bin/bash
```
- **What it does**: This line tells the computer that we are writing a script in Bash. It’s like saying, “Hey, use Bash to run this program!”

### Checking Input Arguments

```bash
if [ $# -ne 1 ]; then
    echo "Usage: $0 <log_file_path>"
    exit 1
fi
```
- **What it does**: This part checks if you gave the script exactly one piece of information (called an argument). If not, it shows you how to use the script and stops running. 
- **Key Points**:
  - `$#` is the number of arguments given.
  - `-ne 1` means "not equal to 1".
  - `$0` is the name of the script.

### Getting the Log File Path

```bash
LOG_FILE="$1"
```
- **What it does**: This line saves the argument you provided (the path to the log file) into a variable called `LOG_FILE`. Think of a variable as a box where you can store information.

### Checking if the Log File Exists

```bash
if [ ! -f "$LOG_FILE" ]; then
    echo "Error: Log file '$LOG_FILE' not found."
    exit 1
fi
```
- **What it does**: This checks if the log file you provided actually exists. 
- **Key Points**:
  - `-f` checks if the file exists.
  - If the file doesn’t exist, it tells you and stops running.

### Initialize Variables

```bash
ERROR_COUNT=0
declare -A ERROR_MESSAGES
CRITICAL_EVENTS=()
TOTAL_LINES=0
```
- **What it does**: Here, we set up some boxes (variables) to store information as we analyze the log file:
  - `ERROR_COUNT` keeps track of how many error messages we find.
  - `ERROR_MESSAGES` is a special box that can hold multiple messages and their counts.
  - `CRITICAL_EVENTS` will store any critical events we find.
  - `TOTAL_LINES` counts how many lines are in the log file.

### Analyzing the Log File

```bash
while IFS= read -r line; do
    ((TOTAL_LINES++))
```
- **What it does**: This starts a loop to go through each line of the log file one by one. `IFS=` makes sure spaces in the line don’t cause problems.
- **`((TOTAL_LINES++))`**: This line adds 1 to `TOTAL_LINES` for every line we read. It’s like saying, “We’ve read one more line!”

### Counting Error Messages

```bash
if [[ "$line" == *"ERROR"* || "$line" == *"Failed"* ]]; then
    ((ERROR_COUNT++))
```
- **What it does**: For each line, we check if it has the words "ERROR" or "Failed". If it does, we add 1 to the `ERROR_COUNT`.
- **`*` means "anything can be here"**: This means the word can be anywhere in the line.

### Counting Specific Error Messages

```bash
ERROR_MESSAGES["$line"]=$((ERROR_MESSAGES["$line"] + 1))
```
- **What it does**: This line keeps track of how many times each specific error message appears. If we see the same message again, we add 1 to its count.

### Collecting Critical Events

```bash
if [[ "$line" == *"CRITICAL"* ]]; then
    CRITICAL_EVENTS+=("$line")
fi
```
- **What it does**: If we find a line with "CRITICAL", we store that line in the `CRITICAL_EVENTS` list.

### Summary Report Generation

```bash
REPORT_FILE="summary_report_$(date +%Y-%m-%d).txt"
{
    echo "Date of Analysis: $(date)"
    echo "Log File Name: $LOG_FILE"
    echo "Total Lines Processed: $TOTAL_LINES"
    echo "Total Error Count: $ERROR_COUNT"
    echo "Top 5 Error Messages:"
```
- **What it does**: This part creates a new file to store our summary report. It starts by writing the current date, the name of the log file, the total lines processed, and the total error count.

### Displaying Top Error Messages

```bash
for error in "${!ERROR_MESSAGES[@]}"; do
    echo " - $error: ${ERROR_MESSAGES[$error]}"
done | sort -k2 -nr | head -n 5
```
- **What it does**: This loop goes through all the error messages we found and displays them along with how many times they occurred. 
- **Sorting**: It sorts them so the most common messages show up first, and only the top 5 are shown.

### Displaying Critical Events

```bash
echo "Critical Events:"
for i in "${!CRITICAL_EVENTS[@]}"; do
    echo " - Line $((i + 1)): ${CRITICAL_EVENTS[$i]}"
done
```
- **What it does**: This part lists the critical events we found along with their line numbers.

### Archiving the Log File

```bash
ARCHIVE_DIR="./archive"
mkdir -p "$ARCHIVE_DIR"
mv "$LOG_FILE" "$ARCHIVE_DIR/"
```
- **What it does**: After the analysis, we create a folder called `archive` (if it doesn't exist) and move the processed log file there. This helps keep things organized!
