# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm run dev      # Start dev server at http://localhost:4321
npm run build    # Build to ./dist/
npm run preview  # Preview the production build locally
```

No linting or testing setup exists in this project.

## Architecture

This is a single-page Astro static site — a personal profile card template. All customization happens in one place.

**Data flow**: `src/pages/index.astro` → passes props to `<Card>` → renders via `src/components/Card.astro`

**To personalize the card**, edit the `<Card>` props in [src/pages/index.astro](src/pages/index.astro):
- `name`, `position`, `aboutMe` — displayed text content
- `linkedin`, `github` — social link URLs
- `cvLink` — path to resume PDF (place file in `public/files/`)
- `profileImage` — path to profile photo (place image in `public/images/`, `.webp` preferred)
- `title` and `description` on `<BaseLayout>` — browser tab title and SEO meta description

**External dependencies** loaded via CDN (configured in [src/layouts/BaseLayout.astro](src/layouts/BaseLayout.astro)):
- Google Fonts: Lato (300, 400)
- Bootstrap Icons 1.10.3

**Styling**: [src/styles/card.css](src/styles/card.css) controls the card layout and responsive breakpoints (mobile at `≤576px`). The card uses a teal gradient (`#024945` → `#12a89c`) on a dark background (`#131516`).
