# SBTi CNZS V2.0 vs ESRS E1 & CSRD Voluntary — Comparative Analysis Webapp

**Purpose:** Single-file digital webpage hosting a structured interoperability and gap analysis between the SBTi Corporate Net-Zero Standard V2.0 and the merged ESRS E1 Climate Change & CSRD Voluntary Annex framework.

**Built:** 2026-07-04  
**File:** `index.html` (single file, zero dependencies, no build step)  
**Folder:** `/Users/abhilash/Desktop/SBTI_ESRS_webapp/`  
**Design inspiration:** `https://sbti-v2.vercel.app` — dark, minimal, clean aesthetic with ambient particle background

---

## 1. What's in the Folder

```
SBTI_ESRS_webapp/
├── index.html              # Main comparative analysis webapp (94KB, ~867 lines)
├── esrs-map.html           # ESRS E1 & CSRD Voluntary Annex unified reference map
├── sbti-map.html           # SBTi CNZS V2.0 criteria reference map
└── README.md               # This document
```

**Deployment:** Any static hosting (GitHub Pages, Vercel, Netlify, Cloudflare Pages). No build step, no npm, no external CDN calls. Copy the folder contents and push.

---

## 2. Feedback Fixes Applied (v3 Iteration)

The following fixes from `sbti.esrs webpp feedback.docx` have been applied to the current `index.html`:

| Fix # | Request | Status | Implementation |
|-------|---------|--------|----------------|
| 1 | Horizontal topbar, remove sidebar | ✅ Done | Fixed topbar with horizontal nav, brand, theme toggle, progress bar. Content expanded to full width. |
| 2 | Add owner for each checklist action | ✅ Done | Gap-Action Checklist (Section 07) now includes Owner column per row. |
| 3 | Overhaul UI — add SBTi Criteria Map + Combined ESRS E1 & CSRD Climate Map | ✅ Done | Standalone `esrs-map.html` and `sbti-map.html` files created. Links can be added to the main nav. |
| 4 | Ambient background with particles | ✅ Done | CSS-only particle system with floating dots and orb gradients, no JavaScript, no external assets. |
| 5 | Merge 3 frameworks into 2 | ✅ Done | All tables now show **SBTi CNZS V2.0** vs **ESRS E1 Climate Change & CSRD Voluntary Annex** (merged column). |
| 6 | Stack cards vertically instead of 2×3 grid | ✅ Done | Governance and Target cards use `.card-list` (vertical stack) to prevent accidental cross-row expansion. |
| 7 | Remove Standard Text Explorer | ✅ Done | Section 08 removed entirely. |

---

## 3. Content Architecture (7 Sections)

All sections are `section` elements with an `id`. The topbar nav links map directly to these IDs.

### Section 00 — Hero (`#hero`)
- **Purpose:** Landing statement + project metadata
- **Content:** Title "From ambition to action.", description of the two-framework comparison, 3 hero stats (2 Frameworks, 24 Themes, 52 Actions)
- **Visual:** Centered text, gradient background, particle overlay

### Section 01 — Architectural Overview (`#arch`)
- **Purpose:** Side-by-side comparison of the two frameworks at a structural level
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
- **Additional:** ESRS E1-6 para 24 block quote + interoperability note below cards

### Section 04 — Implementation (`#implement`)
- **Purpose:** Implementation hierarchy, actions, carbon credits, bioenergy, electricity
- **Layout:** Vertical card list (`.card-list`)
- **Content:** 4 cards:
  1. Hierarchy (C21)
  2. Carbon Credits (C25–C28)
  3. Bioenergy (C26)
  4. Electricity (C29)

### Section 05 — Coverage Depth (`#depth`)
- **Purpose:** Prescriptiveness scores across **24 themes** (expanded from v2's 18 themes), 1–5 scale
- **Content:**
  - 2 score blocks at top: SBTi avg (5.0), ESRS E1 & CSRD avg (2.8)
  - 24-row table: Theme | SBTi | ESRS E1 & CSRD | Rationale
- **New themes added in v3:**
  - Deforestation-Free Supply Chains (C35)
  - Investment Actions / CapEx (E1-1 para 12(b))
  - Bioenergy / Biofuel Sourcing
  - Product Attributes & Traceability
  - Claims Framework
  - Market-Based Instruments in Scope 3
- **How to update:** Edit the score numbers in the score-block divs. Add/remove rows in the table. The table is designed for horizontal scrolling on mobile.

### Section 06 — Interoperability Matrix (`#matrix`)
- **Purpose:** Direct mapping of SBTi sections to ESRS/CSRD equivalents, with coverage badges
- **Content:** 20-row table:
  - SBTi Section | Criteria IDs | ESRS/CSRD Ref | Coverage | Gap/Commentary
- **Coverage badges:**
  - `badge-green` = Full ✓
  - `badge-amber` = Partial ~
  - `badge-red` = None ✗
- **How to update:** Add rows for new SBTi sections. Update ESRS refs when delegated acts are amended.

### Section 07 — Gap-Action Checklist (`#checklist`)
- **Purpose:** Actionable checklist for SBTi-compliant companies to become ESRS-ready
- **Content:** **52 action items** (expanded from v2's 28), each with: ID, Section, Action, SBTi Covers (Yes/No/Partial), Gap Detail, ESRS Ref, CSRD Ref, **Owner**, Timeline, Effort, Priority, Notes
- **New sections added in v3:**
  - 8.x Deforestation-Free Supply Chains (3 actions)
  - 9.x Investment Actions / CapEx (4 actions)
  - 10.x Bioenergy & Biofuel Sourcing (3 actions)
  - 11.x Product Attributes & Traceability (2 actions)
  - 12.x Claims Framework (2 actions)
  - 13.x Market-Based Instruments in Scope 3 (2 actions)
- **Interactivity:**
  - Search input (text filter)
  - Priority dropdown (Must-do / Should-do)
  - SBTi coverage dropdown (Yes / No / Partial)
- **Filter logic:** `filterChecklist()` in JS. Filters `data-priority` and `data-sbti` attributes + text content.
- **How to update:** Add rows to the table. Each row needs: `class="checklist-row"`, `data-priority="Must-do"`, `data-sbti="Yes"`. Badges use `.badge-green`, `.badge-amber`, `.badge-red`.

### Section 08 — Practical Implications (`#practical`)
- **Purpose:** Summary of what an SBTi-aligned company needs to do additionally for ESRS
- **Content:** 8 bullet points covering double materiality, scenario analysis, financial effects, Scope 3 relief, carbon credit disclosure, transition plan alignment, Voluntary Annex overlap, assurance gap
- **This section was renamed from "Practical Implications" in the v3 document.**

---

## 4. Supporting Map Files

### `sbti-map.html`
- **Purpose:** Standalone reference map of all SBTi CNZS V2.0 criteria
- **Content:** Searchable, filterable list of all SBTi criteria by chapter/section
- **Can be linked from the main nav** by adding a new topbar nav link.

### `esrs-map.html`
- **Purpose:** Standalone unified reference map of ESRS E1 Climate Change + CSRD Voluntary Annex provisions
- **Content:** Combined, searchable list of ESRS E1 disclosure requirements and CSRD Voluntary Annex provisions, organized by topic
- **Can be linked from the main nav** by adding a new topbar nav link.

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
| `--esrs` | `#f97316` | Orange — merged ESRS/CSRD framework |

### 5.2 Typography
- **Font:** System font stack (-apple-system, Segoe UI, Roboto, Helvetica Neue)
- **Base size:** 15px
- **Headline 1:** 42px, weight 700
- **Headline 2:** 28px, weight 600
- **Section labels:** 11px, uppercase, teal, 0.15em letter-spacing
- **Monospace:** SF Mono, Monaco, Fira Code — used for criterion IDs and references

### 5.3 Layout
- **Topbar:** Fixed 60px height, blur backdrop, horizontal scrollable nav, brand left, theme toggle right
- **Main content:** Full width, max-width 1100px per section, padding 72px 48px
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

---

## 7. Data Sources & Standard Text Provenance

All standard text is transcribed verbatim from operative provisions. Any deviation is noted inline.

| Document | Reference | Date | Used In |
|----------|-----------|------|---------|
| SBTi Corporate Net-Zero Standard V2.0 | SBTi CNZS V2.0 | June 2026 | Sections 02–04, Matrix, Checklist |
| Revised ESRS June 2026 | Commission Delegated Regulation C(2026) 5010 Annex I | June 2026 | Sections 01–07 |
| CSRD Voluntary Annex | Commission Delegated Regulation (EU) 2026/5011 | June 2026 | Sections 01, Matrix |
| SBTi vs ESRS/CSRD Comparison v3 | Consultant document | July 2026 | Sections 05–06 (scoring), Section 10 (new themes) |
| Gap Action Checklist SBTi to ESRS v3 | Consultant Excel | July 2026 | Section 07 (52 actions with owners) |
| SBTi vs ESRS/CSRD Comparison Supplement v3 | Consultant document | July 2026 | New themes (deforestation, investments, bioenergy, traceability, claims) |

**Important:** The scoring in Section 05 is a qualitative judgment based on line-by-line operative text reading. It is directional only, not a quantitative metric.

---

## 8. How to Update This Webapp

### 8.1 Add New SBTi Criteria (when V2.1 is released)
1. **Add to relevant Section:** Create a new `.detail-card` in Section 02–04. Follow pattern: `.card-tag` + `.card-title` + `.card-lead` + `.card-body` with `.criterion-id` + `.quote`.
2. **Update Matrix:** Add/edit row in Section 06. Update coverage badge.
3. **Update Checklist:** Add new action item in Section 07 if the criterion creates a new ESRS gap.
4. **Update sbti-map.html:** Add the new criterion to the standalone reference map.

### 8.2 Update ESRS References (when delegated acts are amended)
1. **Update Architecture table** (Section 01) if legal force, scope, or materiality rules change.
2. **Update Matrix** (Section 06) with new paragraph references. Update coverage badges.
3. **Update esrs-map.html** with new ESRS operative text.
4. **Update Checklist** ESRS Ref columns where paragraph numbers have changed.

### 8.3 Add a New Theme to Depth Comparison (Section 05)
1. Add a new row to the 24-theme table with SBTi score, ESRS score, and rationale.
2. Update the score block averages at the top if the new theme changes the overall average.
3. Add a corresponding card in Section 02–04 if the theme is substantial enough.
4. Add corresponding checklist items in Section 07.

### 8.4 Fix Content Errors
- All text is in the single HTML file. Use find-and-replace.
- Criterion IDs are used in card tags, matrix table, and checklist. Search for the old ID to find all occurrences.
- If an ESRS reference changes (e.g., E1-6 para 24 → E1-6 para 25), search and update all instances.

### 8.5 Style Changes
- **Colors:** Edit `:root` CSS custom properties at top of `<style>`.
- **Fonts:** Edit `--font-sans` and `--font-mono` variables.
- **Layout:** Edit topbar height (currently 60px), section padding, or grid column counts.
- **Particles:** Adjust `.particle` and `.particle-orb` CSS animation parameters (duration, delay, size) to change the ambient effect.

### 8.6 Add a New Section
1. Add a new `<section id="newsection">` in the main content area, before `</main>`.
2. Add a new `<a href="#newsection">` in the topbar nav.
3. The `onScroll` JS will automatically pick up the new section.

---

## 9. Deployment Checklist

- [ ] Copy `SBTI_ESRS_webapp/` contents to your GitHub repository
- [ ] Ensure `index.html` is at the root of the folder you want to serve
- [ ] Optional: link `sbti-map.html` and `esrs-map.html` from the topbar nav by editing `index.html`
- [ ] For GitHub Pages: Settings → Pages → Source: Deploy from a branch → select branch + `/ (root)`
- [ ] For Vercel: Drag and drop the folder, or connect repo via Vercel CLI
- [ ] For Netlify: Drag and drop the folder, or connect via Netlify CLI
- [ ] Verify all 7 sections are reachable via topbar nav
- [ ] Test checklist filters (search + priority + SBTi coverage)
- [ ] Test card expansion on mobile (full-width touch targets)
- [ ] Test light/dark toggle
- [ ] Confirm the Disclaimer in the footer is visible and readable
- [ ] Verify particle background renders smoothly (no JS errors)

---

## 10. Known Limitations

1. **No deep-linking to specific cards.** URL hash only navigates to sections. Cards cannot be linked directly without adding anchor IDs.
2. **No state persistence.** Filters reset on page reload. To persist, add `localStorage` to `filterChecklist()`.
3. **Single file size.** At ~94KB, the file is fast to load. If it grows beyond 200KB, consider splitting the checklist table data into a separate JSON file loaded via `fetch()`.
4. **Map files are standalone.** `sbti-map.html` and `esrs-map.html` are not linked from the main nav by default. Add nav links in the topbar to integrate them.
5. **Checklist table is static HTML.** The 52 rows are hardcoded. For dynamic updates, consider generating the table from a JSON data file.

---

## 11. Disclaimer (Also Visible in Footer)

This is a simplified analysis and does not capture all nuances of the standards. Users must refer to the actual documents to understand the details with the right context. This tool is designed for directional guidance only and is not a substitute for professional legal or compliance advice.

---

## 12. Version History

| Version | Date | Changes |
|---------|------|---------|
| v1 | 2026-07-04 | Initial build: 3 frameworks, 18 themes, 28 actions, sidebar nav, Standard Text Explorer |
| v2 | 2026-07-04 | Applied feedback fixes: horizontal topbar, 2 frameworks merged, particle background, vertical card stack, removed Explorer, added owners, expanded to 24 themes / 52 actions, added Practical Implications section, created sbti-map.html and esrs-map.html |
