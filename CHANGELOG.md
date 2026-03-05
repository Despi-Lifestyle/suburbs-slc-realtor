# Changelog

All notable changes to the SLC Suburbs Relocation Resource Hub.

---

## [Unreleased]

### Remaining
- [ ] Replace `YOUR_FORM_ID` in relocation-guide form with Formspree endpoint
- [ ] Set up Lofty CRM connection (Zapier bridge from Formspree)
- [ ] Add agent headshot / og:image (1200x630 branded image)
- [ ] Replace `BASE_URL` in UTM link builder with production domain
- [ ] Add GA4 snippet to all pages
- [ ] Generate final PDF from relocation-guide-2026.html
- [ ] Explore password-protected internal resource section

---

## [0.5.0] — 2026-03-04

### Added
- Internal UTM link builder tool at `/internal/utm-link-builder.html`
  - Interactive link builder with dropdowns for destination, source, medium, and campaign
  - Pre-built links table for common YouTube scenarios (6 links, copy-to-clipboard)
  - Video description template with UTM-tracked links, ready to paste
  - Form data vs analytics data reference guide
  - UTM naming conventions with rules and examples
  - Google Analytics setup instructions with code snippet
- Lead capture form wired to Formspree (AJAX submit with redirect to thank-you page)
- `name` attributes on all form inputs (firstName, email, phone)
- Honeypot spam protection (`_gotcha` field)
- Footer with Instagram link on thank-you page

### Fixed
- Footer phone/email now clickable (tel:/mailto:) across all 9 resource pages
- 6 plain-text URLs in relocation planner now clickable links (dld.utah.gov, vote.utah.gov, immunize.utah.gov, rideuta.com)
- Back-link CSS inconsistency on 4 pages (added flex layout)
- `rel="noopener noreferrer"` added to external links on relocation-guide and thank-you pages
- Brokerage name corrected to full "Realty One Group Signature South Valley"
- Headshot placeholder text hidden from public view
- Cost-of-living: housing badge "At Average" → "Above Average", income tax 4.85% → 4.65%
- School districts: "Four" → "Three" school districts
- Relocation planner: item count 42 → 41
- Market report: Bluffdale badge corrected from "Seller's Market" to "Competitive"
- Mobile table layout for cost-of-living suburb comparison
- Print stylesheet fixes: color-adjust rules, school district corrections in guide
- Quiz print stylesheet added with branded header/footer
- Misleading "check your inbox" messaging removed from form flow

---

## [0.4.0] — 2026-03-04

### Added
- Full 40+ page print-ready HTML Relocation Guide (2026 Edition) at `assets/pdfs/relocation-guide-2026.html`
- All 17 chapters: Welcome, How to Use, 9 Suburbs at a Glance overview table, 9 individual suburb profiles (South Jordan, Draper, Herriman, Sandy, Cottonwood Heights, Holladay, Millcreek, Riverton, Bluffdale), School District Comparison, Outdoor & Recreation Access, Cost of Living Breakdown, Relocation Timeline, Working with Natalie
- Updated all suburb data to 2025 market figures (median prices, price/sqft, days on market, walk scores)
- Print-optimized layout with branded cover page, headers, and footers on every page

---

## [0.3.0] — 2026-03-04

### Added
- "Download as PDF" button on 4 resource pages: Suburb Comparison, Market Report, First-Time Buyer Checklist, and Relocation Planner
- Print stylesheets with Natalie's branding (header + footer) baked into every PDF
- Print-optimized layout: hides nav/footer/CTAs, forces white background, handles page breaks, adapts dark forecast box for print

---

## [0.2.0] — 2026-03-04

### Added
- Interactive "Is Utah Right for You?" quiz (10 questions, weighted suburb matching)
- Relocation Timeline & Moving Planner (42 tasks, 6 phases, localStorage persistence)
- Side-by-Side Suburb Comparison Chart (table + 9 profile cards with real data)
- SLC Suburbs Market Report (market snapshot + 9 suburb cards + 2026 forecast)
- All 4 new pages linked from hub page

### Changed
- Reorganized hub page from gated/ungated sections to user-journey stages (Explore → Choose → Buy)
- Replaced YouTube nav button with "Get the Free Guide" gold CTA
- Updated Instagram link to real URL
- Added rel="noopener noreferrer" to external links

---

## [0.0.1] — 2026-03-02

### Added
- Initial import of all assets from Claude browser
- 7 HTML pages (main hub, 5 free resources, thank-you page)
- 1 lead capture landing page (relocation guide)
- 1 PDF relocation guide (9 pages, partial content)
- Project documentation (PRD, Architecture, Issues tracker)
- CLAUDE.md, README.md, CHANGELOG.md, .gitignore
