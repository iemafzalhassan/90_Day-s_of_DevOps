# Challenge Day 12:

---

### Current Status
- **Day Completed**: 12
- **Total Days in Challenge**: 90

Join #TrainWithShubham Community on an exhilarating journey of learning and growth as we embark on the #90DaysofChallenge!

---

# Day 12 Challenge: Deep Dive into Git & GitHub for DevOps Engineers

Welcome to **Day 12** of your 90-day DevOps journey! Today, we are focusing on **Git** and **GitHub**, two crucial tools that every DevOps engineer must master. We'll explore their importance and dive into some hands-on tasks.
---

## What is Git, and Why is it Important?

Imagine you're working on a project with multiple people, and everyone is editing files at the same time. Without a way to track and manage changes, it would be chaos! **Git** is like a smart librarian that keeps track of all changes in your code. It helps you maintain versions of your project, and even go back to previous versions if needed. Git is a **distributed version control system**. That means everyone has their own complete copy of the project. Changes can be tracked, merged, or rolled back if needed.

Git ensures:
- **Collaboration**: Multiple people can work on the same project without overwriting each other’s work.
- **History**: Every change is logged, so you can see who made what change and when.
- **Backup**: With Git, you have the full project history available in every developer's copy of the project.

Think of Git like the "Undo" button for your code, but on a much bigger scale.

## What is the Difference Between the Main Branch and Master Branch?

Originally, Git used **master** as the default branch. However, there was a movement to rename this to **main** to be more inclusive and neutral. Technically, they are the same — both are just names of the default branch where the main code lives — but now, **main** is the preferred name used when initializing new repositories. 

## Git vs GitHub

This is a common confusion: **Git** and **GitHub** are different tools, but they work hand in hand. 
- **Git**: A version control system used locally on your machine to manage your project's history and track changes.
- **GitHub**: A platform that hosts your Git repositories online. It allows teams to collaborate, review code, and manage projects together using Git.

**Analogy**: Imagine Git is your personal journal where you write daily logs. GitHub is like an online library where you can share your journal, collaborate with others, and see everyone’s logs.

## How to Create a New Repository on GitHub?

Here’s how you can create a repository:
1. Go to [GitHub.com](https://github.com) and log in.
2. Click the **+** icon in the top-right corner and choose **New repository**.
3. Name your repository (e.g., **DevOps**).
4. Add a description (optional).
5. Decide whether it’s **Public** (anyone can see) or **Private** (only you and invited collaborators can see).
6. Click **Create repository**.

## Difference Between Local and Remote Repository & Connecting Them

- **Local Repository**: This is your project stored on your own computer.
- **Remote Repository**: This is the version of your project stored on GitHub (or any other hosting platform).

To connect them:
1. Create a repository on GitHub.
2. On your local machine, navigate to your project folder and run the following commands:
    ```bash
    git init
    git remote add origin https://github.com/yourusername/DevOps.git
    ```
3. Now, your local repository is connected to the remote one on GitHub.

---

## Tasks

### Task 1: Set Your User Name and Email Address

When you make a commit, Git needs to know who is making the changes. Set up your username and email with these commands:

```bash
git config --global user.name "Your Name"
git config --global user.email "youremail@example.com"
```

### Task 2: Create and Connect a Repository

1. **Create a repository** named **DevOps** on GitHub by following the steps above.
2. On your local machine, create a directory:
    ```bash
    mkdir DevOps
    cd DevOps
    git init
    ```
3. Connect your local repository to GitHub:
    ```bash
    git remote add origin https://github.com/yourusername/DevOps.git
    ```

4. Create a file and add content:
    ```bash
    mkdir -p Git
    echo "This is Day 02 of my DevOps journey!" > Git/Day-02.txt
    ```

5. **Stage** and **commit** your changes:
    ```bash
    git add Git/Day-02.txt
    git commit -m "Added Day 02 file with content"
    ```

6. **Push** your changes to GitHub:
    ```bash
    git push origin main
    ```

---
> **Tip**: Always keep practicing these commands until you are comfortable using Git and GitHub in real projects.

--- 