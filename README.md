# 🌐 Viveksite — Personal Portfolio & Blog

A clean, fast, and minimal personal portfolio and blog built with [Hugo](https://gohugo.io/) and the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme. Deployed on [Netlify](https://www.netlify.com/).

🔗 **Live Site:** [kpvivek.netlify.app](https://kpvivek.netlify.app/)

---

## 📋 Table of Contents

- [Features](#-features)
- [Project Structure](#-project-structure)
- [Prerequisites](#-prerequisites)
- [Getting Started](#-getting-started)
- [Running Locally](#-running-locally)
- [Adding Content](#-adding-content)
  - [Adding a New Project](#1-adding-a-new-project)
  - [Adding a Trip / Blog Post](#2-adding-a-trip--blog-post)
  - [Adding a New Section](#3-adding-a-new-section-page)
  - [Adding Images](#4-adding-images)
- [Configuration Guide](#%EF%B8%8F-configuration-guide)
- [Deployment](#-deployment)
- [Contributing](#-contributing)
- [Troubleshooting](#-troubleshooting)
- [License](#-license)

---

## ✨ Features

- ⚡ **Blazing fast** — Hugo generates the entire site in ~40ms
- 🌗 **Dark / Light mode** — Auto-detects system preference, with manual toggle
- 📱 **Fully responsive** — Works on mobile, tablet, and desktop
- 🔍 **Built-in search** — Client-side search powered by [Fuse.js](https://fusejs.io/)
- 📊 **SEO optimized** — OpenGraph, Twitter Cards, structured data, robots.txt
- 📖 **Reading time & word count** — Displayed on every post
- 🏷️ **Tags & categories** — Automatic taxonomy pages
- 📄 **Profile mode** — Homepage shows profile photo, bio, and social links

---

## 📁 Project Structure

```
Viveksite/
├── archetypes/
│   └── default.md              # Template for new posts (hugo new)
├── content/
│   ├── about.md                # About page
│   ├── projects/               # Project showcase posts
│   │   ├── BloodBankApp.md
│   │   ├── DBMS.md
│   │   ├── EXPL_Compiler.md
│   │   └── RealEstateWebApp.md
│   └── trips/                  # Weekend trip blog posts
│       ├── _index.md           # Section landing page
│       └── coorg-himalayan-450.md
├── static/
│   ├── images/                 # Content images (trips, etc.)
│   │   └── trips/coorg/
│   ├── profile4.jpeg           # Profile photo (used on homepage)
│   └── vicon.png               # Favicon
├── themes/
│   └── PaperMod/               # Theme (git submodule)
├── hugo.yaml                   # Main site configuration
├── netlify.toml                # Netlify deployment settings
└── README.md                   # ← You are here
```

---

## 📦 Prerequisites

Before you begin, make sure you have the following installed:

| Tool | Version | Install |
|------|---------|---------|
| **Git** | 2.x+ | [git-scm.com](https://git-scm.com/) |
| **Hugo (Extended)** | 0.126.1+ | See below |

### Install Hugo

**macOS (Homebrew):**
```bash
brew install hugo
```

**Windows (Chocolatey):**
```bash
choco install hugo-extended
```

**Windows (Scoop):**
```bash
scoop install hugo-extended
```

**Linux (Snap):**
```bash
snap install hugo
```

**Verify installation:**
```bash
hugo version
# Expected: hugo v0.1xx.x+extended ...
```

> ⚠️ **Important:** You need the **extended** edition of Hugo for SCSS/SASS support used by PaperMod.

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/vivek1570/Viveksite.git
cd Viveksite
```

### 2. Initialize the Theme Submodule

The PaperMod theme is included as a git submodule. You **must** initialize it after cloning:

```bash
git submodule update --init --recursive
```

> 💡 If you see an empty `themes/PaperMod/` directory, this step was missed.

### 3. Verify Everything Is Ready

```bash
ls themes/PaperMod/layouts/
# Should show: _default/  partials/  shortcodes/  ...
```

---

## 🖥️ Running Locally

Start the Hugo development server with live reload:

```bash
hugo server -D
```

| Flag | What it does |
|------|-------------|
| `-D` | Include draft posts (`draft: true`) |
| `--disableFastRender` | Full rebuild on every change (slower but more reliable) |
| `-p 1414` | Use a custom port (default is 1313) |

The site will be available at: **http://localhost:1313/**

Any changes to content, config, or static files will **automatically reload** in the browser.

### Build for Production

To generate the static site into the `public/` directory:

```bash
hugo --gc --minify
```

---

## ✍️ Adding Content

### 1. Adding a New Project

Create a markdown file in `content/projects/`:

```bash
hugo new projects/my-awesome-project.md
```

Then edit the file with this frontmatter structure:

```yaml
---
title: "My Awesome Project"
date: "2025-01-15"
draft: false
hideLastModified: true
toc: true
weight: 50                              # Controls display order (lower = first)

tags:
  - Python
  - React
  - PostgreSQL
summary: "A brief one-line description of the project"
showInMenu: false
---

# My Awesome Project

## Overview
Describe your project here...

## Features
- Feature 1
- Feature 2

## Screenshots
![Screenshot description](https://link-to-image.png)
```

### 2. Adding a Trip / Blog Post

Create a markdown file in `content/trips/`:

```bash
hugo new trips/my-trip-name.md
```

Example frontmatter for a trip post:

```yaml
---
title: "Trip Title 🏍️"
date: 2025-03-15
draft: false
description: "A brief description of the trip for SEO and previews"
tags: ["motorcycle", "travel", "destination-name"]
cover:
    image: "/images/trips/destination/hero.png"
    alt: "Alt text for cover image"
    caption: "Caption that appears below the image"
    hidden: false           # Set to true to hide cover on the post page
ShowToc: true               # Show table of contents
TocOpen: true               # TOC expanded by default
---

Write your trip blog content here using standard Markdown...

![Image description](/images/trips/destination/photo.png)
```

### 3. Adding a New Section / Page

To add a completely new section (like Trips was added alongside Projects):

**Step 1:** Create the content directory and section index:

```bash
mkdir -p content/my-section
```

Create `content/my-section/_index.md`:

```yaml
---
title: "My Section Title"
description: "Section description for SEO"
---

Optional introductory text for the section listing page.
```

**Step 2:** Add it to the navigation menu in `hugo.yaml`:

```yaml
menu:
  main:
    # ... existing items ...
    - identifier: my-section
      name: My Section
      url: /my-section/
      weight: 35             # Controls menu order (lower = more to the left)
```

**Step 3:** Add posts inside `content/my-section/` like any other content.

### 4. Adding Images

Place images in the `static/` directory. They will be served from the root URL:

```
static/images/trips/coorg/hero.png  →  /images/trips/coorg/hero.png
static/my-photo.jpg                 →  /my-photo.jpg
```

Reference them in markdown:

```markdown
![Alt text for the image](/images/trips/coorg/hero.png)
```

**Recommended image organization:**

```
static/
└── images/
    ├── projects/
    │   └── project-name/
    ├── trips/
    │   └── destination-name/
    └── general/
```

---

## ⚙️ Configuration Guide

All site-wide settings live in [`hugo.yaml`](hugo.yaml). Key sections:

### Site Identity

```yaml
baseURL: "https://kpvivek.netlify.app/"
title: Vivek
```

### Profile Mode (Homepage)

```yaml
params:
  profileMode:
    enabled: true
    title: "Vivek"
    subtitle: "Your bio text here..."
    imageUrl: "/profile4.jpeg"
    imageWidth: 120
    imageHeight: 120
```

### Social Links

```yaml
params:
  socialIcons:
    - name: github
      url: https://github.com/vivek1570
    - name: linkedin
      url: https://www.linkedin.com/in/kpvivek/
    - name: instagram
      url: "https://www.instagram.com/_callmevivek_/"
```

Available icon names: `github`, `linkedin`, `twitter`, `instagram`, `youtube`, `email`, `rss`, `stackoverflow`, `codepen`, `dev`, `medium`, and [more](https://github.com/adityatelange/hugo-PaperMod/wiki/Icons).

### Favicon

Replace the favicon by placing your icon in `static/` and updating:

```yaml
params:
  assets:
    favicon: "/vicon.png"
    favicon16x16: "/vicon.png"
    favicon32x32: "/vicon.png"
    apple_touch_icon: "/vicon.png"
```

### Display Settings

```yaml
params:
  ShowReadingTime: true        # Show estimated reading time
  ShowWordCount: true          # Show word count
  ShowBreadCrumbs: true        # Show breadcrumb navigation
  ShowPostNavLinks: true       # Show prev/next post links
  ShowShareButtons: false      # Social share buttons
  defaultTheme: auto           # auto, dark, or light
  disableThemeToggle: false    # Allow users to toggle theme
```

---

## 🚢 Deployment

### Netlify (Current Setup)

The site is configured for Netlify deployment via [`netlify.toml`](netlify.toml):

```toml
[build.environment]
HUGO_VERSION = "0.126.1"

[build]
publish = "public"
command = "hugo --gc --minify"
```

**To deploy:**
1. Push your changes to the `main` branch
2. Netlify automatically builds and deploys

**First-time Netlify setup:**
1. Log in to [Netlify](https://app.netlify.com/)
2. Click "Add new site" → "Import an existing project"
3. Connect your GitHub repository
4. Build settings should auto-detect from `netlify.toml`
5. Click "Deploy site"

### Other Hosting Options

<details>
<summary><strong>GitHub Pages</strong></summary>

1. In your repo, go to **Settings → Pages**
2. Set source to **GitHub Actions**
3. Create `.github/workflows/hugo.yml`:

```yaml
name: Deploy Hugo site to GitHub Pages

on:
  push:
    branches: [main]

jobs:
  build-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          submodules: true
          fetch-depth: 0
      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v3
        with:
          hugo-version: "latest"
          extended: true
      - name: Build
        run: hugo --gc --minify
      - name: Deploy
        uses: peaceiris/actions-gh-pages@v4
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
```

</details>

<details>
<summary><strong>Vercel</strong></summary>

1. Import the repo on [Vercel](https://vercel.com/)
2. Framework: **Hugo**
3. Build command: `hugo --gc --minify`
4. Output directory: `public`
5. Add environment variable: `HUGO_VERSION` = `0.126.1`

</details>

---

## 🤝 Contributing

Contributions are welcome! Whether it's fixing a typo, improving content, or suggesting new features.

### How to Contribute

1. **Fork** the repository

2. **Clone** your fork:
   ```bash
   git clone https://github.com/YOUR-USERNAME/Viveksite.git
   cd Viveksite
   git submodule update --init --recursive
   ```

3. **Create a feature branch:**
   ```bash
   git checkout -b feature/your-feature-name
   ```

4. **Make your changes** and test locally:
   ```bash
   hugo server -D
   ```

5. **Commit** with a clear message:
   ```bash
   git add .
   git commit -m "feat: add new trip post about Munnar"
   ```

6. **Push** and create a Pull Request:
   ```bash
   git push origin feature/your-feature-name
   ```
   Then open a PR on GitHub.

### Commit Message Convention

| Prefix | Use for |
|--------|---------|
| `feat:` | New content, features, or pages |
| `fix:` | Bug fixes, broken links, typos |
| `docs:` | README or documentation updates |
| `style:` | CSS / formatting changes (no logic) |
| `chore:` | Config, build, or dependency updates |

### What You Can Contribute

- 📝 Fix typos or improve wording
- 🎨 CSS improvements or theme customizations
- 📄 Suggest new content sections
- 🐛 Report issues with the site
- 🔧 Improve build/deployment config

---

## 🔧 Troubleshooting

### Common Issues

<details>
<summary><strong>❌ Empty <code>themes/PaperMod/</code> directory</strong></summary>

The theme submodule wasn't initialized. Run:
```bash
git submodule update --init --recursive
```

</details>

<details>
<summary><strong>❌ <code>partial "partials/templates/_funcs/get-page-images" not found</code></strong></summary>

Your PaperMod version is outdated for your Hugo version. Update the theme:
```bash
cd themes/PaperMod
git checkout master
git pull origin master
cd ../..
```

</details>

<details>
<summary><strong>❌ <code>Raw HTML omitted</code> warnings</strong></summary>

Hugo's Goldmark renderer blocks raw HTML by default. This is already fixed in `hugo.yaml`:
```yaml
markup:
  goldmark:
    renderer:
      unsafe: true
```

</details>

<details>
<summary><strong>❌ <code>command not found: hugo</code></strong></summary>

Hugo is not in your PATH. Try:
```bash
# macOS
brew install hugo

# Or use the full path
/opt/homebrew/bin/hugo server -D
```

</details>

<details>
<summary><strong>❌ Changes not showing up</strong></summary>

1. Make sure the post doesn't have `draft: true` (or use the `-D` flag)
2. Try stopping the server and restarting with `--disableFastRender`
3. Clear the Hugo cache: `hugo --gc`

</details>

---

## 📚 Useful Links

| Resource | URL |
|----------|-----|
| Hugo Documentation | [gohugo.io/documentation](https://gohugo.io/documentation/) |
| PaperMod Wiki | [github.com/adityatelange/hugo-PaperMod/wiki](https://github.com/adityatelange/hugo-PaperMod/wiki) |
| PaperMod Icons List | [PaperMod Icons](https://github.com/adityatelange/hugo-PaperMod/wiki/Icons) |
| Hugo Themes Gallery | [themes.gohugo.io](https://themes.gohugo.io/) |
| Markdown Guide | [markdownguide.org](https://www.markdownguide.org/) |

---

## 📄 License

This project is open source. The [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme is licensed under the MIT License.

---

<p align="center">
  Built with ❤️ using <a href="https://gohugo.io/">Hugo</a> + <a href="https://github.com/adityatelange/hugo-PaperMod">PaperMod</a>
</p>
