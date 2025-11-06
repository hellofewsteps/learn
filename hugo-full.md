---
title: 🚀 Hugo Setup from Beginning to End (Using YAML + Hugo Profile Theme)
---

This tutorial explains how to set up a **Hugo** static site from scratch using the **Hugo Profile** theme, a **YAML configuration file**, and **Netlify deployment**.

## 🧩 Step 1: Install Hugo (Extended Version)

Open your terminal and run:

```bash
brew install hugo
```

Verify the installation:

```bash
hugo version
```

Expected output:

```
hugo v0.133.1+extended darwin/arm64 ...
```

Make sure it says **extended** — required for themes using SCSS.

---

## 📁 Step 2: Create a New Hugo Site

```bash
hugo new site mycoursesite
cd mycoursesite
```

This creates the Hugo project folder structure.

---

## 🎨 Step 3: Add the Hugo Profile Theme

Add the theme as a Git submodule:

```bash
git init
git submodule add https://github.com/gurusabarish/hugo-profile.git themes/hugo-profile
```

---

## ⚙️ Step 4: Convert to YAML Configuration

Replace the default TOML config with a YAML file:

```bash
mv config.toml config.yaml
nano config.yaml
```

Paste the following content:

```yaml
baseURL: "https://example.com/"
languageCode: "en-us"
title: "My Courses Hub"
theme: "hugo-profile"

params:
  author: "Your Name"
  description: "My Udemy and YouTube Courses"
  favicon: "images/favicon.png"

  social:
    youtube: "https://youtube.com/@YourChannel"
    twitter: "https://twitter.com/YourProfile"
    linkedin: "https://linkedin.com/in/YourProfile"

menu:
  main:
    - name: "Home"
      url: "/"
      weight: 1
    - name: "Udemy Coupons"
      url: "/udemy-coupons/"
      weight: 2
    - name: "YouTube Courses"
      url: "/youtube-courses/"
      weight: 3
    - name: "YouTube Videos"
      url: "/youtube-videos/"
      weight: 4
    - name: "Contact"
      url: "/contact/"
      weight: 5
```

Save and close (`Ctrl + O`, `Enter`, `Ctrl + X`).

---

## 🏗️ Step 5: Create Site Pages

Create five main pages:

```bash
hugo new _index.md
hugo new contact.md
hugo new udemy-coupons.md
hugo new youtube-courses.md
hugo new youtube-videos.md
```

Then edit each file under the `content/` folder.

### content/\_index.md

```markdown
---
title: "Home"
---

# 👋 Welcome to My Courses Hub

Here you’ll find all my courses, tutorials, and links to Udemy discounts and YouTube lessons.
```

### content/contact.md

```markdown
---
title: "Contact Me"
---

You can reach me via email at [you@example.com](mailto:you@example.com)  
or on [LinkedIn](https://linkedin.com/in/yourprofile).
```

### content/udemy-coupons.md

```markdown
---
title: "Udemy Coupons"
---

Here are my latest Udemy courses with active coupons:

- [Python for Beginners](https://www.udemy.com/course/xyz/?couponCode=NOV25)
- [Web Development Masterclass](https://www.udemy.com/course/abc/?couponCode=NOV25)
```

### content/youtube-courses.md

```markdown
---
title: "YouTube Courses"
---

Watch my free full-length courses on YouTube:

- [Full Python Bootcamp](https://www.youtube.com/watch?v=xxxxx)
- [HTML & CSS Crash Course](https://www.youtube.com/watch?v=yyyyy)
```

### content/youtube-videos.md

```markdown
---
title: "YouTube Videos"
---

Check out some of my shorter tutorials:

- [Python Tips & Tricks](https://www.youtube.com/watch?v=zzzzz)
- [Web Dev Setup on Mac](https://www.youtube.com/watch?v=wwwww)
```

---

## 💻 Step 6: Run the Site Locally

Run the local development server:

```bash
hugo server -D
```

Open your browser and go to:

👉 [http://localhost:1313](http://localhost:1313)

You’ll see the homepage and menu navigation.

---

## 🌐 Step 7: Deploy to Netlify

### 1️⃣ Push the Site to GitHub

```bash
git add .
git commit -m "Initial Hugo site"
git remote add origin https://github.com/yourname/mycoursesite.git
git push -u origin main
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

| Task               | Command                                 |
| ------------------ | --------------------------------------- |
| Update Hugo        | `brew upgrade hugo`                     |
| Update theme       | `git submodule update --remote --merge` |
| Add a new page     | `hugo new new-page.md`                  |
| Rebuild for deploy | `hugo`                                  |

---

## 🧱 Folder Structure Overview

```
mycoursesite/
├── config.yaml
├── netlify.toml
├── content/
│   ├── _index.md
│   ├── contact.md
│   ├── udemy-coupons.md
│   ├── youtube-courses.md
│   └── youtube-videos.md
├── themes/
│   └── hugo-profile/
└── public/   ← built site (after running `hugo`)
```

---

## ✅ Summary

You’ve now built a complete Hugo website from scratch using:

- **Hugo Extended**
- **YAML-based configuration**
- **Hugo Profile theme**
- **Netlify for free hosting**

Your site is ready to customize and publish!

---

Would you like me to make a **ready-to-use folder structure (ZIP)** of this tutorial’s project so you can start instantly?
