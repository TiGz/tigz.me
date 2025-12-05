# CLAUDE.md

This file provides guidance for Claude Code when working on this repository.

## Project Overview

tigz.me is a static showcase homepage that links to sibling web applications. It's a simple, single-page site with no build step.

## Architecture

- **index.html** - The entire site in one file (HTML, CSS, no JavaScript except structured data)
- **.github/workflows/deploy.yml** - GitHub Actions workflow for deployment to GitHub Pages

## Design System

The site uses a cohesive dark theme that bridges the color schemes of the featured apps:

- **Base colors**: Dark slate (`#020617`) foundation from Foosbournament
- **Accent primary**: Indigo (`#818cf8`) connecting to Avatarz
- **Accent secondary**: Orange (`#f97316`) from Foosbournament
- **Accent tertiary**: Cyan (`#06b6d4`) from Foosbournament

Typography uses Satoshi (display) and General Sans (body) from Fontshare.

## Development

No build step required. Serve with any static file server:

```bash
python -m http.server 8000
```

## Deployment

Pushes to `main` automatically deploy via GitHub Actions to GitHub Pages.

## Related Repositories

- `../avatarz` - AI avatar generation app (Vite + React)
- `../foosbournament` - Tournament management app (Vite + React)

## Common Tasks

### Adding a new project card

1. Copy an existing `.project-card` block in `index.html`
2. Update the modifier class (e.g., `project-card--newproject`)
3. Add corresponding CSS for the new card's accent color and hover effects
4. Update the icon, title, description, and tags

### Updating SEO

Meta tags are in the `<head>` section. Structured data (JSON-LD) is at the bottom before `</body>`.
