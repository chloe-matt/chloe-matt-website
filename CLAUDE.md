# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the single-page corporate card for **Chloe & Matt OÜ** (Estonian registry no. 14305217), the consulting and B2B contracting vehicle of [Asep Bagja](https://www.asepbagja.com). There are no sub-pages; all consulting portfolio and marketing live on `asepbagja.com`.

## Architecture

- **Type**: Static site generator (Astro), output is a single static HTML page (`dist/index.html`) — no server, no CMS, no external backend.
- **Styling**: Hand-written CSS using custom properties (design tokens), no framework/utility CSS.
- **Structure**: One Astro page (`src/pages/index.astro`) built from a shared layout and two small components (nav, footer).
- **Deployment**: `npm run build` emits static files to `dist/`; deploy `dist/` to any static host.

## File Structure

```
/
├── astro.config.mjs      # minimal Astro config (no integrations)
├── src/
│   ├── layouts/Layout.astro   # <head>, global page CSS, skip link, main/slot wiring
│   ├── components/
│   │   ├── Nav.astro          # floating pill nav + mobile menu toggle script
│   │   └── Footer.astro       # statement footer
│   └── pages/index.astro      # 1-page corporate & billing card + principal overview
├── public/
│   ├── tokens.css             # design tokens (served verbatim at /tokens.css)
│   └── images/                # brand assets (logo, principal photo)
└── dist/                      # build output (gitignored)
```

## Development

- **Install**: `npm install`
- **Local dev**: `npm run dev` (Astro dev server)
- **Build**: `npm run build` → outputs static files to `dist/`
- **Preview build**: `npm run preview`
