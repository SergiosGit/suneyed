# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

SunEyed is a static marketing website for a free iOS app that calculates solar panel ROI and savings. No build step required — files are served directly from the repository root via Netlify.

## Development

**Local preview**: Open any `.html` file directly in a browser, or use a simple server:
```
python3 -m http.server 8000
```

**Deployment**: Push to `main` → Netlify auto-deploys. Configuration is in `netlify.toml`.

## Architecture

**Pages** (all at repo root):
- `index.html` — Landing page: hero, how-it-works summary, features grid, installer CTA
- `how-it-works.html` — Step-by-step app walkthrough
- `installers.html` — Installer program marketing + Netlify signup form (`installer-interest`)
- `privacy.html` — Privacy policy (references Firebase/Firestore/Crashlytics, Apple SwiftData)
- `support.html` — FAQ using `<details>`/`<summary>` elements

**Single stylesheet**: `css/style.css` — shared across all pages, no CSS preprocessor.

**Assets**: `assets/README.md` documents required images (app-icon.png, screenshot-*.png, og-image.png) and their dimensions. Many image slots use emoji placeholders pending real screenshots.

## Design System

CSS variables defined at the top of `css/style.css`:
- Primary blue: `#0d6b8c` / dark: `#08485e` / light: `#e6f4f9`
- Accent amber: `#f5a623`
- Font: Apple system stack (`-apple-system, BlinkMacSystemFont, ...`)

Key component classes: `.btn`, `.btn--primary`, `.btn--amber`, `.btn--outline`, `.hero`, `.section`, `.feature-card`, `.step`, `.step-row`, `.screenshot-card`, `.form-box`, `.form-success`, `.page-content`.

## Netlify Configuration

`netlify.toml` handles:
- Clean URL redirects (e.g., `/how-it-works` → `/how-it-works.html`)
- Form success redirect: `/installer-form-success` → `/installers.html?success=true`
- Security headers on all routes

## Form Handling

`installers.html` uses Netlify Forms (`data-netlify="true"`, name `installer-interest`). On page load, JS checks for `?success=true` in the URL to toggle `.form-success` visibility.

## SEO

Each page includes Schema.org structured data, Open Graph tags, Twitter Card meta, and a canonical URL. `sitemap.xml` lists all 5 pages.
