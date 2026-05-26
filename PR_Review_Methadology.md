## Create a folder locally
```
mkdir -p /Users/shaarav/Documents/<Folder>/.../<Folder>/PR<no.>
```

## Move to that folder
```
cd /Users/shaarav/Documents/<Folder>/.../<Folder>/PR<no.>
```

## Clone repo 
```
git clone <REPO_URL> .
```

## Fetch PR proposal as branch/ pull latest PR updates
```
git fetch origin pull/<no.>/head:pr-<no.>
```

## Switches working directory to branch
```
git checkout pr-<no.>
```

### NOTE (during PR update)
You cannot update branch pr-<no.>
while actively standing inside pr-<no.>
Therefore, follow the below steps
```
git checkout main
git fetch origin pull/<no.>/head:pr-<no.>
git checkout pr-<no.>
git reset --hard FETCH_HEAD
```
Ensure your main doesn't get the PR branch update and if it happens by mistake, then:
```
git checkout main
git reset --hard origin/main
```

## Reset PR to latest PR state (only when PR gets updated)
```
git reset --hard FETCH_HEAD
```

## See new commits or the files that changed
```
git log --oneline main..pr-<no.>
```

## Quick way to check additions/ deletions/ changes (compare)
```
git diff main..pr-<no.>
```

## Creates a file to store the comparison
```
git diff main..pr-<no.>  >  pr<no.>.diff
```

## Open Antigravity IDE
```
open -a "Antigravity" .
```

## Open Visual Studio Code IDE
```
open -a "Visual Studio Code" .
```

## Open Cursor IDE
```
open -a "Cursor" .
```

## Open Codex IDE
```
open -a "Codex" .
```

## AI Prompt Template
```
Review this PR completely. Analyze pr<no.>.<v.>.diff file.

Check for:
- all functional changes
- security issues
- logic bugs
- race conditions
- unnecessary complexity
- bad architecture
- code smells
- missing validations
- performance issues
- architecture impacts

Decide whether the PR should be approved. (I don't want to keep the contributor waiting for very long, you may ignore silly issues)
(This is the PR message provided:)
(Avoid reviewing things other than what this PR is meant for.)
```

## Delete branch (if needed)
```
git branch -D pr-<no.>
```
