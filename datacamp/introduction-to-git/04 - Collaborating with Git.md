# 04 - Collaborating with Git

## Creating repos

### Benefit of repos

- Systematically track versions
- Collaborate with colleagues
- Git stores everything!

### Creating a new repo

```shell
git init <a-new-subdir-name-in-current-dir>
cd <a-new-subdir-name-in-current-dir>
git status
```

### Converting a project

```shell
cd <an-exting-project-dir>
git init
git status

# You can see Git has immediately recognized that there are modified files, so we encouraged to add our files to the staging area and make a commit!
```

### Nested repositories

- Do not create a Git repo inside another Git repo.
  - Known as **nested repos**.

- There will be two `.git` directories.
  - When we try to make commits. Git will get confused about which directory it needs to update.

- Generally, **nested repo** is not necessary except when working on extremely large and complex data projects!

---

## Working with remotes

A **remote repo** is a repo stored in the cloud through an online repo hosting service such as GitHub.

### Benefits of remote repos

- Everything is backed up
- Collaboration, regardless of location

### Cloning locally

```shell
git clone <path-to-source-project-dir>

# Example
git clone /home/john/repo

git clone <path-to-source-project-dir> <a-new-subdir-name>

# Example
git clone /home/john/repo new_repo
```

### Cloning a remote

```shell
git clone [URL]

# Example
git clone https://github.com/datacamp/project
```

### Identifying a remote

- When cloning a repo
  - Git remembers where the original was
- Git stores a remote tag in the new repo's configuration

```shell
# To list all remote names in the current repo
git remote

# To get more information about each remote while listing: -v = verbose
git remote -v
```

### Creating a remote

When cloning, Git will automatically name the remote `origin`

```shell
git remote add <a-new-remote-name> [URL]

# Example
git remote add george https://github.com/george_datacamp/repo
```

Defining remote names is useful for merging branches as a shortcut.

---

## Gathering from a remote

### Fetching from a remote

If you are not sure how the contents of a remote repo compare to your local repo, then you can gather the remote contents from a specific branch and then compare them to your local branch.

To compare the files in a remote against the contents of a local repo, we first need to fetch versions from the remote by:

```shell
git fetch <remote-name> <local-branch-name-to-fetch-into>

# Example
git fetch origin main
```

And then compare it by:

```shell
git diff main origin

# or

git diff origin main
```

### Synchronizing content

After fetching, we now have the contents of the remote in our local repo.

However, we still need to synchronize contents between the two repos. To do this, we need to merge the remote into the local repo's branch, where we currently located.

```shell
git merge <remote-name> <local-branch-name-to-fetch-into>

# Example
git merge origin main

# NOTE: Fast-forward merged means the local repo was behind the remote and this merge aligned it.
```

### Pulling from a remote

Pull from remote = Fetch from remote + Merge from remote

To simplify the process, Git allows us to `fetch` and `merge` using a single command `pull`.

```shell
git pull <remote-name> <local-branch-name-to-fetch-into>

# Example
git pull origin main
```

### Pulling with unsaved local changes

If we have been working locally and not yet committed our changes, then Git won't allow us to pull from a remote.

So, it is important to commit locally before pulling from a `remote`.

---

## Pushing to a remote

To bring our local changes into a remote repo:

> NOTE: As pulling contents from a remote, we need to commit local changes before we can push to the remote.

```shell
git push <remote-name> <local-branch>

# Example
git push origin main
```

---
