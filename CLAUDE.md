# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Cecilia Curreli's personal academic website (GitHub Pages), built on Jekyll with the `minimal-mistakes` remote theme, extended into a template for scientific project pages and a publication overview. There are no tests or linters; verification is done by building/serving the site and looking at it.

## Commands

```bash
bundle install                 # one-time setup (Ruby + Jekyll ~> 4.4)
bundle exec jekyll serve       # run locally with live reload of content
bundle exec jekyll build       # build into _site/
```

- `_config.yml` is NOT reloaded by `jekyll serve` — restart the server after editing it.
- Deployment is automatic: pushing to `main` triggers `.github/workflows/jekyll3.yml`, which builds with Ruby 3.1 and deploys `_site/` to GitHub Pages.
- `_site/` and `.jekyll-cache/` are generated output; never edit them.
- `jekyll serve`'s file watcher can miss rapid in-place overwrites of the same filename (e.g. regenerating a video clip several times with `ffmpeg -y`), leaving a stale — or even 0-byte — copy in `_site/` that neither a browser refresh nor a server restart fixes. If a video/image looks wrong after editing it, don't assume it's a code bug: `rm -rf _site && bundle exec jekyll build`, and `md5sum` the source file against its `_site/` copy to confirm before digging further.

Media conversion helpers:

```bash
./video2webm.bash input.mp4 30                       # .mp4/.gif → .webm (preferred video format), 30 = crf
./split_past_future.py input.mp4 output_prefix        # crops a past(green)/future(blue) motion clip (the --c-obs/--c-pred color convention) into output_prefix_past.mp4 + output_prefix_future.mp4, time-aligned: past freezes on its last frame, future stays blank white until motion starts. See --help for color/threshold overrides.
inkscape --export-type="svg" input.pdf                # .pdf → .svg (preferred image formats: .png/.svg)
```

## Architecture

### Front page
`index.html` is an empty shell rendered by `_layouts/welcome.html`, which contains the about/bio text directly in its HTML and pulls news entries from `_data/news.yml` (list of `date` + `description`, newest first). The left sidebar (name, photo, bio, social links) comes from the `author:` block in `_config.yml`.

### Publications (the core of the site)
Publications form a Jekyll collection (`_publications/`, sorted by date). Each publication is a directory `_publications/<name>/` containing:

- `index.md` — all metadata in front matter; its body is just `{% include_relative content.html %}`. Key fields: `permalink`, `date` (format `YYYY_MM_DD`, determines sort order), `image` / `image_mouseover` (thumbnail + hover asset for the overview, supports `.webm`/`.mp4`), `title`, `venue`, `authors`, `affiliations`, `description`, `links` (buttons: Paper/Code/Video/Poster..., with Bootstrap-icon `style` classes), optional `citation` (rendered with copy-to-clipboard button) and `acknowledgements`. An optional `external_link` makes the overview link out instead of to the local page.
- `content.html` — the hand-written page body (results, videos, figures).
- `assets/` — the publication's media files.

`_layouts/publications.html` provides the page shell: it renders `_includes/header.html` (title, author list, link buttons), then the content, then `_includes/citation.html` and `_includes/acknowledgements.html`. It loads Bulma, icon fonts, and MathJax from CDNs.

Authors and affiliations in `index.md` are shortname keys resolved against `_data/authors_internal.yaml`, `_data/authors_external.yaml`, and `_data/affiliations.yaml` (with `long`/`short` name variants; `is_me: true` marks the site owner). Add new co-authors/affiliations there, not inline.

`_pages/publication_overview.html` (permalink `/publications/`) builds the overview automatically from each publication's front matter — publications never need to be registered anywhere manually. Thumbnails with mouseover swap are rendered by `_includes/preview.html`.

### Reusable content components
`_includes/` holds components for use inside `content.html`, e.g. `comparison_slider.html` (image-comparison slider; requires adding `<script defer src="/js/slider-component.js"></script>` at the end of the `content.html` that uses it). Its CSS is already loaded by the publications layout.

### Styling
Global styles live in `assets/css/` (`style.scss`, `header.scss`, `publication_overview.css`, ...) — Jekyll compiles the `.scss` files that carry front matter, so some names exist as both `.scss` source and stale compiled `.css`. Theme overrides live in `_sass/custom.scss`.

### PDF embedding
`assets/pdfjs/web/` holds a pdf.js viewer used to embed PDFs in publication pages via an iframe, e.g. `assets/pdfjs/web/viewer.html?file=_publications/<name>/assets/<file>.pdf` (see `_publications/skeletondiffusion/content_new.html`). The top-level `pdf.js-master/` directory is the vendored pdf.js source it was built from, not part of the site.

## Reference

`README.md` documents the template in detail, including a fully commented example `index.md` front matter — consult it when creating a new publication page.
