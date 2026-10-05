# TODO

Status tracker for outstanding work. Check items off (`[x]`) as they're done; add new
ones as they come up rather than tracking them only in chat/PR comments.

## Content

- [ ] Get real headshot photos for the People page (currently using initial-letter
  placeholder avatars) — confirm usage rights per person before adding.
- [ ] Double-check every bio/news item against the live old site one more time before
  retiring it — a prior pass was based on a paraphrased fetch and had to be redone with
  verified source text; worth a second human proofread.
- [x] Confirm official group name/wording — README says "Libraries, Archives, and Digital
  Curation," the site tagline currently says "Libraries, Archives, and Curation" (no
  "Digital"). Pick one and make them consistent. The name is Libraries, Archives, and digital Curation (digital is not capitalized because of the acronym)
- [ ] Audit `content/activities/` and DAIS page text against the live old site (past speakers list, current framing), determine what's missing and what should be ported into new site.

## Config / deploy

- [ ] Confirm the real production URL and update `baseURL` in `hugo.toml` accordingly
  (currently `https://larc.si.umich.edu/`, but deploying to GitHub Pages).
- [ ] Decide on final footer legal links — `Report abuse` / `Privacy policy` entries are
  currently commented out in `hugo.toml`; only the UMSI link is live.
- [ ] If U-M IT/security review requires self-hosted (no third-party CDN) assets,
  vendor Bootstrap into the repo instead of loading from jsDelivr.
- [ ] Set up a custom domain (if applicable) and confirm HTTPS/DNS once the final URL
  is locked in.

## Design / polish

- [ ] Real design/UX review against the U-M Library Design System component docs
  (header, footer, cards) beyond the current best-effort pass.
- [ ] Accessibility pass: color contrast check on hero text over the photo background,
  keyboard nav through the dropdown menu, screen-reader pass on the People page.
- [ ] Cross-browser/device check — most verification so far has been build-level
  (`hugo --gc --minify` clean) plus spot-checks, not full manual QA.
- [ ] Favicon is still the Hugo default placeholder (`static/favicon.ico`) — replace with
  a real LARC/UMSI icon.

## Process

- [ ] Figure out a lightweight content-editing workflow for non-technical collaborators
  (direct Markdown edits via GitHub web UI are workable short-term; consider whether a
  CMS front-end is worth it later).
