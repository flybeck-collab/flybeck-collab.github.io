# Flybeck — Keyboard Design Archive

A single-page static site showcasing six custom mechanical keyboards: SL65, Nectar, Khora, VNDL, Zoku and ech0.

## Contents

```
index.html          the whole site — markup and CSS in one file
images/             six board photos, 1200x750, web-optimised
```

No build step, no dependencies, no JavaScript. The only external request is the Google Fonts stylesheet (Archivo, JetBrains Mono, Noto Sans JP).

## Publishing to GitHub Pages

### Option A — user site at `https://<username>.github.io`

1. Create a new **public** repo named exactly `<username>.github.io` (your GitHub username, lowercase).
2. Upload `index.html` and the `images/` folder to the repo root — drag both into the browser upload box, or:
   ```
   git init
   git add .
   git commit -m "Keyboard archive"
   git branch -M main
   git remote add origin https://github.com/<username>/<username>.github.io.git
   git push -u origin main
   ```
3. Go to **Settings → Pages**. Under *Build and deployment*, set **Source** to `Deploy from a branch`, **Branch** to `main`, folder `/ (root)`. Save.
4. Wait about a minute. The site is live at `https://<username>.github.io`.

### Option B — project site at `https://<username>.github.io/<repo>`

Same as above, but name the repo whatever you like (e.g. `keebs`). The site lands at `https://<username>.github.io/keebs`. All asset paths here are relative, so this works without changes.

## Editing

Everything is in `index.html`.

- **Board specs** live in the `<dl class="spec">` block inside each `<article class="card">`.
- **Colours** are CSS custom properties at the top of the `<style>` block — change `--accent` to recolour the whole page.
- **Adding a board:** copy any `<article class="card hud">` block, change the number, status chip class (`ship` / `open` / `test` / `oneoff`), image path, heading, pitch and spec rows. Drop the new photo into `images/` cropped to 16:10.

## Custom domain

Add a file named `CNAME` at the repo root containing just your domain (e.g. `flybeck.com`), then point a CNAME DNS record at `<username>.github.io`. Set it under Settings → Pages → Custom domain.
