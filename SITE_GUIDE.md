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
   section text, visuals, links, and AI transparency note as needed.

### Step 2 — Add the project card to the listing page

1. Open `projects.md`.

2. Copy this block and paste it inside the `<div class="project-grid">` section,
   just above the `<!-- ADD MORE PROJECT CARDS HERE -->` comment:

   ```html
   <a href="{{ '/projects/your-project-name/' | relative_url }}" class="project-card">
     <div class="project-card-thumb"
          style="background-image: url('{{ '/assets/images/projects/your-project-name.jpg' | relative_url }}');">
     </div>
     <div class="project-card-footer">
       <p class="project-card-name">Your Project Title</p>
     </div>
   </a>
   ```

3. Replace `your-project-name` and `Your Project Title` with the real values.

4. The card shows a clean dark background until you add a cover image
   (see **Add a Cover Image to a Project Card** below).

5. Commit and push.

---

## Add a Cover Image to a Project Card

The cover image is the square thumbnail shown on the Projects listing page.
Until you add one, the card shows a plain dark background — that's intentional,
not a bug. No placeholder file is needed.

### Housing Affordability cover image

1. Pick any screenshot or image you want to represent the project.
   **A square crop looks best** (e.g. export at 600×600 px or just crop it square).

2. Name the file exactly:
   ```
   housing-affordability.jpg
   ```
   (PNG or WEBP also work — just keep the name `housing-affordability` and update the
   extension in `projects.md` line 15 to match, e.g. `.png`)

3. Drop it into:
   ```
   assets/images/projects/
   ```
   That folder already exists in the repo.

4. Commit and push. **No code changes needed** — the card is already wired to that filename.

### Adding a cover image for a future project

Same process — the card in `projects.md` has a `background-image` style pointing to
`assets/images/projects/your-project-name.jpg`. Just drop the correct file in and push.

---

## Add a Visual / Chart to a Project Page

Images in a project page use `<img>` tags with the class `proj-visual`.

### Adding a single visual

1. Save your chart/graph image (PNG or JPG recommended) and name it descriptively.
   Example: `ha-visual-3.png`

2. Drop it into:
   ```
   assets/images/projects/
   ```

3. Open the project HTML file (e.g. `projects/housing-affordability.html`).

4. Add or update the `<img>` tag where you want the visual:
   ```html
   <img class="proj-visual" src="{{ '/assets/images/projects/ha-visual-3.png' | relative_url }}" alt="Description of visual">
   ```
   Make sure the filename in `src=` matches your actual file.

5. Commit and push.

### Adding two visuals side by side

Wrap two `<img>` tags in a `proj-visual-row-2` div:

```html
<div class="proj-visual-row-2">
  <img class="proj-visual" src="{{ '/assets/images/projects/ha-visual-1.png' | relative_url }}" alt="First visual">
  <img class="proj-visual" src="{{ '/assets/images/projects/ha-visual-2.png' | relative_url }}" alt="Second visual">
</div>
```

On mobile, the two images will stack vertically automatically.

### Current visuals in Housing Affordability

The project page already has 4 `<img>` tags wired to these filenames:

| Slot     | Filename            | Description                      |
|----------|---------------------|----------------------------------|
| Visual 1 | `ha-visual-1.png`   | Median vs. Average Home Price    |
| Visual 2 | `ha-visual-2.png`   | Price Divergence                 |
| Visual 3 | `ha-visual-3.png`   | Affordability Ratios             |
| Visual 4 | `ha-visual-4.png`   | HPI vs. Income                   |

**To make them show up:** export your charts with those exact filenames, drop them
into `assets/images/projects/`, commit, and push. No code changes needed.

---

## Add an Image to a Blog Post

1. Drop the image file into `assets/images/`.

2. Reference it in your blog post Markdown:

   ```markdown
   ![description of image]({{ '/assets/images/your-image.jpg' | relative_url }})
   ```

3. If you want the image smaller, use this HTML version in your post:

   ```html
   <img class="post-image-small" src="{{ '/assets/images/your-image.jpg' | relative_url }}" alt="description">
   ```

4. To change the size, open `assets/css/style.css` and edit the width in `.post-image-small`:

   ```css
   .post-image-small {
     width: min(420px, 100%);
   }
   ```

   Change `420px` to any value you want (e.g. `320px` smaller, `520px` bigger).

---

## Edit the AI Transparency Note on a Project

Each project page has an AI Transparency section at the bottom. To edit it:

1. Open the project HTML file (e.g. `projects/housing-affordability.html`).

2. Find the `<!-- ── AI Transparency -->` comment near the bottom.

3. Edit the text inside the `<div class="proj-section-body">`.

4. To add a link, use:
   ```html
   <a href="https://your-url-here" target="_blank" rel="noopener noreferrer">Link Text</a>
   ```

5. To bold a word, wrap it in `<strong>word</strong>`.

---

## Edit About Me

Open `_layouts/home.html` and edit the text directly in the About Me section (lines 10–18).
It's plain text — just change the words, don't touch the `<p>`, `<ul>`, or `<li>` tags.

---

## Edit Navigation Links

The nav bar (Home, Blogs, Projects) is in `_layouts/default.html` lines 18–20.
To add a new page to the nav, add a new `<a>` tag following the same pattern.

---

## Edit Footer (Social Links)

Social links are controlled by `_config.yml`:
- `social.linkedin` — your LinkedIn URL
- `social.github` — your GitHub URL

The footer template is in `_layouts/default.html` lines 31–39 if you want to add
more links (e.g. email, Twitter).

---

## Edit Site-Wide Info

Open `_config.yml`:
- `title` — your name (appears in the browser tab)
- `url` — your GitHub Pages URL
- `baseurl` — the repo name path (e.g. `/aashutosh.github.io`)

---

## Previewing Changes Locally

If you have Jekyll installed, run:
```
bundle exec jekyll serve
```
from the repo root. Then open `http://localhost:4000/aashutosh.github.io/` in your browser.

If you don't have Jekyll installed, just push to GitHub and check the live site after
the GitHub Actions build completes (takes about 1–2 minutes).

---

## File Map

```
_posts/                        ← blog post files go here
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
SITE_GUIDE.md                  ← this file
CHANGELOG.md                   ← log of changes made to the site
```
