# Git Pre-commit Hooks

## What Is a Pre-commit Hook?

A **pre-commit hook** is a script that Git automatically executes **before a commit is created**.

Pre-commit hooks allow developers to run checks and validations before code enters the repository, helping catch issues early and maintain code quality.

If a pre-commit hook exits with a non-zero status code, Git cancels the commit.

---

## Why Use Pre-commit Hooks?

Pre-commit hooks help automate quality checks and prevent common mistakes.

### Common Uses

* Prevent committing broken code
* Enforce code formatting standards
* Run linters and static analysis tools
* Execute tests before committing
* Block sensitive information (API keys, passwords, secrets)
* Validate file naming conventions
* Ensure commit requirements are met

---

## How Git Hooks Work

Git stores hook scripts inside the `.git/hooks` directory.

```text
.git/
└── hooks/
    ├── pre-commit
    ├── pre-push
    ├── commit-msg
    └── ...
```

Each hook runs automatically when the corresponding Git event occurs.

---

## Creating a Pre-commit Hook

### 1. Navigate to the Hooks Directory

```bash
cd .git/hooks
```

### 2. Create or Edit the Pre-commit Script

```bash
nano pre-commit
```

### 3. Add a Simple Script

```bash
#!/bin/sh

echo "Running pre-commit checks..."
```

### 4. Make the Hook Executable

```bash
chmod +x pre-commit
```

The hook will now run automatically before every commit.

---

## Example: Block `.log` Files from Being Committed

The following hook prevents accidentally committing log files.

```bash
#!/bin/sh

if git diff --cached --name-only | grep "\.log$"; then
    echo "Error: .log files should not be committed."
    exit 1
fi
```

### How It Works

* `git diff --cached --name-only` lists staged files.
* `grep "\.log$"` searches for files ending in `.log`.
* `exit 1` stops the commit if a match is found.

---

## Example: Run Tests Before Committing

```bash
#!/bin/sh

npm test

if [ $? -ne 0 ]; then
    echo "Tests failed. Commit aborted."
    exit 1
fi
```

This prevents commits when tests fail.

---

## Skipping a Pre-commit Hook

In special cases, hooks can be bypassed:

```bash
git commit --no-verify
```

> ⚠️ Use this option carefully, as it skips all pre-commit checks.

---

## Common Git Hooks

| Hook          | When It Runs                          |
| ------------- | ------------------------------------- |
| `pre-commit`  | Before a commit is created            |
| `commit-msg`  | After entering a commit message       |
| `pre-push`    | Before pushing to a remote repository |
| `post-commit` | After a successful commit             |
| `post-merge`  | After a merge completes               |

---

## Best Practices

* Keep hooks fast and lightweight.
* Use hooks to automate repetitive checks.
* Avoid long-running tasks that slow development.
* Share hook configurations across the team using tools such as `pre-commit`, Husky, or custom scripts.
* Combine hooks with CI/CD pipelines for stronger validation.

---

## What I Learned

* Pre-commit hooks run automatically before each commit.
* Hooks can prevent bad code, secrets, or unwanted files from entering the repository.
* Hook scripts are stored in the `.git/hooks` directory.
* Hooks must be executable to run.
* Returning `exit 1` from a hook stops the commit.
* Hooks can be used to run tests, linters, formatters, and custom validation scripts.
* The `--no-verify` flag bypasses pre-commit hooks when necessary.

