---
title: 🚀 Hugo Setup from Beginning to End (Using YAML + Hugo Profile Theme)
---

## 🧩 Step 1: Install Hugo (Extended Version)

Open your terminal and run and Make sure it says **extended** — required for themes using SCSS.

```bash
brew upgrade hugo                         # Update Hugo
git submodule update --remote --merge     # Update theme
brew install hugo                         # install
hugo version                              # verify version
hugo v0.133.1+extended darwin/arm64 ...   # Expected output:

hugo new site . --format yaml             # Create a New Hugo Site in root folder

hugo new _index.md                        # create new phome page
hugo new contact.md                       # create other pages


# ----------------------------------------
#     Add .gitignore first
# ----------------------------------------

git add .
git commit -m "Initial Hugo site"
git remote add origin https://github.com/yourname/mycoursesite.git
git push origin main


                                         # install theme: Papermod/Zen
git submodule add https://github.com/gurusabarish/hugo-profile.git themes/hugo-profile


hugo server       # Run locally
hugo server -D    # Debug mode Run the local development server:
hug build         # Build the project

```

## Sample `.gitignore` file

```
.DS_Store
Thumbs.db
.hugo_build.lock
hugo_stats.json
public/
resources/
node_modules/
.vscode/
.firebase/
```

## `hugo.yaml` file content

- PaperMod Ref: https://github.com/adityatelange/hugo-PaperMod/wiki/Installation
- Zen Ref:

## Sample content of the pages:

```bash
---
title: "Home"
draft: false
---
```

## Deploy to Netlify

- Go to [https://app.netlify.com](https://app.netlify.com)
  → Click **“Add New Site → Import from GitHub”**
  → Select your repository.
- Then click **Deploy**.
- At the root of your project, create `netlify.toml` and add:

```toml
[build]
  command = "hugo --gc --minify"
  publish = "public"

[build.environment]
  HUGO_VERSION = "0.152.2"
  HUGO_ENV = "production"
  HUGO_EXTENDED = "true"
  HUGO_ENABLEGITINFO = "true"

[context.production.environment]
  HUGO_ENV = "production"

[context.deploy-preview.environment]
  HUGO_ENV = "staging"
```

## Firebase Hosting/Deploy:

```bash
hugo
npm install -g firebase-tools
firebase login
firebase init   #configure whatever needed
hugo
firebase deploy
```

## Suggestion for modification

```
# https://discourse.gohugo.io/t/issue-with-hugo-site-links-after-deploying-to-netlify/56216

1) Edit the .gitignore file in the root of your project. It should look something like this:

.DS_Store
.hugo_build.lock
hugo_stats.json
node_modules/
public/
resources/


2) Remove the public directory (and other cruft) from source control and push changes:

git rm -rf public/
git rm .hugo_build.lock
git rm .DS_Store
git add -A && git commit -m "Cleanup repo" && git push
```
