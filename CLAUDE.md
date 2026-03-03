# Showcase App — Claude Code Project Instructions

## Overview
This is a static showcase/portfolio site served by Express.js on Railway. It uses a **folder/dashboard** navigation structure:

- `index.html` — top-level dashboard with category folder cards
- `archetypes.html` — dashboard for archetype identity apps
- `client-work.html` — dashboard for client landing pages and SEO projects
- `tools.html` — dashboard for utilities, trackers, and productivity tools

Each dashboard links to individual HTML pages in `public/`.

## Tech Stack
- **Server**: Node.js + Express, serves static files from `public/`
- **Deployment**: Railway (Nixpacks builder, auto PORT, `npm start`)
- **Frontend**: Pure HTML/CSS, no build step. All styling is embedded in each HTML file.

## Site Structure

### Index Page (`public/index.html`)
Shows 3 **folder cards** (`.folder-card` class) linking to category dashboards:
- Archetypes → `archetypes.html`
- Client Work → `client-work.html`
- Tools → `tools.html`

Folder cards are `height: 140px` with an icon, title, and page count meta line. Do NOT add individual page cards to index.html — it only contains category folders.

### Category Dashboards (`archetypes.html`, `client-work.html`, `tools.html`)
Each dashboard shows a grid of **page cards** (`.demo-card` class) linking to individual pages. They share the same card structure:

```html
<a href="page-name.html" class="demo-card">
  <span class="arrow">&rarr;</span>
  <div class="title">Card Title</div>
  <div class="desc">Short one-line description</div>
</a>
```

- Cards have a fixed `height: 110px`
- Titles use `text-overflow: ellipsis`, descriptions use `-webkit-line-clamp: 2`
- Each dashboard has a `<!-- Add new cards here -->` comment marker for the CCP bot
- Each dashboard has a `<a href="/" class="back">` link to return to the index
- Only `archetypes.html` has a private/hidden section

### Adding a New Page
1. Create the HTML page in `public/` (e.g., `public/my-page.html`)
2. Add a card to the correct **category dashboard** (NOT index.html), before the `<!-- Add new cards here -->` comment
3. Use the exact `.demo-card` structure above
4. Update the page count in `index.html`'s folder card `.meta` element if needed

### Categories
- **archetypes** — identity apps, archetype-themed experiences, ritual/practice tools
- **client-work** — landing pages, SEO pages, client projects, business sites
- **tools** — utilities, dashboards, productivity tools, trackers

## Design Tokens (CSS Variables)
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

## Typography
- **Headings/card titles**: `'Lora', serif` — weight 400
- **Body/descriptions**: `'Inter', sans-serif` — weight 300
- Card title: `0.95rem`, description: `0.72rem`

## Animation
- Cards use staggered `fadeUp` animations via `nth-child` selectors (supports up to 10 cards per dashboard)
- Do NOT use inline animation styles — the CSS nth-child rules handle it

## Things to NEVER Do
- Do NOT add page cards to `index.html` — it only has folder cards
- Do NOT add cards outside the `.grid` or `.hidden-grid` containers
- Do NOT create alternate card layouts or styles
- Do NOT change the grid system — `auto-fill` handles responsiveness
- Do NOT use inline styles on cards for animation
- Do NOT add separate CSS files — all styles stay embedded in HTML
- Do NOT use JavaScript frameworks or build tools

## Individual Showcase Pages
Each page in `public/` is self-contained HTML with embedded CSS. They should:
- Maintain the dark aesthetic (dark backgrounds, light text, amber accents)
- Use the same Google Fonts (Inter + Lora) for consistency
- Be fully self-contained (no shared CSS/JS imports between pages)
