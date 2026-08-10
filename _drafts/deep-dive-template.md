---
title: "Deep-Dive Post Template"
excerpt: "A scaffold post exercising every feature a deep-dive post can use — TOC, math, code, footnotes. Not real content; delete this front-matter note and everything below it when you start a real post."
tags:
  - template
---

This file lives in `_drafts/`, so Jekyll only builds it when you run
`bundle exec jekyll serve --drafts`. It won't appear on the live site.
To start a real post: copy this into `_posts/` as
`YYYY-MM-DD-my-post-title.md`, delete this paragraph, and write.

Everything below demonstrates what's available.

## Headings become the table of contents

Every `##`/`###` heading on this page shows up in the "On This Page"
box to the right (on wide viewports) — that's `kramdown`'s `auto_ids`
plus the `{:toc}` include wired into `_layouts/single.html` for any
post with `toc: true` in front matter, which is on by default for all
posts (see `_config.yml`'s `_posts` defaults).

### A subheading

Subheadings nest one level in the TOC.

## Math

Inline math works: the waypoint loss is $\mathcal{L} = \sum_t w_t \lVert \hat{y}_t - y_t \rVert^2$.

Display math too:

$$
w_t = 0.5 + \frac{t}{T}(1.5 - 0.5), \qquad t \in [0, T]
$$

(MathJax is loaded site-wide in `_includes/head/custom.html`, no
per-post opt-in needed.)

## Code

```python
def waypoint_loss(pred, target, horizon=5):
    # penalize drift more heavily near the grasp waypoint
    weights = torch.linspace(0.5, 1.5, horizon)
    err = (pred - target).pow(2)
    return (weights * err).mean()
```

Syntax highlighting uses the Catppuccin mapping in `_sass/_syntax.scss`,
so it follows the light/dark toggle automatically.

## Footnotes

Claims that need a citation or aside can use a footnote[^1] instead of
breaking the paragraph's flow.

## Blockquotes

> Quotes from papers, reviewers, or past-you render like this.

## Front matter reference

```yaml
---
title: "Post Title"
excerpt: "One or two sentences — used in previews and social cards."
tags:
  - imitation-learning
  - robotics
---
```

`toc`, `read_time`, `share`, `related` all default on for posts already
(`_config.yml`) — no need to repeat them per post unless overriding.

[^1]: Like this one.
