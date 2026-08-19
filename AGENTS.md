# AGENTS.md

## Essential commands

```bash
# After cloning — theme is a submodule, missing this breaks the build
git submodule update --init --recursive

# Dev server (includes draft posts)
hugo server -D

# Production build → ./public/
hugo

# New post (created as draft by default)
hugo new posts/my-post-title.md
```

## Theme: PaperMod

- Git submodule at `themes/PaperMod/` — actively maintained, Hugo v0.124+ compatible.
- Previously WonderMod; switched due to `.Site.Social` removal in Hugo v0.124.
- For syntax highlighting, add to `hugo.yaml`:
  ```yaml
  markup:
    highlight:
      style: dracula
      noClasses: false
      guessSyntax: true
  ```
  Always use explicit language identifiers on fences (` ```go `), `guessSyntax` is unreliable.

## Content

- Only section: `content/posts/`
- All new posts are `draft: true` by default (archetype) — set `draft: false` to publish.
- Date format in use: RFC 3339 with offset (`2026-08-19T11:49:51+02:00`).

## Config quirks

- `hugo.yaml` `baseURL` is still `https://example.org/` — update before deploying.
- `locale: en-us` may need to be `languageCode: en-us` depending on Hugo version.

## Structure notes

- `assets/`, `data/`, `i18n/`, `layouts/`, `static/` are intentionally empty — Hugo override points, keep them.
- No CI workflows exist yet.
