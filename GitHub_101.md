# Git & GitHub Essentials: The Concepts You Must Know

Think of Git as a **time machine + collaboration system** for code.

---

# 1. Repository (Repo)

A repository is your project and its complete history.

Example:

```text
MyProject/
├── src/
├── README.md
└── .git/
```

The `.git` folder stores all commits, branches, and history.

---

# 2. Working Directory

The files you are currently editing.

```text
main.py
README.md
index.html
```

When you modify a file, the change exists only in your working directory.

---

# 3. Staging Area (Index)

A temporary area where you choose what goes into the next commit.

```bash
git add main.py
```

Now Git knows:

> "Include this file in the next snapshot."

---

# 4. Commit

A commit is a snapshot of your project at a specific point in time.

```bash
git commit -m "Add login page"
```

Creates something like:

```text
A → B → C
```

where:

- A = Initial commit
- B = Added README
- C = Added login page

Each commit has a unique hash.

---

# 5. Branch

A branch is an independent line of development.

```text
main
  A → B → C

feature-login
  A → B → C → D
```

You can experiment without affecting `main`.

Create:

```bash
git checkout -b feature-login
```

---

# 6. Main Branch

`main` is usually the primary branch.

```text
main
A → B → C
```

When PRs are merged, they typically go into `main`.

Historically this was called `master`.

---

# 7. HEAD

One of the most important concepts.

`HEAD` is simply:

> "Where am I currently?"

Example:

```text
main
A → B → C
          ↑
        HEAD
```

You are currently on commit C.

If you switch branches:

```bash
git checkout feature-login
```

then:

```text
feature-login
A → B → C → D
              ↑
            HEAD
```

HEAD always points to your current branch/commit.

---

# 8. Checkout

Move to another branch or commit.

```bash
git checkout main
```

or

```bash
git checkout feature-login
```

HEAD moves with it.

---

# 9. Origin

`origin` is just a nickname.

Usually it refers to:

> Your GitHub repository.

Example:

```text
https://github.com/username/project.git
```

Git stores it as:

```text
origin
```

Check:

```bash
git remote -v
```

Example:

```text
origin  https://github.com/username/project.git
```

---

# 10. Upstream

In open source:

```text
Original Repo
      ↑
   upstream

Your Fork
      ↑
    origin
```

Example:

```text
upstream = organization/project
origin   = yourusername/project
```

---

# 11. Fetch

Downloads changes from a remote repository.

```bash
git fetch origin
```

or

```bash
git fetch upstream
```

## What it does

Downloads commits.

## What it does NOT do

Does not modify your files.

Example:

Before:

```text
Local Main
A → B

Origin Main
A → B → C
```

After:

```bash
git fetch origin
```

Git knows commit C exists, but your branch stays:

```text
Local Main
A → B
```

---

# 12. Pull

Fetch + Merge

```bash
git pull origin main
```

Equivalent to:

```bash
git fetch origin
git merge origin/main
```

Updates your local branch.

Before:

```text
Local Main
A → B

Origin Main
A → B → C
```

After:

```text
Local Main
A → B → C
```

---

# 13. Push

Upload your commits to GitHub.

Before:

```text
Local
A → B → C

GitHub
A → B
```

Run:

```bash
git push origin main
```

After:

```text
GitHub
A → B → C
```

---

# 14. Add

Stages files.

```bash
git add file.py
```

or

```bash
git add .
```

Workflow:

```text
Working Directory
       ↓
   git add
       ↓
 Staging Area
```

---

# 15. Status

Most-used command.

```bash
git status
```

Shows:

- Modified files
- Staged files
- Current branch

Example:

```text
modified: app.py
new file: login.py
```

---

# 16. Merge

Combines branches.

Before:

```text
main
A → B

feature
A → B → C
```

Run:

```bash
git checkout main
git merge feature
```

After:

```text
main
A → B → C
```

---

# 17. Rebase

Moves your work onto a newer base.

Before:

```text
main
A → B → C

feature
A → B → D
```

Run:

```bash
git rebase main
```

After:

```text
main
A → B → C

feature
A → B → C → D'
```

Creates cleaner history than merge.

---

# 18. Fork

Creates your own copy of someone else's repository on GitHub.

```text
Original Repo
       ↓
      Fork
       ↓
 Your Repo
```

Common in open source.

---

# 19. Pull Request (PR)

A request to merge code.

```text
feature branch
      ↓
      PR
      ↓
main branch
```

Maintainers review your code before merging.

---

# 20. Merge Commit

When a PR is merged, Git may create:

```text
A → B → C
         \
          D
         /
        M
```

`M` is the merge commit.

---

# 21. Squash Merge

Instead of:

```text
feature
D → E → F
```

Git combines everything into:

```text
main
A → B → C → G
```

One clean commit (`G`).

Common in open source projects.

---

# 22. Clone

Download a repository.

```bash
git clone https://github.com/user/repo.git
```

Creates:

```text
repo/
```

on your machine.

---

# 23. The Complete Workflow

```text
Edit files
    ↓
git add .
    ↓
git commit -m "message"
    ↓
git push origin feature-branch
    ↓
Create PR
    ↓
Review
    ↓
Merge
```

---

# Git Architecture

```text
                GitHub / Remote Repository
                           ▲
                           │
                     git push
                           │
                           ▼
                Local Repository (.git)
                           ▲
                           │
                     git commit
                           │
                           ▼
                    Staging Area
                           ▲
                           │
                      git add
                           │
                           ▼
                  Working Directory
```

---

# Local vs Remote Branches

```text
Local:
main
feature-login

Remote:
origin/main
origin/feature-login

Original Repo:
upstream/main
```

---

# Understanding HEAD

```text
main
A → B → C
          ↑
        HEAD
```

HEAD points to your current location.

If you switch branches:

```bash
git checkout feature
```

HEAD moves to that branch.

---

# Understanding Origin vs Upstream

```text
                    Original Repository
                           │
                      upstream
                           │
                           ▼

                    Your GitHub Fork
                           │
                        origin
                           │
                           ▼

                    Your Computer
```

Typical setup:

```bash
git remote -v
```

Output:

```text
origin    https://github.com/yourname/project.git
upstream  https://github.com/org/project.git
```

---

# Fetch vs Pull

## Fetch

```bash
git fetch upstream
```

Downloads changes only.

```text
Safe
No file changes
No merge
```

## Pull

```bash
git pull upstream main
```

Downloads and updates your branch.

Equivalent to:

```bash
git fetch upstream
git merge upstream/main
```

---

# Common Open Source Workflow

## One-time setup

```bash
git clone https://github.com/yourname/project.git

cd project

git remote add upstream https://github.com/org/project.git
```

Verify:

```bash
git remote -v
```

---

## Sync your fork

```bash
git checkout main

git fetch upstream

git pull upstream main

git push origin main
```

---

## Create a feature branch

```bash
git checkout -b fix-navbar-bug
```

---

## Make changes

```bash
git add .

git commit -m "Fix navbar alignment issue"
```

---

## Push branch

```bash
git push origin fix-navbar-bug
```

---

## Create Pull Request

```text
fix-navbar-bug
      ↓
Create PR
      ↓
Review
      ↓
Merge
```

---

# Rebase vs Merge

## Merge

```text
A → B → C
     \
      D → E
           \
            M
```

Preserves history.

Command:

```bash
git merge main
```

---

## Rebase

```text
A → B → C → D' → E'
```

Rewrites history into a straight line.

Command:

```bash
git rebase main
```

---

# Useful Commands Cheat Sheet

## Check status

```bash
git status
```

## See remotes

```bash
git remote -v
```

## View branches

```bash
git branch
```

## Create branch

```bash
git checkout -b feature
```

## Switch branch

```bash
git checkout main
```

## Stage files

```bash
git add .
```

## Commit changes

```bash
git commit -m "message"
```

## Push

```bash
git push origin branch-name
```

## Fetch

```bash
git fetch upstream
```

## Pull

```bash
git pull upstream main
```

## Merge

```bash
git merge branch-name
```

## Rebase

```bash
git rebase main
```

## Clone repository

```bash
git clone <repository-url>
```

---

# The 10 Concepts Every Open Source Contributor Must Master

1. Repository
2. Branch
3. Commit
4. HEAD
5. Origin
6. Upstream
7. Add
8. Push
9. Fetch / Pull
10. Pull Request

Once these concepts click, most Git and GitHub workflows become straightforward and predictable.
