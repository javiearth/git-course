# Git Essentials cheatsheet
<small>More information in my [git-course](https://github.com/javiearth/git-course).</small>

### Basic commands

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

### Tags

| Syntax | Description |
|---|---|
|git tag -a tag-name | Adds a tag to the last commit |
|git tag tag-name commit-hash | Adds a tag to the specified commit |
|git tag -d tag-name | Deletes the specified tag (you can use --delete instead of -d) |

### Reset

| Syntax | Description |
|---|---|
|git reset --soft hash-number | Deletes all commits made after the specified one but preserves stage and working directory |
|git reset --mixed hash-number | Deletes all commits made after the specified and the stage, but preserves the working directory (default reset, you can use it without '--mixed')|
|git reset --hard hash-number | Deletes all commits made after the specified one, as well as stage and working directory |
|git reset HEAD~N | (Substitute N with a number) You can use this notation to delete the last N commits with any reset |

### Branches

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

### Stash

| Syntax | Description |
|---|---|
|git stash |Saves the stage and working directory to the stash area |
|git stash pop |Recovers stage and working directory from the last stash and deletes it|
|git stash pop stash@{index}|Recovers stage and working directory from the indexed stash and deletes it|
|git stash apply |Recovers stage and working directory from the last stash preserving the stash|
|git stash list |Displays the stash list |
|git stash drop |Deletes the last stash |
|git stash drop stash@{index} |Deletes the specified stash |

---
<small>Licensed under the [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) by [Javi Molina (JaviEarth)](https://github.com/javiearth).</small>
