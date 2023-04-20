# 03 - Collaboration with GitHub

## Using other repos

### Cloning

- Similar to copy-paste but there is a link to the original repo additionally.
- Creates a copy on a local computer.
- Allow updates to go back and forth.

How does it work?

- With `git`:
  - Push changes back to the original repo
  - Pull changes into our local version

Note that **anyone** can clone a **public** repo, but for a **private repo**, **owner** needs to grant access.

### Forking

- Copy **without a link to the original repo**.
- Forking creates **an independent copy** of it on **our GitHub**.
  - Means that we can run experiments without the risk of anything reaching the original repo.

Note that **anyone with a GitHub account** can fork a **public** repo, but for a **private repo**, **owner** needs to allow this feature.

- You can also select the branch we want to fork from.

For a **public** repo, this opens up the opportunity for a log of collaboration if **anyone, not just collaborators of the public repo**, finds the repo and has an idea.

After forking, that contributor, not one of the collaborators, can make changes to the project and submit them through **a pull request**.

Forking differs from **creating a new branch** where we need to be registered as **project collaborators**.

### Recap: Clone vs. Fork

Cloning

- Creates a linked copy on a local computer
- Requires use of `git`
- Push and pull updates with `git` with a particular branch
- Great for collaboration as a project **collaborator**

Forking

- Creates an independent copy on GitHub
- Can all be done within GitHub, no need for `git`
- Submit changes through a **PR**
- Great for collaboration as a volunteer or public contributor and for experimenting

---

## GitHub issues

### What is an issue?

**Messages** to help:

- Track problem fixes
- Plans
- Important tasks
- Other communications for a project

### Assign vs. Tag

You can **assign** the issue to someone you want them to work with and add a **tag with @NAME** in the message to let them see the notification and work on the issue.

- Assign: Who should work on the issue
- Tag: Who needs to read the issue

### Comments on an issue

We can continue communicating on **the same issue** using the **comment** feature.

Type `#ISSUE_NUMBER` to link to the other issue in the current repo.

For a comment, if you want to only reply that comment just select that comment and select `Quote reply` menu on the top-right corner of that comment.

`>` symbol represents a quote reply in a previous comment.

### Close an issue

Once everything in the issue has been addressed, we can close the issue.

There are multiple types of closing the issue:

- **Close with comment**
  - **Close as completed** indicates that items in this issue were successfully addressed
  - **Close as not planned** indicates that a fix was not possible

---

## Pull requests (PR)

### What is a PR?

- A way to notify others about changes we would like to make to a branch within a repo.
- Allow the repo owner to check changes before they are added.
- Best practice to add changes to a separate branch from the default `main` branch.
  - This ensures that `main` only contains finished work.
- A successful PR is merging two branches.

Example scenario

- We already have a branch for the task we are working on in our forked repo and have made our updates.
- We now want to merge the changes to the `main` repo with a PR.
- Here we are on the page for the `update_readme` branch on the forked repo.
- Click `New pull request` button
  - `base` branch = the branch we want to add our updates to
  - `compare` branch = the branch that contains our updates
    - GitHub will tell us if we have any conflicts.
  - Then click `Create pull request` button
- Now, add some information about the changes we want to make.
  - Optionally, you can assign a specific user as an assignee and/or reviewer
  - Then click `Create pull request` button again

> NOTE: Many projects are collaborative, meaning we want to make sure everyone is happy with the changes before they are implemented. One way to do this is to assign a reviewer to a PR in GitHub.

---

## Reviewing pull requests

This time, we are going to request a review.
This works similarly to assigning someone, except we click on the gear icon in the **Reviewers** section.

### Assign vs. Review

Assignee

- Approves the PR

Reviewers

- Looks at the changes before the PR is merged
- We can review PR by going to the **Pull requests** tab and select a PR to review changes.
- To finish the review,by a reviewer, at this point, our PR comments are only visible to us. We need to respond to the PR to submit the comments. We have three options:

  - Comment only
  - Submit the comment and approve
  - Submit the comment and request additional changes before merging

### Comment vs. Request changes

Comment

- Imply feedback or suggestions.
- Not required to be incorporated to change the project
  - For example, the reviewer does not have any changes, but want to discuss a few things about the PR.
  - Or, you have some general feedback for the contributor to consider first, but are not ready to approve.

Request changes

- The comment or feedback from the reviewer does include things that the contributor need to be incorporated first
  - For example, you the reviewer do not think one of the changes works well and would like to suggest something else.
- Once the reviewer select an option, an alert reaches the contributor where they can make the requested changes
  - And then the contributor can resubmit by selecting Re-request review.

Approving PR

- Select **Approve** when the reviewer happy with everything
- Then merge the PR by hitting **Merge pull request** button > **Confirm merge**
- Once a PR is complete, the changes merge into the base branch.
- To keep a clean workflow, it is good practice to delete the branch where the changes came from.
  - Note you can restore the deleted branch later.

---
