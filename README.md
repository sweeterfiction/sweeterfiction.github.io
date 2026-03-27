# sweeterfiction.github.io

Personal research blog built with [Quarto](https://quarto.org). Posts are Jupyter notebooks or markdown, rendered locally and served via GitHub Pages.

---

## Adding a post

Create a subdirectory under `posts/` with an `index.qmd` or `index.ipynb` file.

**Markdown post**

```
posts/my-post/index.qmd
```

```yaml
---
title: "My post title"
date: "2026-03-26"
description: "One sentence summary."
---

Content here.
```

**Jupyter notebook post**

Add a Raw cell at the very top of the notebook with YAML front matter:

```yaml
---
title: "My analysis"
date: "2026-03-26"
description: "One sentence summary."
---
```

Then place the notebook at `posts/my-post/index.ipynb`. Any data files the notebook needs at runtime are not committed — only the notebook with its saved cell outputs.

To make Altair/Vega-Lite charts fill the column width, set `"width": "container"` and `"autosize": {"type": "fit", "contains": "padding"}` in the chart spec before saving outputs.

---

## Rendering and deploying

```bash
# Preview locally (live reload)
quarto preview

# Build to docs/
quarto render

# Commit and push
git add .
git commit -m "add post: my-post"
git push
```

GitHub Pages serves the `docs/` folder on the `main` branch. No CI needed.

**First-time GitHub Pages setup:** repo Settings → Pages → Source: Deploy from branch → Branch: `main` → Folder: `/docs`.

---

## Structure

```
├── _quarto.yml          # site config, theme
├── styles.scss          # CSS overrides on top of cosmo theme
├── index.qmd            # blog listing (homepage)
├── about.qmd
├── posts/
│   ├── _metadata.yml    # shared: freeze: true, echo: false
│   └── <post-name>/
│       └── index.qmd or index.ipynb
└── docs/                # rendered output (committed, served by GitHub Pages)
```
