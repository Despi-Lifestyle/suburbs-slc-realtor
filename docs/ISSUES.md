# Known Issues & Bugs

Discovered during initial code review on March 2, 2026.

---

## Critical (Will break the site)

### ISS-001: File structure doesn't match link paths
- **Status**: RESOLVED (commit b20bece)
- **Phase**: 1
- **Description**: All HTML files were in the root directory, but index.html linked to them as `free-resources/*.html`.
- **Fix**: Reorganized files into proper directory structure. All 27 internal links verified.

### ISS-002: Relocation guide page in sandbox path
- **Status**: RESOLVED (commit b20bece)
- **Phase**: 1
- **Description**: The lead capture landing page was at `mnt/user-data/outputs/...` — a Claude browser sandbox artifact.
- **Fix**: Moved to `/relocation-guide/index.html`. Deleted `mnt/` directory.

### ISS-003: Cloudflare-specific code won't work on Vercel
- **Status**: RESOLVED (commit b20bece)
- **Phase**: 1
- **Description**: Email address was encoded with Cloudflare email protection + Cloudflare decoder script.
- **Fix**: Replaced with plain `mailto:natalie@griffithteamre.com`. Removed Cloudflare script.

### ISS-004: PDF download path broken
- **Status**: RESOLVED (commit b20bece)
- **Phase**: 1
- **Description**: thank-you.html linked to `../assets/pdfs/` which didn't exist.
- **Fix**: Created `assets/pdfs/` directory and moved PDF there. Path now resolves correctly.

### ISS-005: Lead form has no backend
- **Status**: Open
- **Phase**: 2
- **File**: `relocation-guide/index.html` lines 1024-1029
- **Description**: `handleSubmit()` only hides the form and shows a success message. Data is not sent anywhere — all leads are lost.
- **Fix**: Integrate a form backend service (Formspree, serverless function, etc.) with Lofty CRM bridge.

---

## Medium (Functional issues)

### ISS-006: Placeholder social media links
- **Status**: Open (waiting on Despi for real URLs)
- **Phase**: 2
- **Description**: YouTube and Instagram links point to generic `youtube.com` and `instagram.com` instead of Natalie's actual profiles.
- **Files**: `index.html` lines 447, 649, 650; `thank-you.html` line 71

### ISS-007: Three resource cards link to `#`
- **Status**: Open
- **Phase**: 3
- **File**: `index.html` lines 506, 521, 536
- **Description**: "Suburb Comparison Chart", "2025 Market Report", and "Relocation Timeline & Planner" cards all link to `#` with no actual content pages.
- **Fix**: Either build these pages or mark them as "Coming Soon" like the quiz card.

### ISS-008: No Open Graph / social meta tags
- **Status**: Open
- **Phase**: 2
- **Description**: No og:title, og:description, og:image tags on any page. Since this will be shared on YouTube and social media, preview cards will look blank/broken.
- **Fix**: Add OG tags to all pages. Create or source a social sharing preview image.

### ISS-009: No favicon
- **Status**: Open
- **Phase**: 2
- **Description**: No favicon configured on any page.
- **Fix**: Create a small gold house icon favicon matching the nav logo.

### ISS-010: PDF doesn't match marketing copy
- **Status**: Open (Despi will expand PDF separately)
- **Phase**: 3
- **Description**: The relocation guide landing page says "40+ pages" and "9 suburbs covered" but the actual PDF is only 9 pages covering 2 suburbs (South Jordan and Draper).
- **Fix**: Despi will expand the PDF. Until then, this is a known content gap.

---

## Low (Polish)

### ISS-011: Checklist progress doesn't persist
- **Status**: Open
- **Phase**: 2
- **File**: `first-time-buyer.html`
- **Description**: The page says "your progress saves automatically" but there's no localStorage implementation. Refreshing the page resets all checkboxes.
- **Fix**: Add localStorage save/load for checked items.

### ISS-012: Copyright year is 2025
- **Status**: Open
- **Phase**: 2
- **Files**: `index.html` line 654; relocation-guide page line 1019
- **Description**: Footer copyright says 2025. It's now 2026.
- **Fix**: Update to 2026.

### ISS-013: No .gitignore
- **Status**: RESOLVED (commit 94a51f0)
- **Phase**: 1
- **Description**: .DS_Store files throughout the project would be committed without a .gitignore.
- **Fix**: Created `.gitignore` excluding .DS_Store, .vscode, .claude, Thumbs.db.

---

## Tracking

| ID | Severity | Phase | Status |
|----|----------|-------|--------|
| ISS-001 | Critical | 1 | RESOLVED |
| ISS-002 | Critical | 1 | RESOLVED |
| ISS-003 | Critical | 1 | RESOLVED |
| ISS-004 | Critical | 1 | RESOLVED |
| ISS-005 | Critical | 2 | Open |
| ISS-006 | Medium | 2 | Open (blocked — waiting on URLs) |
| ISS-007 | Medium | 3 | Open |
| ISS-008 | Medium | 2 | Open |
| ISS-009 | Medium | 2 | Open |
| ISS-010 | Medium | 3 | Open (Despi handling) |
| ISS-011 | Low | 2 | Open |
| ISS-012 | Low | 2 | Open |
| ISS-013 | Low | 1 | RESOLVED |
