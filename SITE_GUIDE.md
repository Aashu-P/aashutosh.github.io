# Site Guide

Quick reference for adding content to this site. No HTML knowledge needed for any of these.

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

## Add a Project

1. Open `_data/projects.yml`

2. Add a new entry at the bottom (copy-paste this block):

   ```yaml
   - title: "Your Project Name"
     description: "What it does in a sentence or two."
     tech: "Python, Pandas, scikit-learn"
     link: "https://github.com/Aashu-P/your-repo"
   ```

   - `tech` and `link` are optional — delete those lines if you don't have them yet.
   - The Projects page will automatically switch from "Coming Soon" to showing your cards.

3. Commit and push.

---

## Add an Image

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
_posts/          ← blog post files go here
_data/
  projects.yml   ← add projects here (plain list)
assets/
  images/        ← drop image files here
  css/
    style.css    ← all styling (edit if you want to change design)
_layouts/
  default.html   ← nav header + footer (edit to change nav links)
  home.html      ← home page content (About Me lives here)
  post.html      ← individual blog post template
  page.html      ← generic page template
index.md         ← home page (just points to home layout)
blog.md          ← blog list page
projects.md      ← projects page (reads from _data/projects.yml)
_config.yml      ← site title, author, social links
```
