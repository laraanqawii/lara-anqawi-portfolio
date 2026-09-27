# Lara Anqawi — Portfolio

Personal portfolio site. Plain HTML, CSS (BEM + custom properties) and vanilla JavaScript — no build step.

```
index.html
css/styles.css
js/main.js
```

## Before publishing

Replace these placeholders in `index.html`:

| Placeholder | Replace with |
|---|---|
| `[LINKEDIN_URL]` | Your LinkedIn profile URL |
| `[GITHUB_URL]` | Your GitHub profile URL |
| `[GITHUB_REPO_URL]` | The PalCareerLink repository URL |
| `[LIVE_DEMO_URL]` | A live demo URL (or remove that button) |
| `[CV_PDF_PATH]` | e.g. `assets/Lara_Anqawi_CV.pdf` (add the PDF to the repo) |
| `[PROJECT_SCREENSHOT]` | Swap the placeholder `<div>` for the `<img>` shown in the HTML comment |

## Deploy to GitHub Pages

1. Create a repository on GitHub, e.g. `lara-anqawi.github.io` (for a user site) or any name (for a project site).
2. Upload the files so `index.html` sits at the repository root:
   ```bash
   git init
   git add .
   git commit -m "Initial portfolio"
   git branch -M main
   git remote add origin https://github.com/<username>/<repo>.git
   git push -u origin main
   ```
3. In the repository, open **Settings → Pages**.
4. Under **Build and deployment**, set **Source** to *Deploy from a branch*, choose `main` and `/ (root)`, then **Save**.
5. After a minute or two the site is live at `https://<username>.github.io/` (user site) or `https://<username>.github.io/<repo>/` (project site).

## Preview locally

Open `index.html` directly in a browser, or run `python3 -m http.server` in this folder and visit `http://localhost:8000`.
