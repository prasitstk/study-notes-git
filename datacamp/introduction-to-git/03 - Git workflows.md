# 03 - Git workflows

## Configuring Git

To access the list of customizable settings:

```shell
git config --list
```

Git has three levels of settings:

1. `--local`: settings for one specific project
2. `--global`: settings for all of our projects in the current system user
3. `--system`: settings for every users on this computer

Setting Level: `--local` settings >> overrides >> `--global` settings >> overrides >> `--system`.

### Changing our settings

```shell
git config --global setting value

# For example, change email address to xxx@email.com
git config --global user.email xxx@email.com

# For example, change username to John Smith
git config --global user.name 'John Smith'
```

### Using an alias

- Set up an alias thorugh global settings
- Typically used to shorten a command

To create an alias for committing files by executing `ci`:

```shell
git config --global alias.ci 'commit -m'
```

- We can now commit files by executing:

  ```shell
  git ci
  ```

To create an alias to unstage files:

```shell
git config --global alias.unstage 'reset HEAD'
```

> IMPORTANT: Be careful not to overwrite existing commands!

### Tracking aliases

Git helps us track our aliases by storing them in a `.gitconfig` file by:

```shell
git config --global --list

# Result:
# alias.ci=commit -m
# alias.unstage=reset HEAD
```

### Ignoring specific files

Create `.gitignore` file in the repo.

- `*` = Wildcard

---

## Branches

Git uses **branches** to systematically track multiple versions of files.

### Source and destination

When merging two branches:

- the commits are called parent commits
- `source`: the branch we want to merge `from`
- `destination`: the branch we want to merge `into`

Identify branches by: `git branch`

- `*` = current branch

Creating a new branch by: `git checkout -b new-branch-name`.

Compare the differences between two branches by: `git diff branch1 branch2`.

### How do we switch branches?

```shell
git checkout target-branch-name
```

> NOTE: Omit `-b` flag compared to create a new branch: `git checkout -b new-branch-name`.

### Merging branches

```shell
git merge source-branch-name destination-branch-name
```

> NOTE: Fast-forward merge = additional commits were made on the source branch, Git brings the destination branch up to date

---

## Handling conflict

### What is a conflict?

Sometimes, we will experience what Git calls a conflict.

A conflict occurs when a file in different branches has different contents that prevent them from automatically **merging** into a single version.

### Attempting to merge a conflict

```shell
# Current branch is `main` and try to merge `update` branch into `main` branch
git merge update main

# Result:
# CONFLICT (add/add): Merge conflict in todo.txt
# Auto-merging todo.txt
# Automatic merge failed; fix conflicts and then commit the result.
```

So, follow Git's advice and resolve the conflict.

```shell
nano todo.txt
# Save the modified file, which no longer contains any of the Git conflict syntax.
```

Then, add the updated file to the staging area and then commit it to the `main` branch.

```shell
# Use `git add <file>` to mark resolution
git add todo.txt
git commit -m "Resolving todo.txt conflict"
```

Finally, try to merge `update` into `main` branch again.

```shell
git merge update main

# Result
# Already up to date.
```

### How do we avoid conflicts?

- Prevention is better than cure
- Use each branch for a specific task
- Avoid editing a file in multiple braches
- Doesn't guarantee we'll avoid conflicts, but it does reduce the risk.

---
