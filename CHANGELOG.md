# Changelog

Log of changes made to the site, what was changed, and how.

---

## 2026-02-26 — AI Transparency made collapsible and right-aligned

**What changed:**
The AI Transparency section on the Housing Affordability project page was converted from
a full visible section panel to a collapsible element. It now appears as a small
"AI Transparency +" label at the bottom-right of the page. Clicking it expands a card
with the full AI disclosure text. Clicking again collapses it.

**Files modified:**
- `projects/housing-affordability.html` — replaced `<section class="proj-section proj-section--ai">`
  with a `<details class="ai-transparency">` / `<summary>` element. Content unchanged.
- `assets/css/style.css` — removed `.proj-section--ai` and `.proj-section-title--ai` styles.
  Added `.ai-transparency`, `.ai-transparency-toggle`, and `.ai-transparency-body` styles
  with right-alignment (`margin-left: auto`), custom toggle indicators (+ / −), and a
  card-style expanded body.

**How it was done:**
Used the native HTML `<details>` + `<summary>` elements for expand/collapse behavior
(no JavaScript). The default browser disclosure triangle is hidden via
`::-webkit-details-marker` and `list-style: none`, replaced with a `+` / `−`
character via CSS `::after`. The entire element is pushed right with `margin-left: auto`
and `max-width: fit-content`.

---

## 2026-02-25 — AI Transparency section upgrade

**What changed:**
The AI Transparency note at the bottom of the Housing Affordability project was changed
from a small italicized paragraph to a full styled section panel (matching the other
project sections but with a grey accent border instead of blue).

**Files modified:**
- `projects/housing-affordability.html` — replaced `<p class="proj-ai-note">` with
  `<section class="proj-section proj-section--ai">` containing the updated text,
  bold emphasis on key words, and a clickable link to the original analysis document.
- `assets/css/style.css` — added `.proj-section--ai` and `.proj-section-title--ai`
  styles (grey left border, muted title color). Added `.proj-section-body a` link
  styling (blue underline, hover to white).

**How it was done:**
The old `<p>` tag with class `proj-ai-note` was deleted and replaced with a `<section>`
using the same panel classes as other project sections (`proj-section`) plus an `--ai`
modifier class. CSS for the old `.proj-ai-note` class was replaced with the new
modifier styles. Links inside section bodies are now styled site-wide.

---

## 2026-02-25 — Visual placeholders replaced with live img tags

**What changed:**
The 4 dashed-border CSS placeholder boxes in the Housing Affordability project page
were replaced with actual `<img>` tags pointing to expected filenames.

**Files modified:**
- `projects/housing-affordability.html` — replaced all `<div class="visual-placeholder">`
  blocks with `<img class="proj-visual">` tags. The two-column group now uses
  `<div class="proj-visual-row-2">` instead of `<div class="visual-row-2">`.

**How it was done:**
Each placeholder `<div>` (which contained an HTML comment showing the replacement `<img>`)
was deleted and replaced with the `<img>` tag from the comment. No CSS changes needed —
the `.proj-visual` and `.proj-visual-row-2` styles already existed.

**What you still need to do:**
Export your chart images as `ha-visual-1.png` through `ha-visual-4.png` and drop them
into `assets/images/projects/`. See SITE_GUIDE.md for the filename table.

---

## 2026-02-25 — Project card image fix (background-image approach)

**What changed:**
The project card on the Projects listing page was using an `<img>` tag with a JavaScript
`onerror` fallback that was nearly invisible on the dark theme. Replaced with a CSS
`background-image` approach that gracefully shows a dark background when no image exists.

**Files modified:**
- `projects.md` — replaced `<img>` + `<span>` fallback inside `.project-card-thumb`
  with an inline `style="background-image: url(...)"` on the thumb div itself.

**How it was done:**
The `<img>` element and `onerror` handler were removed. The `.project-card-thumb` div
now uses an inline `background-image` CSS property. The existing CSS (`background-size: cover`,
`background-position: center`, `background-color: var(--bg-hover)`) handles display and
fallback automatically.

---

## 2026-02-25 — Projects section added to site

**What changed:**
Full projects section added: listing page with square clickable cards, individual project
page layout, and the Housing Affordability project.

**Files created:**
- `_layouts/project.html` — layout template for project pages
- `projects/housing-affordability.html` — Housing Affordability project content
- `assets/images/projects/` — directory for project images

**Files modified:**
- `projects.md` — rewritten from empty data-driven template to square card grid
- `assets/css/style.css` — added ~280 lines of CSS for project grid, project cards,
  project page sections, visual placeholders/images, resource links, and responsive rules
- `SITE_GUIDE.md` — fully rewritten with project instructions, image guides, and file map

**How it was done:**
Created a `project.html` layout extending `default.html`. The listing page (`projects.md`)
uses a CSS grid of cards with `background-image` thumbnails. The project page uses styled
section panels (`proj-section`) with blue left-accent borders, a tag bar, resource link
cards, and an AI transparency note. All CSS uses existing site variables for consistency.

---

## 2026-02-25 — SITE_GUIDE.md audit and update

**What changed:**
Site guide was audited for completeness and accuracy. Several sections were outdated
or missing after the project card and visual changes.

**Fixes applied:**
- Updated "Add a project card" template from `<img>` with `onerror` to `background-image` approach
- Updated "Add a Visual" section to reflect that placeholders are already replaced with `<img>` tags
- Added table of current Housing Affordability visual filenames
- Added "Edit the AI Transparency Note" section
- Added "Edit Navigation Links" section
- Added "Edit Footer (Social Links)" section
- Added "Previewing Changes Locally" section
- Updated File Map to include `CHANGELOG.md`
