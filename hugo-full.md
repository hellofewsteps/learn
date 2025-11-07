---
title: 🚀 Hugo Setup from Beginning to End (Using YAML + Hugo Profile Theme)
---

## 🧩 Step 1: Install Hugo (Extended Version)

Open your terminal and run and Make sure it says **extended** — required for themes using SCSS.

```bash
brew install hugo                         # install
hugo version                              # verify version
hugo v0.133.1+extended darwin/arm64 ...   # Expected output:

hugo new site . --format yaml             # Create a New Hugo Site
```

## Step 2: Add `.gitignore` file

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

## 🎨 Step 3: Add the Hugo Profile Theme

Add the theme as a Git submodule:

```bash
git init
git submodule add https://github.com/gurusabarish/hugo-profile.git themes/hugo-profile
```

# Step 4: Add `hugo.yaml` file content

- Ref: https://github.com/adityatelange/hugo-PaperMod/wiki/Installation

## 🏗️ Step 5: Create Site Pages

Create five main pages:

```bash
hugo new _index.md
hugo new contact.md
hugo new udemy-coupons.md
hugo new youtube-courses.md
hugo new youtube-videos.md
```

Sample content of the pages:

```
---
title: "Home"
draft: false
---
```

## 💻 Step 6: Run the Site Locally

```bash
hugo server
hugo server -D    # Debug mode Run the local development server:
```

## 🌐 Step 7: Deploy to Netlify

### 1️⃣ Push the Site to GitHub

```bash
git add .
git commit -m "Initial Hugo site"
git remote add origin https://github.com/yourname/mycoursesite.git
git push origin main
```

### 2️⃣ Create a Netlify Account

Go to [https://app.netlify.com](https://app.netlify.com)
→ Click **“Add New Site → Import from GitHub”**
→ Select your repository.

Set build settings:

```
Build command: hugo
Publish directory: public
```

Then click **Deploy**.
Netlify will build and host your site (e.g., [https://yourname.netlify.app](https://yourname.netlify.app)).

---

## 🧾 Step 8: Add a `netlify.toml` File

At the root of your project, create `netlify.toml` and add:

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

**Explanation:**

- Enables garbage collection and minification
- Uses the correct Hugo extended version
- Sets environment variables for production and preview builds

---

## 🧹 Maintenance Commands

```bash
brew upgrade hugo                              # Update Hugo
git submodule update --remote --merge          # Update theme
hugo new new-page.md                           # Add a new page
hugo                                           # Rebuild for deploy
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
