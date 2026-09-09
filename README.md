# Portfolio — deployment walkthrough

This is a plain HTML/CSS/JS site — no build step, no npm install. That means GitHub Pages
can serve it directly with zero configuration.

## Files

```
portfolio-site/
├── index.html      → all content lives here, organized by section
├── styles.css       → design tokens at the top (colors, fonts), then component styles
├── script.js         → one small effect: highlights the active nav item as you scroll
├── README.md          → this file
└── assets/
    ├── Elliott_Hirko_CV.pdf   → your CV, already copied in, linked from the hero button
    ├── projects/               → drop generated benchmark plots / diagrams here
    ├── reactor/                → drop IEC reactor photos here
    └── images/                 → anything else (headshot, etc.)
```

## 1. Create the GitHub repo

1. Go to github.com → **New repository**.
2. Name it `<your-username>.github.io` exactly (e.g. if your username is `ehirko`, name it
   `ehirko.github.io`). This special name makes GitHub serve it at the root of your own domain
   automatically — `https://ehirko.github.io` — instead of a `/repo-name/` subpath.
   - If you'd rather keep it as a normal-named repo (e.g. `portfolio`), that's fine too — it'll
     just live at `https://<username>.github.io/portfolio/` instead. Step 3 below covers both.
3. Set it to **Public**. Don't initialize with a README (you already have one).

## 2. Push these files

From the folder containing `index.html`, `styles.css`, `script.js`, `README.md`, and `assets/`:

```bash
git init
git add .
git commit -m "Initial portfolio"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

## 3. Turn on GitHub Pages

1. In the repo on GitHub, go to **Settings → Pages**.
2. Under **Build and deployment → Source**, choose **Deploy from a branch**.
3. Under **Branch**, choose `main` and folder `/ (root)`, then **Save**.
4. Wait ~1 minute, then refresh — GitHub shows the live URL at the top of the Pages settings page.
   - `<username>.github.io` repo → served at `https://<username>.github.io`
   - any other repo name → served at `https://<username>.github.io/<repo-name>/`

That's it — the site is live. Any time you `git push` again, it redeploys automatically in
about a minute.

## 4. Editing content

Everything is in `index.html`, split into commented sections (`<!-- ---------- PROJECTS ---------- -->`
etc.). To add a project, copy one existing `<article class="panel">...</article>` block and
edit the text. To reorder sections, move the whole `<section>` block — the sidebar nav links
to `#id`s so order doesn't need to match the nav.

### Adding generated plots/diagrams

Each project panel has a commented `<!-- PROMPT FOR CLAUDE CODE -->` block above a placeholder
`<figure class="panel-media">`. Workflow:

1. `cd` into that project's actual repo.
2. Run the suggested prompt with Claude Code — it'll generate an SVG/PNG plot.
3. Copy the generated image into `portfolio-site/assets/projects/`.
4. In `index.html`, uncomment the `<img src="...">` line inside that panel's `<figure>` and
   delete/adjust the placeholder caption.

### Adding IEC reactor photos

Same idea, but no code generation needed — just drop real photos into `assets/reactor/` and
point the `<img>` tags at them. If you have several good shots, duplicate the `<figure>` block
to make a small gallery within that panel.

### Fixing placeholder links

Search `index.html` for `YOUR_GITHUB` and `href="#"` — replace with your actual GitHub
username and each project's repo URL.

## 5. Custom domain (optional)

If you buy a domain later: **Settings → Pages → Custom domain**, add the domain, then add a
`CNAME` record at your registrar pointing to `<username>.github.io`. GitHub handles HTTPS
automatically once DNS resolves.

## Local preview

No server needed for basic viewing — just open `index.html` in a browser. If you want it to
behave exactly like it will when deployed (in case you add fetch calls or routing later), run
a tiny local server instead:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```
