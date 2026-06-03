# Git Stash

## What Is Git Stash?

`git stash` allows you to temporarily save **uncommitted changes** without creating a commit. This is useful when you need to switch branches or work on something else before finishing your current task.

Think of it as putting your unfinished work into a temporary storage area and restoring it later.

---

## Why Use Git Stash?

* Pause work without making a commit
* Switch branches quickly
* Handle urgent bug fixes
* Keep commit history clean and meaningful
* Save work in progress safely

---

## Basic Stash Workflow

### Save Your Changes

git stash

This stores your modified tracked files and reverts your working directory to a clean state.

### View Saved Stashes

git stash list

Displays all saved stash entries.

### Restore Your Changes

Apply the latest stash and remove it from the stash list:

git stash pop


Apply the latest stash but keep it in the stash list:

git stash apply

---

## Stash with a Custom Message

Adding a message makes it easier to identify saved work later.


git stash push -m "WIP: login feature

Example output in `git stash list`:

stash@{0}: On main: WIP: login feature

---

## Remove Stashes

### Remove the Most Recent Stash

git stash drop

### Remove a Specific Stash

git stash drop stash@{1}

### Remove All Stashes

git stash clear

---

## What I Learned

* `git stash` temporarily saves uncommitted changes.
* `git stash pop` restores changes and removes the stash entry.
* `git stash apply` restores changes while keeping the stash entry.
* Custom messages make stashes easier to manage.
* Stashing is a quick and effective way to switch tasks without committing unfinished work.

