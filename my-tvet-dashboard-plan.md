# MY TVET Dashboard — Plan

## Overview

Build a single-file `dashboard.html` page titled **MY TVET Dashboard**.
The page uses plain HTML, CSS, and JavaScript — no frameworks, no build tools.
It runs directly in any browser by opening the file.

The page contains:
- A dark header bar with the title
- Three summary cards (Students Registered, Tasks Remaining, Workshop Status)
- A preparation checklist with interactive checkboxes
- All data is hardcoded sample data — no backend required

Visual style: bold and colorful with vibrant accent colors per card, dark header.

---

## Sub-Tasks

---

### Sub-Task 1 — Page Shell and Header

**Intent**
Establish the HTML skeleton and the dark top header bar that frames the whole dashboard.

**Expected Outcomes**
- A valid HTML5 file exists at `dashboard.html`
- The page renders a full-width dark header bar
- The header displays the title "MY TVET Dashboard"
- A main content area below the header is ready to receive cards and checklist

**Todo List**
- [ ] Create `dashboard.html` with standard HTML5 boilerplate
- [ ] Add a `<header>` element styled with a dark background and white title text
- [ ] Add a `<main>` content wrapper below the header
- [ ] Add base CSS reset and body font

**Relevant Context**
- No existing files — this is a greenfield single file
- All CSS lives inside a `<style>` block in `<head>`
- All JS lives inside a `<script>` block before `</body>`

**Status:** [x] done

---

### Sub-Task 2 — Summary Cards Section

**Intent**
Render three side-by-side summary cards, each with a distinct vibrant accent color, a label, and a prominent metric value drawn from sample data.

**Cards:**
| Card | Accent Color | Sample Data |
|---|---|---|
| Students Registered | Blue | 48 students |
| Tasks Remaining | Orange | 7 tasks left |
| Workshop Status | Green | "In Progress" |

**Expected Outcomes**
- Three cards are displayed in a responsive row
- Each card has its own background accent color
- Each card shows an icon or emoji, a label, and a bold numeric or text value
- Cards stack vertically on narrow screens

**Todo List**
- [ ] Add a cards container `<section>` with CSS flexbox layout
- [ ] Create a card component structure: wrapper div, icon, label, value
- [ ] Apply a unique accent color class to each card
- [ ] Populate each card with hardcoded sample values
- [ ] Add hover effect for visual polish

**Relevant Context**
- Cards sit inside `<main>` from Sub-Task 1
- Use CSS custom properties (variables) for the accent colors to keep the palette consistent

**Status:** [x] done

---

### Sub-Task 3 — Preparation Checklist

**Intent**
Render an interactive preparation checklist below the summary cards. Items are hardcoded sample data. Clicking a checkbox marks the item as done (strikethrough + muted color) and updates a live "X of Y completed" counter.

**Sample Checklist Items**
1. Confirm student registrations
2. Prepare workshop materials
3. Set up workstations and tools
4. Brief facilitators on schedule
5. Test projector and audio equipment
6. Print attendance sheets
7. Prepare evaluation forms

**Expected Outcomes**
- A checklist section is visible below the cards
- Each item has a checkbox, label text, and responds to click
- Checked items appear struck through and visually muted
- A progress counter updates in real time (e.g. "3 of 7 completed")
- The section has a clear heading "Preparation Checklist"

**Todo List**
- [ ] Add a `<section>` for the checklist below the cards section
- [ ] Render each checklist item as a `<label>` wrapping a `<input type="checkbox">` and text
- [ ] Add a progress counter `<div>` above the list
- [ ] Write a JS function that recounts checked boxes and updates the counter on every change event
- [ ] Style checked items with strikethrough and reduced opacity

**Relevant Context**
- All checklist data is a JS array of strings defined in the `<script>` block
- The list is rendered by JS into an `<ul>` in the checklist section

**Status:** [x] done

---

## Final File Layout

```
dashboard.html
  <head>
    <style> ... all CSS ... </style>
  </head>
  <body>
    <header>  ← Sub-Task 1
    <main>
      <section class="cards">   ← Sub-Task 2
      <section class="checklist">  ← Sub-Task 3
    </main>
    <script> ... all JS ... </script>
  </body>
```
