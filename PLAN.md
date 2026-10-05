# Project plan

## Primary Goal as of September 2026

Migrate the LARC Research Group website from its old Google Sites home
(`iarg.si.umich.edu`) to a self-hosted Hugo static site, redesigned to follow the
[U-M Library Design System](https://design-system.lib.umich.edu/), with all real content
carried over (not placeholder copy).

## Source of truth

- **Old site**: https://iarg.si.umich.edu/ — a Google Site. Content is client-rendered,
  so pulling exact text requires a real/headless browser render, not a plain HTTP fetch.
- **Design system**: https://design-system.lib.umich.edu/ — color palette, typography
  scale, and component guidance (header, footer, cards) referenced throughout the theme.
- **Content owners**: Jesse Johnston and Lavinia Dunagan — the people to check with on
  anything content-accuracy related (bios, roster changes, news items).

## Status

Core migration is done and deploying. Site structure:

- **Home** — hero (photo + gradient overlay, headline, subtitle), About section, (an
  earlier "Get involved" card row is currently commented out in `home.html`)
- **Activities** — overview + DAIS subpage
- **People** — Faculty / PhD Students / Campus Affiliates, grouped, with real bios and
  links (UMSI profile, ORCID, personal site) pulled from the old site
- **News** — individual hugo posts, dated and possibility (not requirement to add an author)

Theme (`themes/larc`) is custom-built on Bootstrap 5 (via CDN) with U-M brand colors and
Noto Sans, not based on a third-party Hugo theme.

Deploy: GitHub Actions → GitHub Pages, on push to `main`.

## Known gaps / decisions still open

See `TODO.md` for the actionable list. Bigger open questions:

- **Final hosting URL.** `hugo.toml` baseURL is set to `https://larc.si.umich.edu/`, but
  the site is currently deploying to GitHub Pages. Confirm the real production URL before
  calling this done — baseURL affects every absolute link Hugo generates.
- **Real headshots.** People page currently uses initial-letter placeholder avatars; no
  stock or AI-generated photos were used intentionally. Needs real photos, with consent/
  rights confirmed for each person.
