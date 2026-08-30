# ByTamilan — One Small Problem at a Time

A community landing page sharing Tamil Nadu's vision — **a better tomorrow, a happy present** — built
around one idea: the state's $1.5 trillion-by-2036 goal is not a thing anyone builds, it is the
*residue* of a few crore people each solving one small, specific problem.

The page is a single scrolling experience over a real-time WebGPU field (four states — **Vision ·
Residue · Lanes · Rules** — rendered from one compute pass). No build step, no assets pipeline: the
folder is the site.

## Run locally

```bash
npx --yes serve . -l 5173
# or any static server pointed at the repo root
```

Requires a WebGPU-capable browser (Chrome, Edge, or Safari 26+ on desktop).

## Deploy to GitHub Pages

Deployment is automatic via GitHub Actions (`.github/workflows/pages.yml`):

1. Push to `main`.
2. In the repo, go to **Settings → Pages** and set **Source** to **GitHub Actions**.
3. The `Deploy to GitHub Pages` workflow publishes the repo root as a static site at
   `https://<org>.github.io/<repo>/` on every push.

All asset paths are relative, so the site works both at a domain root and under a project subpath.

## Structure

```
index.html               entry point — skeleton and all body copy for the four chapters
styles/main.css          colour variables, typography, chapter layout
src/main.js              boot sequence: adapter → pipelines → scroll handover
src/site/scroll.js       scroll choreography (scroll → travel & phase)
src/scene/               WebGPU field: compute pass, terrain, sky, palettes
```

Libraries (three.js r185, GSAP 3.13, Lenis) load from jsDelivr via the import map in
`index.html`; fonts (Geist, Geist Mono, Instrument Serif, Noto Sans Tamil) come from Google
Fonts. The `vendor/` and `assets/fonts/` folders are local-only fallbacks and are git-ignored —
the deployed site does not need them.
