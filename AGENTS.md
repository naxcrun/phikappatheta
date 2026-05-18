# AGENTS.md

## Cursor Cloud specific instructions

### Repository structure

This repository hosts the **Phi Kappa Theta Indiana Zeta** website (www.phik.app) — a static React/Vite/Tailwind SPA deployed via GitHub Pages.

- **`main` branch**: Contains only a `CNAME` file (custom domain config). No source code.
- **`gh-pages` branch**: Contains the pre-built production assets (bundled JS/CSS, images, HTML). This is the deployed site.

There is **no buildable source code** in this repo — no `package.json`, no `vite.config.*`, no `tsconfig.*`. The React/Vite source is maintained externally.

### Running the site locally

Extract the `gh-pages` branch and serve it with a static file server:

```bash
mkdir -p /workspace/_site
git archive origin/gh-pages | tar -x -C /workspace/_site
serve -s /workspace/_site -l 3000
```

The site is then accessible at `http://localhost:3000/`.

### Key caveats

- **No lint, test, or build commands exist** since the repo has no source code or `package.json`.
- The site is a client-side SPA — all pages are rendered in the browser via React (no server-side rendering).
- External resources (Google Fonts, Qualtrics forms, Instagram embeds) require internet access to render fully.
- The `serve -s` flag enables SPA mode (all routes fall through to `index.html`), which is required for client-side routing to work.
