# Git for Beginners: Basics and Essential Commands

A beginner-friendly guide to Git, covering repositories, commits, branches, essential Git commands, and a complete Git workflow from scratch.

> Originally published on Hashnode.

## 1\. Introduction

Imagine we are working on a project and keep saving different versions like this:

*   project
    
*   project\_final
    
*   project\_final\_new
    
*   project\_final\_latest
    
*   project\_final\_latest2
    

After a while, it becomes difficult to remember which version is the latest or which one contains the correct changes. Now imagine working with a team where multiple developers are editing the same project at the same time. Managing all those changes manually would quickly become confusing and error-prone.

This is exactly the problem Git was created to solve.

In this article, we’ll start from the basics by understanding what Git is, why it’s used, the core concepts like repositories, commits, branches, and HEAD, and then walk through the most commonly used Git commands.

## 2\. Why is Git?

Git is used because it makes software development safer and more organized.

Some major benefits include:

*   Track every change made to code.
    
*   Undo mistakes easily.
    
*   Work on new features without affecting the main project.
    
*   Collaborate with multiple developers.
    
*   Contribute to open-source projects.
    
*   Maintain a complete history of project.
    

Without Git:

```text
project_final
project_final2
project_final_final
project_final_latest
```

With Git:

```text
Version 1
      │
Version 2
      │
Version 3
```

## 3\. What is Git?

Git is a distributed version control system that helps developers track changes in their code, collaborate with others, and safely manage different versions of a project.

#### Why is Git called a **Distributed Version Control System?**

*   **Version Control** means tracking every version of our project.
    
*   **Distributed** means every developer has a complete copy of the project’s history on their own computer.
    

Unlike older systems that relied on a single central server, Git allows us to work even when we are **offline**.

## 4\. Core Terminologies

Before using Git commands, let’s understand a few important terms.

**Working Directory**: The Working Directory is where we create and edit files. For Example:

```text
index.html
style.css
script.js
```

Whenever we modify a file, the changes first appear in the working directory.

**Repository (repo)**: the project folder that Git is tracking.

**Staging Area**: The Staging Area acts like a waiting room.

Before Git permanently saves our changes, we decide which files should be included in the next commit.  
When we make changes to a file, Git notices, but it doesn't automatically save those changes to the project's history. we have to explicitly tell Git which changes we want to include in the next snapshot. Moving a file into the Staging Area is how we do that.

**Commit**: A saved snapshot of our work at a specific moment. Each commit has a unique ID and a message we write, like "Added conclusion paragraph" or "Fixed SEO headline". It's how Git knows what changed and when.

**Branch**: A branch allows us to work on new features without affecting the main project. The default branch is called main (or master in older setups).

For example:

```text
main
│
├── login-feature
└── payment-feature

//Once the feature is complete, it can be merged into the main branch.
```

We often create a branch called to test a major structural rewrite, leaving our published version untouched.

**Head**: HEAD points to the latest commit we are currently working on. or, we can say... Usually it points to the latest commit on the current branch.

```text
Commit A
   │
Commit B
   │
Commit C
   ▲
  HEAD
```

**Merge**: Combining one branch back into another. Once our draft/new-article branch is ready, we merge it into main, and Git weaves the changes together.

**Clone**: Creating a full copy of an existing repository, including its entire history. Useful when collaborating with co-authors or setting up a new machine.

**Push / Pull**: Git push uploads our commits to a remote server (like GitHub). Git pull downloads the latest commits from that server. These keep our local copy and the shared online copy in sync.

## 5\. Common Git Commands

Here's a complete interactive reference for all essential Git commands, grouped by what we're actually trying to do.

#### Category 1: Setup and init

a. **git init**: Start tracking a folder with Git.

Creates a hidden .git/ folder inside our project. This is where Git stores all version history. Run this once at the start of any new project.

```bash
cd my-project
git init
# → Initialized empty Git repository in my-project/.git/
```

Git now starts tracking our project.

#### Category 2: Track Changes

a. **git status**: Shows which files are modified, which are staged, and which are new. Always run this before committing. This command tells us:

*   Which files are modified
    
*   Which files are staged
    
*   Which files are untracked
    

```text
git status
# On branch main
# Changes not staged for commit:
#   modified: post.md
# Untracked files:
#   new-draft.md
```

It is one of the most frequently used Git commands.

b. **git add filename**: Moves changes into the staging area. Only staged changes get saved in the next commit. Use git **add .** to stage all changed files at once. For Example:

```bash
git add post.md          # stage one file
git add images/ post.md  # stage multiple
git add .                # stage everything
```

c. **git commit -m "message"**:This saves a snapshot of our staged files with a description. Write the message in **present tense**, describing what this snapshot contains.

For example:

```bash
git commit -m "Add intro section to Python tutorial"
git commit -m "Fix broken image link in post #12"
```

d. **git commit -am "message"** : git commit -am "message" combines two flags:

*   \-a → Automatically stages all modified tracked files.
    
*   \-m → Adds the commit message.
    

So, git commit -am "message" means: “Stage all modified tracked files and commit them with the given message in one command.”

**Note**: This command only stages and commits files that are already being tracked by Git and have been modified. It does not include new (untracked) files.

The critical word is "tracked." This flag does not stage brand-new files that Git has never seen before. Those are called "untracked" files and still require an explicit git add.

Example: Suppose our project contains these files:

```text
index.html     ← tracked
style.css      ← tracked
script.js      ← new (untracked)
```

Now when we:

*   Edit index.html
    
*   Edit style.css
    
*   Create a new file script.js
    

If you run:

```bash
git commit -am "Update website"
```

Git will do this: Staged and committed:

```text
index.html
style.css
```

Not staged or committed:

```text
script.js
```

Because script.js is untracked.

To include it, we must first run:

```bash
git add script.js
git commit -m "Add JavaScript file"
```

e. **git diff**: Shows a line-by-line diff of unstaged changes. Lines starting with + were added, - were removed. Use git diff --staged to see staged changes.

```bash
git diff           # unstaged changes
git diff --staged  # changes ready to commit
git diff HEAD      # all changes since last commit
```

git diff shows the changes we have made but haven’t staged yet. It compares our working directory with the staging area. Example: Suppose index.html originally contains:

```html
<h1>Welcome</h1>
```

we change it to:

```html
<h1>Welcome to My Website</h1>
```

Now run: git diff Output:

```diff
- <h1>Welcome</h1>
+ <h1>Welcome to My Website</h1>
```

This means:

*   (- indicates a line that was removed.)
    
*   (+ indicates a line that was added.)
    

After staging the file

If we run:

```bash
git add index.html
```

Then:

```bash
git diff
```

shows nothing, because there are no **unstaged changes**.

To see the staged changes instead, use:

```bash
git diff --staged
```

One-line summary

git diff shows the unstaged changes we’ve made to tracked files before we commit them.

#### Category 3: History

a. **git log**: git log displays the history of commits in our repository. Lists all commits from newest to oldest, with commit ID, author, date, and message. Use the compact version for a cleaner view.

```bash
git log                   # full history
git log --oneline         # one line per commit
git log --oneline -5      # last 5 commits only
git log --oneline post.md # history for one file
```

For Example:

```text
commit 8f3a9b2...
Author: Krishna Kumar <krishna@example.com>
Date:   Mon Jun 22 15:30:10 2026

    Fix login bug

commit c12d4e5...
Author: Krishna Kumar <krishna@example.com>
Date:   Mon Jun 22 14:45:21 2026

    Add login page

commit a56b7c8...
Author: Krishna Kumar <krishna@example.com>
Date:   Mon Jun 22 14:10:05 2026

    Initial project setup
```

#### Category 4: Undo & recover

a. git revert commitId: Safely undo a past commit.

Creates a new commit that reverses the changes from a past commit. The original commit stays in history — this is the safe way to undo shared work.

```bash
git revert a1b2c3d
# Creates a new "Revert" commit on top
```

b. git reset --hard commitId: git reset --hard is one of Git's most powerful — and most dangerous — commands.

It moves our current branch backwards to a specific commit and wipes everything after it, including our working directory and staging area.

![](https://cdn.hashnode.com/uploads/covers/699b471cf5291f20937649a4/a716266c-e066-4d17-b4e9-ff357d5c8727.png align="center")

The three things --hard destroys:

When we run git reset --hard , Git obliterates three things simultaneously:

Commits after the target — any commits newer than the one we specify become unreachable. They're not immediately deleted from Git's object store, but no branch points to them anymore, so they're effectively gone.

The staging area — everything we had staged with git add is wiped clean.

Our working directory — every unsaved edit in every tracked file is thrown away. our files are reset to exactly how they looked at the target commit.

This is the key difference from git reset --soft (which only moves the branch pointer, keeping our changes staged) and git reset --mixed (the default, which unstages changes but keeps our file edits).

How to use it:

```bash
# Reset to a specific commit by hash
git reset --hard b3c4d5e

# Reset to the previous commit (one step back)
git reset --hard HEAD~1

# Reset two commits back
git reset --hard HEAD~2

# Reset to where the remote branch currently is
git reset --hard origin/main
```

The escape hatch — git reflog  
Even after a hard reset, Git secretly keeps all commits alive for about 30 days in a log called the reflog. It records every position HEAD has ever been at.

```bash
git reflog
# Shows something like:
# b3c4d5e HEAD@{0}: reset: moving to b3c4d5e
# d7e8f9a HEAD@{1}: commit: Add conclusion section
# c5d6e7f HEAD@{2}: commit: Fix headline

# Recover by resetting back to the "lost" commit
git reset --hard d7e8f9a
```

So git reset --hard is dangerous but not always fatal — as long as we act within the reflog window and haven't run git gc(git gc: It cleans up and optimizes the Git repository by removing unnecessary files and compressing Git data to save space).

![](https://cdn.hashnode.com/uploads/covers/699b471cf5291f20937649a4/2748422f-7b23-42cc-955b-6b2a6535ba36.png align="center")

`--hard` should be used only if we genuinely want to throw everything away and start fresh from a known good state. For anything less drastic, `--soft` or `--mixed` are safer choices.

## 6\. Basic developer workflow (From Scratch)

Step 1: Create a project

```bash
mkdir my-project
cd my-project
```

Step 2: Initialize Git

```bash
git init
```

This creates an empty Git repository in our project.

Step 3: Create a file

```bash
touch index.html
```

Step 4: Check the repository status

```bash
git status
```

Git shows that index.html is an untracked file.

Step 5: Stage the file

```bash
git add index.html
```

This moves the file to the staging area.

Step 6: Commit the file

```bash
git commit -m "Add index.html"
```

This saves the staged changes in Git’s history.

Step 7: View the commit history

```bash
git log
```

This displays the commits made so far.

Step 8: Connect our project to GitHub

```bash
git remote add origin <repository-url>
```

This links our local repository to a remote repository on GitHub.

Step 9: Rename the default branch to main

```bash
git branch -M main
```

Step 10: Push our project to GitHub for the first time

```bash
git push -u origin main
```

This uploads our project to GitHub and sets main as the default upstream branch.

A typical Git workflow is: initialize a repository, create and edit files, stage them, commit them, connect to GitHub, push our work, then repeatedly pull the latest changes, make updates, commit them, and push them back to GitHub.

To keep this guide simple and beginner-friendly, only the most essential Git commands are covered in detail. Additional commands used in the workflow are explained briefly where they are introduced.

## 7\. Git Workflow Visuals

### a. Git working directory → staging area → repository

![](https://cdn.hashnode.com/uploads/covers/699b471cf5291f20937649a4/a5c957b4-5052-4fd0-819d-a3633329e33a.png align="center")

### b. Local repository structure overview

![](https://cdn.hashnode.com/uploads/covers/699b471cf5291f20937649a4/7c679715-9e06-4640-a0ed-772ecca96da5.png align="center")

### c. Commit history flow

![](https://cdn.hashnode.com/uploads/covers/699b471cf5291f20937649a4/af3884e5-a3c1-4345-9293-ef594032611d.png align="center")

## 8\. Conclusion

Git is more than just a tool—it’s an essential skill that helps developers write code with confidence. By understanding concepts like repositories, commits, branches, and the basic Git workflow, we can keep our projects organized, track every important change, and collaborate with others more effectively.

If we’re just starting out, don’t worry about memorizing every Git command. Focus on understanding the workflow: create or modify files, check the status, stage your changes, commit them, and repeat. With regular practice, these steps will become second nature.

The best way to learn Git is by using it in our own projects. Start small, commit often, write meaningful commit messages. Every project we build will strengthen our Git skills and prepare us for real-world software development.


--

[⬆ Back to Top](#git-for-beginners-basics-and-essential-commands)