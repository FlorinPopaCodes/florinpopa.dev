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
- **Homepage h1 is visually hidden** (`sr-only`) — intentional. Content flows bio → posts → connect → footer without a visible title to encourage full-page reading

## Commands

- `npm run dev` — dev server
- `npm run build` — static build to `dist/`
- `npm run preview` — preview build

## Constraints

- No client-side JavaScript
- No external CSS/fonts/CDN
- Keep brutalist: no decoration, no gradients, no shadows

## Design Context

### Users
Backend engineering hiring managers, CTOs, and fellow developers. They land here from a LinkedIn profile, a shared blog link, or a search result. They want to quickly assess competence and read something useful — not wade through a portfolio spectacle.

### Brand Personality
**Direct, competent, honest.** The site is the resume: no fluff, no selling, no performance. The work and writing speak for themselves. Brutalism is not an aesthetic choice — it's the honest expression of "I don't overcomplicate things."

### Emotional Goals
1. **Calm clarity** — "This is refreshingly simple." Relief from overstimulated dev portfolios.
2. **Trust and respect** — "This person clearly knows what they're doing." Quiet confidence.
3. **Curiosity** — "I want to read more." The writing pulls them in, not the design.

### Aesthetic Direction
- **North stars**: [brutalist-web.design](https://brutalist-web.design/), [macwright.com](https://macwright.com/), [borretti.me](https://borretti.me/) — content-first, refined minimalism, zero decoration
- **Anti-references**: Anything with gradient text, glassmorphism, animated hero sections, card grids, "dark mode SaaS landing page" energy, or AI-generated portfolio aesthetics
- **Theme**: Dark-only. Warm parchment palette on near-black. No light mode planned.

### Design Principles
1. **Content is the interface.** Typography, spacing, and hierarchy do all the work. If it doesn't serve the text, remove it.
2. **Subtract, don't add.** Every element must justify its existence. When in doubt, delete it.
3. **Respect the reader.** Fast loads, no tracking, no layout shifts, accessible markup, readable type. The reader's time is more valuable than the designer's cleverness.
4. **System defaults over custom.** System fonts, native scrollbars, browser focus rings (enhanced), semantic HTML. Work with the platform, not against it.
5. **Ship the minimum.** No speculative features, no "nice to haves," no infrastructure for hypothetical scale.

### Accessibility
- Target: **WCAG 2.1 AA**
- All text passes 4.5:1 contrast minimum
- `focus-visible` outlines on all interactive elements
- Semantic HTML with proper landmarks and heading hierarchy
- No motion to reduce, no auto-playing media, no CAPTCHA
