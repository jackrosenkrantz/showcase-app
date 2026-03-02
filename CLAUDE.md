# Showcase App — Claude Code Project Instructions

## Overview
This is a static showcase/portfolio site served by Express.js on Railway. It displays demo cards linking to various web experiences hosted as HTML pages in `public/`.

## Tech Stack
- **Server**: Node.js + Express, serves static files from `public/`
- **Deployment**: Railway (Nixpacks builder, auto PORT, `npm start`)
- **Frontend**: Pure HTML/CSS, no build step. All styling is embedded in each HTML file.

## Showcase Index Page (`public/index.html`) — Design Rules

### Card Grid System
- The index page uses a **CSS Grid** with `repeat(auto-fill, minmax(220px, 1fr))` — cards automatically flow into rows and columns based on screen width.
- All cards **MUST** use the `.demo-card` class and follow this exact HTML structure:
```html
<a href="page-name.html" class="demo-card">
  <span class="arrow">&rarr;</span>
  <div class="title">Card Title</div>
  <div class="desc">Short one-line description</div>
</a>
```
- Cards have a fixed `height: 110px` so they all appear exactly the same size.
- Titles use `text-overflow: ellipsis` and descriptions use `-webkit-line-clamp: 2` to gracefully truncate overflow.
- **Descriptions should be kept short** (under ~60 characters preferred) but longer text will be truncated cleanly.

### Adding a New Card
1. Create the HTML page in `public/` (e.g., `public/my-new-page.html`)
2. Add a new `<a>` element inside the `<div class="grid">` section of `public/index.html`, **before** the closing comment marker
3. Use the exact card structure above — do NOT deviate from this format
4. **Do NOT** add cards outside the `.grid` div — no full-width cards, no separate sections, no different card styles
5. If linking to an external URL, add `target="_blank"` to the `<a>` tag

### Adding a Private Card
Private cards go in the `<div class="hidden-grid">` section (below the "Private" divider). Same card structure applies.

### Design Tokens (CSS Variables)
```
--bg: #141210          (page background)
--surface: #1e1c19     (card background)
--surface-hover: #272420
--border: #2e2a26      (card border)
--border-hover: #4a4238
--muted: #6b6058
--text-secondary: #9a918a
--text-primary: #e8e0d8
--text-bright: #f5f0eb
--amber: #c4956a       (accent color)
```

### Typography
- **Headings/card titles**: `'Lora', serif` — weight 400
- **Body/descriptions**: `'Inter', sans-serif` — weight 300
- Card title: `0.95rem`, description: `0.72rem`

### Animation
- Cards use staggered `fadeUp` animations via `nth-child` selectors (supports up to 20 cards)
- If adding more than 20 public cards, extend the nth-child animation delay rules in the CSS

### Things to NEVER Do
- Do NOT add cards outside the `.grid` or `.hidden-grid` containers
- Do NOT create full-width card styles or alternate card layouts
- Do NOT change the grid system (e.g., fixed columns) — `auto-fill` handles responsiveness
- Do NOT use inline styles on cards for animation — the CSS nth-child rules handle it
- Do NOT add a separate CSS file — all styles stay embedded in the HTML
- Do NOT use JavaScript frameworks or build tools

## Individual Showcase Pages
Each page in `public/` is self-contained HTML with embedded CSS. They should:
- Maintain the dark aesthetic (dark backgrounds, light text, amber accents)
- Use the same Google Fonts (Inter + Lora) for consistency
- Be fully self-contained (no shared CSS/JS imports between pages)
