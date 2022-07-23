---
title: "Basics of Git"
excerpt: Git is a free and open-source distributed version control system.
date: 2022-07-23T02:31:41+05:00
draft: false
hero: /images/posts/basics-of-git/hero.webp
authors:
    - Hamza Mughal
---

## What is git?

Git is a free and open-source distributed version control system. But what does that actually mean? It makes it easier and more efficient for us to track and manage changes to the code.

Read more about [git](https://git-scm.com/about).

## Installation
Installation of *git* is a pretty simple procedure. For **Mac** or **Windows** navigate to the [download page](https://git-scm.com/downloads) and download the installer. If you're new to version controlling system then it is best to leave everything to default.

On **Mac** it can also be installed using **xcode**.

```shell
$ git --version
```

Run the above command from your terminal to check the installed version. If git wasn't installed it would prompt you whether you want to install it.

### Installation on GNU/Linux based systems.

Most of the **GNU/Linux** distributions are based on **Arch** or **Debian** linux. Git is present in almost all default package managers of the distribution.

```shell
# Debian and debian based systems (Ubuntu, Mint, MX etc)
$ sudo apt install git

# Arch and arch based systems (Manjaro, Artix etc)
$ sudo pacman -S git
```

### Checking the installed status

Upcoming steps are same for all operating systems. To verify you can run `git --version` from your **terminal** or the **command-prompt** on Windows.

```shell
$ git --version
git version 2.37.1
```

If git was correctly installed it would produce an output like this otherwise it would output something like *git: command not found*. In rare cases it may also occur if the *git installation directory* was not added in the path but it should happen automatically with the installtion.

## Getting started

Git comes with `config` command that lets you get and set global variables for git. Variables are stored in a `.gitconfig` file, which may reside in your **home directory** or your **config directory**. But to get started we just need to know about two of them, your **name** and your **email**. Run these commands from your terminal with right information to set them.

```shell
$ git config --global user.name "Hamza Mughal"
$ git config --global user.email hamza@prodesquare.com
```

## Working with Git

Create a new directory or navigate to an existing one and run `git init` to instantiate git repository in the directory.

```shell
$ mkdir code
$ cd code
$ git init
```

This would create a hidden `.git` folder in the current directory. To check the status of your git repository run:

```shell
$ git status
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

This would output the status of your repository whether it is clean or not. Our git repository is empty and there are no files yet. So let's create a text file and run git status again.

```shell
$ touch file.txt
$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	file.txt

nothing added to commit but untracked files present (use "git add" to track)
```

Output has changed from before and now it recognizes the text file we created in the directory. The file is currently **untracked** meaning this this file would not be staged for **commit**. We can use `git add file.txt` to add it to tracking, no output means no error. We can run `git status` again to check the repository status.

```shell
$ git add file.txt
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   file.txt
```

This time `git status` told us there was a new file named **file.txt**. To remove it from staging we can run `git rm --cached file.txt` and it would no longer be added to the commit. Let's modify the file and run `git status` again.

```shell
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   file.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   file.txt
```

Along with the old output we got a newer output this time, informing us that our file was updated. If we were to `git commit` it would commit the older version of the file which was just an empty text file because when we added it, it was blank. So let's run `git commit`.

```shell
$ git commit -m "first commit"
[master (root-commit) 2ffdb78] first commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 file.txt
```

**-m** flag is used to add a meaningful message for your commits. From the information we got is:
- 1 file was changed (created in this case)
- 0 insertions (we didn't added any text to the file *before adding*) 
- 0 deletions (we didn't removed any text from the file *before adding*)

Let's now run `git add` again to stage the latest changes for the commit. You can either run `git add <filename>` or you can run `git add .` to add all **unstaged** or **untracked** files in the current directory. But right before we add it we want to check for the changes, for that we can take help of `git diff`.

```shell
$ git diff
diff --git a/file.txt b/file.txt
index e69de29..3b18e51 100644
--- a/file.txt
+++ b/file.txt
@@ -0,0 +1 @@
+hello world

$ git add .
$ git commit -m "added text to the file"
[master 711f779] added text to the file
 1 file changed, 1 insertion(+)
```

`git diff` shows our **insertions** and **deletions** in the unstaged files. Commit message shows:
- 1 file was changed (file.txt)
- 1 insertion (we wrote *hello world*)

### Ignoring files
This could be achieved by `.gitignore` file and is helpful in defining patterns or files those are not to be added to the repository. Below is an example `.gitignore` file.

```git
patches
st
*.o
*.orig
```

This would exclude the following:
- `patches` directory
- `st` directory
- any `<filename>.o`
- any `<filename>.orig`

### Git remote

Your commits are only stored locally by default. It would not be **pushed** to the remote origin automatically. Some popular **code hosting** and **version control platforms**:

- [GitHub](https://github.com)
- [GitLab](https://gitlab.com)

Create an **empty repository** for your project to be hosted on **GitHub**. Copy the **remote repository URL** and run:

```shell
$ git remote add origin <repository_url>
```

The use `git push` to push your code to the `remote repository` on **GitHub**.

```shell
$ git push -u origin master
```

Once this command is successful you will see your code on **GitHub**.