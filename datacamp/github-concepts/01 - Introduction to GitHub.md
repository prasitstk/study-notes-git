# 01 - Introduction to GitHub

## What is GitHub?

### Git vs. GitHub

Git

- Version control software
- Can be used without GitHub or other hosting platform

GitHub

- Cloud-based hosting service, providing resources such as storage space on the internet.
- Enhances Git
- Easier to manage projects and collaborate
- Can't use GitHub without Git

### GitHub repo

Repo will contain all files of a project and *record post versions of files*.

Since *a GitHub repo* is stored on the internet, it is also known as *a remote repo*.

---

## Setting up a repo

Public repo = Visible to anyone on the internet, but we can still control who can make changes to our projects.

We need to initialize the repo with some files

- `README.md` file:
  - It is standard practice for all repos to include `README.md` file, these act as a guide for the project.
  - It is helpful for collboration as they provide details on what the project is about and how it can be used.
- `.gitignore` file:
  - It blocks or ignores specific files from being commited or saved into our repo.
  - These files usually contain confidential information or are system files.

**Issues** section is where we track tasks or problems and also communicate with others.

**Pull requests** section is where we use for a pull request (PR) to make a change to the project. Think of it like a suggestion box.

- A **PR** will show the suggested changes and compare them to the project's current version.
- We can view the suggestion and decide if we want to accept it.

---

## Creating a README

### Headings

```markdown
# Heading 1
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6
```

### Text formatting

```markdown
**bold**

*italics*
```

### Hyperlinks

```markdown
[Google](https://www.google.com)
```

### Images

```markdown
![Alt text of the image](https://path.to/image.png)
```

### Writing a README.md

- Need to be descriptive
  - Anyone should understand our project
- List the contents of the repository
- Clearly explains the project to others
- Consider it to be the instruction manual for our repository

### README fundamentals

- Title
- Description of technology
  - Why?
- Description of the process used to answer the question
  - Why?
- Table of Contents

### README extras

- How the project came about
- The motivation
- Limitations
- Challenges encountered
- A reap of the problem it intends to solve
- What the intended use is
- If we are sourcing information from elsewhere, it's also essential to include the necessary credits.

---
