# Challenge Day 14:

---

### Current Status
- **Day Completed**: 14
- **Total Days in Challenge**: 90

Join #TrainWithShubham Community on an exhilarating journey of learning and growth as we embark on the #90DaysofChallenge!

---
## Day 14: **Git Basics: Starting with Version Control**

### **1. `git init` - Initialize a Repository**
- **Usage**: Initializes a new Git repository in your current directory.
  
  ```bash
  git init
  ```

  **Pro Tip**: Always run this command in an empty directory to start tracking version control.

---

### **2. `git clone` - Clone a Repository**
- **Usage**: Copies a remote repository into your local machine.

  ```bash
  git clone <repository_url>
  ```

  **Pro Tip**: Use the `--depth 1` flag to clone only the latest snapshot of the repository if you don’t need the entire history.

---

### **3. `git config` - Configure Git Settings**
- **Usage**: Set up your username, email, and other Git settings.

  ```bash
  git config --global user.name "Your Name"
  git config --global user.email "your.email@example.com"
  ```

  **Pro Tip**: The `--global` flag sets this configuration for all repositories. If you want to set it for just one project, omit the flag.

---

## **Working with the Stage & Snapshot: Adding and Committing Changes**

### **4. `git add` - Stage Changes for Commit**
- **Usage**: Adds files to the staging area.

  ```bash
  git add <file>
  ```

  **Pro Tip**: Use `git add .` to stage all modified and new files in the current directory.

  **Common Flags**:
  - `-p`: Stage changes interactively, allowing you to select specific parts of files.
  
  ```bash
  git add -p
  ```

---

### **5. `git commit` - Snapshot Your Changes**
- **Usage**: Record changes from the staging area into the local repository.

  ```bash
  git commit -m "Descriptive message here"
  ```

  **Pro Tip**: Write concise and clear commit messages that reflect the nature of your changes. Always follow a consistent format (e.g., subject: `Fix`, `Add`, `Remove`).

  **Common Flags**:
  - `-a`: Automatically stage all tracked files before committing.
  
  ```bash
  git commit -a -m "Auto-stage and commit"
  ```

  - `--amend`: Modify the last commit (if you forgot to include changes or mistyped the message).

  ```bash
  git commit --amend -m "Updated commit message"
  ```

---

## **Branching & Merging: Handling Multiple Lines of Development**

### **6. `git branch` - Manage Branches**
- **Usage**: Lists, creates, or deletes branches.

  ```bash
  git branch
  ```

  **Pro Tip**: To create and switch to a new branch in one go, use the `-b` flag with `checkout`:
  
  ```bash
  git checkout -b <new_branch>
  ```

  **Common Commands**:
  - **Create a new branch**:
    
    ```bash
    git branch <new_branch>
    ```

  - **Delete a branch**:
    
    ```bash
    git branch -d <branch>
    ```

---

### **7. `git checkout` - Switch Branches**
- **Usage**: Switch to another branch or restore files.
  
  ```bash
  git checkout <branch>
  ```

  **Pro Tip**: Use `git checkout .` to discard local changes to all files.

---

### **8. `git merge` - Combine Branches**
- **Usage**: Merges the changes from one branch into your current branch.

  ```bash
  git merge <branch_to_merge>
  ```

  **Pro Tip**: Always merge with caution, as it may create conflicts. Use `git status` and `git diff` to review changes before merging.

---

### **9. `git rebase` - Reapply Commits on Top of Another Base**
- **Usage**: Move or combine commits from one branch to another.

  ```bash
  git rebase <branch>
  ```

  **Pro Tip**: Rebase keeps a cleaner history compared to merge. Use `git pull --rebase` to fetch and reapply local commits on top of the latest changes from the remote branch.

---

### **10. `git cherry-pick` - Apply Specific Commits**
- **Usage**: Apply changes from a specific commit onto your current branch.

  ```bash
  git cherry-pick <commit_hash>
  ```

  **Pro Tip**: Use cherry-pick if you want to pick specific changes from another branch without merging the entire branch.

---

## **Logs, Compare, and Inspecting History**

### **11. `git log` - View Commit Logs**
- **Usage**: Shows the commit history.
  
  ```bash
  git log
  ```

  **Pro Tip**: Use `git log --oneline --graph --decorate --all` for a visual graph of commits and branches.

---

### **12. `git show` - Show Commit Details**
- **Usage**: Displays changes and metadata of a specific commit.
  
  ```bash
  git show <commit_hash>
  ```

  **Pro Tip**: Combine `git show` with `git diff` to see changes in files between commits.

---

### **13. `git diff` - Compare Changes**
- **Usage**: Shows the differences between two commits or between your working directory and the staging area.

  ```bash
  git diff
  ```

  **Pro Tip**: Use `git diff --staged` to compare staged changes with the last commit.

---

## **Rewriting History and Fixing Mistakes**

### **14. `git reset` - Undo Commits**
- **Usage**: Resets the current branch to a previous state.

  ```bash
  git reset --soft <commit_hash>
  ```

  **Pro Tip**: Use `--soft` to keep changes in your working directory or `--hard` to discard them entirely.

---

### **15. `git revert` - Undo a Commit by Creating a New One**
- **Usage**: Reverts a previous commit by creating a new commit that undoes its changes.

  ```bash
  git revert <commit_hash>
  ```

  **Pro Tip**: Use revert instead of reset in shared repositories, as it doesn't remove history and is safer for collaboration.

---

### **16. `git stash` - Save Changes Temporarily**
- **Usage**: Stashes your changes away to work on something else without committing.

  ```bash
  git stash
  ```

  **Pro Tip**: Use `git stash list` to see your stashed changes and `git stash pop` to reapply and delete them.

---

## **Remote Operations: Pushing & Fetching from Repositories**

### **17. `git remote` - Manage Remotes**
- **Usage**: Adds, removes, and views remote connections.

  ```bash
  git remote add origin <repository_url>
  ```

  **Pro Tip**: Use `git remote -v` to list all remote connections and their URLs.

---

### **18. `git push` - Upload Changes to Remote**
- **Usage**: Pushes local commits to a remote repository.

  ```bash
  git push origin <branch>
  ```

  **Pro Tip**: Use `git push -u origin <branch>` to set the upstream branch so that future pushes can be done with just `git push`.

---

### **19. `git fetch` - Download Changes from Remote**
- **Usage**: Fetches updates from the remote repository without merging them.

  ```bash
  git fetch origin
  ```

  **Pro Tip**: Use fetch if you want to see what’s new in the remote repository without affecting your current branch.

---

### **20. `git pull` - Fetch & Merge**
- **Usage**: Fetches and automatically merges changes from the remote repository into your current branch.

  ```bash
  git pull origin <branch>
  ```

  **Pro Tip**: Always pull frequently to keep your local repository updated, especially when collaborating with others.

---

## **Ignoring Files: Managing Untracked Files**

### **21. `.gitignore` - Ignore Specific Files or Folders**
- **Usage**: Specifies intentionally untracked files to be ignored by Git.
  
  Example `.gitignore`:
  ```bash
  # Ignore all log files
  *.log
  
  # Ignore node_modules directory
  node_modules/
  
  # Ignore environment files
  .env
  ```

  **Pro Tip**: Make sure your `.gitignore` is properly configured before committing sensitive or unnecessary files.

---

## **Reviewing Your Work: Analyzing and Debugging**

### **22. `git blame` - Track Line-by-Line Changes**
- **Usage**: Shows who made changes to each line of a file.
  
  ```bash
  git blame <file>
  ```

  **Pro Tip**: Use `git blame` to identify who introduced a specific bug or change in a large codebase.

---

### **23. `git bisect` - Binary Search to Find a Bug

**
- **Usage**: Helps find the commit that introduced a bug through binary search.

  ```bash
  git bisect start
  git bisect good <commit_hash>
  git bisect bad <commit_hash>
  ```

  **Pro Tip**: This is your go-to tool for efficiently identifying the problematic commit in a large repository.

---

## **Conclusion: Final Thoughts for Mastering Git**

This cheat sheet covers all essential commands that will help you navigate through almost any Git-based workflow. Whether you're pushing new features, fixing bugs, or reviewing the commit history, mastering these commands will elevate your Git skills to a professional level. 

**Pro Tips Recap:**
1. Commit small, meaningful changes frequently.
2. Keep your commit messages short but informative.
3. Always work on branches, not directly on `main` or `master`.
4. Use stash frequently to avoid committing half-baked code.
5. Use revert and bisect to avoid messy histories.
