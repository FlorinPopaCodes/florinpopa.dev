# CLAUDE.md

## Project Overview

Personal portfolio + blog for Florin Popa. Built with Astro, mirrors florinsays.com architecture. Brutalist web design.

## Architecture

- **Framework**: Astro 5 with MDX, RSS, sitemap
- `src/pages/index.astro` — homepage (bio → posts → connect links)
- `src/pages/[slug].astro` — dynamic post/page routes
- `src/pages/rss.xml.js` — RSS feed
- `src/layouts/BlogPost.astro` — post layout with dates + structured data
- `src/components/` — BaseHead, Footer, FormattedDate
- `src/content/blog/` — MD/MDX posts (content collections)
- `src/content.config.ts` — collection schema (title, description, date, last, heroImage)
- `src/styles/global.css` — all base styles
- `src/consts.ts` — SITE_TITLE, SITE_DESCRIPTION
- `public/` — favicon.svg, robots.txt

## Content Collections

- Posts have `date` (sorted reverse-chronological on homepage)
- Pages have no `date` (listed separately below posts)
- Prefix filenames with `_` to exclude from build

## Design

- **Brutalist web design** ([brutalist-web.design](https://brutalist-web.design/))
- Dark theme: `--bg: #0c0c0c`, warm parchment text colors
- Georgia serif body, system sans headings, monospace metadata
- 600px max-width column, 19px base font, 1.75 line-height
- Links always underlined, `focus-visible` outline for a11y
- No transitions, no animations, no border-radius, no external fonts

## Commands

- `npm run dev` — dev server
- `npm run build` — static build to `dist/`
- `npm run preview` — preview build

## Constraints

- No client-side JavaScript
- No external CSS/fonts/CDN
- Keep brutalist: no decoration, no gradients, no shadows
