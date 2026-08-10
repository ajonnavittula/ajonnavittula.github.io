# ajonnavittula.github.io

Personal site and blog for Ananth Jonnavittula, built with [Jekyll](https://jekyllrb.com/) on the [academicpages](https://academicpages.github.io/) template (a fork of the [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/) theme by Michael Rose, MIT licensed — see `LICENSE`).

## Structure

- `_pages/about.md` — homepage / bio / news
- `_data/publications.yml` — publication list rendered by `_pages/publications.html`
- `_pages/cv.html` — embeds `files/Ananth-CV.pdf`
- `_posts/` — blog posts
- `markdown_generator/` — notebooks/scripts for generating publication & talk markdown from a BibTeX/TSV source

## Running locally

1. Install Ruby, Bundler, and Node.js.
2. `bundle install`
3. `bundle exec jekyll serve` (or `bundle exec jekyll liveserve` for auto-reload) — serves at `localhost:4000`.

`_config.dev.yml` overrides analytics/comments for local development; merge it in with:

```
bundle exec jekyll serve --config _config.yml,_config.dev.yml
```
