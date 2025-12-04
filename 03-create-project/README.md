# Lab 03 - Create a Project  

**Goal:** Learn how to create a brand-new Git repository from scratch and make the very first commit.

### What We Learned (in plain English)

1. `git init` -> tells Git: "Hey, from now on this folder is under your control!"

2. Create/edit files however you want.

3. `git add <file>` -> tell Git which changes you want to include in the next snapshot.

4. `git commit -m "message"` -> take a permanent snapshot and save it with a description.

### Important Note for This Lab

I **intentionally skipped** `git init` here.  

Why? Because this folder lives inside the main `learn-git` repository that was already initialized. Git automatically tracks everything inside it.

In real life / any new project you will **always** run `git init` first thing after creating the folder.

### The Golden Workflow (memorize this forever)

```bash

mkdir my-new-project && cd my-new-project

git init                   # <- ALWAYS the first command!

# create files, code, have fun...

git add .

git commit -m "Initial commit"

Now we truly understand how a Git repository is born!  

Ready for the next lab
