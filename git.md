---
title: Git Daily
---

// tell git who you are

- git config --global user.name "Sam Smith" [set your username]
- git config --global user.email sam@example.com [set your email]

// create a new local repository

- git init [initialize repository]

// check out a repository

- git clone /path/to/repository [clone local repo]
- git clone username@host:/path/to/repository [clone from remote repo]

// add files

- git add <filename> [stage specific file]
- git add . [stage all files]

// commit changes

- git commit -m "commit message" [commit staged files]
- git commit -a [commit all modified and tracked files]

// push changes

- git push origin master [push commits to master branch]

// check status

- git status [show changed and staged files]

// connect to a remote repository

- git remote add origin <server> [add remote repository]
- git remote -v [list remotes]

// branches

- git checkout -b <branchname> [create and switch to new branch]
- git checkout <branchname> [switch branches]
- git branch [list branches]
- git branch -d <branchname> [delete branch]
- git push origin <branchname> [push branch to remote]
- git push --all origin [push all branches]
- git push origin :<branchname> [delete remote branch]

// update from remote repository

- git pull [fetch and merge from remote]
- git merge <branchname> [merge branch into current branch]
- git diff [view changes]
- git diff --base <filename> [compare with base file]
- git diff <sourcebranch> <targetbranch> [compare branches]
- git add <filename> [mark resolved after conflict]

// tags

- git tag 1.0.0 <commitID> [create tag]
- git log [view commit history / get commitID]
- git push --tags origin [push all tags to remote]

// undo local changes

- git checkout -- <filename> [revert file to last commit]
- git fetch origin [get latest remote changes]
- git reset --hard origin/master [reset local branch to remote]

// search

- git grep "foo()" [search repository for text or function]

```cmd

// First Time Only
- git init
- git remote add origin <serve/urlr> [Connect to a remote repository]
- git clone <remoteURL> [Clone remote to local [First Time Only]]


// two ways to save
- git add . [staging, ‘.’ means all]
- git commit -m “comment or message” [commiting]

- git push origin <branchName> [master/develop] [push commits to remote]
- git pull origin <branchName> [master/develop] [pull latest code from remote branch]
- git merge <branchName>. [merge a different branch into active branch]
  - Flowchart:
    - [switchBranch] → [updateCode(active branch's)] → [merge other branch]

| Step | Command                | Purpose                 |
| ---- | ---------------------- | ----------------------- |
| 1️⃣   | git checkout master    | Switch to target branch |
| 2️⃣   | git pull origin master | Update with latest code |
| 3️⃣   | git merge develop      | Merge another branch    |

// debugging
- git status [show stage staus]
- git branch [show all branches and current branch]

// branches
- git checkout [] <branchName>
  - [if ‘-b’: create new branch, ‘-d’: delete, empty: switch]
- git push origin <branchname>.     [Push the branch to your remote repository, so others can use it:]
- git branch -d <branchName> [-D: force delete local branch] [Delete local branch]
- git push origin --delete dev2 [Delete remote branch]

```

- **git stash**: is a temporary storage feature in Git — it lets you save your uncommitted changes (like edited files) without committing them and return to a clean working directory.

  | Command           | What it does                                               |
  | ----------------- | ---------------------------------------------------------- |
  | `git stash`       | Save (stash) your uncommitted changes.                     |
  | `git stash list`  | Show all stashes you’ve saved.                             |
  | `git stash pop`   | Reapply the most recent stash and remove it from the list. |
  | `git stash apply` | Reapply a stash but keep it in the list.                   |
  | `git stash drop`  | Delete a specific stash.                                   |
  | `git stash clear` | Remove **all** stashes.                                    |

- **.gitignore file**: is a plain text file that tells Git which files or folders it should ignore — meaning not track, commit, or push to your repository.

  - add .gitignore on root folder
  - If you’ve already had files tracked that should be ignored now (e.g., target/ or reports), you’ll need to remove them from tracking first:
    - `git rm -r --cached target/ allure-results/ test-output/`
    - `git commit -m "Remove ignored files from tracking`
  - check hidden files on mac: Command + Shift + .

- **Gist**: A Gist is a simple way to share code snippets, notes, or small files using GitHub. Every Gist is actually a Git repository.

| Type            | Visibility               | Accessible by search? | Use case                            |
| --------------- | ------------------------ | --------------------- | ----------------------------------- |
| **Public Gist** | Anyone can see it        | ✅ Yes                | Sharing code openly                 |
| **Secret Gist** | Only those with the link | 🚫 No                 | Personal notes or sharing privately |

Ref:

- https://confluence.atlassian.com/bitbucketserver/basic-git-commands-776639767.html
- github section of: https://gale.udemy.com/course/rest-api-automation-testing-rest-assured/learn/lecture/11793550#overview
