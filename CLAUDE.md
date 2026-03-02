# CLAUDE.md — Project Instructions

## Project
SLC Suburbs Relocation Resource Hub for Natalie Griffith (realtor client).
Static HTML/CSS/JS site hosted on Vercel, deployed from GitHub.

## Repo
https://github.com/Despi-Lifestyle/suburbs-slc-realtor

## Key Docs
- `docs/PRD.md` — Product requirements, phases, goals
- `docs/ARCHITECTURE.md` — File structure, link map, tech stack
- `docs/ISSUES.md` — Known bugs and issues tracker
- `CHANGELOG.md` — Version history

## Code Conventions
- **No framework** — pure static HTML, CSS (in `<style>` tags), vanilla JS (in `<script>` tags)
- **No build step** — files deploy as-is to Vercel
- **CSS variables** — all colors/fonts defined in `:root` using the established design tokens
- **Inline SVGs** — no icon libraries; all icons are inline SVG
- **Google Fonts only** — DM Serif Display (display) + Plus Jakarta Sans (body)
- **Responsive** — mobile-first media queries, breakpoints at 640px, 768px, 960px
- **Semantic HTML** — proper heading hierarchy, nav/section/footer elements

## Design Tokens
| Token | Value |
|-------|-------|
| Gold | `#C8A84E` |
| Gold Light | `#E8D08C` |
| Gold Dark | `#A8882E` |
| Black | `#1A1A1A` |
| Charcoal | `#2D2D2D` |
| Slate | `#4A4A4A` |
| Warm Gray | `#8A8378` |
| Light Warm | `#F7F4EF` |
| Cream | `#FDFBF7` |
| White | `#FFFFFF` |

## File Structure (target)
```
/
├── index.html
├── relocation-guide/
│   ├── index.html
│   └── thank-you.html
├── free-resources/
│   ├── cost-of-living.html
│   ├── first-time-buyer.html
│   ├── outdoor-access.html
│   ├── school-districts.html
│   └── seasonal-moving-tips.html
├── assets/
│   └── pdfs/
│       └── SLC-Suburbs-Relocation-Guide.pdf
├── docs/
└── CLAUDE.md
```

## Important Context
- This project is designed to be **repeatable/templatizable** — Despi plans to offer this as a product for other realtors if it works well with Natalie.
- Keep code clean and modular so it can be adapted for different agents/brands.
- The site connects to Natalie's main website at griffithteamre.com (it complements, not replaces).
- There is a future need for a **password-protected internal resource section** — design decisions should not preclude this.
- Form submissions must flow to **Lofty CRM** (Natalie's CRM) AND give Despi a copy.

## Rules
- Do NOT commit `.DS_Store` files
- Do NOT introduce npm, build tools, or frameworks unless explicitly discussed
- Do NOT delete or modify the PDF — Despi manages that content separately
- Always update `docs/ISSUES.md` when discovering new bugs
- Always update `CHANGELOG.md` when making meaningful changes
- Prefer editing existing files over creating new ones
