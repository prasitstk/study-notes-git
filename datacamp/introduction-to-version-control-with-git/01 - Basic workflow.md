# 01 - Basic workflow

## Which of the following does Git do?

- Keep track of changes to files.

- Notice conflicts between changes made by different people.

- Synchronize files between different computers.

---

## Where does Git store information?

A **repository** is composed of:

1. The files and directories that you create and edit directly
2. The extra information that Git records about the project's history

**Git** stores all of its extra information in **a directory** called `.git` located in **the root directory of the repository**. Git expects this information to be laid out in a very precise way, so you should **NEVER edit or delete anything in `.git`**.

---

## How can I check the state/status of a repository?

By `git status`.

When you are using Git, you will frequently want to **check the status of your repository**.

To do this, run the command `git status`, which **displays a list of the files that have been modified since the last time changes were saved**.

---

## How can I tell what I have changed?

By `git status`, `git diff filename`, `git diff`, and `git diff directory`

Git has **a staging area** in which it stores **files with changes you want to save that haven't been saved yet** (before **committing**).

Putting files in **the staging area** is like putting things in a box, while **committing** those changes is like putting that box in the mail: you can add more things to the box or take things out as often as you want, but once you put it in the mail, you **can't make further changes**.

![staging-area](images/staging-area.png)

`git status` shows you **which files are in this staging area**, and **which files have changes that haven't yet been put there**.

`git diff filename` compares the file as it currently is to what you last saved.

`git diff` without any filenames will show you all the changes in your repository.

`git diff directory` will show you the changes to the files in some directory.

---

## What is in a diff?

A `diff` is a formatted display of the differences between two sets of files. Git displays diffs like this:

```shell
diff --git a/report.txt b/report.txt
index e713b17..4c0742a 100644
--- a/report.txt
+++ b/report.txt
@@ -1,4 +1,5 @@
-# Seasonal Dental Surgeries 2017-18
+# Seasonal Dental Surgeries (2017) 2017-18
+# TODO: write new summary
```

This shows:

- The command used to produce the output (in this case, `diff --git`). In it, `a` and `b` are placeholders meaning "the first version" and "the second version".

- An `index` line showing **keys into Git's internal database of changes**. We will explore these in the next chapter.

- `--- a/report.txt` and `+++ b/report.txt`, wherein lines being removed are prefixed with `-` and lines being added are prefixed with `+`.

- A line starting with `@@` that tells where the changes are being made. The pairs of numbers are **start line** and **number of lines** (in that section of the file where changes occurred). This diff output `-1,4 +1,5` indicates **changes starting at line 1, with 5 lines where there were once 4**.

- A line-by-line listing of the changes with `-` showing deletions and `+` showing additions (we have also configured Git to show deletions in red and additions in green). Lines that haven't changed are sometimes shown before and after the ones that have in order to give context; when they appear, they don't have either + or - in front of them.

---

## What's the first step in saving changes?

You commit changes to a Git repository in two steps:

1. **Add** one or more files to **the staging area**.
2. **Commit** *everything* in **the staging area**.

To add a file to the staging area, use `git add filename`.

---

## How can I tell what's going to be committed?

By `git diff -r HEAD`.

To compare **the state of your files** with those in **the staging area**, you can use `git diff -r HEAD`.

- The `-r` flag means **"compare to a particular revision"**
- `HEAD` is a shortcut meaning **"the most recent commit"**.

You can restrict the results to a single file or directory using `git diff -r HEAD path/to/file`, where the path to the file is relative to where you are.

`git diff path/to/file` will show the result if the file `path/to/file` is ONLY in **unstaged** state.

`git diff -r HEAD path/to/file` can see the result of both **unstaged** and **staged** files.

`git diff` will show all changes of **unstaged** files in the repository.

`git diff -r HEAD` will show all changes of both **unstaged** and **staged** files in the repository.

---

## How do I commit changes?

By `git commit -m "<log-message>"` and edit the most recent message by `git commit --amend -m "<new-message>"`.

To save the changes in the **staging area**, you use the command `git commit`.

It always saves everything that is in the **staging area** *as one unit (atomic)*:

- as you will see later, when you want to *undo* changes to a project, you *undo all of a commit or none of it*.

When you commit changes, Git **requires** you to enter **a log message**. This serves the same purpose as a comment in a program: it tells the next person to examine the repository **why you made a change**, for example:

```shell
git commit -m "Program appears to have become self-aware."
```

> IMPORTANT: If you accidentally mistype a commit message, you can change it using the `--amend` flag: `git commit --amend -m "new message"`.

If you run `git commit` without `-m "message"`, Git launches a text editor with a template like this:

```text
# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
# On branch master
# Your branch is up-to-date with 'origin/master'.
#
# Changes to be committed:
#       modified:   skynet.R
#
```

The lines starting with `#` are comments, and won't be saved. Your message should go at the top, and may be as long and as detailed as you want.

---

## How can I view a repository's history?

By `git log`.

The command `git log` is used to view the log of the project's history.

When you run `git log`, Git automatically uses a pager to show one screen of output at a time. Press the **space bar** to go down a page or the '**q**' key to quit.

---

## How can I view a specific file's history?

By `git log path/to/file` or `git log path/to/dir`

The log for **a file** shows changes made to that file.

The log for **a directory** shows when files were added or deleted in that directory, rather than when the contents of the directory's files were changed.

---
