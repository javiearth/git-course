#Git course
Version: 0.0.1

## About this course.

This is a brief course that teaches by examples, its aim is to you achive a level of understanding about git enough to work in most projects.

This course is based on my personal experience practicing Git commands on my computer. The content reflects what I learned through experimentation, asking questions, and researching general concepts online.

**Important**
Git commands are the same no matter which OS you're working with. Anyway, the commands in the *installation and previous knowledge* section may be different for you OS. Apart from that, everything should be same in your machine.

## Introduction to git.

Git is an open-source, distributed, version control software created by Linus Torvalds while working on Linux. While using git we work in local (in our computer only), we'll see how to work with the cloud in the GitHub section of this course.

## Previous knowledge:

It is convenient that you learn very few commands to use in your terminal. I recommend to practice these:

- `pwd` prints the current working directory.
- `ls` lists the files and subdirectories in the current directory.
- `cd` change directory to a specified directory.
- `mkdir` creates a new directory.
- `touch` creates a new file.
- `rm -r` removes a file or directory.
- `mv` moves a file from one directory to another.
- `cp` copies a file from one directory to another.

<!-- ADD EXAMPLES FOR EACH COMMAND -->

That's all, let's start with git.

## Installation

In Unix systems (Linux and MacOS) git is usually already installed. You can check if git is installing just typing `git` on your terminal. Anyway, you can install git writing `sudo apt install git` in the terminal (bash). 

## Configuration

We need an username and an email to start working with git, so we need to configure git using the next commands:

`git config --global user.name "yourusername"`
`git config --global user.mail "your@mail.com"`

Aclaration: we write the command `git config` followed by the configuration level (global) followed by the data we want to modify (user's name and email). If you just write `git config` it displays a list of different actions to work with the configuration file.

*If you want to work with GitHub is important that you use one of the email addresses you have verified in your GitHub account. GitHub uses email addresses to link all your contributions to your profile.*

## Starting a version control of your project

Create a new directory with the name of your project.

<!-- ADD EXAMPLE OF THE TERMINAL -->

Change to the directory you want to start your version control and write:

`git init`

This command creates a hidden subdirectory (.git), but you don't need to know anything about it, you won't use it, git manages it for you.

<!--The terminal now displays your current working directory and something like 'master'. This means your are working in the master branch of your project, we'll see mor about this later.-->

Create a new document, a README.md file for example.

`touch README.md`

Let's see now the status of your project with the following command:

`git status`

Because you have made changes in your project, git will show you the modified changes inside the directory of your proyect in read. To save those changes to the git repository you need first, to add the files modified to the git repository and second, to save a snapshot of the current development state of your project. 

*Git can display the changes in each file with the command `git diff`, this prints in your terminal the changes done in every file since the last commit (you don't need to do `git status`, you can use it at any time).*

Write `git add` followed by the name of the files you want to add to the repository or `git add .` to add all modified files.

Next, let's do our first commit as follows:

`git commit -m "your comment here"`

Git has taken a snapshop of your project. If you run the `git status` command again you'll see there are no changes to save in your git repository, it is up to date.

Let's practice a bit more, write something in your README.md file, save it and run the command you've just learnt again.

That's great! We can always see the progress of our projects' versions with the command:

`git log`

This command usually displays the last 4 commits you have done. Let's take a closer view to the log.

You can see that your are working in the branch master because the *HEAD* points (`-->`) to it. You're project has only one branch at the moment, we'll see more about branches in later.

You also see a list of commits with a long code of numbers and letters, that is the hash of your commit, it is the commit's ID. You can see the message you used to describe the changes made to your project in each commit, the author, the date and the time.

There are some other ways to display the log adding some flags (like --graph) to the `git log` command, but we don't need it at the moment.

## Moving among commits.

The interest thing about a version control program like git is be able to do and undo changes, so we can recover a version which works in the case something goes wrong while developing.

Let's say that for some reason we want to come back to a previous version of our project. Remember that about the hash of each commit? use `git log` and copy the hash of your first commit (or any you like, asuming you've being practicing on your own). Write this command:

`git checkout commit_hash_number`

*Remember that in Linux you can use the middle button of your mouse to paste something you copied.*

Open your README.md file, is there something missing? That's is! The project has been restored to a previous state and everything in the directory (including all files and subdirectories) have changed as everything was in the commit you moved on.

Now type `git log`. You'll see that you're working on the commit you selected before, but where is the last commit? Don't panic!. it's there somewhere. To see all commits type the following:

`git reflog`

This command shows all the commits. You see HEAD is in other commit that is not the lastest you did. At this point you can continue working from this state and forget about the last commit (maybe you don't want to keep the changes in the last commit for some reasons) or go back to the last latest commit again. To do so you can use `git checkout` followed by a hash or better option, write the name of the branch. Git understand you want to go to the newer commit in that branch.

`git checkout master`

## How git works: staging and working directory

Before moving any forward is useful to clarify some concepts:

- Commit: a snapshot of the project under development. A commit saves the state of the directory, including all subdirectories and files so far and the information they contain.

- Stage: is a kind of draft that contains all the changes made since the last commit until you add changes to the git repository. That means, it contains all the changes between your last `git commit` and your last `git add`. It is unusual but if for some reason you make changes after using git add, you'll neet to use git add again.

- Working directory: is the directory where you are working. In the case of using git, the working directory of your project, where all files and subdirectories of your project are located.


## Discarding changes and recovering versions.

Checkout allows as to move between commits, but doesn't change the flow of the project. In the last example, when you moved to the master branch (the only one you we have so far), you went to the last commit.

Let's make an error in our README.md file, type something, e.g., "this is an errorrrrrrrrr".

Then use what you already know to save a new version of your project.

<!-- ADD EXAMPLE OF THE TERMINAL 
`git add .
`git commit -m "This is wrong!" -->

Ok, we made a mistake! No problem, let's go back to the precious commit, before "This is wrong", but instead of using `checkout` use the `git reset` followed by the hash of the commit.

`git reset HASHNUMBER`

If you check your project or use `git log` or even `git reflog` everything looks similar, but there is a difference. Try `git checkout master` now and see what happens. Git says `Already in master` and the README.md file doesn't have our error! That's is because for git, our branch ends here and the last commit we did is no anymore in our branch. You still can recover the file with a checkout because you'll see the commit in the reflog anyway, but this is not how `reset` is intended for.

There are different kind of resets we can do: soft, mixed and hard. 

All resets move the HEAD to the commit selected, that means, you're back to that commit and work as if you haven't done any newer commit after that one. The sof reset (`git reset --soft) doesn't make anything else, so the stage and the working directory will remain the same. The soft reset is very useful when you've made a mistake in the last commit and want to fix it quickly, e.g. when you wrote the last message. You can use `reset --soft HEAD~1` so you don't need to copy the hash number of the commit, this is faster because automatically undo the last commit.

The reset by default (`git reset` or `git reset --mixed`) do eliminate the stage, so you'll need to use `git add` before commit any changes to yor git repository. This kind of reset is useful when you want to undo the last commits but want to check the files before do any more commits.

The hard reset (`git reset --hard`) undo the commits after the selected one, eliminates the stage and doesn't conserve any changes in the working directory. That means that the files in your project directory are re-stablished to the version of the commit selected in thehard reset, no changes done after that commit will remain, so there is nothing to add to the stage or changes to commit. Hard resets are useful when you want to eliminate everything since the last commit, like when you are experimenting, you changed something and it didn't work.

## Taggin

Messages in commits may no me enough to locate those versions of our project that are more important than others. While adding comments in every commit is important to track quickly all changes we've done, it is also imprtant to 'destacar' all version that are special for some reason. We can do this adding tags to commits. A tag will be 'destacada' in the log, so we can easily track them.

To add a tag use one the following commands:

`git tag tag_name` adds a tag to the last commit.

`git tag tag_name hash_number` adds a tag to the selected commit.

Important: tags are unique, we can't have the same tag in two different commits.

To delete a tag use any of these commands:

`git tag -d tag_name`
`git tag --delete tag_name`

## Branches.

It is useful to separate the development of our project in branches because it opens the possibility to add features and make changes even further without compromising the safety of our project while organizing all its functionallyties. Branches allows us to work in different aspects of our project that can be devolop independiently from the other parts of our project, like developing a new feature. It is also useful to have a branch where you work more often and another to save just the very important updates that you don't want to compromise for any reason.

At the moment we are working with git locally but branches will take even more sense when we develop projects in teams. Here are a few examples of branches you can use while developing your project and why to organize your git repository with them.

Main: the very important versions of you project you don't want to loose for any reason.
Develop: the branch where you are working in and published more often.
Feature: where you develop additional characteristics of your project that are not essential at the moment.

We'll see just a very few more usual branches in the GitHub course, but there is no point to complicate this git course at the moment.

### Renaming a branch.

You may have noticed that I didn't mention the 'master' branch. This is because currently is uncommon to work with a 'master' branch, it suggests some kind of superiority or jerarquy with most people feels unconfortable working with, so we usually use 'main' instead. So, our first work with branches will be re-name the only one we have so far using the following command:

`git branch -m new_branch_name` (e.g., `git branch -m main`)

This will change the name of the branch we are currently working on. Check it with a `git log`

### Creating a new branch.

To do so we use the command `git branch name_of_new_branch`, e.g.: `git branch develop` or `git branch feature`.

Use `git log`, it won't show anything about any new branch because `git log` only shows the branch you're working on. If you use `git reflog` instead, you'll see the name of all branches and where is the HEAD.

### Switching between different branches.

Use `git switch branch_name` or `git checkout branch_name` to change between branches. Since this moment all changes made in your project will remain in that branch we are currently working on and won't affect others.

So let's make some changes in our project. You can add something at the end of your README.md, create a new one or whatever you prefer.

After committing the changes do a `git log`, you'll see the log of the current branch, but git won't tell you anything about the others. To view all commits you need to do a `git reflog`. Now you see all branches and where the HEAD is located, that means, where you are currently working. You may notice that the develop branch is one commit ahead of the main branch. Switching to the main branch will affect your working directory depending on the commits done.

## Combining branches.

We can update a branch with the changes done in any other at any time. To do so, we have different options:

### git merge

Switch to the branch you want to update and use the merge command followed by the name of the branch you want to copy.

`git merge branch-name`

For example, to update the branch main we need first switch to that branch using `git switch main` or `git checkout main`, and after that merge the develop branch into that one with the command `git merge develop`.

Run `git log` to see the changes made in main. Merge operations are shown in the log.

What merge actually does is combined two branches, creating an aditional commit named merge commit. It keeps the history of both branches and registers how did them combine.

### git rebase

Rebase reorganize the commits in one of the branches to apply in another. Imaging you are working in the feature branch but while working in the new feature the branch develop has been updated. You might be interested in apply those changes in the feature branch and keep working in the new feature. You can do that using rebase. To do so, switch to the branch feature and use `git rebase name-of-the-branch`, e.g., `git rebase develop`. In our example, the commits in the branch feature have moved to apply after the commits in the branch develop.

Rebase re-write the history of the branch (the feature branch in the example).

### git cherry-pick

This command copies one specified commit from one of the branches and applies it to another. For example, let's say we want to apply a commit in the feature branch to the develop branch. We have to switch to the main branch and run the cherry-pick command with the hash nambur of the commit in feature. A new commit will appear in the main branch which is a cipy of the one picked from the feature branch, but it will have a different hash number despites it is a copywith the same content.

## Conflicts.

Solve conflicts is a common task in git while working in different branches. Conflicts may occur when one of the following happens:

- Two branches have modified the same lines of a file.
- A file was modified in one branch but deleted in another.
- There are discrepancies in the changes while doing a merge, rebase or cherry-pick.

When a conflict occurs, git stop the operation and highlight the conflict as "both modified" indicating the files in conflict.

### How to solve a conflict?

1. Identify the files in conflict.
2. Open the file and locate the conflict.
When open the file you'll find that git has make some chenges, showing the conflict. It will look something like this:

*<<<<<<< HEAD
The color is red
=======
The color is yellow
>>>>>>> feature*

3. Solve the conflict manually and save the file.
4. Tell git the conflict is solved. To do so add the file to the stage with `git add file-name`.
5. End the process using `git commit` again.

## The stash.

Sometimes, while we are working in one branch and we need to change to another but we don't want to commit any changes yet, or maybe we want to clean our working environment for some reason but we don't want to lose the changes we made. In these cases, we can use the stash.

The stash is a temporary area where the changes realized in the working directory and the stage are saved. Think about it as a quicksave, or a draft. We can use the following command:

`git stash`

By doing so every changes made so far since the las commit are safe in the stash. Now we can change between branches. Do some changes in your working directory and try to switch to another branch. The operation will be aborted as there are changes don't saved. Write `git stash` and try again, now git allows you to switch between branches. All changes have been remoed from your working directory and stage, there are hidding somewhere else (in the stash). You won't get the changes back until you recover them from the stash.

To recover something from the stash you can use two different commands:

- `git stash pop`. This recovers the stash and clear it.
- `git stash apply`. This recovers the changes saved in the stash but doesn't clean it.

You can have several stash saved. You can list them using `git stash list`. Use the command and you see a list that starts with the word 'stash' followed by an at and a number between brackets, that is the stash index. You can recover any particular stash using its index (e.g., `git stash apply stash@{1}`).

To clean the stash list you can drop one by one with `git stash drop` to clean the newer stash or `git stash drop stash@{index}` to clean a specified stash. You can clear the whole list typing `git stash clear`. Stash are a special kind of commits and they will remain saved until you clear the stash area.

## Conclusion.

We have seen all the git commands you need to start using git as a version control programm of your work. This covers most of the things you'll be using while working in software development. Git is simple and powerful.

In spite that git is very useful working in local, it shanes in cloud environments where teams of software developers work remotely. There are different solutions for that and one of the most used is GitHub. See the GitHub course to learn how to use git in the cloud.

Thank you for using this course to learn git, your feedback will be highly appreciated. You can contact the author of this course by e-mail to contac@javimolina.dev

## License

This course is available under the [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/) license. You are free to chare and adapt this work, even for commercial purposes, as long as you provide proper attribution the the original author.

### How to attribute
Please credit this work to "Javi Molina (JaviEarth)" and include a link to the original project if possible.
