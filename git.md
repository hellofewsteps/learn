---
title: Git Daily
---

- **Tell Git who you are**
  - `git config --global user.name "Few Steps"` [configure your Git user name]
  - `git config --global user.email hellofewsteps@icloud.com `[configure your Git email]
- **First Time Only**
  - `git init`
  - `git remote add origin <serve/urlr>` [Connect to a remote repository]
  - `git clone <remoteURL> `[Clone remote to local [First Time Only]]
- **two ways to save**
  - `git add .` [staging, ‘.’ means all]
  - `git commit -m “comment or message”` [committing]
- **Save to remote and update local**
  - `git push origin <branchName>` [master/develop] [push commits to remote]
  - `git pull origin <branchName>` [master/develop] [pull latest code from remote branch]
  - `git merge <branchName>` [merge a different branch into active branch]
    - merge flow: [switchBranch] → [updateCode(active branch's)] → [merge other branch]

| Step | Command                | Purpose                 |
| ---- | ---------------------- | ----------------------- |
| 1️⃣   | git checkout master    | Switch to target branch |
| 2️⃣   | git pull origin master | Update with latest code |
| 3️⃣   | git merge develop      | Merge another branch    |

- **debugging**
  - `git status` [show stage status]
  - `git branch` [show all branches and current branch]
- branches
  - `git checkout [] <branchName>`
    - [if ‘-b’: create new branch, empty: switch]
  - `git push origin <branchname>` [Push the branch to remote repository]
  - `git push --all origin` [push all branches to remote repository]
  - `git branch -d <branchName>` [-D: force delete local branch] [Delete local branch]
  - `git push origin --delete dev2` [Delete remote branch]
  - `git push origin :<branchname>` [delete a branch on remote repository]
- **Undo local changes**
  - `git fetch origin` [fetch latest history from remote]
  - `git reset --hard origin/master` [reset local branch to remote]
  - Explanation:
    - You changed a file locally, and your teammate updated it on GitHub.
    - `git fetch origin` gets your teammate’s update but doesn’t change your file.
    - `git reset --hard origin/master` then deletes your version and makes your files match GitHub exactly.

| Step                                     | Command                          | Local `hello.txt` says    | Remote `hello.txt` says |
| ---------------------------------------- | -------------------------------- | ------------------------- | ----------------------- |
| Start                                    | —                                | "Hello World"             | "Hello World"           |
| You edit                                 | —                                | "Hello from me"           | "Hello World"           |
| Teammate pushes                          | —                                | "Hello from me"           | "Hello from teammate"   |
| You run `git fetch origin`               | `git fetch origin`               | "Hello from me"           | "Hello from teammate"   |
| You run `git reset --hard origin/master` | `git reset --hard origin/master` | **"Hello from teammate"** | "Hello from teammate"   |

- **Others**
  - git diff [view all merge conflicts]
  - git diff --base <filename> [view conflicts against base file]
  - git diff <sourcebranch> <targetbranch> [preview changes before merging]
  - git tag 1.0.0 <commitID> [tag a specific commit]
  - git log [view commit IDs]
- **Search**

  - git grep "foo()"` [search working directory for a string]

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
