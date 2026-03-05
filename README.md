# SLC Suburbs Relocation Resource Hub

A lead-generation landing page and resource hub for **Natalie Griffith**, a REALTOR specializing in Salt Lake City suburb relocations.

## What This Is

A static website that serves as a destination for Natalie's YouTube channel and social media. Visitors can:
- Browse **9 free resources** (cost of living, school districts, outdoor access, suburb comparison, market report, quiz, relocation planner, first-time buyer checklist, seasonal moving tips)
- Download a **gated relocation guide** by submitting their contact info (lead capture)
- Contact Natalie directly via phone or email

**Domain**: nataliegriffith.com

## Tech Stack

- Static HTML / CSS / vanilla JS (no framework, no build step)
- Google Fonts (DM Serif Display + Plus Jakarta Sans)
- Hosted on **Vercel** (auto-deploys from this repo)
- Form backend: **Formspree** (AJAX submit with honeypot spam protection)
- CRM: Lofty (Zapier bridge from Formspree — pending setup)
- Analytics: GA4 (pending installation)

## Local Development

No build step required. Just open any `.html` file in a browser, or use a local server:

```bash
# Using Python
python3 -m http.server 8000

# Using Node (if npx available)
npx serve .
```

Then visit `http://localhost:8000`

## Project Docs

| Doc | Description |
|-----|-------------|
| [docs/PRD.md](docs/PRD.md) | Product requirements, goals, phases |
| [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) | File structure and tech decisions |
| [docs/ISSUES.md](docs/ISSUES.md) | Known bugs and issue tracker |
| [CHANGELOG.md](CHANGELOG.md) | Version history |
| [CLAUDE.md](CLAUDE.md) | AI assistant project instructions |

## Deployment

Vercel auto-deploys from the `main` branch. Directory structure maps directly to URL routes.

## License

Private — built by Despi for Natalie Griffith Real Estate Team.
