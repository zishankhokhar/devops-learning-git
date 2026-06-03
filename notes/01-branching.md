# Branching in Git

## What Is a Branch?
A branch is a separate line of development used to work on features or fixes without affecting `main`.

## Why Branching Is Useful
- Keeps `main` stable  
- Lets multiple people work in parallel  
- Isolates changes until they’re ready  
- Supports clean workflows  

## Key Commands
- `git branch` — list branches  
- `git checkout -b <name>` — create + switch  
- `git switch <name>` — switch branches  
- `git merge <branch>` — merge into current branch  

## Typical Workflow
1. Create branch  
   `git checkout -b feature/branching`
2. Make changes + commit  
3. Switch to main  
   `git switch main`
4. Merge  
   `git merge feature/branching`

## Branch Naming Tips
- `feature/<name>` for new features  
- `bugfix/<name>` for fixes  
- `hotfix/<name>` for urgent production issues
These conventions help teams stay organised and consistent.

## Screenshot
See: `screenshots/branch-creation.png`  
(Shows creating and listing branches with `git branch`.)

## What I Learned
- How to create/switch branches  
- Why branches isolate work  
- How merging brings work back to main  
- How remote branches are pushed, tracked, and deleted

