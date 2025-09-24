# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a simple static website for Chloe & Matt's web development studio. The site is currently in a "coming soon" state with minimal content.

## Architecture

- **Type**: Static HTML website
- **Styling**: Uses Tailwind CSS via CDN
- **Structure**: Single `index.html` file with supporting images
- **Deployment**: Static files only (no build process required)

## File Structure

```
/
├── index.html          # Main landing page
├── images/            # Static assets (logos, images)
│   ├── c-m-logo.png   # Site favicon and logo
│   └── ...            # Other brand assets
└── .gitignore         # Git ignore rules
```

## Development

Since this is a static site with no build process:

- **Local Development**: Open `index.html` directly in a browser or serve via any static file server
- **No build commands**: Direct file editing
- **No package manager**: Dependencies loaded via CDN
- **No testing framework**: Manual testing in browser

## Technology Stack

- HTML5
- Tailwind CSS (loaded from CDN)
- Static images (PNG, SVG, JPEG)

## Deployment Notes

This site can be deployed to any static hosting service (GitHub Pages, Netlify, Vercel, etc.) by serving the files directly from the repository root.