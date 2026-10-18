# Flybeck — keyboard archive

Single-page static site. Six boards: SL65, Nectar, Khora, VNDL, Zoku, ech0.

## Contents

```
index.html          the whole site — markup and CSS in one file
*-card.jpg          six board photos, 1200x750
```

No build step, no dependencies, no JavaScript. Image paths are flat (same folder as
`index.html`), matching how the repo is laid out. The only external request is the
Google Fonts stylesheet (Instrument Sans, JetBrains Mono).

The Flybeck logo is inline SVG in three places — nav, hero, footer — plus the favicon.
It recolours with CSS `fill` and stays sharp at any size; there is no logo image file.

## Updating

Everything lives in `index.html`.

- **Colours** — the gradient blooms are `.bloom-warm` and `.bloom-cool` in the
  `<style>` block, built from layered `radial-gradient`s. The grain is `.grain`,
  an inline SVG turbulence filter.
- **Board specs** — the `<dl class="spec">` block inside each `<article class="card">`.
- **Status chips** — swap the class: `chip-ship`, `chip-open`, `chip-test`, `chip-one`.
  Each uses a dark base so it stays legible over light *and* dark photos.
- **Adding a board** — copy any `<article class="card">`, change the heading, date,
  pitch, spec rows and image. Crop the photo to **16:10**; anything else will be
  centre-cropped to fit.

## Responsive behaviour

Verified at 390px, 768px and 1366px with no horizontal overflow.

| Width | What changes |
|---|---|
| ≤ 900px | Board grid drops to one column; gutters 48px → 32px |
| ≤ 760px | Stats block goes 4-across → 2×2 |
| ≤ 560px | Gutters → 20px; spec rows go single-column; buttons go full-width |

Headings and section padding use `clamp()`, so they scale continuously between
those breakpoints rather than jumping.

## Publishing

Drop `index.html` and the six `.jpg` files in the repo root, then
**Settings → Pages → Source: Deploy from a branch → `main` / root**.

### Custom domain

Add a `CNAME` file at the repo root containing just the domain, then point a CNAME
DNS record at `<username>.github.io`, and set it under Settings → Pages.
