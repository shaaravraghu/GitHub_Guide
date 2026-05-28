# PR Creation Methodology

---

# Quick Workflow Summary

```bash
mkdir <folder_name>
cd ../<folder_name>

git clone <fork-url>

git remote add upstream <original-repo>

git checkout -b <branch-name>

# make changes

git add .
git commit -m "message"

git push origin <branch-name>
```

---

````md
## Create a folder locally
```bash
mkdir -p /Users/shaarav/Documents/<Folder>/.../<Folder>/<Project>
````

## Move to that folder

```bash
cd /Users/shaarav/Documents/<Folder>/.../<Folder>/<Project>
```

## Fork the repository

* Open GitHub
* Click **Fork**
* Fork into your own account

---

## Clone your fork

```bash
git clone <YOUR_FORK_URL>
```

## Move into repository

```bash
cd <repo-name>
```

## Add upstream remote

```bash
git remote add upstream <ORIGINAL_REPO_URL>
```

## Verify remotes

```bash
git remote -v
```

Expected:

```bash
origin    <YOUR_FORK_URL>
upstream  <ORIGINAL_REPO_URL>
```

---

# Sync Fork With Main Repository

## Fetch latest upstream changes

```bash
git fetch upstream
```

## Switch to main branch

```bash
git checkout main
```

## Reset local main to upstream

```bash
git reset --hard upstream/main
```

## Push updated main to your fork

```bash
git push origin main --force
```

---

# Create Feature Branch

## Create new branch

```bash
git checkout -b <feature-branch-name>
```

Examples:

```bash
git checkout -b fix-auth-race-condition
git checkout -b improve-logging
git checkout -b add-rate-limiter
```

---

# Make Changes

## Open Antigravity IDE

```bash
open -a "Antigravity" .
```

## Open Visual Studio Code IDE

```bash
open -a "Visual Studio Code" .
```

## Open Cursor IDE

```bash
open -a "Cursor" .
```

## Open Codex IDE

```bash
open -a "Codex" .
```

---

# Before Committing

## See changed files

```bash
git status
```

## See exact changes

```bash
git diff
```

## Review staged changes

```bash
git diff --staged
```

## Run tests

```bash
<project-test-command>
```

Examples:

```bash
npm test
cargo test
pytest
pnpm test
```

---

# Commit Changes

## Stage files

```bash
git add .
```

OR specific files:

```bash
git add <file-name>
```

## Commit changes

```bash
git commit -m "<commit-message>"
```

Good examples:

```bash
git commit -m "Fix race condition in websocket handler"
git commit -m "Improve MongoDB reconnection logic"
git commit -m "Add validation for empty API keys"
```

Avoid:

```bash
git commit -m "fix"
git commit -m "changes"
git commit -m "update"
```

---

# Push Branch

## Push branch to your fork

```bash
git push origin <feature-branch-name>
```

---

# Create Pull Request

## Open GitHub

* Navigate to your fork
* Click **Compare & Pull Request**

## PR Title Rules

Use clear titles:

```text
Fix websocket memory leak
Add retry logic for failed requests
Improve error handling in auth middleware
```

Avoid:

```text
Fixed stuff
Changes made
Update
```

---

# PR Description Template

```md
## What does this PR do?
- 

## Why is this needed?
- 

## Changes made
- 
- 
- 

## Testing done
- 

## Screenshots / Recordings (if applicable)
- 

## Checklist
- [ ] Code builds successfully
- [ ] Tests pass
- [ ] No unnecessary files added
- [ ] Documentation updated if needed
- [ ] PR is focused on one issue only
```

---

# Keep PR Updated With Latest Main

## Fetch upstream

```bash
git fetch upstream
```

## Switch to main

```bash
git checkout main
```

## Reset main

```bash
git reset --hard upstream/main
```

## Return to feature branch

```bash
git checkout <feature-branch-name>
```

## Rebase branch onto latest main

```bash
git rebase main
```

If conflicts happen:

```bash
git status
```

Resolve conflicts manually, then:

```bash
git add .
git rebase --continue
```

---

# Update Existing PR

## Push rebased changes

```bash
git push origin <feature-branch-name> --force
```

---

# Clean Up After Merge

## Switch to main

```bash
git checkout main
```

## Delete local branch

```bash
git branch -D <feature-branch-name>
```

## Delete remote branch

```bash
git push origin --delete <feature-branch-name>
```

---

# Important Contributor Rules

* Keep PRs focused on ONE issue/problem
* Avoid unrelated formatting changes
* Avoid huge PRs unless necessary
* Test before opening PR
* Re-read changed code before pushing
* Keep commit messages meaningful
* Respond to review comments properly
* Never commit secrets/API keys/.env files
* Avoid AI-generated code without reviewing it carefully
* Prefer clarity over over-engineering

---

# Helpful Git Commands

## Show branch graph

```bash
git log --oneline --graph --all
```

## Show commit history

```bash
git log --oneline
```

## Undo latest commit (keep changes)

```bash
git reset --soft HEAD~1
```

## Undo latest commit (delete changes)

```bash
git reset --hard HEAD~1
```

## Remove untracked files

```bash
git clean -fd
```

## Abort rebase

```bash
git rebase --abort
```

## Abort merge

```bash
git merge --abort
```

```
```
