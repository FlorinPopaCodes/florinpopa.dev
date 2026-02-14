# CLAUDE.md

## Project Overview

Personal portfolio for Florin Popa. Single static HTML file, zero dependencies, zero build step. Brutalist web design matching florinsays.com.

## Architecture

- `src/index.html` — the entire site (HTML + inline CSS)
- No build system, no npm scripts, no external dependencies
- Deploy by serving `src/index.html` (or copy to root)

## Design

- **Brutalist web design** ([brutalist-web.design](https://brutalist-web.design/))
- Dark theme: `--bg: #0c0c0c`, warm parchment text colors
- Georgia serif body, system sans headings, monospace metadata
- 600px max-width column, 19px base font, 1.75 line-height
- Links always underlined, `focus-visible` outline for a11y
- No transitions, no animations, no border-radius, no external fonts
- Zero external requests

## Content

- Name, haiku, philosophy, three skill labels, connect links, footer
- Links: LinkedIn, GitHub, Twitter, Email

## Constraints

- No JavaScript
- No external CSS/fonts/CDN
- Single file, no build step
- Keep brutalist: no decoration, no gradients, no shadows
