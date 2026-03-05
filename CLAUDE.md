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

## File Structure
```
/
├── index.html                          ← Main resource hub (13 pages total)
├── relocation-guide/
│   ├── index.html                      ← Lead capture (Formspree AJAX)
│   └── thank-you.html                  ← Post-form + PDF download
├── free-resources/
│   ├── cost-of-living.html
│   ├── first-time-buyer.html           ← Interactive checklist (localStorage)
│   ├── market-report.html              ← Market snapshot + 2026 forecast
│   ├── outdoor-access.html
│   ├── quiz.html                       ← "Is Utah Right for You?" (10 questions)
│   ├── relocation-planner.html         ← 41 tasks, 6 phases (localStorage)
│   ├── school-districts.html
│   ├── seasonal-moving-tips.html
│   └── suburb-comparison.html          ← Side-by-side comparison chart
├── internal/                           ← Internal tools (not linked publicly)
│   └── utm-link-builder.html           ← UTM link generator for YouTube/social
├── assets/
│   ├── images/
│   │   └── favicon.svg
│   └── pdfs/
│       ├── SLC-Suburbs-Relocation-Guide.pdf
│       └── relocation-guide-2026.html  ← Print-ready HTML guide (40+ pages)
├── docs/
│   ├── PRD.md
│   ├── ARCHITECTURE.md
│   └── ISSUES.md
├── CHANGELOG.md
├── README.md
├── .gitignore
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
