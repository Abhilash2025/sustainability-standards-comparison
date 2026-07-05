# SBTi CNZS V2.0 vs ESRS E1 & CSRD Voluntary — Comparative Analysis Webapp

**Purpose:** Single-file digital webpage hosting a structured interoperability and gap analysis between the SBTi Corporate Net-Zero Standard V2.0, ESRS E1 Climate Change, and CSRD Voluntary Annex for undertakings below 1,000 employees.

**Built:** 2026-07-06
**File:** `index.html` (single file, zero dependencies, no build step)

---

## 1. What's in the Folder

```
SBTI_ESRS_webapp/
├── index.html              # Main comparative analysis webapp (~96KB)
├── sbti-map.html           # SBTi CNZS V2.0 criteria reference map
├── esrs-map.html           # ESRS E1 Climate Change reference map
├── csrd-map.html           # CSRD Voluntary Annex reference map
└── README.md               # This document
```

**Deployment:** Any static hosting (GitHub Pages, Vercel, Netlify, Cloudflare Pages). No build step, no npm, no external CDN calls. Copy the folder contents and push.

---

## 2. Feedback Fixes Applied (v3 Iteration)

The following fixes have been applied:

| Fix # | Request | Status | Implementation |
|-------|---------|--------|----------------|
| 1 | Horizontal topbar, remove sidebar | ✅ Done | Fixed topbar with horizontal nav, brand, theme toggle, progress bar. Content expanded to full width. |
| 2 | Add owner for each checklist action | ✅ Done | Gap-Action Checklist (Section 07) includes Owner column per row. |
| 3 | Add SBTi Criteria Map + ESRS E1 Map + CSRD Voluntary Map | ✅ Done | Standalone `sbti-map.html`, `esrs-map.html`, and `csrd-map.html` files created. All linked from main nav. |
| 4 | Ambient background with particles | ✅ Done | CSS-only particle system with floating dots and orb gradients, no JavaScript, no external assets. |
| 5 | Merge 3 frameworks into 2 (with CSRD Voluntary as third column) | ✅ Done | Section 01 tables show SBTi vs ESRS E1 & CSRD Voluntary Annex. |
| 6 | Stack cards vertically instead of 2×3 grid | ✅ Done | Governance and Target cards use `.card-list` (vertical stack). |
| 7 | Remove Standard Text Explorer | ✅ Done | Section 08 removed and replaced with Practical Implications. |
| 8 | Add CSRD Voluntary column to Coverage Depth table | ✅ Done | Section 05 now has 4 columns: Theme, SBTi Depth, ESRS Depth, CSRD Voluntary. |
| 9 | Add CSRD Voluntary Ref to Interoperability Matrix | ✅ Done | Section 06 now has 6 columns including CSRD Voluntary Ref. |
| 10 | Add CSRD Voluntary Ref to Criteria Map table | ✅ Done | Section 05 expandable criteria map has 4 columns including CSRD Voluntary. |
| 11 | Remove ESRS E1-6 block quote from Section 03 | ✅ Done | Removed the lengthy ESRS E1-6 para 24 quoted text and interoperability note. |
| 12 | Remove source lines from map pages | ✅ Done | Removed "Source: ..." metadata from sbti-map.html, esrs-map.html, and csrd-map.html. |
| 13 | Text justification across all pages | ✅ Done | `text-align: justify` applied to all `p` and `.lead` elements in all 4 HTML files. |
| 14 | Layout width fix | ✅ Done | Section max-width set to 1100px for proper table display. |
| 15 | Rename CSRD Map → Voluntary CSRD Map | ✅ Done | Nav link renamed to "Voluntary CSRD Map" in all pages. |
| 16 | Restore Section 06 Matrix | ✅ Done | Rebuilt from deployed reference to fix missing section tag. |
| 17 | Remove max-width from paragraphs | ✅ Done | Text now spans full container width alongside tables. |
| 18 | Keep disclaimers, remove sources | ✅ Done | Sources footers removed; disclaimers preserved on all pages. |

---

## 3. Content Architecture (8 Sections)

All sections are `section` elements with an `id`. The topbar nav links map directly to these IDs.

### Section 00 — Hero (`#hero`)
- **Purpose:** Landing statement + project metadata
- **Content:** Title "From ambition to action.", description of the three-framework comparison, 3 hero stats (2 Frameworks, 24 Themes, 52 Actions)
- **Visual:** Centered text, gradient background, particle overlay

### Section 01 — Architectural Overview (`#arch`)
- **Purpose:** Side-by-side comparison of the three frameworks at a structural level
- **Content:** 10-row table comparing Nature, Legal Force, Core Objective, Scope 1/2/3, Transition Plan, Carbon Credits, Target Ambition, Assurance, Boundary, Materiality
- **Styling:** Column headers use framework colors (`td-sbti`, `td-esrs`). 3-column table with border and hover states.
- **How to update:** Edit the table rows directly in the HTML. Each row is a `<tr>` with 3 `<td>` cells.

### Section 02 — Governance & Leadership (`#gov`)
- **Purpose:** Deep dive into SBTi governance criteria (C1, C2) with actual standard text + ESRS mapping
- **Layout:** Vertical card list (`.card-list`) — cards stack one below another, not in columns
- **Content:** 4 interactive detail cards:
  1. C1 — Board sign-off (C1.1, C1.2, C1.3 quoted)
  2. C2 — Transition plan (C2.1, C2.2, C2.4 quoted)
  3. R1.2 — Policy engagement consistency
  4. R2.3 — Transition plan alignment with ESRS
- **Interaction:** Click cards to toggle `open` class → reveals `.card-body` with quoted text and ESRS equivalents.
- **How to update:** Each card is a `.detail-card` div with `.card-tag`, `.card-title`, `.card-lead`, and `.card-body` containing `.criterion-id` + `.quote` blocks + `<p>` explanations.

### Section 03 — Target Setting (`#targets`)
- **Purpose:** Scope 1, 2, 3, Net-Zero targets with actual SBTi criteria text + ESRS E1-6 mapping
- **Layout:** Vertical card list (`.card-list`)
- **Content:** 6 cards:
  1. Scope 1 (C10–C11)
  2. Scope 2 (C12–C13 + C24 hourly matching)
  3. Scope 3 (C14–C16 ≥67%)
  4. Net-Zero (C17)
  5. Base Year (C4 + C8)
  6. Target Revision (C20)
- **Note:** ESRS E1-6 quoted text block removed (cleaner layout). Interoperability note preserved in cards.

### Section 04 — Implementation (`#implement`)
- **Purpose:** Implementation hierarchy, actions, carbon credits, bioenergy, electricity
- **Layout:** Vertical card list (`.card-list`)
- **Content:** 4 cards:
  1. Hierarchy (C21)
  2. Carbon Credits (C25–C28)
  3. Bioenergy (C26)
  4. Electricity (C29)

### Section 05 — Coverage Depth (`#depth`)
- **Purpose:** Prescriptiveness scores across **24 themes**, 1–5 scale, with CSRD Voluntary column
- **Content:**
  - 3 score blocks at top: SBTi avg (5.0), ESRS E1 avg (2.8), CSRD Voluntary avg (1.0)
  - 24-row table: Theme | SBTi Depth | ESRS Depth | CSRD Voluntary | Rationale
  - Expandable Criteria Map table with 4 columns: Theme | SBTi Criteria IDs | ESRS E1/E4 Ref | CSRD Voluntary Ref
- **New themes:** Deforestation-Free Supply Chains, Investment Actions/CapEx, Bioenergy/Biofuel, Product Attributes & Traceability, Claims Framework, Market-Based Instruments in Scope 3
- **How to update:** Edit the score numbers in the score-block divs. Add/remove rows in the tables.

### Section 06 — Interoperability Matrix (`#matrix`)
- **Purpose:** Direct mapping of SBTi sections to ESRS/CSRD equivalents, with coverage badges
- **Content:** 22-row table:
  - SBTi Section | SBTi Criteria IDs | ESRS E1 Ref | CSRD Voluntary Ref | Coverage | Gap/Commentary
- **Coverage badges:**
  - `badge-green` = Full ✓
  - `badge-amber` = Partial ~
  - `badge-red` = None ✗
- **How to update:** Add rows for new SBTi sections. Update ESRS/CSRD refs when delegated acts are amended.

### Section 07 — Gap-Action Checklist (`#checklist`)
- **Purpose:** Actionable checklist for SBTi-compliant companies to become ESRS/CSRD-ready
- **Content:** **52 action items**, each with: ID, Section, Action, SBTi Covers (Yes/No/Partial), Gap Detail, ESRS Ref, CSRD Ref, **Owner**, Timeline, Effort, Priority, Notes
- **New sections:** 8.x–13.x covering Deforestation, Investments, Bioenergy, Traceability, Claims, Market-Based Instruments
- **Interactivity:**
  - Search input (text filter)
  - Priority dropdown (Must-do / Should-do)
  - SBTi coverage dropdown (Yes / No / Partial)
- **Filter logic:** `filterChecklist()` in JS. Filters `data-priority` and `data-sbti` attributes + text content.

### Section 08 — Practical Implications (`#implications`)
- **Purpose:** Summary of what an SBTi-aligned company needs to do additionally for ESRS & CSRD Voluntary
- **Content:** 52 actions split into 3 categories: 18 already covered by SBTi, 16 partially covered, 18 not covered (full gap)
- **Layout:** Score grid + detailed card list with double materiality, scenario analysis, financial effects, Scope 3 relief, carbon credit disclosure, transition plan alignment, Voluntary Annex overlap, assurance gap

---

## 4. Supporting Map Files

### `sbti-map.html`
- **Purpose:** Standalone reference map of all SBTi CNZS V2.0 criteria
- **Content:** Searchable, filterable list of all SBTi criteria by chapter/section
- **Linked from main nav** as "SBTi Criteria Map"

### `esrs-map.html`
- **Purpose:** Standalone reference map of ESRS E1 Climate Change provisions
- **Content:** Searchable list of ESRS E1 disclosure requirements
- **Linked from main nav** as "ESRS E1 Map"

### `csrd-map.html`
- **Purpose:** Standalone reference map of CSRD Voluntary Annex provisions
- **Content:** Commission Delegated Regulation (EU) 2026/5011 Annex — Basic and Comprehensive Modules
- **Linked from main nav** as "Voluntary CSRD Map"

---

## 5. Design System

### 5.1 Visual Language (Dark Mode Default)

| Token | Hex | Usage |
|-------|-----|-------|
| `--bg` | `#0a0a0a` | Page background |
| `--bg-elevated` | `#111111` | Card hover, code blocks |
| `--bg-card` | `#141414` | Table/card background |
| `--border` | `#262626` | Table borders, card borders |
| `--border-subtle` | `#1c1c1c` | Section dividers |
| `--text-primary` | `#f5f5f5` | Headlines, card titles |
| `--text-secondary` | `#a3a3a3` | Body text, table content |
| `--text-muted` | `#737373` | Labels, captions |
| `--accent` | `#14b8a6` | Teal — active nav, tags, highlights |
| `--sbti` | `#3b82f6` | Blue — SBTi framework |
| `--esrs` | `#f97316` | Orange — ESRS E1 framework |
| `--csrd` | `#22c55e` | Green — CSRD Voluntary framework |

### 5.2 Typography
- **Font:** System font stack (-apple-system, Segoe UI, Roboto, Helvetica Neue)
- **Base size:** 15px
- **Headline 1:** 42px, weight 700
- **Headline 2:** 28px, weight 600
- **Section labels:** 11px, uppercase, teal, 0.15em letter-spacing
- **Monospace:** SF Mono, Monaco, Fira Code — used for criterion IDs and references
- **Text alignment:** `text-align: justify` on all paragraphs for readability

### 5.3 Layout
- **Topbar:** Fixed 60px height, blur backdrop, horizontal scrollable nav, brand left, theme toggle right
- **Main content:** Full width, max-width 1100px per section, padding 72px 48px
- **Text:** Full container width (no max-width constraint on paragraphs)
- **Responsive:** Below 900px topbar hides brand, nav shrinks, score blocks stack, tables scroll horizontally

### 5.4 Ambient Background (Particles)
CSS-only particle system using absolutely positioned `div`s with `animation: floatDrift` and `animation: orbDrift`. No JavaScript, no canvas, no external assets. Particles are teal-colored dots and radial gradients that drift upward infinitely.

### 5.5 Light Mode
Toggle via topbar theme button. Uses `data-theme="light"` on `<html>`. All colors invert via CSS custom properties.

---

## 6. JavaScript Interactivity

All JS is inline at the bottom of `index.html`.

### 6.1 Scroll Navigation (`onScroll`)
- Reads `section[id]` positions
- Highlights active topbar nav link via `active` class
- Updates progress bar width based on scroll position

### 6.2 Card Expansion (`onclick="this.classList.toggle('open')"`)
- Each `.detail-card` toggles `open` class on click
- CSS handles show/hide via `.detail-card.open .card-body { display: block }`

### 6.3 Checklist Filter (`filterChecklist()`)
- Reads 3 inputs: `#checkSearch`, `#checkFilter`, `#checkSBTI`
- Loops over `.checklist-row`, checks `dataset.priority`, `dataset.sbti`, and `innerText`
- Toggles `display: none` for non-matches

### 6.4 Criteria Map Toggle (`toggleCriteriaMap()`)
- Expands/collapses the full criteria-to-theme mapping table in Section 05
- Shows/hides 24-row table with SBTi Criteria IDs, ESRS E1/E4 Ref, and CSRD Voluntary Ref

---

## 7. Data Sources & Standard Text Provenance

All standard text is transcribed verbatim from operative provisions. Any deviation is noted inline.

| Document | Reference | Date | Used In |
|----------|-----------|------|---------|
| SBTi Corporate Net-Zero Standard V2.0 | SBTi CNZS V2.0 | June 2026 | Sections 02–04, Matrix, Checklist |
| Revised ESRS June 2026 | Commission Delegated Regulation C(2026) 5010 Annex I | June 2026 | Sections 01–07 |
| CSRD Voluntary Annex | Commission Delegated Regulation (EU) 2026/5011 | June 2026 | Sections 01, Matrix, Checklist |
| SBTi vs ESRS/CSRD Comparison v3 | Consultant document | July 2026 | Sections 05–06 (scoring), Section 10 (new themes) |
| Gap Action Checklist SBTi to ESRS v3 | Consultant Excel | July 2026 | Section 07 (52 actions with owners) |
| SBTi vs ESRS/CSRD Comparison Supplement v3 | Consultant document | July 2026 | New themes (deforestation, investments, bioenergy, traceability, claims) |

**Important:** The scoring in Section 05 is a qualitative judgment based on line-by-line operative text reading. It is directional only, not a quantitative metric. CSRD Voluntary Annex is proportionate by design; low scores reflect intent, not deficiency.

---

## 8. How to Update This Webapp

### 8.1 Add New SBTi Criteria (when V2.1 is released)
1. **Add to relevant Section:** Create a new `.detail-card` in Section 02–04. Follow pattern: `.card-tag` + `.card-title` + `.card-lead` + `.card-body` with `.criterion-id` + `.quote`.
2. **Update Matrix:** Add/edit row in Section 06. Update coverage badge.
3. **Update Checklist:** Add new action item in Section 07 if the criterion creates a new ESRS/CSRD gap.
4. **Update sbti-map.html:** Add the new criterion to the standalone reference map.

### 8.2 Update ESRS/CSRD References (when delegated acts are amended)
1. **Update Architecture table** (Section 01) if legal force, scope, or materiality rules change.
2. **Update Matrix** (Section 06) with new paragraph references. Update coverage badges.
3. **Update esrs-map.html** and **csrd-map.html** with new operative text.
4. **Update Checklist** ESRS/CSRD Ref columns where paragraph numbers have changed.

### 8.3 Add a New Theme to Depth Comparison (Section 05)
1. Add a new row to the 24-theme table with SBTi score, ESRS score, CSRD Voluntary score, and rationale.
2. Update the score block averages at the top if the new theme changes the overall average.
3. Add a corresponding card in Section 02–04 if the theme is substantial enough.
4. Add corresponding checklist items in Section 07.
5. Add the theme to the Criteria Map table in Section 05.

### 8.4 Fix Content Errors
- All text is in the single HTML file. Use find-and-replace.
- Criterion IDs are used in card tags, matrix table, and checklist. Search for the old ID to find all occurrences.
- If an ESRS/CSRD reference changes, search and update all instances.

### 8.5 Style Changes
- **Colors:** Edit `:root` CSS custom properties at top of `<style>`.
- **Fonts:** Edit `--font-sans` and `--font-mono` variables.
- **Layout:** Edit topbar height (currently 60px), section padding, or grid column counts.
- **Particles:** Adjust `.particle` and `.particle-orb` CSS animation parameters (duration, delay, size) to change the ambient effect.
- **Text alignment:** Edit `p` and `.lead` CSS rules to change text justification.

### 8.6 Add a New Section
1. Add a new `<section id="newsection">` in the main content area, before `</main>`.
2. Add a new `<a href="#newsection">` in the topbar nav.
3. The `onScroll` JS will automatically pick up the new section.

---

## 9. Deployment Checklist

- [ ] Copy `SBTI_ESRS_webapp/` contents to your GitHub repository
- [ ] Ensure `index.html` is at the root of the folder you want to serve
- [ ] Verify `sbti-map.html`, `esrs-map.html`, and `csrd-map.html` are in the same folder
- [ ] For GitHub Pages: Settings → Pages → Source: Deploy from a branch → select branch + `/ (root)`
- [ ] For Vercel: Drag and drop the folder, or connect repo via Vercel CLI
- [ ] For Netlify: Drag and drop the folder, or connect via Netlify CLI
- [ ] Verify all 8 sections are reachable via topbar nav
- [ ] Verify map pages are reachable from main nav (SBTi Map, ESRS Map, Voluntary CSRD Map)
- [ ] Test checklist filters (search + priority + SBTi coverage)
- [ ] Test card expansion on mobile (full-width touch targets)
- [ ] Test light/dark toggle
- [ ] Confirm the Disclaimer is visible on all pages
- [ ] Verify particle background renders smoothly (no JS errors)

---

## 10. Known Limitations

1. **No deep-linking to specific cards.** URL hash only navigates to sections. Cards cannot be linked directly without adding anchor IDs.
2. **No state persistence.** Filters reset on page reload. To persist, add `localStorage` to `filterChecklist()`.
3. **Single file size.** At ~96KB, the file is fast to load. If it grows beyond 200KB, consider splitting the checklist table data into a separate JSON file loaded via `fetch()`.
4. **Map files are standalone.** `sbti-map.html`, `esrs-map.html`, and `csrd-map.html` share CSS but are independent pages.
5. **Checklist table is static HTML.** The 52 rows are hardcoded. For dynamic updates, consider generating the table from a JSON data file.

---

## 11. Disclaimer (Visible on All Pages)

This is a simplified analysis and does not capture all nuances of the standards. Users must refer to the actual documents to understand the details with the right context. ESRS depth is sometimes distributed across multiple disclosure requirements (e.g., governance in ESRS 2, targets in E1-6), which may understate apparent depth if viewed only through E1. CSRD Voluntary Annex is proportionate by design; low scores reflect intent, not deficiency. Timelines and effort estimates are directional, not prescriptive. National transposition of CSRD and sector-specific guidance (e.g., banks, insurers) may add requirements not captured here.

---

## 12. Version History

| Version | Date | Changes |
|---------|------|---------|
| v1 | 2026-07-04 | Initial build: 3 frameworks, 18 themes, 28 actions, sidebar nav, Standard Text Explorer |
| v2 | 2026-07-04 | Applied feedback: horizontal topbar, 2 frameworks merged, particle background, vertical card stack, removed Explorer, added owners, expanded to 24 themes / 52 actions, added Practical Implications, created sbti-map.html and esrs-map.html |
| v3 | 2026-07-06 | Added CSRD Voluntary Annex as third column, created csrd-map.html, added CSRD Voluntary Ref to Matrix and Criteria Map, removed ESRS E1-6 block quote, removed source lines from map pages, text justification, layout width fix, restored Section 06 Matrix, renamed nav to "Voluntary CSRD Map", full content rebuild from deployed reference |
