# Setting Up Git Hooks

## Introduction

Git hooks are scripts that Git executes before or after specific events, providing an opportunity to customize and automate your Git workflow. This guide covers the basics of setting up Git hooks and provides examples of common use cases.

## Types of Git Hooks

1. **Pre-Commit Hook:**
   - Executes before a commit is created.
   - Useful for running code formatting checks or linting.

2. **Pre-Rebase Hook:**
   - Executes before a branch is rebased.
   - Helpful for ensuring a clean working directory before rebasing.

3. **Post-Merge Hook:**
   - Executes after a successful merge.
   - Useful for triggering additional actions after a merge.

## Setting Up a Git Hook

1. **Navigate to Your Git Repository:**
   ```bash
   cd path/to/your/repository
   ```

2. **Navigate to the `.git/hooks` Directory:**
   ```bash
   cd .git/hooks
   ```

3. **Create or Edit the Hook Script:**
   - For a pre-commit hook, create/edit the `pre-commit` file.
   - For a pre-rebase hook, create/edit the `pre-rebase` file.
   - For a post-merge hook, create/edit the `post-merge` file.

4. **Make the Hook Script Executable:**
   ```bash
   chmod +x pre-commit
   ```

5. **Edit the Hook Script with Custom Actions:**
   - Add the desired actions using your preferred scripting language (bash, python, etc.).

### Example Pre-Commit Hook (pre-commit)

```bash
#!/bin/bash

# Example: Run code formatting check before committing
echo "Running code formatting check..."
make format
```

### Example Pre-Rebase Hook (pre-rebase)

```bash
#!/bin/bash

# Example: Check for uncommitted changes before rebasing
if [ -n "$(git status --porcelain)" ]; then
    echo "Error: Uncommitted changes found. Please commit or stash changes before rebasing."
    exit 1
fi
```

### Example Post-Merge Hook (post-merge)

```bash
#!/bin/bash

# Example: Trigger additional actions after a successful merge
echo "Running post-merge actions..."
make update
```

## Conclusion

Setting up Git hooks allows you to customize your Git workflow by automating tasks at key points in the version control process. Explore additional hook types and tailor them to your specific project requirements.
