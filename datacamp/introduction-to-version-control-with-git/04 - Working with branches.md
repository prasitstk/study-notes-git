# 04 - Working with branches

## How can I see what branches my repository has?

By `git branch`.

To list all of the branches in a repository, you can run the command `git branch`. The branch you are currently in will be shown with a `*` beside its name.

---

## How can I view the differences between branches?

By `git diff branch-1..branch-2`.

---

## How can I switch from one branch to another?

By `git checkout target-branch`.

Two notes:

- When you run `git branch`, it puts a `*` beside the name of the branch you are currently in.
- Git will only let you do this **if all of your changes have been committed**.

---

## How can I remove files and stage the removal in one step?

By `git rm`.

`git rm` will remove the file (just like the shell command `rm`) then stages the removal of that file with `git add`, all in one step.

---

## How can I create a branch?

By `git checkout -b new-branch-name`.

To create a branch then switch to it in one step, you add a `-b` flag, calling `git checkout -b branch-name`.

The contents of the new branch are initially identical to the contents of the original. Once you start making changes, they only affect the new branch.

---

## How can I merge two branches?

By `git merge source-branch destination-branch`.

When you merge one branch (call it the source) into another (call it the destination), Git incorporates the changes made to the source branch into the destination branch.

If those changes **don't overlap**, the result is **a new commit in the destination branch** that includes everything from the source branch.

To merge two branches, you run `git merge source-branch destination-branch`. Git automatically **opens an editor** so that you can write a log message for the merge; you can either keep its default message or fill in something more informative.

---

## What are conflicts?

Sometimes the changes in two branches will conflict with each other: for example, bug fixes might touch the same lines of code, or analyses in two different branches may both append new (and different) records to a summary data file. In this case, Git relies on you to reconcile the conflicting changes.

---

## How can I merge two branches with conflicts?

When there is a conflict during a merge, Git tells you that there's a problem, and running `git status` after the merge reminds you which files have conflicts that you need to resolve by printing `both modified:` beside the files' names.

Inside the file, Git leaves markers that look like this to tell you where the conflicts occurred:

```text
<<<<<<< destination-branch-name
...changes from the destination branch...
=======
...changes from the source branch...
>>>>>>> source-branch-name
```

In many cases, the destination branch name will be `HEAD` because you will be merging into the current branch.

To **resolve the conflict**, edit the file to remove the markers and make whatever other changes are needed to reconcile the changes, then **commit** those changes.

---
