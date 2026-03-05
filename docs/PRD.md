# Product Requirements Document (PRD)
## SLC Suburbs Relocation Resource Hub — Natalie Griffith Real Estate

**Version**: 1.2
**Date**: March 5, 2026
**Author**: Despi
**Status**: Draft

---

## 1. Overview

### 1.1 What Is This?
A static landing page and resource hub for **Natalie Griffith**, a REALTOR specializing in helping families relocate to Salt Lake City suburbs. The site serves as a destination from Natalie's YouTube channel and social media — providing free resources that build trust and capturing leads for her real estate business.

This site **complements** Natalie's main website at griffithteamre.com. It is not a replacement — it's a focused lead-gen funnel specifically for relocation content.

### 1.2 Primary Goal
**Lead generation.** Convert YouTube viewers and social media visitors into leads by offering free relocation resources in exchange for contact information (name, email, phone). Captured leads flow into Natalie's **Lofty CRM** for follow-up.

### 1.3 Secondary Goals
- Establish Natalie as the go-to SLC suburbs relocation expert
- Provide genuinely useful free content that builds trust
- Drive traffic to Natalie's YouTube channel and direct contact
- Provide **internal resources** for Natalie's existing clients (future: password-protected section)

### 1.4 Bigger Picture
This project is built by **Despi** as a client engagement. If successful, the site architecture and approach is designed to be **repeatable and templatizable** — potentially offered as a product/service for other realtors and professionals who need lead-gen landing pages tied to their social media presence.

Design and code decisions should keep this scalability in mind — agent name, colors, content, and branding should be easy to swap out for a new client.

---

## 2. Target Audience

| Segment | Description |
|---------|-------------|
| Primary | Families considering relocating to Salt Lake City from out-of-state |
| Secondary | First-time homebuyers in the SLC area |
| Tertiary | YouTube viewers who watch Natalie's SLC suburb content |

**User Journeys**:
1. **Lead capture**: YouTube video / social post → landing page → submit form for gated guide → Natalie follows up via Lofty CRM
2. **Trust building**: YouTube video / social post → landing page → browse free resources → eventually contacts Natalie or returns for gated guide
3. **Internal (future)**: Existing client → login → access internal resources and documents

---

## 3. Site Map & Pages

```
/                                    → Main resource hub (index.html)
/relocation-guide/                   → Lead capture landing page (gated)
/relocation-guide/thank-you          → Post-form confirmation + PDF download
/free-resources/cost-of-living       → Cost of living snapshot
/free-resources/first-time-buyer     → Interactive buyer checklist
/free-resources/outdoor-access       → Outdoor access by suburb
/free-resources/school-districts     → School district overview
/free-resources/seasonal-moving-tips → Seasonal moving guide
/free-resources/suburb-comparison    → Side-by-side suburb comparison chart
/free-resources/market-report        → SLC suburbs market report + 2026 forecast
/free-resources/quiz                 → "Is Utah Right for You?" interactive quiz
/free-resources/relocation-planner   → Relocation timeline & moving planner (41 tasks)
/internal/utm-link-builder           → UTM link generator (internal, not public-facing)
/assets/pdfs/                        → PDF downloads + print-ready HTML guide
```

---

## 4. Functional Requirements

### 4.1 Lead Capture Form (Relocation Guide Page)
| Field | Type | Required |
|-------|------|----------|
| First Name | Text | Yes |
| Email Address | Email | Yes |
| Phone Number | Tel | Yes |

**On Submit:**
1. Send data to form backend service
2. Show success state with PDF download button
3. Data must flow to:
   - Natalie's Lofty CRM (for follow-up)
   - Despi's tracking system (for analytics/oversight)

**Form Backend: Formspree (chosen)**
- AJAX submission with JSON response handling
- Honeypot spam protection (`_gotcha` hidden field)
- Redirects to thank-you page on success with PDF download
- **Still needed**: Replace `YOUR_FORM_ID` placeholder with real Formspree endpoint ID, then set up Zapier bridge to Lofty CRM

### 4.2 Free Resources (Ungated)
- No form required — instant access
- Each page has its own nav, content, and CTA back to the relocation guide
- Interactive checklist (first-time-buyer) should persist progress via localStorage

### 4.3 Navigation
- Sticky nav on all pages
- Brand logo + name links to home
- Sub-pages have "← All Resources" back link
- YouTube CTA button in nav (main page)

### 4.4 CTA Strategy
- Every free resource page ends with a CTA to get the full relocation guide (funneling to the gated form)
- Main page has "Call Natalie" CTA banner
- Phone number is click-to-call on mobile

---

## 5. Non-Functional Requirements

### 5.1 Performance
- All pages must be static HTML/CSS/JS (no build step required)
- Target: < 2s load time on 3G
- No external JS dependencies (except Google Fonts)
- SVG icons inline (no icon library needed)

### 5.2 SEO & Social Sharing
- Each page needs proper `<title>` and `<meta description>` (already done)
- Open Graph meta tags needed for social sharing previews (og:title, og:description, og:image)
- Twitter Card meta tags
- Favicon needed

### 5.3 Mobile Responsiveness
- All pages must work on mobile (375px+), tablet, and desktop
- Existing CSS already handles this with media queries

### 5.4 Accessibility
- Semantic HTML structure
- Proper heading hierarchy
- Alt text for any images added later
- Keyboard navigable interactive elements

---

## 6. Design System

Already established across all pages:

| Token | Value |
|-------|-------|
| Gold | `#C8A84E` |
| Gold Light | `#E8D08C` |
| Gold Dark | `#A8882E` |
| Black | `#1A1A1A` |
| Charcoal | `#2D2D2D` |
| Cream | `#FDFBF7` |
| Display Font | DM Serif Display |
| Body Font | Plus Jakarta Sans |

---

## 7. Phases & Milestones

### Phase 1: Foundation — COMPLETE
- [x] Review all assets from Claude browser
- [x] Create PRD and documentation
- [x] Initialize GitHub repo with raw files
- [x] Reorganize file structure to match site map
- [x] Fix all broken internal links (27 links verified)
- [x] Remove Cloudflare-specific code
- [x] Deploy to Vercel (basic working site)

### Phase 2: Functionality — COMPLETE
- [x] Choose and integrate form backend (Formspree with AJAX submit)
- [ ] Set up Lofty CRM integration (Zapier bridge from Formspree — pending Formspree endpoint ID)
- [x] Add localStorage to first-time-buyer checklist
- [x] Replace placeholder social links with real URLs
- [x] Add Open Graph / social meta tags (og:image pending branded image)
- [x] Add favicon (SVG, gold house icon)
- [x] Update copyright year to 2026

### Phase 3: Content Completion — MOSTLY COMPLETE
- [ ] Expand PDF to full 40+ page guide (Despi handles separately)
- [x] Build out Suburb Comparison Chart page
- [x] Build out Market Report page
- [x] Build out Relocation Timeline/Planner page (41 tasks, 6 phases)
- [ ] Add Natalie's real headshot to agent section
- [x] Add "Is Utah Right for You?" quiz (10 questions, weighted suburb matching)

### Phase 4: Optimization & Launch — IN PROGRESS
- [ ] Performance audit (Lighthouse)
- [ ] Final QA across devices
- [ ] Connect custom domain (nataliegriffith.com)
- [ ] Share links with Natalie for YouTube/social
- [ ] Add GA4 snippet to all 13 HTML pages
- [x] Build internal UTM link builder tool

### Phase 5: Internal Resources & Scalability (Future)
- [ ] Design password-protected internal resource section for existing clients
- [ ] Evaluate authentication approach (simple password gate vs. login system)
- [ ] Document templatization process for reuse with other realtors
- [ ] Create a "white-label" version of the site with swappable branding variables

---

## 8. Known Placeholder Content

| Item | Location | Status |
|------|----------|--------|
| YouTube channel URL | Nav, footer (all pages) | DONE — linked to @LivingintheSuburbsOfSLC |
| Instagram URL | Footer (all pages) | DONE — linked to nataliegsuburbspecialistofslc |
| Natalie's headshot | Agent section (relocation-guide page) | Placeholder hidden (needs real photo) |
| Suburb Comparison Chart | index.html card | DONE — fully built |
| Market Report | index.html card | DONE — fully built |
| Relocation Timeline/Planner | index.html card | DONE — fully built (41 tasks, 6 phases) |
| "Is Utah Right for You?" Quiz | index.html card | DONE — fully built (10 questions) |
| og:image | All pages | Pending — needs 1200x630 branded image |
| Formspree endpoint ID | relocation-guide/index.html | Pending — `YOUR_FORM_ID` placeholder |
| GA4 measurement ID | All pages | Pending — no analytics snippet installed |

---

## 9. Tech & Deployment

| Item | Value |
|------|-------|
| Hosting | Vercel |
| Repo | https://github.com/Despi-Lifestyle/suburbs-slc-realtor |
| Framework | None (static HTML/CSS/JS) |
| Build Step | None required |
| Domain | nataliegriffith.com |
| CRM | Lofty (integration TBD) |

---

## 10. Success Metrics

| Metric | Target |
|--------|--------|
| Form submissions (leads) | Track monthly |
| Page views from YouTube | Track via Vercel Analytics or similar |
| PDF downloads | Track via form completion rate |
| Time on site | Track engagement with free resources |

> Analytics solution TBD — Vercel Analytics (free tier) or simple Google Analytics.
