# 02 - Working with Repos

## Modifying a repo structure

### Committing the new/updated file

- We can commit directly into our current branch, or
- Create a new branch for this commit and start a pull request

### Creating a new directory

GitHub will not allow us to create an empty directory, so we need to add a file.

---

## Working with branches

If we are collaborating , we use branches to work on different project tasks simultaneously.

Generally, the `main` branch (Default branch) holds the final versions of our files.

We only incorporate contents from other branches into `main` once we are finished and know there are no issues.

### Branch protection rules

Rules for specific branches

- Require a pull request before merging.
  - This adds a layer of protection against bringing incorrect code into our `main` branch.
- Require that pull requests are approved before merging.
  - This will help improve code quality.
- Restrict who can delete a protected branch.

---

## Repo access

You can restrict who can SEE in our **private** repo.

If someone does not sign in to GitHub and try to visit the repo's URL, the page cannot be located.

In **private** repo, you can choose who can access your repo, called **collaborators**.

---

## Personal Access Tokens (PAT)

When we perform Git commands in the terminal to interact with a **remote** repo such as clone, fetch, pull, or push, it will be prompted for our password, we actually need to provide a **personal access token** instead of your password to access to GitHub website.

**Personal Access Tokens (PAT)**

- An alternative to using passwords for authentication in the terminal.
- More secure than password
- **PAT** is not required when using GitHub, **ONLY** when interacting with a **remote** repo via the **terminal**.

You can set by go to `Settings` tab > `Developer settings` menu.

We can also set the **Expiration time**, after which the token won't work.

We can also set **Scopes** of the token to define what the PAT allows us to do.

We should not share our PAT with anyone else!

While using terminal and interact with a remote repo, `git` command will ask to input your password, **use your generated PAT** instead of GitHub password.

> NOTE: Sometimes cloning a public repo via the terminal may require PAT.

---
