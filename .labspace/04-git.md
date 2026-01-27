# Version Control

![git object model](/.labspace/images/git.png)


### Why Version Control?

> You are completing a coding project. Your code is working great! But then you made a few changes and everything breaks...

_or_

> You're working on a team project and need to make edits to reports and code. You waiting for your team member to make a change and then email you back another a copy... 

There has to be a better way!

![named folders xkcd](/.labspace/images/versions.png)



"Version control is the lab notebook of the digital world: it’s what professionals use to keep track of what they’ve done and to collaborate with other people. Every large software development project relies on it, and most programmers use it for their small jobs as well. And it isn’t just for software: books, papers, small data sets, and anything that changes over time or needs to be shared can and should be stored in a version control system." -- [Version Control with Git](http://swcarpentry.github.io/git-novice/)


## Understanding Git

What better way to understand git than to check out git itself! This will take a while...(if necessary, run this locally)

```bash
git clone https://github.com/git/git
```

We'll be working inside the git/ directory set our working state to v2.31.0

```bash
cd git
git reset --hard v2.31.0
```

### Git's Object Model: Content-Addressable Data Store.

![detailed git object model](/.labspace/images/git_object_model.png)

* Every object has a SHA-1 hash: 40 hex characters.
* Given 40 hex characters, we can find the unique object with that hash.

Let's examine a single commit.

```bash
git log -1 --abbrev=40
```

### Object Types: Blobs, Trees, Commits

![git object overview](/.labspace/images/git-overview.png)


We will use the `git cat-file` command to help us search for objects inside the store.
If we provide git with a partial hash, it will attempt to find a unique match, and if it is unable to, it will provide a list of those that did match.

```bash
git cat-file -p 8348
```

#### Blobs

Let's examine a **blob** object. A blob contains _file contents_. 
![git blob](/.labspace/images/git-blob.png)

```bash
git cat-file -p 83484a
```

**📝 Exercise:** Create a text file called `git.txt` to answer some questions throughout this activity. 1) What is the method signature (return type, method name, and parameters) of the last function in this blob?


#### Trees

Let's examine a **tree** object. A tree contains _folder contents_. 
![git tree](/.labspace/images/git-tree.png)

```bash
git cat-file -p 83484f
```
A simple example representation of folder contents contained by a tree is below: 

![Git tree example](/.labspace/images/git-tree-folder.png)

**📝 Exercise:** 2) What is the output of `git cat-file -p 83484f | tail -4 | head -1`? Briefly explain what this command does.

#### Commits 

Perhaps one of the most important type of object inside the object model is a commit. A **commit** contains many things:

* A root **tree**
* A list of **parent commits**
* A commit message
* An author name, email, time.
* A committer name, email, time.

![git commit](/.labspace/images/git-commit.png)


Let's examine an example commit.

```bash
git cat-file -p 834845
```

**📝 Exercise:** 3) What is the commit message submitted with this commit?

We can examine the commit graph (but only the first part!).

```bash
PAGER='head -n 80' git log --graph --oneline
```

#### Diffs

Diffs are _not_ part of the object model!

> **Commits are NOT diffs**

Instead, diffs are dynamically calculated from the commit graph inside the object store. For example, even object attributes, such as _file renames_ are not represented inside the datastore and must be calculated dynamically.

Let's examine a diff.

```bash
git diff --raw v2.31.0 v2.31.1
```

Press **q** to exit. To get a closer look at specific changes, use:

```bash
git diff v2.31.0 v2.31.1
```

You can use the **down arrow** to view specific changes to files. Press **q** to exit.

**📝 Exercise:** 4) What is the name of the first file listed that changed between versions 2.31.0 and 2.31.1?


### Branches

_Branches_ are simply pointers to commits. _Tags_ are pointers to anything (commits, trees, blobs).

![git-branches](/.labspace/images/git-branches.png)

Use `git branch` to see the current branch and `git branch -a` to view a list of branches for the project.

#### Move between branches with git switch

`git switch` is a new feature in v2.23.0 of git. It essentially replaces and does less work than `git checkout`. Primarily, `git switch` will:

* Change `HEAD` to point to a new branch.
* Updates the working directory to match the commit's tree.

We can switch our branch to the maintenance branch.
```bash
git switch todo
```

Let's confirm.

```bash
git status ; git branch
```

We can return to the main branch.

```bash
git switch master
```

## 📝 Activity: Creating a Repo

Let's try the basics. A repository (repo) is where the backup (master) copies of all files are stored.
– **Local repository:** on your computer
– **Remote repository:** shared repository in the cloud

Let's create a new local git repository.

Create a new directory (Basics) and file (README.md).

```save-as=README.md
# CS5704 SE Basics Workshop
Hello!
```

We are going to create a new git repository, but maybe not the way you've done it before. 
In the next set of commands, we will be working inside the `Basics/` directory.

This will create a new .git directory to store commits and other objects.

```bash
cd Basics
git init
```

We can quickly inspect the contents of the git's directory and object store.

```bash
ls -l .git
echo "objects:"
ls -l .git/objects
```

Before adding a file to the repository, it must first be staged.

```bash
git add README.md
```

We will commit our staged changes into the repository.

```bash
git commit -m "initial commit"
```

**Nice work! We will revisit this later...**

### Stage, unstage, and discard changes

Changes flow from our working tree, to staging index, and into repository.

![git-staging](/.labspace/images/git-staging.png)

Use the following sets of steps to observe what happens to the _working tree_ and _index_, by running the `git status` command:

Update the README.md and stage our change.

```bash
echo " Update: $(date)" >> README.md
cat README.md
git add README.md
```

View the current state of our **working tree** and **index**.

```bash
git status
```

Unstage file (remove from index), but keep changes in working tree.

```bash
git restore --staged README.md
```

Discard changes in worktree (we will lose our work!). This will restore changes to both the index and the working tree based on the latest version in the repo.

```bash
git restore --source=HEAD --staged --worktree README.md
```

### Remote Repositories

While having a local git repository is cool, we should connect it to another remote repository. In other words, **we have no place to `git push` to**...

![git-remote](/.labspace/images/git-remote.png)

#### Remote operations

* Get new data: `git fetch <remote> [branch]`
* Upload your data: `git push <remote> <branch>`
* Get new data and merge into working tree: `git pull <remote> <refspec>`


## 📝 Activity: Let's create a remote repo!

Now let's push the local repository you created earlier to make it a remote repository! This will allow others on your team to access and make changes to the project. For this class, we will primarily use GitHub for remote repositories.

1. Create a new _private_ repository on GitHub (https://github.com account is needed). Name your repository Basics and set a description to be something about "CS5704 Software Engineering Basics Workshop". Skip the initialization steps and create your repo.

2. Follow the instructions to add a remote url to an existing git repository (**push an existing repository from the command line**). It should start with something like: `git remote add origin https://github.com/<user>/<repo>.git`

3. Push your changes to GitHub. Verify you can see your updated README.md!

4. On GitHub, edit the README.md (click on the pencil icon in the top right corner of the file) to add your first and last name under the heading and modify the next line to say "Hello GitHub!". Commit the changes directly on GitHub. Now you have changes in your remote (origin) repository that are missing on your local copy.

5. Run `git pull` locally. Verify you now have the updated changes.

```bash
git pull
```

6. Invite the instructor (chbrown13) to be a collaborator to your repository (`Settings -> Manage access`).

**7. This repository is where you will place all the materials to submit the workshop today. Add your FizzBuzz program, `practice.js`, `reflection.txt`, and `git.txt` from the previous activities (there is nothing to submit for the REPL activity). In addition, add a README with your name and PID.**

