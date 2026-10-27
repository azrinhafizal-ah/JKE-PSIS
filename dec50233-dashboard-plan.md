# DEC50233 Student Dashboard — Plan

## Overview

Rebuild `dashboard.html` into a fully-featured, **modern-looking** student portal for **DEC50233** (JKE, Politeknik Sultan Idris Shah).
All UI text must be in **English**. The single-page dashboard uses tab-based navigation to organise 4 modules:
Assignments, Practical Work, Technical Skills, and Tests.
No external libraries or frameworks — pure HTML, CSS, and vanilla JavaScript only.

---

## Design System

### Colour Palette
| Role | Value |
|---|---|
| Page background | Deep gradient `#0f172a` → `#1e3a5f` (dark navy-to-blue) |
| Header | `#0a0f1e` semi-transparent with blur |
| Card background | Glassmorphism: `rgba(255,255,255,0.07)` + `backdrop-filter: blur(16px)` |
| Card border | `rgba(255,255,255,0.12)` |
| Assignments accent | `#3b82f6` (blue) |
| Practical Work accent | `#f97316` (orange) |
| Technical Skills accent | `#14b8a6` (teal) |
| Tests accent | `#ef4444` (red) |
| Text primary | `#f1f5f9` (near white) |
| Text secondary | `#94a3b8` (slate grey) |

### Visual Components
- **Cards:** Glassmorphism style — frosted glass effect, coloured top-border glow, icon with coloured glow ring
- **Progress bars:** Animated gradient fill (`from accent colour → lighter shade`), height 8px, rounded
- **Tabs:** Pill-style buttons; active tab has solid accent background + box-shadow glow
- **Badges:** Fully rounded pill badges with colour-coded backgrounds and matching text
- **Tables:** Dark-tinted rows (`rgba(255,255,255,0.04)`), striped alternate rows, hover highlight with accent colour left-border
- **Icons:** Large emoji (32–40px) inside a circular glow ring using the module's accent colour
- **Transitions:** All hover states use `transition: all 0.2s ease`
- **Shadows:** Cards use `box-shadow: 0 8px 32px rgba(0,0,0,0.4)`

---

## Sub-Task 1 — Header & Student Identity Bar

**Intent:** Replace the generic "MY TVET Dashboard" header with institution-specific branding and a student info row.

**Expected Outcomes:**
- Header shows: logo badge + "DEC50233" title + "JKE, Politeknik Sultan Idris Shah" subtitle
- Below the header: a student info bar showing Name and Matric Number (editable input fields with placeholder values)
- Colour scheme remains dark navy (`#12192b`)

**Todo List:**
- [ ] Update `<header>` HTML — logo text, h1 title, subtitle
- [ ] Add a `.student-bar` row beneath the header with Name + Matric No input fields
- [ ] Style the student bar (light background, compact padding)

**Relevant Context:** `dashboard.html` lines 284–292 (current header block)

**Status:** [ ] pending

---

## Sub-Task 2 — 4 Summary Cards

**Intent:** Replace the 3 existing generic cards with 4 colour-coded cards that summarise each module at a glance.

**Expected Outcomes:**
- 4 cards in a responsive row: Assignments (blue), Practical Work (orange), Technical Skills (teal), Tests (red)
- Each card shows an icon, label, a key metric value, and a short sub-label
- Cards update dynamically from JavaScript data arrays (same pattern as existing cards)

**Todo List:**
- [ ] Update `.cards` HTML to 4 card divs with correct class names
- [ ] Add a `.red` card colour variant to CSS
- [ ] Add a `.teal` card colour variant to CSS
- [ ] Wire card values to computed counts from each module's data array

**Relevant Context:** `dashboard.html` lines 299–322 (current cards section), CSS lines 116–118

**Status:** [ ] pending

---

## Sub-Task 3 — Tab Navigation System

**Intent:** Add a tab bar that switches between the 4 module panels without a page reload.

**Expected Outcomes:**
- A tab bar with 4 buttons: Assignments, Practical Work, Technical Skills, Tests
- Clicking a tab shows its panel and hides the others
- Active tab is visually highlighted
- Default active tab is Assignments

**Todo List:**
- [ ] Add `.tab-nav` HTML with 4 `<button>` elements
- [ ] Add 4 `.tab-panel` `<section>` divs (one per module)
- [ ] Style `.tab-nav` and `.tab-btn.active` in CSS
- [ ] Write `switchTab(tabId)` JavaScript function that toggles visibility and active state

**Relevant Context:** `dashboard.html` lines 324–392 (current checklist section to be replaced)

**Status:** [ ] pending

---

## Sub-Task 4 — Assignments Tab (Interactive)

**Intent:** Give students a checklist of assignments they can tick off as submitted, with deadline and status visibility.

**Expected Outcomes:**
- List of 5 assignments (A1–A5) with title, deadline date, and status badge
- Each item has a checkbox; ticking it toggles status to "Submitted" and applies strikethrough style
- Progress pill and progress bar update live as checkboxes are ticked
- Unticked items show "Not Submitted" badge (orange); ticked items show "Submitted" badge (green)

**Todo List:**
- [ ] Define assignments data array in JS: `{ id, title, deadline, marks }`
- [ ] Render checklist items dynamically from the array (reuse existing render pattern)
- [ ] Add deadline badge next to each item
- [ ] Add status badge that changes on checkbox toggle
- [ ] Wire progress pill and progress bar to checked count

**Relevant Context:** Existing checklist render logic at `dashboard.html` lines 341–391 — reuse and extend this pattern

**Status:** [ ] pending

---

## Sub-Task 5 — Practical Work Tab (Read-Only)

**Intent:** Show a read-only log table of practical sessions with attendance and report submission status.

**Expected Outcomes:**
- Table with columns: No, Session Title, Date, Venue, Attendance, Report
- 8 pre-filled rows (P1–P8) with sample data
- Attendance cell shows colour-coded badge: "Present" (green), "Absent" (red), "Replacement" (orange)
- Report cell shows "Submitted" or "Pending" badge

**Todo List:**
- [ ] Define practicals data array in JS: `{ id, title, date, venue, attendance, report }`
- [ ] Render `<table>` from the array inside the Practical Work tab panel
- [ ] Style `.badge-present`, `.badge-absent`, `.badge-replacement`, `.badge-submitted`, `.badge-pending` CSS classes
- [ ] Add table responsive wrapper for small screens

**Relevant Context:** New section — no existing HTML to reuse; follow the card/checklist styling conventions

**Status:** [ ] pending

---

## Sub-Task 6 — Technical Skills Tab (Interactive)

**Intent:** Let students track their competency against a set of NOSS/SKM-aligned technical skill elements.

**Expected Outcomes:**
- Checklist of 10 technical skill elements (based on DEC50233 course outcomes)
- Each item has a checkbox; ticking marks it "Competent"
- Items show current status badge: "Not Yet" (grey), "Competent" (green)
- Overall progress bar shows % of skills marked competent

**Todo List:**
- [ ] Define skills data array in JS: `{ id, unit, element }`
- [ ] Render checklist items dynamically from the array
- [ ] Status badge updates on checkbox toggle: "Not Yet" → "Competent"
- [ ] Wire overall progress bar to checked count
- [ ] Group items by unit/competency area with a section sub-heading

**Relevant Context:** Reuse the interactive checklist pattern from Sub-Task 4

**Status:** [ ] pending

---

## Sub-Task 7 — Tests Tab (Read-Only)

**Intent:** Display a schedule of tests with marks obtained and pass/fail status.

**Expected Outcomes:**
- Table with columns: No, Test Name, Date, Topics, Marks, Full Marks, Result
- 4 pre-filled rows (Test 1 – Test 4) with sample data
- Result cell shows "Pass" (green badge) or "Fail" (red badge) based on marks threshold (>= 50%)
- Summary row at the bottom: Total Marks, Overall %

**Todo List:**
- [ ] Define tests data array in JS: `{ id, name, date, topics, marks, fullMarks }`
- [ ] Render `<table>` from the array inside the Tests tab panel
- [ ] Compute pass/fail per row: pass if marks/fullMarks >= 0.5
- [ ] Add summary row computing total and overall percentage
- [ ] Style consistent with the Practical Work table

**Relevant Context:** Reuse table styles from Sub-Task 5

**Status:** [ ] pending

---

## Non-Goals

- No backend or server — all data is static sample data in JavaScript arrays
- No file upload functionality
- No login / authentication
- No external CSS frameworks or JS libraries

---

## File Affected

- `dashboard.html` — full rebuild in place
