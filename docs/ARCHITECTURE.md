# Architecture & File Structure

## Current State (from Claude Browser export)

This is what was exported — everything is flat in the root with a leftover sandbox path:

```
/
├── index.html                          ← Main resource hub
├── cost-of-living.html                 ← Should be in /free-resources/
├── first-time-buyer.html               ← Should be in /free-resources/
├── outdoor-access.html                 ← Should be in /free-resources/
├── school-districts.html               ← Should be in /free-resources/
├── seasonal-moving-tips.html           ← Should be in /free-resources/
├── thank-you.html                      ← Should be in /relocation-guide/
├── SLC-Suburbs-Relocation-Guide.pdf    ← Should be in /assets/pdfs/
├── mnt/                                ← SANDBOX ARTIFACT — should not exist
│   └── user-data/outputs/slc-relocation-resources/
│       └── relocation-guide/
│           └── index.html              ← Should be at /relocation-guide/index.html
└── .DS_Store                           ← Should be gitignored
```

### What's Broken
- All links from index.html point to `free-resources/*.html` — but files are in root
- All sub-pages link back to `../index.html` — but they're in root (not a subfolder)
- Relocation guide page is in `mnt/` sandbox path
- thank-you.html links to `../assets/pdfs/` which doesn't exist
- Cloudflare email-protection code in index.html won't work on Vercel

---

## Target State (after reorganization)

```
/
├── index.html                          ← Main resource hub
├── relocation-guide/
│   ├── index.html                      ← Lead capture landing page
│   └── thank-you.html                  ← Post-form confirmation
├── free-resources/
│   ├── cost-of-living.html
│   ├── first-time-buyer.html
│   ├── outdoor-access.html
│   ├── school-districts.html
│   └── seasonal-moving-tips.html
├── assets/
│   └── pdfs/
│       └── SLC-Suburbs-Relocation-Guide.pdf
├── docs/                               ← Project documentation (not deployed)
│   ├── PRD.md
│   ├── ARCHITECTURE.md
│   └── ISSUES.md
├── .gitignore
└── README.md (optional)
```

### Link Map (after fix)

| From | Link | To |
|------|------|----|
| index.html | `relocation-guide/` | relocation-guide/index.html |
| index.html | `free-resources/cost-of-living.html` | free-resources/cost-of-living.html |
| index.html | `free-resources/first-time-buyer.html` | free-resources/first-time-buyer.html |
| index.html | `free-resources/outdoor-access.html` | free-resources/outdoor-access.html |
| index.html | `free-resources/school-districts.html` | free-resources/school-districts.html |
| index.html | `free-resources/seasonal-moving-tips.html` | free-resources/seasonal-moving-tips.html |
| free-resources/*.html | `../index.html` | index.html |
| free-resources/*.html | `../relocation-guide/` | relocation-guide/index.html |
| relocation-guide/index.html | `../index.html` | index.html |
| relocation-guide/thank-you.html | `../assets/pdfs/SLC-Suburbs-Relocation-Guide.pdf` | assets/pdfs/*.pdf |

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
| Forms | TBD | Needs to integrate with Lofty CRM |

## Deployment

Vercel with GitHub integration:
1. Push to `main` branch on GitHub
2. Vercel auto-detects static site (no framework config needed)
3. Deploys all HTML files as pages
4. Directory structure maps directly to URL routes
