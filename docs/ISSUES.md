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
- **Status**: Partially resolved (YouTube updated, Instagram still placeholder)
- **Phase**: 2
- **Description**: YouTube and Instagram links point to generic `youtube.com` and `instagram.com` instead of Natalie's actual profiles.
- **Fix**: YouTube updated to `@LivingintheSuburbsOfSLC` in index.html (2 links) and thank-you.html (1 link). Instagram still needs real URL.
- **Files**: `index.html` lines 447, 649, 650; `thank-you.html` line 71

### ISS-007: Three resource cards link to `#`
- **Status**: RESOLVED (commit 2626c27)
- **Phase**: 3
- **File**: `index.html` lines 506, 521, 536
- **Description**: "Suburb Comparison Chart", "2025 Market Report", and "Relocation Timeline & Planner" cards all link to `#` with no actual content pages.
- **Fix**: Converted all three to "Coming Soon" state matching the existing quiz card pattern.

### ISS-008: No Open Graph / social meta tags
- **Status**: RESOLVED (partial — text tags added, og:image pending)
- **Phase**: 2
- **Description**: No og:title, og:description, og:image tags on any page. Since this will be shared on YouTube and social media, preview cards will look blank/broken.
- **Fix**: Added og:type, og:title, og:description + twitter:card, twitter:title, twitter:description to all 8 pages. Also added `<meta name="description">` to the 6 pages that were missing it. og:image will be added when a 1200x630 branded image is provided.

### ISS-009: No favicon
- **Status**: RESOLVED (commit 63d096d)
- **Phase**: 2
- **Description**: No favicon configured on any page.
- **Fix**: Created SVG favicon (`assets/images/favicon.svg`) — gold rounded square with white house icon. Added to all 8 HTML pages.

### ISS-010: PDF doesn't match marketing copy
- **Status**: Open (Despi will expand PDF separately)
- **Phase**: 3
- **Description**: The relocation guide landing page says "40+ pages" and "9 suburbs covered" but the actual PDF is only 9 pages covering 2 suburbs (South Jordan and Draper).
- **Fix**: Despi will expand the PDF. Until then, this is a known content gap.

---

## Low (Polish)

### ISS-011: Checklist progress doesn't persist
- **Status**: RESOLVED (commit 2626c27)
- **Phase**: 2
- **File**: `free-resources/first-time-buyer.html`
- **Description**: The page says "your progress saves automatically" but there's no localStorage implementation. Refreshing the page resets all checkboxes.
- **Fix**: Added localStorage save/load with `saveProgress()`, `loadProgress()` functions. Progress persists across page refreshes.

### ISS-012: Copyright year is 2025
- **Status**: RESOLVED (commit 2626c27)
- **Phase**: 2
- **Files**: `index.html`, `relocation-guide/index.html`, `free-resources/first-time-buyer.html`
- **Description**: Footer copyright said 2025. It's now 2026.
- **Fix**: Updated all 3 instances from 2025 to 2026.

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
| ISS-007 | Medium | 3 | RESOLVED |
| ISS-008 | Medium | 2 | RESOLVED (og:image pending) |
| ISS-009 | Medium | 2 | RESOLVED |
| ISS-010 | Medium | 3 | Open (Despi handling) |
| ISS-011 | Low | 2 | RESOLVED |
| ISS-012 | Low | 2 | RESOLVED |
| ISS-013 | Low | 1 | RESOLVED |
