# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is Chloe & Matt's marketing site: a single static homepage plus a standalone
prompt-pack landing page, built with Astro.

## Architecture

- **Type**: Static site generator (Astro), output is fully static HTML/CSS/JS — no server, no CMS, no external backend.
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
│   └── pages/index.astro      # homepage content (hero, offers, FAQ, etc.)
├── public/
│   ├── tokens.css             # design tokens (served verbatim at /tokens.css)
│   ├── images/                # brand assets (logo, team photo, icons)
│   └── prompt-pack/            # standalone static landing page, untouched, served as-is
└── dist/                       # build output (gitignored)
```

## Development

- **Install**: `npm install`
- **Local dev**: `npm run dev` (Astro dev server)
- **Build**: `npm run build` → outputs static files to `dist/`
- **Preview build**: `npm run preview`

## Technology Stack

- Astro (static output mode only — no SSR, no adapters, no integrations)
- Hand-written CSS with custom properties, Google Fonts (Bricolage Grotesque, Geist, Geist Mono)
- Static images (PNG, SVG, JPEG)

## Deployment Notes

Build the site (`npm run build`) and deploy the `dist/` directory to any static hosting
service (GitHub Pages, Netlify, Vercel, etc.).

## Notes on `public/prompt-pack/`

This is a pre-existing standalone static HTML page (with its own inline styles and a
Buttondown waitlist form) that predates the Astro rewrite. Per `public/prompt-pack/verification.md`,
this page is not currently live and its waitlist form does not submit successfully. It is
carried over unmodified as a static passthrough asset — fixing it is out of scope for the
Astro migration and would require adding a third-party integration, which this project
intentionally avoids.
