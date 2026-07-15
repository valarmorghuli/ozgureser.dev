# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Static personal website for **ozgureser.dev**. Hand-written HTML/CSS served directly — there is
**no build system, package manager, framework, or test suite**. The content is in **Turkish**
(`<html lang="tr">`); keep new copy Turkish unless asked otherwise.

## Files

- `index.html` — the entire site (single page).
- `css/styles.css` — all styling.
- `robots.txt` / `sitemap.xml` — SEO. `sitemap.xml` `<lastmod>` and the footer `© year` in
  `index.html` are maintained by hand.
- `*.bak` (`index.html.bak`, `css/styles.css.bak`) — manual snapshots, gitignored.

## Running / previewing

No dev server or build step. Open `index.html` directly in a browser, or serve statically:

```
python3 -m http.server
```

There are no lint, test, or build commands.

## Design system

- Dark, terminal/CLI-inspired aesthetic. Color scheme is fixed dark
  (`<meta name="color-scheme" content="dark">`).
- All colors are **OKLCH custom properties defined in `:root`** at the top of `css/styles.css`.
  Change these tokens rather than hardcoding colors. `--accent` is the single accent hue (green, 165).
- Two fonts loaded from Google Fonts: `Hanken Grotesk` (`--sans`, body text) and `IBM Plex Mono`
  (`--mono`). Mono is used for the "terminal" elements — the `~/ozgureser` path, chips, badges,
  tags, contact rows, and footer.
- Layout is a single centered column (`max-width: 680px`) of card sections. One mobile breakpoint
  at `max-width: 560px`, plus a `@media print` override.

## Analytics

The inline `<script>` at the bottom of `index.html` requests `/status.gif?page=...` as a
server-side tracking pixel (handled by nginx, not part of this repo). It is not a JS analytics library.

## Deployment

Served by nginx on an Ubuntu server at https://ozgureser.dev. No CI/CD config lives in the repo —
deployment is external/manual.
