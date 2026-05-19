# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Jekyll-based academic personal website using the [Academic Pages](https://academicpages.github.io/) theme (a Minimal Mistakes fork). Hosted on GitHub Pages at `https://gunavarans.github.io`.

## Commands

```bash
# Install dependencies (first time)
bundle install
npm install

# Serve locally with live reload
bundle exec jekyll serve -l -H localhost

# Build JavaScript assets
npm run build:js
npm run watch:js   # watch mode
```

Deployment is automatic via GitHub Pages on push to `master`.

## Architecture

### Content Collections

Content lives in collection directories as Markdown/HTML with YAML frontmatter:

| Directory | URL pattern | Layout |
|-----------|-------------|--------|
| `_pages/` | varies (set in frontmatter) | `single` or `splash` |
| `_publications/` | `/publication/:title/` | `single` |
| `_talks/` | `/talks/:title/` | `talk` |
| `_research/` | `/research/:title/` | `single` |
| `_posts/` | `/posts/YYYY/MM/:title/` | `single` |
| `_teaching/` | `/teaching/:title/` | `single` |
| `_portfolio/` | `/portfolio/:title/` | `single` |

The homepage is `_pages/about.md` (permalink: `/`).

### Layout Hierarchy

```
_layouts/default.html          ← base wrapper
├── _layouts/single.html       ← most pages, posts, collection items
├── _layouts/talk.html         ← _talks/
└── _layouts/splash.html       ← full-width pages
```

### Key Configuration Files

- `_config.yml` — site metadata, author info, collection definitions, plugin list, default layouts
- `_data/navigation.yml` — main menu links (edit to add/remove nav items)
- `_data/ui-text.yml` — UI string overrides
- `_includes/author-profile.html` — sidebar bio and social links
- `_sass/_variables.scss` — theme colors and spacing

### Assets

- Images go in `images/` (author avatar: `images/guna.png`, hero: `images/home.jpeg`)
- Downloadable files (PDFs) go in `files/`
- JS is in `assets/js/`; `_main.js` is the source, `main.min.js` is the built output

### Markdown Generator

`markdown_generator/` contains Python scripts and Jupyter notebooks to bulk-generate publication and talk markdown files from TSV input files — useful when adding multiple entries at once.
