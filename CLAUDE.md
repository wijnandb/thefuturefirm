# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

The Future Firm (thefuturefirm.com) — website for a culture and strategy transformation consultancy founded by Gijs Pothof. Client of Bollenstreekdigitaal, a brand under Perceptum.

## Architecture

- **Main site** (`index.html`, `privacy.html`, `network.html`): Static HTML with inline CSS/JS, no build step. Uses GT Cinetype custom font, light/dark theme toggle, scroll animations via IntersectionObserver. `network.html` is an interactive force-directed partner network mindmap using HTML5 Canvas.
- **Lencioni assessment app** (`lencioni/app/`): React + Vite SPA for Lencioni's Five Dysfunctions team assessment. Uses Supabase for data, Tailwind CSS for styling, React Router for navigation. **This directory is gitignored** — it lives separately.

## Deployment

- Hosted on **GitHub Pages** from repo `PerceptumNL/thefuturefirm`
- Custom domain: `thefuturefirm.com` (see `CNAME`)
- Pushes to `main` trigger automatic deployment

## Key Details

- **CSP header** is set via meta tag in `index.html` — must include `analytics.perceptum.nl` for both `script-src` and `connect-src`
- **Analytics**: LiveView Analytics (Perceptum product), cookieless, loaded via `analytics.perceptum.nl/liveview.js` with key `lv_live_FKiLqqr_XVGGvdsb93ct6i6ziZgJ_EJS`
- **Privacy page** is in Dutch (`lang="nl"`), noindexed
- **Contact**: gijs.pothof@thefuturefirm.com
- **KvK**: 52970833

## Lencioni App (when working in lencioni/app/)

```bash
cd lencioni/app
npm install
npm run dev      # Vite dev server
npm run build    # Production build
```

Routes: `/t/:token` (participant entry), `/s/:sharedToken` (shared entry), `/take/:participantId` (assessment), `/results/:participantId` (results), `/admin` (dashboard).
