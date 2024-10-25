# Challenge Day 13:

---

### Current Status
- **Day Completed**: 13
- **Total Days in Challenge**: 90

Join #TrainWithShubham Community on an exhilarating journey of learning and growth as we embark on the #90DaysofChallenge!

---

# Day 13 Challenge: Advanced Git & GitHub for DevOps Engineers

Welcome to **Day 13**! Today, we’re diving deeper into **Git branching**, **reverting**, **resetting**, and understanding the difference between **merging** and **rebasing**. These are powerful tools that allow you to control and manage your code in complex, real-world scenarios.
---

## Git Branching: Isolating Work Without Affecting Others

### What Are Git Branches?

Imagine your code is like a tree. The **main branch** is the trunk, and when you want to add new features or fixes, you create **branches** off the trunk to work independently. Each branch allows you to develop features without disturbing the main codebase. Once you're happy with your changes, you can merge them back into the main branch (trunk).

In the real world, this means that when you’re building a new feature (like adding a new button to an app), you create a branch to work on it. If there’s a bug, you can also create a branch for that and fix it without messing up other people’s work. 

- **Command**: `git checkout -b dev`
    - This command creates a new branch called `dev` and switches to it.
    - **`-b` flag**: The `-b` flag tells Git to create a new branch and immediately switch to it. Without this, you would only switch branches, not create a new one.

### Why Are Branches Important?

- **Isolation**: Branches isolate your work, allowing multiple features or bug fixes to be worked on simultaneously.
- **Collaboration**: Different team members can work on their own branches without interfering with each other's code.
- **Safety**: You can experiment in branches without affecting the production code.

---

## Git Revert and Reset: Undoing Mistakes Like a Pro

### What is Git Revert?

In real life, imagine you’re writing an essay and make a mistake in one paragraph. Instead of erasing the whole page, you cross out the paragraph and add a correction at the bottom. **Git revert** works similarly. It undoes changes by creating a new commit that reverses the bad changes, but the history of the mistake is still there. This way, your history is transparent, showing both the mistake and the fix.

- **Command**: `git revert HEAD~2`
    - This reverts the last two commits.
    - **`HEAD~2`**: This refers to the second-to-last commit. In Git, `HEAD` always refers to the latest commit, and `~2` means "go back two commits."

### What is Git Reset?

Now, let’s say you want to rewrite history like the mistake never happened. This is where **Git reset** comes in. It wipes out a part of your commit history, like a magic eraser. However, use it carefully! Once you reset, it’s as if the changes never existed. It’s useful when you’re still in development and the history isn’t as important.

- **Command**: `git reset --hard HEAD~1`
    - This command resets your repository to one commit before the current state.
    - **`--hard` flag**: This means it will not only remove the commit from the history but also from your working directory, wiping out any changes.
    - **Scenario**: Imagine you've pushed a commit with some confidential info, like passwords. A `git reset --hard` can remove the commit and wipe out the traces.

---

## Git Rebase vs. Git Merge: How to Combine Your Work

### What is Git Merge?

When two people (or more) work on different features, they can merge their changes into the main codebase. **Git merge** combines the changes from one branch into another, but it keeps a history of both branches. Think of this as merging two different storylines into one — but you can still look back at each storyline separately.

- **Command**: `git merge dev`
    - Merges the `dev` branch into your current branch (usually `master` or `main`).
    - **Scenario**: Two developers are working on different parts of a website — one on the header, the other on the footer. They merge their branches into the main code so both changes appear together.

### What is Git Rebase?

**Git rebase** is like editing the history of your project to make it appear as if your work was done in a smooth, linear way. It rewrites your commit history to make it look like the changes in one branch happened directly after the changes in the branch you're rebasing onto. It’s cleaner, but it can hide the reality of what happened.

- **Command**: `git rebase master`
    - Re-applies the changes from your branch (e.g., `dev`) on top of the `master` branch.
    - **Scenario**: Imagine you’re building a feature that depends on other changes made in `master`. Rebasing makes it look like your feature was built directly after those changes, keeping the history clean.

---

## Tasks for Day 13

### Task 1: Feature Development with Branches

#### 1.1: Create a New Branch and Add a Feature

1. **Create a text file** called **version01.txt** in the `Devops/Git/` directory:
   ```bash
   echo "This is the first feature of our application." > Devops/Git/version01.txt
   ```

2. **Create a new branch** for development:
   ```bash
   git checkout -b dev
   ```
   - This switches to a new branch called `dev`.

3. **Add and commit your changes**:
   ```bash
   git add Devops/Git/version01.txt
   git commit -m "Added new feature"
   ```
   - **`git add`** stages the file for commit.
   - **`git commit -m "message"`** creates a snapshot of your changes with a message explaining what was done.

4. **Push your changes** to GitHub:
   ```bash
   git push origin dev
   ```
   - **`origin`** refers to the remote repository (GitHub in this case), and `dev` is the branch you’re pushing.

#### 1.2: Add More Features with Separate Commits

1. **Add the first line** (bug fix):
   ```bash
   echo "This is the bug fix in development branch" >> Devops/Git/version01.txt
   git commit -am "Added feature2 in development branch"
   ```
   - **`-a` flag**: Automatically stages all modified and deleted files.
   - **Scenario**: You’re fixing a bug in the `dev` branch while leaving the main codebase untouched.

2. **Add the second line** (bad code):
   ```bash
   echo "This is gadbad code" >> Devops/Git/version01.txt
   git commit -am "Added feature3 in development branch"
   ```
   - This adds some bad code that we’ll revert later.

3. **Add the third line** (this will break everything):
   ```bash
   echo "This feature will gadbad everything from now" >> Devops/Git/version01.txt
   git commit -am "Added feature4 in development branch"
   ```

#### 1.3: Revert to a Previous Version

Now we need to undo the bad changes.

1. Use **`git revert`** to go back to the last good state:
   ```bash
   git revert HEAD~2
   ```
   - This creates a new commit that undoes the last two commits (removing the bad code).

---

### Task 2: Working with Branches

#### 2.1: Demonstrate Branches

1. **Create two or more branches**:
   ```bash
   git checkout -b feature1
   git checkout -b feature2
   ```
   - Take screenshots of your branches using:
     ```bash
     git branch -v
     ```

#### 2.2: Merge Changes into Master

Let’s merge the changes from `dev` into `master`.

1. **Switch to the master branch**:
   ```bash
   git checkout master
   ```

2. **Merge dev into master**:
   ```bash
   git merge dev
   ```
   - This brings the changes from `dev` into `master`, keeping both histories intact.

#### 2.3: Practice Rebase

1. **Rebase dev onto master**:
   ```bash
   git checkout dev
   git rebase master
   ```
   - This re-applies the commits from `dev` onto `master`, keeping the history linear.

---