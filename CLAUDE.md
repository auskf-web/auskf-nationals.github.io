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

**Tournament configuration** is centralized in `_config.yml`. Almost all year-to-year updates (dates, venue, fees, deadlines) happen there via Liquid variables like `{{ site.tournament_year }}`, `{{ site.tournament_date }}`, etc. Pages reference these variables throughout.

**Layouts:**
- `landing-page` — used only by `index.html`; includes the hero banner
- `default` — used by all other pages; no banner
- `post` — available but unused

**Navigation** is hardcoded in `_includes/header.html`. Many nav items are commented out and toggled on/off depending on the stage of the tournament (e.g., Register, Schedule, Results are hidden until relevant).

**Page lifecycle pattern:** Pages like `register.html`, `schedule.html`, `results.html`, `sponsors.html`, and `gear.html` exist but are linked/unlinked from the nav by commenting/uncommenting entries in `header.html`.

**Assets:** `assets/banner.jpg` is the hero image. Banner attribution vars in `_config.yml` point to the image source.

**`show_save_the_date`** in `_config.yml` controls display of a save-the-date PDF link; requires `assets/{{ tournament_year }}-welcome.pdf` to exist when enabled.
