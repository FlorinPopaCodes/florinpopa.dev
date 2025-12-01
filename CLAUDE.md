# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal portfolio website for Florin Popa (Backend Engineer) using a **Japanese Minimal** aesthetic with no JavaScript. Built with Tailwind CSS CLI v4 (not the traditional PostCSS setup).

## Development Commands

### Development
```bash
npm run dev
```
Watches `src/style.css` and outputs to `src/output.css` with hot reloading.

### Production Build
```bash
npm run build
```
Minifies CSS to `dist/output.css` and copies `src/index.html` and `src/public/` to `dist/`.

### CSS Generation (Manual)
```bash
npx @tailwindcss/cli -i ./src/style.css -o ./src/output.css
```

## Architecture

### Build System
- **Tailwind CSS CLI v4**: Uses `@import "tailwindcss"` syntax (NOT `@tailwind` directives)
- **No Vite, no PostCSS**: Direct Tailwind CLI compilation only
- **No bundler**: Plain HTML with inline styles and external CSS

### File Structure
```
src/
  index.html          # Single-page site with all content
  style.css           # Tailwind source file (@import "tailwindcss")
  output.css          # Generated CSS (do not edit)
  public/             # Static assets copied to dist/
```

### Design System

All styling is **inline** in `src/index.html` within `<style>` tags. The design implements Japanese aesthetic principles:

#### Key Visual Elements
1. **Animated Enso (SVG brush stroke)** - Draws a circle using `stroke-dashoffset` animation with SVG filters for brush texture
2. **Floating cherry blossom petals** - CSS animations with rotation and translation
3. **Ink splatter effects** - Timed to appear after enso completes
4. **Floating stones** - Represent experience markers with gentle vertical animation
5. **Bamboo line** - Vertical decorative element on desktop
6. **Paper texture background** - Repeating linear gradients

#### Color Palette
- Background: `#f5f1e8` → `#e8e4dc` gradient (washi paper)
- Accent: `#8b7355` (bamboo brown)
- Text: `#2d2d2d` (warm black)

#### Typography
- **Primary**: Noto Serif JP (Japanese-inspired serif)
- **Display**: Shippori Mincho (traditional Japanese)
- **Vertical text**: Japanese characters (フローリン・ポパ) using `writing-mode: vertical-rl`

#### Animation Philosophy
All animations are **intentional and restrained**:
- Entrance: Staggered delays (300ms, 500ms, 700ms, etc.)
- Duration: Slow (1-2.5s) with ease-out/cubic-bezier
- Infinite loops: Only for ambient elements (petals, stones, ink wash)

### Responsive Design
- **Desktop**: 12-column grid with vertical text and bamboo decoration
- **Mobile**: Single column, hides vertical decorative elements
- **Breakpoint**: `md:` (768px)

## Design Constraints

### What NOT to Change
1. **No JavaScript**: Site is intentionally JS-free
2. **Inline styles**: All animations and custom styles live in `<style>` tag
3. **Single page**: Not a multi-page site, don't split content
4. **Japanese aesthetic**: Maintain Zen principles (wabi-sabi, ma, shibui)
5. **Color palette**: Stick to bamboo brown (#8b7355) and paper tones

### Animation Requirements
- Use `animation-delay` for choreographed reveals
- Infinite animations must have long durations (6s+)
- Opacity transitions should be gradual
- No jarring or rapid movements

### Tailwind Usage
- Utility classes from Tailwind v4
- Custom classes defined in inline `<style>` for complex animations
- No Tailwind config file (uses defaults)

## Content Updates

When updating personal information:
- **Name**: "Florin Popa" appears in H1, vertical Japanese text, and title tag
- **Haiku**: 5-7-5 syllable structure in English about Rails/backend
- **Philosophy section**: Backend engineering philosophy and location
- **Stones labels**: Three short phrases (Rails Mastery, Performance, Mentorship)
- **Links**: LinkedIn, GitHub, Twitter, Email

## Documentation

See `DESIGN.md` for comprehensive design rationale, Japanese aesthetic principles, and visual language details.
