# Challenge Day 06: 

---

### Current Status
- **Day Completed**: 6
- **Total Days in Challenge**: 90

---

## Day 08: File Permissions and Access Control Lists

## What Are File Permissions?

In Linux, every file and directory has three types of users:

1. **Owner**: The person who created the file.
2. **Group**: A collection of users who can share access to the file.
3. **Others**: Everyone else who has access to the system.

Each user category can have different permissions, which determine what actions they can perform on a file:

- **Read (`r`)**: Permission to look at the file.
- **Write (`w`)**: Permission to change the file.
- **Execute (`x`)**: Permission to run the file if it’s a program or script.

### Visualizing Permissions

Let’s say we have a file called `my_script.sh`. When we run the command `ls -l my_script.sh`, we might see something like this:

```bash
-rwxr-x--- 1 Aarav devteam 1024 Oct 24 12:00 my_script.sh
```

Here's what that means:
- `-`: This indicates that it’s a file (not a directory).
- `rwx`: The owner (Aarav) can read, write, and execute.
- `r-x`: The group (devteam) can read and execute, but not write.
- `---`: Others have no permissions.

## Changing Permissions with `chmod`

### What is `chmod`?

The `chmod` command lets us change the permissions of a file. We can use two methods: **numeric** and **symbolic**.

### Numeric Method

Each permission is represented by a number:
- Read = 4
- Write = 2
- Execute = 1

To combine permissions, we simply add the numbers. For example, `chmod 755 my_script.sh` gives:
- Owner: 7 (read + write + execute = 4 + 2 + 1)
- Group: 5 (read + execute = 4 + 1)
- Others: 5 (read + execute = 4 + 1)

### Symbolic Method

You can also use letters to specify permissions. For example:
- `chmod g+x my_script.sh` adds execute permission for the group.

### Real-World Example of `chmod`

Imagine you have a deployment script called `deploy.sh`. Initially, only you can run it:

```bash
ls -l deploy.sh
# Output: -rwx------ 1 Aarav devteam 1024 Oct 24 12:00 deploy.sh
```

After discussing with your team, you use `chmod g+x deploy.sh` to allow your team to execute it:

```bash
chmod g+x deploy.sh
ls -l deploy.sh
# Output: -rwx--x--- 1 Aarav devteam 1024 Oct 24 12:00 deploy.sh
```

Now your whole team can run the deployment script!

## Changing Ownership with `chown`

### What is `chown`?

The `chown` command changes the owner of a file. This is useful when someone leaves a project or you need to transfer responsibilities.

### Real-World Example of `chown`

Suppose you have a backup file called `backup.tar.gz` that was created by **Raj**. You need to transfer ownership to **Priya**. You run:

```bash
chown priya backup.tar.gz
```

Now Priya is the owner!

```bash
ls -l backup.tar.gz
# Output: -rw-r--r-- 1 priya devteam 2048 Oct 24 12:00 backup.tar.gz
```

## Changing Group Ownership with `chgrp`

### What is `chgrp`?

The `chgrp` command changes the group associated with a file. This is helpful when teams change and certain files need to be shared with different groups.

### Real-World Example of `chgrp`

Imagine you have a report file called `team_report.docx`, which was initially part of the **marketing** group. Now it needs to be accessible to the **research** team. You run:

```bash
chgrp research team_report.docx
```

Now, the report is available to the research team!

```bash
ls -l team_report.docx
# Output: -rw-r--r-- 1 Aarav research 5120 Oct 24 12:00 team_report.docx
```

## Understanding Ownership Changes

Let’s explore a scenario to clarify ownership and permissions:

1. **Initial Setup**:
   - User **Aarav** creates a file called `test.txt`.
   - Permissions are set to `rwx` (read, write, execute) for **Aarav** and group members.

   ```bash
   ls -l test.txt
   # Output: -rwxr----- 1 aarav devops 1024 Oct 24 12:00 test.txt
   ```

2. **Ownership Change**:
   - The owner of `test.txt` is changed to **Riya** using `chown`.

   ```bash
   chown riya test.txt
   ```

   Now, the permissions look like this:

   ```bash
   ls -l test.txt
   # Output: -r-xr----- 1 riya devops 1024 Oct 24 12:00 test.txt
   ```

3. **Permission Implications**:
   - **Aarav**: As part of the `devops` group, **Aarav** can still read and execute the file, but cannot modify it.
   - **Riya**: Now has `rx` permissions, meaning she can read and execute but not write to the file.

This scenario shows how changing ownership affects who can do what with the file.

## Conclusion

In this challenge, we learned about Linux file permissions, how to use `chmod`, `chown`, and `chgrp`, and we explored real-world scenarios. Understanding these concepts is crucial for effective collaboration in a DevOps environment.

---

Feel free to adjust any parts of this document as needed! If you have more requests or further questions, just let me know!