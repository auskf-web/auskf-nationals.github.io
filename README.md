# auskf-nationals.github.io

The official website for the AUSKF National Championships, powered by GitHub Pages and Jekyll. Please visit [www.auskf-nationals.com][1] for more information.

Design adapted from [Twenty by HTML5 UP][2], free for personal and commercial use under the [CCA 3.0 license][3].

## Running locally with Jekyll

```bash
bundle install
bundle exec jekyll serve
```

The site will be available at `http://localhost:4000`. Jekyll will watch for changes and rebuild automatically.

## Updating tournament information

Most year-to-year changes (dates, venue, fees, deadlines) are made in one place: `_config.yml`. Update the variables there and they will propagate throughout the site automatically.

## Updating page content

Content pages are written in Markdown:

- `index.md` — welcome/home page
- `info.md` — tournament info (schedule, divisions, rules, food, shinpan, etc.)
- `travel.md` — airport and hotel information
- `past.md` — past tournament results

## Toggling nav links

Navigation is hardcoded in `_includes/header.html`. Links for pages like Register, Schedule, and Results are commented out and uncommented as the tournament approaches.

[1]: http://www.auskf-nationals.com
[2]: https://html5up.net/twenty
[3]: https://html5up.net/license
