# Merging in Git

## What Is Merging?
Merging combines changes from one branch into another.

## Types of Merges
### Fast‑Forward
Happens when main hasn’t moved.  
`main` pointer simply moves forward.

### Three‑Way Merge
Used when both branches have new commits.  
Creates a merge commit.

## How To Merge
1. Switch to main  
   `git switch main`
2. Merge branch  
   `git merge feature/branching`

## Merge Conflicts
Conflicts happen when both branches edit the same lines.

Conflict markers:
<<<<<<< HEAD
main version
=======
branch version
>>>>>>> feature


Fix manually → `git add` → `git commit`.

## Screenshots
- `screenshots/branch-merge.png`
- `screenshots/merge-conflict.png`
- `screenshots/conflict-resolved.png`

## What I Learned
- Difference between fast‑forward and 3‑way merges  
- How to resolve conflicts  
- How Git marks conflict sections  


