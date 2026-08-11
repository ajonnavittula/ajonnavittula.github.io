# ajonnavittula.github.io

Personal site and blog for Ananth Jonnavittula, built with [Jekyll](https://jekyllrb.com/) on the [academicpages](https://academicpages.github.io/) template (a fork of the [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/) theme by Michael Rose, MIT licensed — see `LICENSE`).

## Structure

- `_pages/about.md` — homepage / bio / news
- `_data/publications.yml` — publication list rendered by `_pages/publications.html`
- `_pages/cv.html` — embeds `files/Ananth-CV.pdf`, which is kept in sync automatically (see below) — don't hand-edit it, it'll just get overwritten
- `_posts/` — blog posts
- `markdown_generator/` — notebooks/scripts for generating publication & talk markdown from a BibTeX/TSV source

## Writing a blog post

1. Create `_posts/YYYY-MM-DD-slug.md` — the date in the filename is required (Jekyll uses it for the post's date and sort order); the slug becomes part of the URL.
2. Add front matter. Layout, TOC, read time, comments, share buttons, and related posts are all defaulted on for every post already (`_config.yml`), so only post-specific fields are needed:
   ```yaml
   ---
   title: "Post Title"
   excerpt: "One or two sentences — used in the listing page and social previews."
   tags:
     - some-tag
   ---
   ```
3. Write Markdown below the front matter. Headings (`##`/`###`) populate the TOC sidebar automatically. Math works inline (`$...$`) and as display blocks (`$$...$$`, via MathJax). Fenced code blocks get syntax highlighting. Footnotes work (`text[^1]` + `[^1]: note`).
4. Commit and push to `master` — GitHub Pages rebuilds automatically and the post appears on `/year-archive/` (the Blog nav link), newest first. No separate indexing step.

`_drafts/deep-dive-template.md` is a reference post exercising all of the above (headings, math, code, footnotes) — copy it into `_posts/` with a real dated filename and replace the content. Anything else placed in `_drafts/` (undated filename) only builds locally with `jekyll serve --drafts`, never on the live site — useful for in-progress posts.

## CV automation

`files/Ananth-CV.pdf` is kept in sync with an Overleaf project automatically by `.github/workflows/update-cv.yml`: it pulls the project via Overleaf's Git integration, compiles it, and commits the PDF if it changed. Runs weekly and on manual dispatch (repo → Actions → "Update CV from Overleaf" → Run workflow). Requires the `OVERLEAF_GIT_TOKEN` repo secret (Overleaf account settings → Git integration).

## Running locally

1. Install Ruby, Bundler, and Node.js.
2. `bundle install`
3. `bundle exec jekyll serve` (or `bundle exec jekyll liveserve` for auto-reload) — serves at `localhost:4000`.

`_config.dev.yml` overrides analytics/comments for local development; merge it in with:

```
bundle exec jekyll serve --config _config.yml,_config.dev.yml
```
