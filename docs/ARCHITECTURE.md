# Architecture & File Structure

## File Structure

```
/
├── index.html                          ← Main resource hub
├── relocation-guide/
│   ├── index.html                      ← Lead capture landing page
│   └── thank-you.html                  ← Post-form confirmation
├── free-resources/
│   ├── cost-of-living.html
│   ├── first-time-buyer.html
│   ├── market-report.html
│   ├── outdoor-access.html
│   ├── quiz.html
│   ├── relocation-planner.html
│   ├── school-districts.html
│   ├── seasonal-moving-tips.html
│   └── suburb-comparison.html
├── internal/                              ← Internal tools (not linked from public pages)
│   └── utm-link-builder.html              ← UTM link generator for YouTube/social
├── assets/
│   ├── images/
│   │   └── favicon.svg
│   └── pdfs/
│       ├── SLC-Suburbs-Relocation-Guide.pdf
│       └── relocation-guide-2026.html     ← Print-ready HTML guide (40+ pages)
├── docs/                               ← Project documentation (not deployed)
│   ├── PRD.md
│   ├── ARCHITECTURE.md
│   └── ISSUES.md
├── .gitignore
└── README.md (optional)
```

### Link Map

| From | Link | To |
|------|------|----|
| index.html | `relocation-guide/` | relocation-guide/index.html |
| index.html | `free-resources/cost-of-living.html` | free-resources/cost-of-living.html |
| index.html | `free-resources/first-time-buyer.html` | free-resources/first-time-buyer.html |
| index.html | `free-resources/outdoor-access.html` | free-resources/outdoor-access.html |
| index.html | `free-resources/school-districts.html` | free-resources/school-districts.html |
| index.html | `free-resources/seasonal-moving-tips.html` | free-resources/seasonal-moving-tips.html |
| index.html | `free-resources/suburb-comparison.html` | free-resources/suburb-comparison.html |
| index.html | `free-resources/market-report.html` | free-resources/market-report.html |
| index.html | `free-resources/quiz.html` | free-resources/quiz.html |
| index.html | `free-resources/relocation-planner.html` | free-resources/relocation-planner.html |
| free-resources/*.html | `../index.html` | index.html |
| free-resources/*.html | `../relocation-guide/` | relocation-guide/index.html |
| relocation-guide/index.html | `../index.html` | index.html |
| relocation-guide/index.html | `thank-you.html` | relocation-guide/thank-you.html (via Formspree AJAX redirect) |
| relocation-guide/thank-you.html | `../assets/pdfs/SLC-Suburbs-Relocation-Guide.pdf` | assets/pdfs/*.pdf |
| internal/utm-link-builder.html | — | Not linked from any public page (direct URL access only) |

---

## Tech Stack

| Layer | Choice | Notes |
|-------|--------|-------|
| Markup | Static HTML | No framework, no build step |
| Styling | Inline `<style>` | CSS variables for theming, each page self-contained |
| JS | Inline `<script>` | Minimal — scroll reveal observer, form handling, checklist toggle |
| Fonts | Google Fonts (CDN) | DM Serif Display + Plus Jakarta Sans |
| Icons | Inline SVGs | No icon library dependency |
| Hosting | Vercel | Auto-deploys from GitHub |
| Forms | Formspree (AJAX) | Wired with honeypot spam protection; needs endpoint ID + Zapier → Lofty CRM |

## Deployment

- **Domain**: nataliegriffith.com
- **Host**: Vercel with GitHub integration

1. Push to `main` branch on GitHub
2. Vercel auto-detects static site (no framework config needed)
3. Deploys all HTML files as pages
4. Directory structure maps directly to URL routes

## Analytics (not yet active)

UTM link builder is ready at `/internal/utm-link-builder.html`. Google Analytics 4 (GA4) needs to be added to all 13 public HTML pages before UTM tracking data will be captured. See the UTM builder's Section 6 for setup instructions.
