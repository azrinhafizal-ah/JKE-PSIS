# My Assignment Tracker — Plan

## Top-Level Overview

Create a new file `assignment-tracker.html` in the playground.
The page is a standalone dashboard titled **"My Assignment Tracker"** that allows a teacher/facilitator to track which students have submitted their assignments.

It must satisfy three rules from the requirement image:
1. **Three summary cards** — Total Students, Submitted, Not Submitted
2. **A checklist of five students** using sample names
3. **A checkbox** per student to mark their submission status

The page must reuse the existing visual style from `dashboard.html` (same header, card gradients, checklist row styles, and JS update pattern).

---

## Sub-Tasks

---

### Sub-Task 1 — Create the page shell

**Intent**
Scaffold `assignment-tracker.html` with the full base structure: DOCTYPE, `<head>` with shared CSS (reset, body, header, card, checklist styles copied from `dashboard.html`), and an empty `<body>` with the header block.

**Expected Outcomes**
- File `assignment-tracker.html` exists and opens in a browser showing only the dark header with the "My Assignment Tracker" title and tagline "Assignment Tracking".
- All shared CSS classes are present and ready to be used.

**Todo List**
- [ ] Create `assignment-tracker.html`
- [ ] Copy and adapt CSS from `dashboard.html` (reset, body, header, card, checklist styles)
- [ ] Render header with brand logo `AT`, title `My Assignment Tracker`, tagline `Assignment Tracking`

**Relevant Context**
- Source: `dashboard.html` lines 1–279 (full CSS block)
- Header markup: `dashboard.html` lines 283–292
- Reuse `.card`, `.checklist-section`, `.checklist-list`, `.done` styles exactly

**Status:** `[ ] pending`

---

### Sub-Task 2 — Build the three summary cards

**Intent**
Add a `<section class="cards">` with three cards that display:
- **Total Students** (blue) — static value of `5`
- **Submitted** (green) — starts at `0`, updates live
- **Not Submitted** (orange) — starts at `5`, updates live

**Expected Outcomes**
- Three gradient cards visible below the header.
- Submitted and Not Submitted cards show `id` attributes so JavaScript can update their values.
- Cards match the existing blue/green/orange gradient styles.

**Todo List**
- [ ] Add section label "Summary" above cards
- [ ] Card 1 (blue): icon 👥, label "Total Students", value `5`
- [ ] Card 2 (green): icon ✅, label "Submitted", value element `id="submitted-count"`
- [ ] Card 3 (orange): icon ⏳, label "Not Submitted", value element `id="not-submitted-count"`

**Relevant Context**
- Reuse `.card.blue`, `.card.green`, `.card.orange` from `dashboard.html` lines 116–118
- Card inner markup pattern: `dashboard.html` lines 301–321

**Status:** `[ ] pending`

---

### Sub-Task 3 — Build the student checklist

**Intent**
Add a `<section class="checklist-section">` containing a list of five students. Each row has a checkbox. Checking the box marks the student as submitted (green row, strikethrough name). Unchecking reverts.

**Sample student names:**
1. Ahmad Syafiq
2. Nurul Aisyah
3. Haziq Danial
4. Siti Nurfazira
5. Muhammad Irfan

**Expected Outcomes**
- Five student rows rendered inside a `<ul class="checklist-list">`.
- Clicking a checkbox toggles `.done` on the `<li>`, applying green background and strikethrough.
- A progress bar updates to show how many have submitted.

**Todo List**
- [ ] Add section label "Student Submissions" above the checklist section
- [ ] Render checklist header with title "Assignment Submission Checklist" and a live `<div id="progress-pill">` showing "X of 5 submitted"
- [ ] Add progress bar `<div id="progress-bar">` below header
- [ ] Render `<ul id="checklist">` — populated by JavaScript

**Relevant Context**
- Reuse `.checklist-section`, `.checklist-header`, `.checklist-list`, `.done` from `dashboard.html` lines 164–271
- Progress pill and bar: `dashboard.html` lines 187–214

**Status:** `[ ] pending`

---

### Sub-Task 4 — Wire up live counters with JavaScript

**Intent**
Add a `<script>` block that:
1. Defines the array of 5 student names
2. Dynamically renders each student as a `<li>` with a checkbox, index number, and name
3. On every checkbox change, recalculates Submitted / Not Submitted counts and updates the card values and progress bar

**Expected Outcomes**
- Checking a student checkbox immediately increments Submitted card and decrements Not Submitted card.
- Progress bar fill width reflects the percentage of submitted students.
- All DOM updates are driven by one `updateCounts()` function called on every `change` event.

**Todo List**
- [ ] Define `students` array with 5 names
- [ ] Loop over array to create `<li>` elements with checkbox, number span, name span
- [ ] Attach `change` listener on each checkbox calling `updateCounts()`
- [ ] Implement `updateCounts()` — reads checked count, updates `#submitted-count`, `#not-submitted-count`, `#done-count`, `#progress-bar`

**Relevant Context**
- JavaScript pattern: `dashboard.html` lines 341–392 (`items` array, `forEach`, `updateProgress()`)

**Status:** `[ ] pending`

---

## File Output

| File | Action |
|---|---|
| `assignment-tracker.html` | Create new |
| `assignment-tracker-plan.md` | This plan file |

## Non-Goals
- No server-side logic or data persistence
- No navigation link from `dashboard.html` to this page (unless requested)
- No more than 5 students (per requirement)
