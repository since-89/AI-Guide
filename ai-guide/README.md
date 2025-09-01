# AI Guide — America–India Living, Made Easy

A minimal, ready-to-deploy **GitHub Pages** site using **Jekyll + Minimal Mistakes** theme.

## Quick Start

1) Create a new repo on GitHub (public): e.g. `ai-guide` or `username.github.io`  
2) Download this ZIP, extract, and **push everything** to your repo’s `main` branch.  
3) In your repo: **Settings → Pages → Build and deployment → Source: GitHub Actions**.  
4) Wait for the **Pages** workflow to finish. Your site will be live at:  
   - `https://<your-username>.github.io/` (if repo is `username.github.io`), or  
   - `https://<your-username>.github.io/<repo-name>/` (for any other repo).

## Local preview (optional)

If you want to run locally:

```bash
# Requires Ruby + Bundler
bundle install
bundle exec jekyll serve
# open http://127.0.0.1:4000
```

## Edit Content

- Home page: `index.md`  
- Navigation: `_data/navigation.yml`  
- Posts: `_posts/` (Markdown files)  
- Pages: `_pages/` (About, Guides index, etc.)

Happy writing!
