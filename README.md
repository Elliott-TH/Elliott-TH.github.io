# Elliott Hirko — Engineering Portfolio Website

Responsive static portfolio based on the Minimal Dossier print portfolio. It uses plain HTML, CSS, and a few lines of JavaScript, so there is no build step and no framework dependency.

## Repository structure

```text
.
├── index.html
├── styles.css
├── script.js
├── .nojekyll
├── README.md
└── assets/
    ├── projects/
    │   ├── iapws95-benchmark.svg
    │   ├── iapws95-derivative-validation.svg
    │   ├── liquid-metal-uncertainty.svg
    │   ├── sca-inference-speed.svg
    │   └── sca-surrogate-validation.svg
    └── reactor/
        └── project photos
```

## Preview locally

From the repository root:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000`.

## Publish on GitHub Pages

1. Create a GitHub repository.
2. Copy the contents of this folder to the repository root.
3. Commit and push to `main`.
4. Open **Settings → Pages** in the GitHub repository.
5. Under **Build and deployment**, select **Deploy from a branch**.
6. Select `main` and `/ (root)`, then save.

A project repository is normally published at:

```text
https://YOUR_USERNAME.github.io/YOUR_REPOSITORY/
```

A repository named exactly `YOUR_USERNAME.github.io` is published at:

```text
https://YOUR_USERNAME.github.io/
```

All paths in the site are relative, so both deployment styles work without changing the HTML.

## Common edits

### Add your GitHub repository link

Add a normal anchor wherever you want it in `index.html`, for example:

```html
<a href="https://github.com/YOUR_USERNAME/YOUR_REPO">GitHub</a>
```

### Change colors or spacing

The main design variables are at the top of `styles.css` under `:root`.

## Notes

- The site is intentionally dependency-free so GitHub Pages can serve it directly.
- Figures are retained as SVG where possible for sharp rendering on high-DPI displays.
- The layout is responsive down to mobile widths rather than reproducing fixed US-Letter pages in the browser.
