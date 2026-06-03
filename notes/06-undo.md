# Undoing Changes in Git

## What Does "Undo" Mean in Git?

Git provides several ways to undo changes, depending on where those changes exist in the workflow:

* **Unstaged changes** (working directory)
* **Staged changes** (staging area)
* **Local commits** (not yet pushed)
* **Shared commits** (already pushed)

Understanding the difference is important because each scenario requires a different command.

---

## Undo Unstaged Changes

If you've modified a file but haven't staged it yet, you can discard those changes and restore the file to its last committed state.

### Undo Changes in a Specific File

```bash
git restore <file>
```

### Undo All Unstaged Changes

```bash
git restore .
```

> ⚠️ This permanently removes uncommitted changes from your working directory.

---

## Undo Staged Changes

If you've already added files to the staging area using `git add`, you can move them back to the unstaged state without losing the actual changes.

### Unstage a Specific File

```bash
git restore --staged <file>
```

The file remains modified, but it is no longer staged for commit.

---

## Undo the Last Commit (Keep Changes)

If you created a commit too early but want to keep all your work, use a soft reset.

```bash
git reset --soft HEAD~1
```

This command:

* Removes the most recent commit
* Keeps all changes intact
* Returns the changes to the staging area

---

## Undo the Last Commit (Discard Changes)

If you want to completely remove the most recent commit and all associated changes:

```bash
git reset --hard HEAD~1
```

This command:

* Removes the latest commit
* Deletes all changes from that commit
* Resets the working directory

> ⚠️ Use with caution. Discarded changes cannot be easily recovered.

---

## Undo a Commit That Has Already Been Pushed

For commits that have been shared with others, use `git revert` instead of `git reset`.

```bash
git revert <commit-hash>
```

This command:

* Creates a new commit
* Reverses the changes introduced by the specified commit
* Preserves project history
* Is safe for shared branches

---

## Quick Reference

| Situation                         | Command                       |
| --------------------------------- | ----------------------------- |
| Undo changes in a file            | `git restore <file>`          |
| Undo all unstaged changes         | `git restore .`               |
| Unstage a file                    | `git restore --staged <file>` |
| Undo last commit, keep changes    | `git reset --soft HEAD~1`     |
| Undo last commit, discard changes | `git reset --hard HEAD~1`     |
| Undo a pushed commit              | `git revert <commit-hash>`    |

---

## What I Learned

* `git restore` is used to undo file changes and unstage files.
* `git reset --soft` removes commits while preserving changes.
* `git reset --hard` removes both commits and changes.
* `git revert` safely undoes commits that have already been pushed.
* The correct undo command depends on the stage of the Git workflow where the change exists.
