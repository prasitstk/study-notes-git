# 03 - Undo

## How can I commit changes selectively?

By `git add path/to/file` to *stage* it.

The syntax for staging a single file is `git add path/to/file`.

---

## How can I change the staged file to the unstaged one selectively?

By `git reset HEAD path/to/file`.

In other words, **staged** -> **unstaged**.

If you make a mistake and accidentally stage a file you shouldn't have, you can unstage the additions with `git reset HEAD` and try again.

---

## How can I undo changes to unstaged files?

By `git checkout -- filename`.

Suppose you have made changes to a file, then decide you want to undo them. Your text editor may be able to do this, but a more reliable way is to let Git do the work.

```shell
git checkout -- filename
```

will discard the changes that have **not yet been staged**. (The double dash `--` must be there to separate the `git checkout` command from **the names of the file or files** you want to recover.)

In other words, **unstaged** updated after **staged** -> **staged** before updated.

---

## How can I undo changes to staged files?

By combining `git reset` with `git checkout`.

You can undo changes to a file that you staged changes to. The syntax is as follows.

```shell
git reset HEAD path/to/file1
git checkout -- path/to/file1
```

---

## How do I restore an old version of a file?

By `git checkout <minified-commit-hash> path/to/file`.

The syntax for restoring an old version takes two arguments: **the hash** that identifies the version you want to restore, and **the name of the file**.

`git checkout 2242bd report.txt` would replace the current version of `report.txt` with the version that was committed on October 16.

Notice that this is the same syntax that you used to undo the unstaged changes, except `--` has been replaced by a **hash**.

> IMPORTANT: Restoring a file **doesn't erase any of the repository's history**. Instead, the act of restoring the file is **saved as another commit**, because you might later want to undo your undoing.

---

## How can I undo all of the changes I have made?

### From staged -> unstaged

By `git reset HEAD path/to/dir`, it will **unstage** any files from the `path/to/dir` directory.

By `git reset` or `git reset HEAD`, it will **unstage** everything.

> NOTE: `HEAD` is the default commit to unstage.

### From unstaged -> original

By `git checkout -- path/to/dir`, it will restore the files in the `path/to/dir` directory to their previous state.

By `git checkout -- .`, it will revert all files in the current directory.

> NOTE: You can't leave the file argument in `git checkout --` completely blank, so use `.` meaning the current directory instead.

---
