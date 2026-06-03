# Git Cherry-pick

## What Is Git Cherry-pick?

`git cherry-pick` allows you to take a **specific commit from one branch** and apply it onto another branch.

Instead of merging an entire branch, cherry-pick lets you selectively copy individual commits.

### When to Use Cherry-pick

* You need a **hotfix** from another branch on `main`
* You want to apply a **single feature or fix** without merging everything
* You need a **specific commit** from an experimental or long-running branch
* You want to avoid bringing in unrelated commits or history

---

## How Cherry-pick Works

When you cherry-pick a commit, Git:

1. Takes the changes introduced by that commit
2. Applies them to your current branch
3. Creates a **new commit with a new hash**

The original commit remains unchanged in its original branch.

---

## Step-by-Step: Using Cherry-pick

### 1. Find the Commit Hash

Use `git log` to locate the commit you want:

```bash id="k3h9p2"
git log --oneline
```

### Example Output

```text id="m7xq21"
a1b2c3d Fix login bug
9f8e7d6 Add login form
```

Copy the commit hash (e.g., `a1b2c3d`).

---

### 2. Switch to the Target Branch

Move to the branch where you want to apply the commit:

```bash id="q8w1n4"
git switch main
```

---

### 3. Cherry-pick the Commit

Apply the selected commit:

```bash id="z2p9c5"
git cherry-pick a1b2c3d
```

Git will replay the changes and create a new commit on the current branch.

---

## Handling Conflicts

Conflicts may occur if the same parts of files were changed in both branches.

### Example Conflict Marker

```text id="c1v8t0"
<<<<<<< HEAD
current branch version
=======
cherry-picked commit version
>>>>>>> a1b2c3d
```

---

### How to Resolve Conflicts

1. Open the conflicting file
2. Choose or combine the correct changes
3. Remove conflict markers
4. Stage the resolved file:

```bash id="r4k2d7"
git add <file>
```

5. Continue the cherry-pick:

```bash id="t9y3m6"
git cherry-pick --continue
```

---

## Aborting a Cherry-pick

If something goes wrong or you change your mind:

```bash id="x6n8s1"
git cherry-pick --abort
```

This restores your branch to its state before the cherry-pick began.

---

## Common Cherry-pick Commands

| Command                      | Purpose                            |
| ---------------------------- | ---------------------------------- |
| `git cherry-pick <hash>`     | Apply a specific commit            |
| `git cherry-pick --continue` | Continue after resolving conflicts |
| `git cherry-pick --abort`    | Cancel the operation               |
| `git log --oneline`          | Find commit hashes                 |

---

## Cherry-pick vs Merge

| Cherry-pick             | Merge                  |
| ----------------------- | ---------------------- |
| Copies specific commits | Combines entire branch |
| Creates new commit      | Preserves full history |
| Selective changes       | All changes included   |
| More controlled         | More automatic         |

---

## What I Learned

* Cherry-pick applies specific commits to another branch.
* It creates a new commit with a new hash.
* `git log --oneline` helps find commit IDs.
* Conflicts can happen and must be resolved manually.
* `--continue` resumes and `--abort` cancels the operation.
* Cherry-pick is useful for hotfixes and selective changes.
