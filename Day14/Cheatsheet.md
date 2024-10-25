# Git Command Cheatsheet - Quick Reference

This cheat sheet provides a thorough overview of essential Git commands, along with various options.
---

### **1. Initialize Repository**

- **`git init`**  
  Initializes a new local Git repository.

- **`git init <repo_name>`**  
  Initializes a new repository in a directory named `<repo_name>`.

---

### **2. Clone Repository**

- **`git clone <repo_url>`**  
  Clones a remote repository into your local machine.
  
- **`git clone <repo_url> --depth 1`**  
  Clones only the latest snapshot without full history.

- **`git clone --branch <branch_name> <repo_url>`**  
  Clones a specific branch from the remote repository.

---

### **3. Configure Git**

- **`git config --global user.name "Your Name"`**  
  Sets the global username.

- **`git config --global user.email "you@example.com"`**  
  Sets the global email.

- **`git config --global core.editor "editor"`**  
  Sets the default text editor for commit messages.

- **`git config --list`**  
  Lists all Git configuration settings.

---

### **4. Stage Changes**

- **`git add <file>`**  
  Stages a specific file.

- **`git add .`**  
  Stages all changes in the current directory.

- **`git add -A`**  
  Stages all changes (including file deletions) in the repository.

- **`git add -p`**  
  Interactively stages parts of a file.

---

### **5. Commit Changes**

- **`git commit -m "Message"`**  
  Commits staged changes with a message.

- **`git commit -a -m "Message"`**  
  Stages and commits tracked files in one command.

- **`git commit --amend -m "Updated message"`**  
  Amends the last commit with a new message.

- **`git commit --allow-empty -m "Empty commit"`**  
  Creates an empty commit (useful for triggering CI/CD pipelines).

---

### **6. Branch Management**

- **`git branch`**  
  Lists all branches.

- **`git branch <branch_name>`**  
  Creates a new branch.

- **`git branch -d <branch_name>`**  
  Deletes a branch.

- **`git branch -D <branch_name>`**  
  Forces deletion of a branch, regardless of unmerged changes.

- **`git branch --merged`**  
  Lists branches that have been merged into the current branch.

---

### **7. Switch Branches**

- **`git checkout <branch>`**  
  Switches to the specified branch.

- **`git checkout -b <branch_name>`**  
  Creates and switches to a new branch.

- **`git switch <branch_name>`**  
  A more intuitive command for switching branches.

- **`git switch -b <branch_name>`**  
  Creates and switches to a new branch (alternative to `checkout`).

---

### **8. Merge Branches**

- **`git merge <branch>`**  
  Merges the specified branch into the current one.

- **`git merge --no-ff <branch>`**  
  Merges a branch without fast-forwarding, preserving history.

- **`git merge --squash <branch>`**  
  Combines changes from the branch into a single commit.

---

### **9. Rebase**

- **`git rebase <branch>`**  
  Reapplies commits from the current branch onto another.

- **`git rebase -i <commit_hash>`**  
  Starts an interactive rebase to modify commit history.

- **`git rebase --continue`**  
  Continues the rebase process after resolving conflicts.

---

### **10. Cherry-Pick**

- **`git cherry-pick <commit_hash>`**  
  Applies the changes from a specific commit onto your branch.

- **`git cherry-pick --no-commit <commit_hash>`**  
  Applies the changes without committing them immediately.

---

### **11. View Logs**

- **`git log`**  
  Shows the commit history.

- **`git log --oneline`**  
  Displays a simplified view with each commit on a single line.

- **`git log --graph`**  
  Shows a graphical representation of the commit history.

- **`git log --oneline --graph --decorate --all`**  
  Visualizes the entire commit history with branch names and tags.

- **`git log <file>`**  
  Shows commit history for a specific file.

---

### **12. Show Commit**

- **`git show <commit_hash>`**  
  Shows changes made in a specific commit.

- **`git show <tag>`**  
  Displays information about a specific tag.

---

### **13. Compare Changes**

- **`git diff`**  
  Compares working directory changes to the staging area.

- **`git diff --staged`**  
  Compares staged changes to the last commit.

- **`git diff <branch1> <branch2>`**  
  Shows differences between two branches.

- **`git diff HEAD`**  
  Compares the working directory to the last commit.

---

### **14. Undo Commits**

- **`git reset --soft <commit>`**  
  Resets to a previous commit but keeps changes in the working directory.

- **`git reset --mixed <commit>`**  
  Resets to a previous commit and unstages changes.

- **`git reset --hard <commit>`**  
  Resets to a previous commit and discards all changes.

---

### **15. Revert Commit**

- **`git revert <commit>`**  
  Reverts a previous commit by creating a new commit that undoes it.

- **`git revert HEAD`**  
  Reverts the most recent commit.

---

### **16. Stash Changes**

- **`git stash`**  
  Saves uncommitted changes temporarily.

- **`git stash pop`**  
  Reapplies stashed changes.

- **`git stash apply`**  
  Applies stashed changes without removing them from the stash.

- **`git stash list`**  
  Lists all stashed changes.

- **`git stash drop stash@{n}`**  
  Deletes a specific stash.

---

### **17. Remote Operations**

- **`git remote -v`**  
  Lists remote repositories.

- **`git remote add origin <repo_url>`**  
  Adds a remote repository.

- **`git remote remove <remote_name>`**  
  Removes a remote repository.

- **`git fetch origin`**  
  Downloads changes from the remote repository without merging.

- **`git pull origin <branch>`**  
  Fetches and merges remote changes into the current branch.

- **`git push origin <branch>`**  
  Pushes local commits to a remote branch.

- **`git push -u origin <branch>`**  
  Pushes and sets the upstream branch for future pushes.

---

### **18. Ignore Files**

- **`.gitignore`**  
  Defines patterns for files or directories to ignore.

- **`git check-ignore -v <file>`**  
  Checks if a file is ignored and shows which pattern is causing it.

---

### **19. Blame**

- **`git blame <file>`**  
  Shows who made changes to each line in a file.

- **`git blame -L <start>,<end> <file>`**  
  Limits the blame output to specific line ranges.

---

### **20. Bisect**

- **`git bisect start`**  
  Begins binary search to find the commit that introduced a bug.

- **`git bisect good <commit_hash>`**  
  Marks a commit as good.

- **`git bisect bad <commit_hash>`**  
  Marks a commit as bad.

- **`git bisect reset`**  
  Ends the bisect session and returns to the original branch.

---

### **21. Inspect and Compare**

- **`git reflog`**  
  Shows the history of all changes, even those not in the commit history.

- **`git status`**  
  Displays the current state of the working directory and staging area.

- **`git diff --cached`**  
  Shows differences between staged files and the last commit.

---

### **22. Rewrite History**

- **`git rebase -i HEAD~<n>`**  
  Interactive rebase to modify the commit history.

- **`git filter-branch --env-filter '...' HEAD`**  
  Rewrites the history to change commit information like author and email.

---

### **23. Temporary Commits**

- **`git stash save "message"`**  
  Temporarily saves changes with a description.

- **`git stash save --keep-index`**  
  Stashes changes while keeping the staged changes intact.

---
