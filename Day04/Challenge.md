# Challenge Day 04: 

---

### Current Status
- **Day Completed**: 4
- **Total Days in Challenge**: 90

Join #TrainWithShubham Community on an exhilarating journey of learning and growth as we embark on the #90DaysofChallenge!

---

## Day 04: Basic Linux Shell Scripting for DevOps Engineers


### What is the Kernel?
The **kernel** is the core component of an operating system. It manages system resources such as CPU, memory, and device inputs/outputs. The kernel acts as a bridge between applications and the hardware of the computer, ensuring that all system operations are performed smoothly and efficiently.

### What is the Shell?
A **shell** is a user interface that allows users to interact with the operating system. It accepts commands from the user, processes them, and communicates with the kernel to perform tasks. Shells can be command-line based (like bash) or graphical, and they enable users to execute programs, manage files, and configure system settings.

### What is Linux Shell Scripting?
**Linux shell scripting** refers to writing a series of commands for the shell to execute as a single script. These scripts can automate repetitive tasks, configure system settings, and perform system administration tasks. For instance, a shell script can be created to automate file backups, deploy applications, or run system checks.

### Tasks

#### Task 1: Explain Shell Scripting for DevOps
Shell scripting for DevOps means writing small programs that can automate repetitive tasks, improving efficiency and consistency in operations. For instance, if you need to back up files daily, instead of doing it manually each time, you can create a shell script that runs the backup command automatically at a scheduled time using tools like `cron`.

#### Task 2: What is `#!/bin/bash`?
The line `#!/bin/bash` is known as a **shebang** (or hashbang). It indicates which interpreter should be used to execute the script that follows. In this case, it specifies that the Bash shell should be used. You can also use `#!/bin/sh`, but Bash includes more features than `sh`, so it is often preferred for scripting.

#### Task 3: Write a Shell Script that prints "I will complete #90DaysOfDevOps challenge."
Here’s a simple script:

```bash
#!/bin/bash
echo "I will complete #90DaysOfDevOps challenge."
```

#### Task 4: Create a Shell Script that takes user input and prints variables
This script takes the full name as the first argument and the company name as the second argument:

```bash
#!/bin/bash
full_name=$1
company=$2
echo "Hi $full_name, hope you are doing well."
echo "Thank you for sharing your company name, it's nice to know you are working at $company."
```

**Explanation:**
- `$1` and `$2` are special variables that capture the first and second command-line arguments passed to the script. This allows users to input their full name and company name when they run the script.

#### Task 5: Create a script using If-Else for a calculator
Here’s a calculator script that performs addition, subtraction, multiplication, and division:

```bash
#!/bin/bash
echo "Enter first number:"
read num1
echo "Enter second number:"
read num2

echo "Choose an operation: +, -, *, /"
read operation

if [ "$operation" == "+" ]; then
    result=$((num1 + num2))
    echo "The result of $num1 + $num2 is: $result"
elif [ "$operation" == "-" ]; then
    result=$((num1 - num2))
    echo "The result of $num1 - $num2 is: $result"
elif [ "$operation" == "*" ]; then
    result=$((num1 * num2))
    echo "The result of $num1 * $num2 is: $result"
elif [ "$operation" == "/" ]; then
    if [ $num2 -ne 0 ]; then
        result=$((num1 / num2))
        echo "The result of $num1 / $num2 is: $result"
    else
        echo "Error: Division by zero is not allowed."
    fi
else
    echo "Invalid operation. Please use +, -, *, or /."
fi
```
