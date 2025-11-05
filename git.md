---
title: Git Daily
---

| Git Task                       | Git Commands                                                                                                                                                                                                                                              |
| ------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Tell Git who you are           | git config --global user.name "Sam Smith"<br>git config --global user.email sam@example.com                                                                                                                                                               |
| Create a new local repository  | `bash\ngit init\n`                                                                                                                                                                                                                                        |
| Check out a repository         | `bash\ngit clone /path/to/repository\n`\n`bash\ngit clone username@host:/path/to/repository\n`                                                                                                                                                            |
| Add files                      | `bash\ngit add <filename>\n\ngit add *\n`                                                                                                                                                                                                                 |
| Commit                         | `bash\ngit commit -m "Commit message"\n`\n`bash\ngit commit -a\n`                                                                                                                                                                                         |
| Push                           | `bash\ngit push origin master\n`                                                                                                                                                                                                                          |
| Status                         | `bash\ngit status\n`                                                                                                                                                                                                                                      |
| Connect to a remote repository | git remote add origin <server><br>git remote -v                                                                                                                                                                                                           |
| Branches                       | `bash\ngit checkout -b <branchname>\n`\n`bash\ngit checkout <branchname>\n`\n`bash\ngit branch\n`\n`bash\ngit branch -d <branchname>\n`\n`bash\ngit push origin <branchname>\n`\n`bash\ngit push --all origin\n`\n`bash\ngit push origin :<branchname>\n` |
| Update from remote repository  | git pull<br>`bash\ngit merge <branchname>\n`\ngit diff<br>git diff --base <filename><br>`bash\ngit diff <sourcebranch> <targetbranch>\n`\n`bash\ngit add <filename>\n`                                                                                    |
| Tags                           | `bash\ngit tag 1.0.0 <commitID>\n`\n`bash\ngit log\n`\n`bash\ngit push --tags origin\n`                                                                                                                                                                   |
| Undo local changes             | `bash\ngit checkout -- <filename>\n`\n`bash\ngit fetch origin\n\ngit reset --hard origin/master\n`                                                                                                                                                        |
| Search                         | git grep "foo()"                                                                                                                                                                                                                                          |

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
