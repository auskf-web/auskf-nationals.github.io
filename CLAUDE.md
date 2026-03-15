# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
# Install dependencies
bundle install

# Serve locally with live reload
bundle exec jekyll serve

# Build site (output to _site/)
bundle exec jekyll build
```

The site runs at `http://localhost:4000` by default.

## Architecture

This is a static Jekyll site for the AUSKF National Kendo Championships, deployed via GitHub Pages.

**`CLAUDE.md` is excluded from Jekyll builds** via `exclude` in `_config.yml` — necessary because Jekyll would otherwise try to process the Liquid syntax examples it contains.

**Tournament configuration** is centralized in `_config.yml`. Almost all year-to-year updates (dates, venue, fees, deadlines) happen there via Liquid variables like `{{ site.tournament_year }}`, `{{ site.tournament_date_with_day }}`, etc. Pages reference these variables throughout.

**Layouts:**
- `landing-page` — used by `index.md`; includes the hero banner. Wraps content in `<article id="main"><header class="special container">`.
- `inner-page` — used by `info.md`, `travel.md`, `past.md`; wraps content in `<article id="main"><section class="wrapper style4 container">` and renders `page.title` as the page heading.
- `default` — base layout; no structural wrappers beyond `<div class="page-content">`.

**Navigation** is hardcoded in `_includes/header.html`. Many nav items are commented out and toggled on/off depending on the stage of the tournament (e.g., Register, Schedule, Results are hidden until relevant).

**Page lifecycle pattern:** Pages like `register.html`, `schedule.html`, `results.html`, `sponsors.html`, and `gear.html` exist but are linked/unlinked from the nav by commenting/uncommenting entries in `header.html`.

**Assets:** `assets/banner.jpg` is the hero image. Banner attribution vars in `_config.yml` point to the image source.

## Markdown pages

Content pages are Markdown (`.md`) using kramdown. Key patterns:

**Indented content blocks** use `<div markdown="1" class="indented">` — defined in `css/style.css` as `padding: 0 0 0 2em` with no border or italic (overriding the default blockquote style). The `markdown="1"` attribute tells kramdown to process the contents as Markdown.

**Kramdown gotchas:**
- Tables must be the first block inside a `<div markdown="1">`. If introductory text is needed before a table, place it outside the div.
- Section anchor IDs cannot start with a digit (`{#2023}` fails; use `{#y2023}`).
- Trailing two spaces create a hard line break (`<br>`). The Write tool strips trailing spaces — use a Python one-liner to add them after writing.
- `{: style="..."}` on the line after a block element applies inline styles via kramdown IAL (e.g. `{: style="margin-bottom: 0"}` to close the gap between a paragraph and a following list).
- Use `{%- if %}` / `-%}` to strip whitespace around Liquid tags that would otherwise produce blank lines in rendered output.

**CSS reset:** `css/skel.css` resets `ul { list-style: none }`. Lists inside `.indented` divs get bullets restored via `.content .indented ul { list-style: disc }` in `css/style.css`. Plain lists outside `.indented` remain unstyled.

**Tables** are styled via `.content table / th / td` rules in `css/style.css`. Use `<br>` inside table cells for multi-line cell content.
