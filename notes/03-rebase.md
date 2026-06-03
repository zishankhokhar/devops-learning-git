# Git Rebase

## What Is Git Rebase?

`git rebase` integrates changes from one branch into another by **replaying your commits on top of the latest version of the target branch** (commonly `main`).

Unlike a merge, rebase creates a **linear commit history**, making the project's timeline cleaner and easier to follow.

### Example

Before rebasing:

```text
main:     A ── B ── C
                 \
feature:          D ── E
```

After rebasing `feature` onto `main`:

```text
main:     A ── B ── C
                       \
feature:                D' ── E'
```

Your commits are replayed on top of the latest commit from `main`.

---

## Why Use Rebase?

* Keeps commit history clean and linear
* Avoids unnecessary merge commits
* Makes feature branches appear up-to-date
* Simplifies project history and log inspection
* Produces cleaner pull requests

---

## Basic Rebase Workflow

### 1. Switch to Your Feature Branch

git switch feature/rebase

### 2. Rebase Onto the Latest Main Branch

git rebase main

Git takes your branch's commits and reapplies them on top of the current `main` branch.

---

## Handling Rebase Conflicts

Sometimes Git cannot automatically apply a commit because changes conflict with those in the target branch.

Example conflict markers:

```text
<<<<<<< HEAD
main version
=======
feature version
>>>>>>> commit
```

### Resolve the Conflict

1. Open the file and choose the correct code.
2. Remove the conflict markers.
3. Save the file.

### Stage the Resolved File

git add <file>

### Continue the Rebase

git rebase --continue

Git will continue replaying the remaining commits.

---

## Aborting a Rebase

If you decide not to continue or something goes wrong:

git rebase --abort

This restores your branch to the state it was in before the rebase started.

---

## Updating a Remote Branch After Rebasing

Because rebase rewrites commit history, the rebased branch will have different commit IDs.

If the branch has already been pushed to a remote repository, update it with:

git push --force-with-lease


### Why Use `--force-with-lease`?

It is safer than `--force` because Git checks whether someone else has pushed changes before overwriting the remote branch.

---

## Rebase vs Merge

| Rebase                          | Merge                             |
| ------------------------------- | --------------------------------- |
| Creates a linear history        | Creates a merge commit            |
| Rewrites commit history         | Preserves commit history          |
| Cleaner project log             | Shows exact branch structure      |
| Often used for feature branches | Commonly used for shared branches |

---

## Common Rebase Commands

| Command                       | Purpose                               |
| ----------------------------- | ------------------------------------- |
| `git rebase main`             | Rebase current branch onto `main`     |
| `git rebase --continue`       | Continue after resolving conflicts    |
| `git rebase --abort`          | Cancel the rebase                     |
| `git rebase -i HEAD~3`        | Interactively edit the last 3 commits |
| `git push --force-with-lease` | Update remote after a rebase          |

---

## What I Learned

* `git rebase` replays commits on top of another branch.
* Rebasing creates a clean, linear project history.
* Conflicts may occur and must be resolved manually.
* `git rebase --continue` resumes a paused rebase.
* `git rebase --abort` cancels the rebase process.
* Rebasing changes commit history, so a force push may be required afterward.
* `git push --force-with-lease` is the preferred way to update a remote branch after rebasing.
