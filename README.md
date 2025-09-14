# MOVING TO USA GUIDE VIA J1 & J2

A public, community-friendly guide for people moving to the USA on J1/J2 visa category (Socia Secutiry, Accomodation, Commute, EAD, driving license, groceries, etc.) built entirely with **GitHub** and published via **GitHub Pages** using **MkDocs + Material**.

## Quick start
1. **Create a new GitHub repo** named `durham-move-guide` (public or private).
2. On your computer, open **VS Code** and a terminal.
3. Clone your repo and copy these starter files into it (or just upload the ZIP contents on GitHub).
4. Commit & push.
5. In GitHub, go to **Settings → Pages → Build and deployment** and set **Source = GitHub Actions**.
6. Push to `main` — the included workflow will build and deploy automatically. Your site will appear at `https://<your-username>.github.io/durham-move-guide/`.

## Local preview (optional)
```bash
# install Python if you don't have it (3.10+ works great)
python -m pip install --upgrade pip
pip install mkdocs mkdocs-material

# from the repo folder
mkdocs serve
```
Then open http://127.0.0.1:8000 in your browser while you edit files inside `docs/`.

## Writing content
- Add a new page as a Markdown file inside `docs/` (e.g., `docs/ead.md`).
- Update the **nav** in `mkdocs.yml` to include it in the sidebar.
- Commit → push; GitHub Actions will rebuild your site.

## Contributing
If you accept community help, use GitHub **Issues** and **Discussions**. See `docs/contributing.md` for a friendly guide and code of conduct pointers.

---

### Git basics (cheat sheet)

```bash
# set your identity once per machine
git config --global user.name "Your Name"
git config --global user.email "your@email.com"

# starting from an empty folder
git init
git remote add origin https://github.com/<you>/durham-move-guide.git
git add .
git commit -m "Initial commit: Durham Move Guide starter"
git branch -M main
git push -u origin main

# regular workflow
git add -A
git commit -m "Update EAD page with I-765 tips" /* Example you are pushing file for EAD application */
git push

# create a feature branch
git checkout -b ead-tips
# ...edit files...
git add -A && git commit -m "First draft of EAD page"
git push -u origin ead-tips
# then open a Pull Request on GitHub
```

### VS Code tips
- Use the **Source Control** panel (left sidebar) to stage/commit without typing commands.
- Use the **Git Graph** or **GitLens** extensions (optional) to visualize branches.
- Open an integrated terminal with <kbd>Ctrl</kbd>+<kbd>`</kbd> (backtick).

---

### Alternatives (if you ever want them)
- **Jekyll (native GitHub Pages)** — blog-style, works with `_config.yml` and Markdown.
- **Docusaurus** — great for documentation portals; needs Node.js.
- **Hugo** — very fast static site generator (Go-based).
- **Just a README/Wiki** — keep everything in the repo README or enable the repo’s Wiki.

This starter uses **MkDocs + Material** because it's simple for guides, has search, and looks good by default.
