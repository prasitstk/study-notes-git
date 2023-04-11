# 05 - Collaborating

## How can I create a brand new repository?

By `git init project-name`, `git init` or `git init /path/to/project`.

So far, you have been working with pre-existing repositories. If you want to create a new repository (a new sub-directory with `.git` directory inside) for a new project in the current working directory, you can simply say `git init project-name`, where **"project-name"** is the name you want the new repository's root directory to have.

`git init` will convert the current project root directory (can be non-empty) to be a repository by creating and initializing a new `.git` directory.

`git init /path/to/project` will do `git init` to `/path/to/project` from anywhere else on your computer.

> NOTE: One thing you should NOT do is **create one Git repository inside another**. While Git does allow this, updating nested repositories becomes **very complicated** very quickly, since you need to tell Git which of the two `.git` directories the update is to be stored in. Very large projects occasionally need to do this, but most programmers and data analysts try to avoid getting into this situation.

---

## How can I create a copy of an existing repository?

By `git clone URL`, `git clone /path/to/existing-project`, or `git clone /path/to/existing-project new-project-name`.

Cloning a repository does exactly what the name suggests: it creates a copy of an existing repository (**including all of its history**) in a new directory.

To clone a repository, use the command `git clone URL`, where `URL` identifies the repository you want to clone. This will normally be something like:

```shell
git clone https://github.com/datacamp/project.git
```

inside the current directory, this will create a new directory called 'project' which is a Git repository as well.

To clone a repository in your local system, `git clone /path/to/existing-project` will copy an existing repository of `/path/to/existing-project` and create a new directory called `existing-project` inside your home directory.

If you want to call the clone to something else, add the directory name you want to the command:

```shell
git clone /path/to/existing-project new-project-name
```

---

## How can I find out where a cloned repository originated?

By `git remote` or `git remote -v`.

When you a clone a repository, Git remembers **where the original repository was**. It does this by storing a **remote** in the new repository's configuration. A **remote** is like a browser bookmark with a name and a URL.

If you are in a repository, you can list the names of its remotes using `git remote`.

If you want more information, you can use `git remote -v` (for **"verbose"**), which shows the remote's `URLs`.

Note that "`URLs`" is plural: it's possible for **a remote to have several URLs** associated with it for different purposes, though **in practice** each remote is almost always paired with just **one URL**.

---

## How can I define remotes?

Adding by `git remote add remote-name URL` and removing by `git remote rm remote-name`.

When you **clone** a repository, Git automatically creates a remote called `origin` that points to the original repository. You can add more remotes using:

```shell
git remote add remote-name URL
```

and remove existing ones using:

```shell
git remote rm remote-name
```

You can connect any two Git repositories this way, but in practice, you will almost always connect repositories that share some common ancestry.

---

## How can I pull in changes from a remote repository?

By `git pull remote-name branch-name`.

Git keeps track of **remote** repositories so that you can **pull** changes from those repositories and **push** changes to them.

Pulling changes is straightforward: the command `git pull remote-name branch-name` gets everything in `branch` in the **remote repository** identified by `remote` and **merges** it into **the current branch** of your **local repository**.

For example, if you are in the `quarterly-report` branch of your local repository, the command:

```shell
git pull thunk latest-analysis
```

would get changes from `latest-analysis` branch in the repository associated with the remote called `thunk` and **merge** them into your `quarterly-report` branch.

### What happens if I try to pull when I have unsaved changes?

Just as Git **stops you from switching branches** when you have *unsaved work*, it also **stops you from pulling** in changes from a remote repository when doing so might overwrite things you have done locally.

The fix is simple: either **commit** your local changes or **revert** them (like `git checkout -- .`), and then try to **pull again**.

---

## How can I push my changes to a remote repository?

By `git push remote-name branch-name`.

This will push the contents of your branch `branch-name` into a branch **with the same name** in the **remote** repository associated with `remote-name`.

> NOTE: It's possible to use different branch names at your end and the remote's end, but doing this quickly becomes confusing: it's almost always better to use the same names for branches across repositories.

### What happens if my push conflicts with someone else's work?

To prevent this happening, Git **does not allow you to push changes to a remote repository** *unless you have merged* the contents of the remote repository into your own work.

Fix this by `git pull remote-name branch-name`. It will bring your repository up to date with `remote-name`. It will open up an editor for the new commit message after merging that you can exit with `Ctrl+X`.

Now that you have **merged** the remote repository's state into your local repository (and already **committing** it), try the `git push remote-name branch-name` again.

> NOTE: If you want to avoid the editor from opening after `git pull`, you can use the `--no-edit` flag after `git pull`.

---
