# Site Guide

Quick reference for adding content to this site. No HTML knowledge needed for most of these.

---

## Add a Blog Post

1. Create a new file in `_posts/` following this exact naming format:

   ```
   _posts/YYYY-MM-DD-your-post-title.md
   ```

   Example: `_posts/2025-03-10-my-new-post.md`

2. Start the file with this front matter (copy-paste this block):

   ```
   ---
   layout: post
   title: "Your Post Title Here"
   date: 2025-03-10
   excerpt: "One sentence that summarizes the post. Shows up in previews."
   ---
   ```

3. Write your content below the `---` using normal Markdown.

4. Commit and push. The post appears automatically on the Blog page and in the home page preview (shows 3 most recent).

**Markdown basics:**
- `## Heading` for a section heading
- `**bold**` for bold
- `- item` for a bullet list
- `1. item` for a numbered list
- `[link text](https://url.com)` for a hyperlink

---

## Add a Project (new project page + card)

### Step 1 — Create the project page

1. Duplicate `projects/housing-affordability.html` and rename it.
   Use the format: `projects/your-project-name.html`

2. At the very top of the file, update the front matter:

   ```
   ---
   layout: project
   title: "Your Project Title"
   permalink: /projects/your-project-name/
   ---
   ```

3. Edit the content below the front matter — update the title, lead paragraph, tags,
   section text, visual placeholders, links, and AI note as needed.

4. Follow the placeholder comments inside the file to know where to swap in real images
   once you have them (see **Add a Visual to a Project Page** below).

### Step 2 — Add the project card to the listing page

1. Open `projects.md`.

2. Copy this block and paste it inside the `<div class="project-grid">` section,
   just above the `<!-- ADD MORE PROJECT CARDS HERE -->` comment:

   ```html
   <a href="{{ '/projects/your-project-name/' | relative_url }}" class="project-card">
     <div class="project-card-thumb">
       <img src="{{ '/assets/images/projects/your-project-name.jpg' | relative_url }}"
            alt="Your Project Title"
            onerror="this.style.display='none'; this.nextElementSibling.style.display='flex';"
            style="display:block;">
       <span class="project-card-thumb-placeholder" style="display:none;">&#9632;</span>
     </div>
     <div class="project-card-footer">
       <p class="project-card-name">Your Project Title</p>
     </div>
   </a>
   ```

3. Replace `your-project-name` and `Your Project Title` with the real values.

4. The card will show a dark placeholder square until you add a cover image
   (see **Add a Cover Image to a Project Card** below).

5. Commit and push.

---

## Add a Cover Image to a Project Card

The cover image is the thumbnail shown on the Projects listing page.

1. Prepare your image — a square crop works best (e.g. 600×600 px). Any common format works (JPG, PNG, WEBP).

2. Rename the file to match the project name. For example:
   ```
   housing-affordability.jpg
   ```

3. Drop the file into:
   ```
   assets/images/projects/
   ```
   Create the `projects/` subfolder inside `assets/images/` if it doesn't exist yet.

4. The card on the Projects page will automatically show the image — no code changes needed,
   as long as the filename matches what's already in `projects.md`.

   For the Housing Affordability project the expected filename is:
   ```
   assets/images/projects/housing-affordability.jpg
   ```

5. Commit and push.

---

## Add a Visual to a Project Page

Visuals inside a project page are currently shown as dashed placeholder boxes.
Here is how to replace one with a real image.

### For a single visual

1. Save your chart/graph image (PNG or JPG recommended) and name it descriptively.
   Example: `ha-visual-3.png`

2. Drop it into:
   ```
   assets/images/projects/
   ```

3. Open the project HTML file (e.g. `projects/housing-affordability.html`).

4. Find the placeholder div for that visual. It looks like this:
   ```html
   <div class="visual-placeholder">
     <span class="visual-placeholder-icon">&#9640;</span>
     <strong>Visual 3</strong>
     Affordability Ratios (Price-to-Income)<br>
     <!-- To replace: remove this div and use:
          <img class="proj-visual" src="{{ '/assets/images/projects/ha-visual-3.png' | relative_url }}" alt="Affordability Ratios">
     -->
   </div>
   ```

5. Delete the entire `<div class="visual-placeholder">...</div>` block.

6. Paste the `<img>` line that was in the comment:
   ```html
   <img class="proj-visual" src="{{ '/assets/images/projects/ha-visual-3.png' | relative_url }}" alt="Affordability Ratios">
   ```
   Make sure the filename in `src=` matches your actual file.

7. Commit and push.

### For the two-column visual pair (Visuals 1 & 2 in Housing Affordability)

1. Save both images, e.g. `ha-visual-1.png` and `ha-visual-2.png`, and drop them into
   `assets/images/projects/`.

2. Find the `<div class="visual-row-2">` block in the project HTML file.
   It contains two placeholder divs side-by-side.

3. Replace the entire `<div class="visual-row-2">` block with:
   ```html
   <div class="proj-visual-row-2">
     <img class="proj-visual" src="{{ '/assets/images/projects/ha-visual-1.png' | relative_url }}" alt="Median vs Average Home Price">
     <img class="proj-visual" src="{{ '/assets/images/projects/ha-visual-2.png' | relative_url }}" alt="Price Divergence">
   </div>
   ```

4. Commit and push.

---

## Add an Image to a Blog Post

1. Drop the image file into `assets/images/` (create this folder if it doesn't exist yet).

2. Reference it in a blog post or page like this:

   ```markdown
   ![description of image]({{ '/assets/images/your-image.jpg' | relative_url }})
   ```

3. If you want the image smaller, use this HTML version in your post:

  ```html
  <img class="post-image-small" src="{{ '/assets/images/your-image.jpg' | relative_url }}" alt="description of image">
  ```

4. To change the size yourself, open `assets/css/style.css` and edit the width in `.post-image-small`:

  ```css
  .post-image-small {
    width: min(420px, 100%);
  }
  ```

  - Change `420px` to any value you want (example: `320px` smaller, `520px` bigger).

---

## Edit About Me

Open `_layouts/home.html` and edit the text directly in the About Me section (lines 10–18).
It's plain text — just change the words, don't touch the `<p>`, `<ul>`, or `<li>` tags.

---

## Edit Site-Wide Info (name, social links)

Open `_config.yml`. Change:
- `title` — your name shown in the browser tab
- `social.linkedin` — your LinkedIn URL
- `social.github` — your GitHub URL

---

## File Map

```
_posts/                        ← blog post files go here
_data/
  projects.yml                 ← (legacy, no longer used)
assets/
  images/
    projects/                  ← project cover images + in-page visuals go here
  css/
    style.css                  ← all styling (edit to change design)
_layouts/
  default.html                 ← nav header + footer
  home.html                    ← home page content (About Me lives here)
  post.html                    ← individual blog post template
  project.html                 ← individual project page template
  page.html                    ← generic page template
projects/
  housing-affordability.html   ← Housing Affordability project page
index.md                       ← home page
blog.md                        ← blog list page
projects.md                    ← projects listing page (square card grid)
_config.yml                    ← site title, author, social links
```
