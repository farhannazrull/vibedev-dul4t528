# PSI Pilot — Bike Tire Pressure Checker

Single-page vanilla HTML/CSS/JS app. No build tools, no package manager, no dependencies.

## Key facts

- **Only file**: `index.html` — open directly in a browser (no server needed)
- **Logic**: hardcoded pressure lookup tables per bike type & weight bracket
- **Bike types**: Road, Mountain, Gravel, Hybrid (selectable via styled radio cards)
- **Weight**: input in kg or lbs with live unit toggle
- **PSI ranges**: front & rear recommendations per weight bracket
- **Status classification**: Underinflated / Ideal / Overinflated with color-coded badge + tip
- **Pressure bar**: visual range from 0 to bike's max PSI, with ideal zone highlighted in green
- **Accessibility**: labels, aria attributes, fieldset/legend, role="alert", focus-visible styles
- **Validation**: weight range check (15-350 kg / 33-770 lbs), error message in alert role
- **XSS prevention**: `esc()` function using DOM textContent before innerHTML injection

## Data tables

Pressure brackets (weight in kg):
- Light: ≤ 60 kg
- Medium: ≤ 85 kg
- Heavy: > 85 kg

## Conventions

- Font: Inter (400–900) — loaded from Google Fonts
- Color palette: dark navy hero (`#1a1a2e`), teal-green accent (`#4fc3a1`), warm beige background (`#f2ece4`)
- Status colors: red (`#ffcdd2`) for under/over, green (`#a5d6a7`) for ideal
- Container: `max-width: 960px; padding: 0 20px;`

## What is NOT here

- No CI, tests, linters, formatters, typecheckers, or codegen
- No package.json, no lockfile, no manifest of any kind
- No server, no API calls, no backend, no database
