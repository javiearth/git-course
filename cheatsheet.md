# Git cheatsheet

### Basic commands

| Syntax | Description |
|---|---|
|git config | Access git configuration options |
|git init | Initializes the control version of the directory |
|git status | Shows changes made in stage and working directory since last commit |
|git add file-name | Adds changes made in the specified file to the stage |
|git add . | Adds changes made in the working directory to the stage |
|git commit -m "your-message" | Commit changes for the stage to the branch |
|git log | Shows the last 4 commits in the current branch |
|git reflog | Shows the history of the whole repository |
|git checkout commit-hash | Recover the working directory of the specified commit |

### Tags

| Syntax | Description |
|---|---|
|git tag -a tag-name | Adds a tag to the last commit |
|git tag tag-name commit-hash | Adds a tag to the specified commit |
|git tag -d tag-name | Deletes the specified tag |
|git tag --delete tag-name | Deletes the specified tag |

### Reset

| Syntax | Description |
|---|---|
|git reset --soft HEAD~1 | Deletes the last commit but preserves stage and working directory | <!-- and other numbers? -->
|git reset --soft hash-number | Deletes all commits made after the specified one but preserves stage and working directory |
|git reset --mixed hash-number | Deletes all commits made after the specified and the stage, but preserves the working directory (default reset)|
|git reset hash-number | Deletes all commits made after the specified one and the stage, but preserves the working directory |
|git reset --hard hash-number | Deletes all commits made after the specified one, as well as stage and working directory |

### Branches

| Syntax | Description |
|---|---|
|git branch new-branch | creates a new branch |
|git branch -m new-branchs-name | Rename the current branch |
|git switch branch-name | Switches to the specified branch |
|git checkout branch-name | Switches to the specified branch |
|git branch -d branch-name | Deletes the specified branch |
|git branch --delete branch-name | Deletes the specified branch |
|git merge branch-name | copy the last commit of the specified branch into the current branch and creates a merge commit |
|git rebase branch-name | moves the commits in the current branch to apply after those from the specified branch |
|git cherry-pick commit-hash | copy the specified commit to the current branch and gives it a different hash |

### Stash

| Syntax | Description |
|---|---|
|git stash | Saves the stage and working directory to the stash area |
|git stash pop | Recovers stage and working directory from the last stash and deletes it|
|git stash pop stash@{index}| Recovers stage and working directory from the indexed stash and deletes it|
|git stash apply | Recovers stage and working directory from the last stash preserving the stash|
|git stash list | Displays the stash list |
|git stash drop | Deletes the last stash |
|git stash drop stash@{index} | Deletes the specified stash |

---
<small>Licensed under the [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) by [Javi Molina (JaviEarth)](https://github.com/javiearth).</small>
