## Create a folder locally
```bash
mkdir -p /Users/shaarav/Documents/<Folder>/.../<Folder>/PR<no.>
```

## Move to that folder
```bash
cd /Users/shaarav/Documents/<Folder>/.../<Folder>/PR<no.>
```

## Clone repo 
```
git clone <REPO_URL> .
```

## Fetch PR proposal as branch
```
git fetch origin pull/<no.>/head:pr-<no.>
```

## Quick way to check additions/ deletions/ changes
```
git checkout pr-<no.>
```

## 
```
git diff main..pr-<no.>
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

## AI Prompt
```
Review this PR completely.
Check for:
- security issues
- logic bugs
- race conditions
- unnecessary complexity
- bad architecture
- code smells
- missing validations
- performance issues
(OR)
Analyze pr14.diff and summarize:
- all functional changes
- potential bugs
- security concerns
- architectural impacts
- whether the PR should be approved
```

## Delete branch (if needed)
```
git branch -D pr-<no.>
```
