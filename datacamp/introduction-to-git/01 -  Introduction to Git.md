# 01 -  Introduction to Git

## Checking Git version

```shell
git --version
```

---

## Saving files

### Repository

A **repository** or just **repo** is composed of:

- Files and directories that we create and edit.
- The extra information that Git records about the project's history in the folder called `.git` located in the main directory of the repo.

> IMPORTANT: Do not edit `.git` directory.

### Staging and committing

Saving a draft >> to >> **Staging area**

Save files/update the repo from the *staging area* all at once >> **Committing changes**

### Git workflow

- Modify a file
- Save the draft to the *staging area*
- Commit the updated file to the *repo*
- Repeat

### Saving a file

Adding a single file: `git add <a-file-name>`.

Adding all modified files: `git add .`.

- `.` = all files and directories in current location

Make a commit: `git commit -m "<commit-log-message>"`.

Check the status of the repo: `git status` that will show which files have changes are in the staging area or not.

---

## Comparing files

We can compare the last committed version of a file with the unstaged version by using the command:

```shell
git diff <a-file-name>
```

This will show as `--- a/<a-file-name>` and `+++ b/<a-file-name>` while `a` means the last one to be committed and `b` is the one that we have not added to the staging area.

`@@ -1,5 +1,5 @@` will represent the start line and the number of lines that are changed. `-1,5` means one line is removed at line 5. `+1,5` shows one line was added back in at line 5.

After we've already added the file to the staging area by `git add <a-file-name>`, we can compare by:

```shell
git diff -r HEAD <a-file-name>
```

- `-r <revision>` indicates to look at a particular revision of the file.
- `HEAD` is a shortcut for the most recent commit revision.

To sum, the above will show the difference between the file in the staging area and the version in the last commit (`HEAD`).

To show the difference between all files in the staging area:

```shell
git diff -r HEAD
```

### Recap

Compare an **unstaged** file with **the last committed** version:

```shell
git diff <a-file-name>
```

Compare an **staged** file with **the last committed** version:

```shell
git diff -r HEAD <a-file-name>
```

Compare **all unstaged and staged file** with **the last committed** versions:

```shell
git diff -r HEAD
```

---
