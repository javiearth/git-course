# Git course
<small>Version: 0.3.4.</small>

### About this course.

This is a brief course that teaches by examples, its aim is to help you achieve a level of understanding about Git enough to work in most projects. 

This course is based on my personal experience practicing Git commands on my computer. The content reflects what I learned through experimentation, asking questions, and researching general concepts online.

This course is under development, so new sections will be added in the following weeks/months. My aim is to cover all levels: zero knowledge, junior developer, medium level and advance for senior developers or software engineers.

The course will have three parts once it is finished. This is the current state of development:

- [X] [1. Git Essentials:](#1-git-essentials) this part is already published and covers everything you need to use in your junior role: use Git for first time, start using Git for version control, work with branches, work in local and remote and a quick introduction of good practices.

- [] Git Intermediate: it will cover good practices for developers that want to advance in their careers and some other useful commands to get a more control of your repository.

- [] Git Advanced: it will cover Git commands for auditory and management, oriented to senior and engineer roles.

**Important**
Git commands are the same no matter which OS you're working with. Anyway, the commands in the *1.3 Installation and 1.4 Previous knowledge* sections may be different for you OS. Apart from that, everything should be same in your machine.

## 1. Git Essentials

##### 1.0 Table of contents:
1. [1.1 Introduction to Git](#11-introduction-to-git)
2. [1.2 Previous knowledge](#12-previous-knowledge)
3. [1.3 Installation](#13-installation)
4. [1.4 Git Configuration](#14-git-configuration)
5. [1.5 Starting a version control of your project](#15-starting-a-version-control-of-your-project)
6. [1.6 How Git works: staging and working directory](#16-how-git-works-staging-and-working-directory)
7. [1.7 Moving among commits](#17-moving-among-commits)
8. [1.8 Discarding changes and recovering versions](#18-discarding-changes-and-recovering-versions)
9. [1.9 Tagging](#19-tagging)
10. [1.10 Branches](#110-branches)
11. [1.11 Cherry-picking](#111-cherry-picking)
12. [1.12 Conflicts](#112-conflicts)
13. [1.13 Rebase](#113-rebase)
14. [1.14 The Stash](#114-the-stash)
15. [1.15 Git remote](#115-git-remote)
16. [1.16 Introduction to good practices](#116-introduction-to-good-practices)
17. [1.17 Git Essentials cheatsheet](#117-git-essentials-cheatsheet)
18. [1.18 Conclusion](#118-conclusion)

### 1.1 Introduction to Git

Git is an open-source, distributed, version control software created by Linus Torvalds while working on Linux. While using Git we work in local (in our computer only). There are online platforms that use git too and are designed for working teams developing together. Some of the most famous platforms are GitHub and GitLab.

### 1.2 Previous knowledge 

*Skip if you are familiar with the Linux terminal*

*Important: The dollar symbol ($) means a new input in your terminal. You don't have to write it.*

This is optional but, it is convenient that you learn very few basic commands to use in your terminal. That will make it easier and faster to navigate through directories and managing files. I am using bash in a Debian based Linux distribution, if you are using any other terminal the following commands may be different. I recommend to practice these:

- `pwd` prints the current working directory.
- `ls` lists the files and subdirectories in the current directory.
- `cd` change directory to a specified directory (`cd ..` to move 1 directory up).
- `mkdir` creates a new directory.
- `touch` creates a new file.
- `rm` removes a file or directory.
- `rm -r` removes a file or directory recursively (removes a directory and its content).
- `mv` moves a file from one directory to another.
- `cp` copies a file from one directory to another.

These are Linux commands (little programs which perform an action, you just type them). Words after a Linux commands that start with one or two hyphens are flags (e.g., -h or --help). Flags are options that modify the behavior of the commands.

```
PRACTICE:

1. Create two directories (my-directory-1 and my-directory-2).
2. Change your working directory to my-directory-1.
3. Create a file.
4. Move that file to my-directory-2.
5. Check the moving operation succeded using ls.
6. Copy the file in my-directory-2 to my-directory-1.
7. Change your working directory to the parent directory of my-directory-1 and my-directory-2.
8. Delete my-directory-1, my-directory-2 and their content.
```
<!--<small>See solution in [my git-course repository](https://github.com/javiearth/git-course/blob/main/git-essentials-solutions.md)
That's all, let's start with git.</small>-->
<small>If you want to practice more commands write 'linux commands cheatsheet' in a search engine.</small>

[Back to Table of Contents](#10-table-of-contents)

### 1.3 Installation

In Unix systems (Linux and MacOS) Git is usually already installed. You can check if Git is installed just typing `git` on your terminal. Anyway, you can install Git typing `sudo apt install git` in the Linux terminal.

### 1.4 Git configuration

We need an username and an email to start working with Git, so we need to configure Git using the next commands:

```
$ git config --global user.name "yourusername"
$ git config --global user.mail "your@mail.com"
```

Aclaration: we write the command `git config` followed by the configuration level (global), followed by the data we want to modify (user's name and user's e-mail). If you just write `git config` it displays a list of different actions to work with the configuration file.

*If you want to work with GitHub is important that you use one of the email addresses you have verified in your GitHub account. GitHub uses email addresses to link all your contributions to your profile.*

[Back to Table of Contents](#10-table-of-contents)

### 1.5 Starting a version control of your project

Create a new directory with the name of our project: awesome-recipes ( $ mkdir awesome-recipes ). Change to the directory you've just created ( $ cd awesome-recipes ) and write:

`$ git init`

Git displays a message confirming the repository has been initialized. It also tells you that it has created a default branch for your project, we'll learn about that a bit later.

The command `git init` creates a hidden subdirectory (.git), but you don't need to know anything about it, you won't use it, git manages it for you.

Now create a new document, I named mine 'recipes.txt' ( $ touch recipes.txt ).

Let's see now the status of your project with the following command:

`$ git status`

Git detected that there is a new file in your project's working directory that wasn't there before. Git tells you that by showing 'recipes.txt' in red.

You have to tell Git that you want to add 'recipes.txt' to the repository using the command `git add`. You can do so in two different ways:

- Adding files one by one:

`$ git add recipes.txt`

- Or adding everything using a dot:

`$ git add .`

If you write again `$ git status` you'll see that 'recipes.md' is displayed in green, that means that git knows now that file is ready to include in your repository, but it hasn't save any state of your working directory yet. To do so use:

`$ git commit -m "your message here"`

When we do a commit, git saves a snapshot of our project. You need to add a description of the changes made to your project in that commit, this helps you to track the history of your project. Let's do our first commit, type:

`$ git commit -m "First commit for awesome-recipes, add recipes.md"`

Git has taken a snapshop of your project. If you run the `git status` command again you'll see there are no changes to save in your git repository, it is up to date.

Let's practice a bit more, write a recipe in recipes.md and save the file (copy the Spanish omelette recipe from [example-recipes.md](https://github.com/javiearth/git-course/blob/main/example-recipes.md)).

Run `$ git status` again. You'll see the same as before, because we have modified 'recipes.md' again. 

Let's try another command, type:

`$ git diff`

This command shows the modifications done in the project's directory since the las commit. This command is useful to check the changes made before commit them.

Now, commit the changes to your repository.

```
Solution:
$ git add .
$ git commit -m "Add Spanish omelette to recipe.md"
```

Did you get it? Brilliant!

Let's see the history of our project so far by using another Git command:

`$ git log`

This command displays all the commits you have done in the current branch, we'll learn more about braches later, don't worry. Let's take a closer view to the log.

At the moment there are only two commits, but you can move along the whole history when it has grown. You can use the '**Q**' key to go back to the terminal and start typing again. 

First, you see the word 'commit' followed by a long code of numbers and letters, that is the hash of the commit, it is the commit's ID.

There is something named master (the name of the only branch so far) and HEAD, we'll see this in a bit.

After each commit hash, the log shows its author and the date it was created, as well as the message you wrote to describe the changes made to the project.

This structure will be repeated for each commit.

*Note: see "1.16 Introduction to good practices" at the end of the section "Git Essentials" to know more about how to write commit messages more efficiently, you can skip that for now.*

[Back to Table of Contents](#10-table-of-contents)

### 1.6 How Git works: staging and working directory

Before moving any forward it is useful to clarify some concepts:

- **Working directory**: is the directory of your project, where all files and subdirectories of your project are located.

- **Stage**: is the place where git stores all changes to apply to the repository with the next commit. When you use `git add` Git prepares those files added, storing the changes made since the last commit until you've added them to the stage. If for some reason you make changes after using `git add` in one of the files added to the stage, you'll need to use `git add` again because those new changes are not in the stage area ready to commit.

*Bonus command!
Did you add changes to the stage but now you regret it? Don't worry! Use `$ git restore --staged .` to remove all changes from stage <small>(You can type the name of all files you want to remove from the stage instead of the dot).</small>*

- **Commit**: a snapshot of the project under development. A commit saves all the changes already added to the stage adding them to the repository.

<span style="color:red;">[Working directory]</span>-----`git add`----> <span style="color:green;">[Stage]</span>-----`git commit`----> [Repository]

Summary:
While working in your project you update the files stored in the working directory. The command `git status` compare your working directory (and stage) with the last snapshot (last commit) of your project detecting any changes. Git displays in red the name of any file that has been modified in your working directory. Then, you can use `git add` to add some or all the files that have been modified to the stage. The changes added to the stage are ready to commit, so if you run `$ git stastus` again git displays them in green. After commit, git saves a snapshot of all the files ready to commit (those saved to the stage).

[Back to Table of Contents](#10-table-of-contents)

### 1.7 Moving among commits

One of the interesting things about a version control program like Git is to be able to do and undo changes, so we can recover a version which works in the case something goes wrong while developing.

Let's say that for some reason we want to come back to a previous version of our project. Remember the hash of each commit? Use `git log` and copy the hash of your first commit (that one with the message 'First commit for awesome-recipes, add recipes.md'). Then, write this command:

`$ git checkout commit_hash_number`

Example: `$ git checkout 6c3fb3825e4982f665eda06ecf94e04f868cb3ec`

*Remember that in the Linux terminal you can use the middle button of your mouse to paste something you copied.*

Now type `git log`. You'll see that you're working on the commit you selected before, but where is the last commit? Don't panic!. It's there, somewhere. To see all commits type the following:

`$ git reflog`

This command shows all the commits. Let's take a moment here. 

You see the only two commits we've made so far. In the top commit (the newest), next to the hash, you see the word 'master', this is the only branch of our project and this means that the last commit in the branch is that one where it is placed.

You also see that the HEAD has moved from the second to the first commit we did, this is because you are working in this version of the project now. So, if you open the directory of the project you'll notice it has come back to a previous version, before adding the Spanish omelette recipe (or whatever you added). The changes made to recipes.md are not longer there, we lost our recipe!

You can continue working again in your project from this version as if the last commit never happened, but we want the Spanish omelette recipe back, don't we? Let's try something:

`$ git checkout master`

Using `git checkout` with the name of a branch moves the HEAD (where we're working) to the last commit of that branch. Alternatively you can write the hash if you want, but in this case this is faster.

[Back to Table of Contents](#10-table-of-contents)

### 1.8 Discarding changes and recovering versions

The command checkout allows us to move between commits, but doesn't change the history of the project.

Let's make an intended error in our recipes.md file by deleting everything regarding having onions in the recipe (yes, that's actually an error and I don't care about what you think).

So, these are the lines to remove from recipes.md. Save the file after that.
```
- Half of an onion
4. Chop the half of an onion and add it to the potatoes. Move the mix from while to while.
```

Then use what you already know to save a new version of your project.

```
Solution:
$ git status
$ git add .
$ git commit -m "Remove onions from Spanish omelette in recipes.md"
```

Alright, we made a mistake... No problem, we can fix it with a reset! Type `git reset` followed by the hash of the commit we want to recover.

`$ git reset commit-hash-number`

Aditionally, you can use `HEAD~N` to select the 'N' commits back. Example:

`$ git reset HEAD~1`

If you use `git reflog` you'll see that 'master' and 'HEAD' have moved to the second newest commit ('Add Spanish omelette to recipe.md'). That means that the last version of the branch master is this commit, and not the newest so if you type `$ git checkout master` you won't recover the last commit. The history of the branch master has been re-written. The commit 'Remove onion from Spanish omelette in recipes.md" is no longer a commit of the branch master.

We can recover the commit where we remove onion from the Spanish recipe by using `checkout` (the HEAD will move to the specific commit, batu the branch name, like master, won't change). You'll recover the files from that commit into your working directory without affecting the branch's current position.

```
Remember:

HEAD: points to the commit you're currently working on, your working directory reflects the state of this commit.

Branch-name (e.g.:master): refers to the latest commit of the branch.

When HEAD is detached (in a different commit that the branch's name), the branch remains in the same commit but you see the version of your project that corresponds to HEAD.
```

There are different kind of resets: soft, mixed and hard. 

<!--**All resets** move the HEAD to the commit selected, that means that your working directory shows the version of the commit where HEAD is. And all resets restore the branch history to the commit of the reset.-->

**All resets** move the HEAD to the commit selected and restore the branch history to this commit.

`reset --soft`: doesn't make anything else, it does not remove any information from the stage or the working directory. The soft reset is very useful when you've made a mistake in the last commit and want to fix it quickly, e.g. when you write a mistake in the last commit's message.

`reset --mixed`: is the reset by default, so is the same as if you write just `reset`. It eliminates the stage, so you'll need to use `git add` before commit any changes to your git repository. This kind of reset is useful when you want to undo the last commits but want to check the files before do any more commits.

`reset --hard`: eliminates the stage and doesn't conserve any changes in the working directory. <!--That means that the files in your project directory are re-stablished to the version of the commit selected in the hard reset, no changes done after that commit will remain, so there is nothing to add to the stage or changes to commit. -->Hard resets are useful when you want to eliminate everything since the last commit, like when you are experimenting, you changed something and it didn't work.

Remember that you can use the commit hash or the notation HEAD~N. Example:

`git reset --soft HEAD~2`

```
PRACTICE:

1. Make a new file named 'soft-reset.txt' and commit the changes.
2. Use a soft reset to move the branch history 1 commit back.
- What shows 'git status'?
- Is 'soft-reset.txt' in the working directory? If so, delete it.
3. Make a new file named 'mixed-reset.txt' and commit the changes.
4. Use a default reset to move the branch history 1 commit back.
- What shows 'git status'?
- Is 'mixed-reset.txt' in the working directory? If so, delete it.
5. Make a new file named 'hard-reset.txt' and commit the changes.
6. Use a hard reset to move the branch history 1 commit back.
- What shows 'git status'?
- Is 'hard-reset.txt' in the working directory? If so, delete it.
```

[Back to Table of Contents](#10-table-of-contents)

### 1.9 Tagging

Adding comments in every commit is important to track quickly all changes we've done, but it is also important to highlight all versions that are special for some reason. We can do this adding tags to commits. A tag will be highlighted in the log, so we can easily track them.

To add a tag use one of the following commands:

`$ git tag tag_name` adds a tag to the last commit.

`$ git tag tag_name hash_number` adds a tag to the selected commit.

Important: tags are unique, we can't have the same tag in two different commits of our project.

To delete a tag use any of these commands:

`$ git tag -d tag_name`
`$ git tag --delete tag_name`

> In git commands, you can usually use -d or --delete for deletting options.

[Back to Table of Contents](#10-table-of-contents)

### 1.10 Branches

It is useful to separate the development of our project in branches because it opens the possibility to add features and make changes without compromising the safety of our project. It is also useful to have a branch where you work more often and another to save just the very important updates that you don't want to compromise for any reason.

#### 1.10.1 Renaming branches

It is common in the software development industry yo name the main branch as, well, main. To rename a branch we use `$ git branch -m new-branch-name`, so to rename master as main type:

`$ git branch -m main`

That looks more professional!

#### 1.10.2 Creating branches

Instead of editing the main branch of our project it is a common practice to use another branch where we do the changes just in case something goes wrong (`$git branch new-branch`). So let's create a new branch to add more recipes. To do so we use `git branch` followed by the name of the new branch. Let's create one branch named 'asadillo-manchego'.

`$ git branch asadillo-manchego`

(We're learning more than just git).

#### 1.10.3 Switching between branches

There are two ways to change to another branch, one you already know because you've used it: checkout (e.g. `$git checkout asadillo-anchego`). But let's try another one that is more modern: `switch`.

`$ git switch asadillo-manchego`

We haven't done any changes yet so if you use `git reflog` you'll see that both branches are in the same commit, and also the head is in that commit pointing (`-->`) to 'asadillo-manchego' because is the branch we are working on.

Copy the recipe from [my repository](https://github.com/javiearth/git-course/blob/main/example-recipes.md), save the file and apply the changes to the new branch.

```
Solution:
$ git status
$ git add .
$ git commit -m "add asadillo manchego to recipes.md"
```
Great! You can check the changes with `git log` and `git reflog`. Let's try the last one.

The HEAD points to 'asadillo-manchego' branch and it is located in the last commit ('add asadillo manchego to recipes.md'). This branch is one commit ahead of the 'main' branch. We can now switch between different verions of our project by switching between branches with `git chechout` or `git switch`. Do you see how convenient this is?

#### 1.10.4 Combining branches with merge

After testing the new version of our project and check that everything works as it should work it is time to apply those changes to the branch 'main'. 

The merge command (`$ git merge branch-name`) combines the whole history of the specified branch into the current branch and creates a new special commit known as merge commit.

```
main   :--A---B---------------E(merge commit)
feature:        \---C---D---/
```

To merge the new branch into 'main' we must first switch to the branch 'main'. Let's do this merge operation:

```
$ git switch main
$ git merge asadillo-manchego
```

How to access to the whole history after a merge operation?

By typing `$ git log` you'll see just the merge commit and the previous ones made on 'main', but git doesn't shows the commits of the merged branch. You need to add `--graph` to the command, like this:

`$ git log --graph`

Now you see a graphic that shows how asadillo-manchego branch merged into the branch main and also all its commits.

#### 1.10.5 Deleting branches

The branch asadillo-manchego has served its purpose and is not longer needed, we can get rid of it with this command:

`$git branch -d asadillo-manchego`

*You can type --delete instead of -d.*

```
PRACTICE (important):

1. Create a new branch with the name 'new-recipes' and switch to it.
2. Add the hummus recipe that you'll find in [example recipes](https://github.com/javiearth/git-course/blob/main/example-recipes.md) to the file recipes.md.
3. Commit the changes.
4. Add the Banana Oat Pancakes recipe and commit the changes again.
(Do not delete the branch neither merge it, we'll use it to learn something new in the next section!)
```

[Back to Table of Contents](#10-table-of-contents)

### 1.11 Cherry-picking

If you made it until here, congratulations! You know almost every day to day git commands. Let's celebrate with learning cherry-picking.

The command `cherry-pick` copies one commit of one branch into another and gives it a new hash. It is important to know that only takes one commit and no any other previous commits to that one. You'll understand it better with an example.

In the last practice, you created a new branch named 'new-recipes' and apply two commits. Try to use cherry-pick to copy the second commit into the branch 'main'. To use the command you need the hash of the commit to copy (`$ git cherry-pick commit-hash`).

```
Solution:
$ git log
$ git checkout main
$ git cherry-pick 6c3fb3825e4982f665eda06ecf94e04f868cb3ec
(obviously you'll have another hash)
```
Open the file recipe.md and take a look. Only the second recipe (Banana Oat Pancakes) has been added to the file, but the hummus recipe is missing. This is because you've only applied the changes done in the second commit.

Before cherry-pick:
```
main:       ---A---B--
new-recipes:         \---C---D--
```
After cherry-pick:
```
main:       ---A---B--------------D'--
new-recipes:         \---C---D--/---
```
In this scheme, D' has same content of D but different hash.

[Back to Table of Contents](#10-table-of-contents)

### 1.12 Conflicts

Try to update the branch 'main' with the commits in the branch 'new-recipes'. You can use cherry-pick or merge, it's up to you. 

You'll probably recived a message informing about a conflict. Conflicts are common while working with different branches, but there are ways to solve it. In this case, the two branches have modified the same file. Git stops the operation and shows the conflict inside the file where the conflict occurs. You'll see something similar to this:

```
*<<<<<<< HEAD
The color is red
=======
The color is yellow
>>>>>>> feature*
```

How to solve a conflict?

1. Identify the files in conflict.
2. Open the file and locate the conflict.
3. Solve the conflict manually and save the file.
4. Tell git the conflict is solved. To do so add the file to the stage (`$ git add recipes.md`).
5. End the process using `git commit` (`$ git commit -m "Add new-recipes to main"`).

You can delete the branch 'new-recipes' now.

[Back to Table of Contents](#10-table-of-contents)

### 1.13 Rebase

This is the last command I'll tech you in Git Essentials about working with branches.

Sometimes, usually when developing in teams, there is somebody working in two diferent branches at the same time. Let's say that one team is working in the branch named 'develop', and another team is working in a new feature in the branch named 'feature'. The branch feature was created from develop, but none of the teams stopped working so when the feature is ready to merge into the other branch, develop has already been modified with some changes, and the merge operation will create a conflict.

Rebase is very useful in this example. This command reorganizes the history of one branch in a way that moves all its commits so they are applied after the last commit of another one.

In the example I mentioned, the team working in feature can do a rebase, so the commits in feature are modified in a way that are apply after the changes made in the branch develop while the feature team was working.

Before rebase:
```
develop:---A---B---E--
feature:     \---C---D--
```
After rebase:
```
develop:---A---B---E--
feature:             \---C'---D'--
```
Notice that the commits in feature after rebase (C' and D') are different from those before rebase (C and D).

[Back to Table of Contents](#10-table-of-contents)

### 1.14 The stash

Sometimes we are working in one branch and we need to change to another, but we don't want to commit any changes yet. Or maybe we want to clean our working directory for some reason, but we don't want to lose the changes we made. In these cases, we can use the stash.

The stash is a temporary area where the changes made in the working directory and the stage are saved. Think about it as a quicksave or a draft. We can use the following command:

`$ git stash`

By doing so all changes made so far since the las commit are safe in the stash. Now we can change between branches. 

Let's try something. Create a new branch with a name of your choice and switch to it. Add a line at the end of each recipe in the recipe.md file (in Markdown this is done adding three asterisks, three underscores or three dashes in a new line: `***`, `___`, `---`).

Now, try to switch to another branch. The operation will be aborted as there are changes unsaved. Write `git stash` and try again, Git allows you to switch between branches now. 

After switching to another branch all changes have been removed from your working directory and the stage, they are hidding somewhere else (in the stash). You won't get the changes back until you recover them from the stash.

To recover something from the stash you can use two different commands:

- `$ git stash pop`. This recovers the stash and clear it.
- `$ git stash apply`. This recovers the changes saved in the stash but doesn't clean it.

You can have several stash saved. Using `stash pop` and `stash apply` recovers the last stash by default unless you specify another one. You can list them using `$ git stash list`. Use the command and you see a list that starts with the word 'stash' followed by an at and a number between brackets (`stash@{0}`). This is the stash index. You can recover any particular stash using its index (e.g., `$ git stash apply stash@{1}`).

Stashes are a special kind of commits and they will remain saved until you clear the stash area. To clean the stash list you can drop one by one using `$ git stash drop` to clean the newest stash, or `$ git stash drop stash@{index}` to clean a specified stash. You can clear the whole list typing `$ git stash clear`.

```
Cleaning the stash:
$ git stash drop
$ git stash drop stash@{index}
$ git stash clear
```

```
PRACTICE:
1. Only if you didn't do it before: create a new branch, switch to that one, make some changes in one of the files, save the stash, switch to the previous branch.
2. Switch again to the new branch.
3. Open recipe.md and take a look.
4. List the stash.
5. Use the command `git apply`
6. Open recipe.md and take a look.
7. Switch to another branch again and then go back to the new one.
8. List the stash.
9. Use the command `git pop`.
10. List the stash.
11. Clean the stash completely.
```

[Back to Table of Contents](#10-table-of-contents)

### 1.15 Git remote

In spite that Git is very useful working in local, it shanes in cloud environments where teams of software developers work remotely. There are different solutions for that (GitHub, GitLab, Bitbucket, SourceForge...), but the commands you'll use to work with your remote repository are the same, no matter in which platform it is located.

These platforms store repositories in the cloud, so teams of developers can work remotely in the same project. The repositories are the same as the ones you have in your machine, but they are accessible from anywhere. The only thing that changes is where they are located. The way you work is the same with the diference that you have to send or request information from the remote repository in a few ocassions.

#### 1.15.1 Authentication

You need to authenticate to the platform to access the remote repository. There are different options to authenticate but SSH keys are widely spreaded and they are very secure. 

A SSH (Secure Shell) key is a pair of keys, one public an another private, used to encrypt the communication between your computer and a server, so you don't have to use a password everytime you access to a remote repository.

Now, let's see how to connect to a remote repository.

**Generating a SSH key**

In the linux terminal type:

`$ ssh-keygen -t ed25519 -C "your-email@mail.com"`

Be sure that the e-mail you write between the double quotes is one verified in the platform where the repository is located (GitHub, GitLab, etc).

The terminal will ask for a passphrase, you can just press enter if you don't want to add it. Then will ask for a directory to save the ssh key, you can press enter again to save it in the default directory (something similar to /username/home). After that, a .ssh directory is created in the directory you chose (the dot means it is a hidden directory).

**Add the key to the agent**

Type the two following commands:
```
$ eval "$(ssh-agent -s)"
$ ssh-add ~/.ssh/id_ed25519
```
The first one starts the ssh agent and the second adds the ssh that is stored in the id_25519 subdirectory inside .ssh.

**Copy the PUBLIC SSH key**

Notice that PUBLIC is in capital letters ;)

Access to the file where your public SSH key is located and copy it, from the begining (ssh-ed25519).

`$ cd ~/.ssh/id_ed25519.pub`

**Save your public SSH in the platform**

The key you've just copy must be added to your account in the platform you're using (try seaching something similar to setting > authentication > SSH).

```
PRACTICE:
1. Create a profile in a platform like GitHub or GitLab.
2. Follow the steps in this section so far and add a SSH key to your GitHub/GitLab account.
```

#### 1.15.2 Conecting to the repository for the first time

Create a new repository in your account, for example, awesome-recipes. The full URL is something like https://github.com/username/awesome-recipes. **IMPORTANT** Do not add any file (e.g., README.md) because it creates conflicts that you have to solve later.

Once your repository is created, configure it:

**Configuration**

Open a terminal in the diretory of your project (where you wrote `git init`) and type:

`$ git remote add origin git@platform.com:username/repository-name.git`

If your repository is named awesome-recipes, your username is superhero96 and you platform is GitHub, it would be something like this:

`$ git remote add origin git@github.com:superhero96/awesome-recipes`

**Verify**

Verify everything is ok with this command:

`$ git remote -v`

You should see something like this:

```
origin
git@github.com:username/repository-name.git(fetch)
git@github.com:username/repository-name.git(push)
```

#### 1.15.3 Working in your own remote repository

You can start sharing your developing skills to the world by uploading to the cloud your own individual repository (or you can make it private, it doesn't change anything about how you work with it).

The way you work in an individual repository is working with git locally in your computer and after finishing some work (committing, merging branches, etc.) you update the remote repository.

**Updating your repository with PUSH**

To update any changes, you can use push to update the history of a branch in your remote repository. Use:

`$ git push origin branch-name`

Example:

`$ git push origin main`

You don't need to push all branches, but you can and I recommend it, so you have a remote copy of your work.

**Updating your local repository with PULL**

If for some reason you made changes in your remote repository but not in the local repository, you can update your local repository using `pull`.

This is useful if you work in different computers, so sometimes you update the remote repository from one of your PCs but then you need to update the repository in the other computer. **Important**: before pull a branch from your remote repository, switch to the right branch in your local repository.

`$ git pull origin branch-name`

Example:
```
$ git switch main
$ git pull origin main
$ git checkout develop
$ git pull origin develop
```

**How PULL works?** (Optional, skip it if not interested)

The command `git pull` is actually a combination of two different commands that you can use separately.

- FETCH:
First, the command `git pull` downloads the changes done from the remote repository and save the downloaded branch as origin/branch-name. You'll receive information about changes done in the remote repository. This part can be done as an individual operation using '$ git fetch origin branch-name')

- MERGE:
You already know merge. The second part of the command `git pull` is to merge origin/branch-name into branch-name. It is the same as doing `$ git merge origin/branch-name`.

Summaryzing:

The command `$ git pull origin branch-name` is similar to:
```
$ git fetch origin branch-name
$ git merge origin/branch-name
```
*Remember to switch to your local branch 'branch-name' before merge*

```
PRACTICE:

1. Create a remote repository in GitHub, GitLab or any platform of your election.
2. Create a repository in your computer and start a version control with it. Add one file.
3. Update the remote repository.
4. Edit the file, upload a file or create one in the remote repository using the options you have in its website.
5. Update the local repository.
```

[Back to Table of Contents](#10-table-of-contents)

### 1.16 Introduction to good practices

This section aims to give you a small introduction to very few tips that may be useful for junior profiles. You'll find much further information about good practices in *Part 2: Git Intermediate* in future updates of this course.

#### 1.16.1 Good practices in commits

Write clear, brief and structured commit messages. Start by following this tips widely accepted by the develop community.

- Use short capitalized titles summarizing the changes (up to 50 characteres).
- Write in an imperative tone.
- Use standard prefix:
  - feat: for new features
  - fix: to solve errors
  - docs: for changes in the documentation
  - style: for formatting changes
  - refactor: changes that do not alter the functionality of the software but improve the code
- Optionally, explain what changed and why using bullet points in small sentences (up to 72 characters).

Here are two different examples to inspire you.

Short commit message:

"feat: Add Spanish omelette recipe to example-recipes.md. and fix typos"

Longer commit message:

"feat: Add about this file section and Banana Oats Pancakes recipe.
- Added a new About this file section in example-recipes.md
- Introduced a new Banana Oats Pancakes recipe
- Fixed links and typos across example-recipes.md
- Updated preparation method in Hummus recipe for clarity"

#### 1.16.2 Work with branches

Make changes in specific branches to keep the branch main stable and safe. You can use the format feature/branch-name for new features or any other branch name that is related to the aim of the branch.

Merge the specific branch into the develop branch. This branch is used to incorporate new versions of your software and test them before release the changes in the branch main. 

Main only incorporates significant changes, tested versions of develop. We usually refer to the branch main as production.

[Back to Table of Contents](#10-table-of-contents)

### 1.17 Git Essentials cheatsheet

#### Basic commands

| Syntax | Description |
|---|---|
|git config |Access git configuration options |
|git init |Initializes the control version of the directory |
|git status |Shows changes made in stage and working directory since last commit |
|git restore --staged file-name |Removes changes from the stage, use a dot `.` to remove all changes |
|git add file-name |Adds changes made in the specified file to the stage |
|git add . |Adds changes made in the working directory to the stage |
|git commit -m "your-message" |Commits changes for the stage to the branch |
|git log |Shows a chronologic backwards history of the commits in the current branch (or add a branch name to show its history)|
|git log --graph|Shows the history with a graphoc representation of branches and their fussions |
|git reflog |Shows every move of the HEAD and local references, including resets, deleted commits, rebase, checkouts... |
|git checkout commit-hash |Recovers the working directory of the specified commit |

#### Tags

| Syntax | Description |
|---|---|
|git tag -a tag-name | Adds a tag to the last commit |
|git tag tag-name commit-hash | Adds a tag to the specified commit |
|git tag -d tag-name | Deletes the specified tag (you can use --delete instead of -d) |

#### Reset

| Syntax | Description |
|---|---|
|git reset --soft hash-number | Deletes all commits made after the specified one but preserves stage and working directory |
|git reset --mixed hash-number | Deletes all commits made after the specified and the stage, but preserves the working directory (default reset, you can use it without '--mixed')|
|git reset --hard hash-number | Deletes all commits made after the specified one, as well as stage and working directory |
|git reset HEAD~N | (Substitute N with a number) You can use this notation to delete the last N commits with any reset |

#### Branches

| Syntax | Description |
|---|---|
|git branch new-branch |Creates a new branch |
|git branch -m new-branchs-name |Rename the current branch |
|git switch branch-name |Switches to the specified branch (modern alternative to checkout)|
|git checkout branch-name |Switches to the specified branch |
|git branch -d branch-name |Deletes the specified branch (you can use --delete instead of -d) |
|git merge branch-name |Copies the last commit of the specified branch into the current branch and creates a merge commit |
|git rebase branch-name |Reorganizes the commits in the current branch to apply after those from the specified branch |
|git cherry-pick commit-hash |Copy the specified commit to the current branch and gives it a different hash |

#### Stash

| Syntax | Description |
|---|---|
|git stash |Saves the stage and working directory to the stash area |
|git stash pop |Recovers stage and working directory from the last stash and deletes it|
|git stash pop stash@{index}|Recovers stage and working directory from the indexed stash and deletes it|
|git stash apply |Recovers stage and working directory from the last stash preserving the stash|
|git stash list |Displays the stash list |
|git stash drop |Deletes the last stash |
|git stash drop stash@{index} |Deletes the specified stash |white_check_mark:

#### Git Remote

| Syntax | Description |
|---|---|
|git add origin git@github.com:username/repository-name.git | Connects a remote repository to the local current one |
|git push origin branch-name |Uploads the local changes in a branch to the remote repository |
|git pull origin branch-name |Downloads the changes from a repository and merges them in the current branch |
|git fetch origin branch-name |Downloads the changes from a remote repository and save them in origin/branch-name |
|git merge origin/branch-name |Merges the previously downloaded changes from a repository into the branch branch-name |

[Back to Table of Contents](#10-table-of-contents)

### 1.18 Conclusion

If you made it until this part, Congratulations!!!

We have seen all the git commands you need to start using git as a version control programm of your work. This covers most of the things you'll be using while working in software development. Git is simple and powerful.

The current state of the course is:

- [X] Git Essentials: covers day to day tasks for a junior developer.
- [ ] Git Intermediate: good practices and more in deep knowledge of the basics.*Coming soon.*
- [ ] Git Advanced: covers advanced tasks only senior levels professionals will use. *Coming soon.*

**Thank you for using this course to learn Git, your feedback will be highly appreciated. You can contact the author of this course by e-mail to contact@javimolina.dev**

[Back to Table of Contents](#10-table-of-contents)

## License

This course is available under the [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/) license. You are free to share and adapt this work, even for commercial purposes, as long as you provide proper attribution to the original author.

### How to attribute
Please credit this work to "Javi Molina (JaviEarth)" and include a link to the original project if possible.
