# Contributing to Viveksite

Thanks for your interest in contributing! Here's how you can help.

## Quick Start

```bash
# 1. Fork & clone
git clone https://github.com/YOUR-USERNAME/Viveksite.git
cd Viveksite

# 2. Initialize theme
git submodule update --init --recursive

# 3. Run locally
hugo server -D

# 4. Open http://localhost:1313/
```

## Types of Contributions

### 🐛 Bug Reports
- Open an [Issue](https://github.com/vivek1570/Viveksite/issues) with:
  - What you expected to see
  - What actually happened
  - Your browser and OS
  - Screenshots if applicable

### 📝 Content Fixes
- Typos, grammar, broken links — just submit a PR directly.

### 🎨 Design Improvements
- Open an Issue first to discuss the change before submitting a PR.

### ✨ New Features
- Open an Issue to discuss before implementing.

## Pull Request Process

1. Create a branch from `main`:
   ```bash
   git checkout -b fix/typo-in-about-page
   ```

2. Make your changes and test locally with `hugo server -D`

3. Ensure the site builds without errors:
   ```bash
   hugo --gc --minify
   ```

4. Commit with a descriptive message:
   ```bash
   git commit -m "fix: correct typo in about page"
   ```

5. Push and open a PR against `main`

## Content Guidelines

- **Markdown only** — All content is written in standard Markdown
- **Images** — Place in `static/images/` with a descriptive subfolder
- **Frontmatter** — Every content file needs proper YAML frontmatter (title, date, draft status)
- **No draft posts in PRs** — Set `draft: false` before submitting

## Code of Conduct

Be respectful and constructive. We're all here to learn and build cool things.
