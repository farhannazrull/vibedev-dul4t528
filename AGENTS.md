# Wanderlist — Travel Bucket List

Single-page vanilla HTML/CSS/JS app. No build tools, no package manager, no dependencies.

## Key facts

- **Only file**: `index.html` — open directly in a browser (no server needed)
- **Data**: persisted in `localStorage` under key `wanderlist_destinations`
- **Statuses**: `Dreaming` → `Planning` → `Visited` (cycled in that order)
- **Storage key**: `wanderlist_destinations` (hardcoded at `index.html:270`)
- **Globals**: `window.__update(id, status)` and `window.__delete(id)` exposed for inline handlers

## Conventions

- Fonts: Playfair Display (headings), Inter (body) — loaded from Google Fonts
- Color palette: dark navy hero (`#1a1a2e`), gold accent (`#f0a500`), warm beige background (`#faf6f0`)
- Badge colors: Dreaming=neutral brown, Planning=gold, Visited=green

## What is NOT here

- No CI, tests, linters, formatters, typecheckers, or codegen
- No package.json, no lockfile, no manifest of any kind
- No server, no API calls, no backend
