# AGENTS.md

Guidance for AI coding assistants (and human contributors) working in this repo.
This is the project's shared context file — update it as conventions change, the same
way you'd update a README.

## What this is

The website for **LARC** (Libraries, Archives, and Curation), a research group at the
University of Michigan School of Information (UMSI). It's a Hugo static site, migrated
from the group's old Google Sites page at `iarg.si.umich.edu`, built as a custom theme
(`themes/larc`) following the [U-M Library Design System](https://design-system.lib.umich.edu/).

Contact for content questions: Jesse Johnston and Lavinia Dunagan (see README.md).

## Stack

- **Hugo** (extended), static site generator. Pin version: see `.github/workflows/hugo.yml`
  (`HUGO_VERSION`) — keep this in sync with whatever version you build/test with locally,
  or deploys will break on template features the pinned version doesn't support yet.
- **Bootstrap 5.3.3**, loaded from the jsDelivr CDN in `themes/larc/layouts/_partials/head.html`
  and `baseof.html` — not vendored into the repo. Don't add a local copy; if self-hosting
  ever becomes a requirement, that's a deliberate swap, not a default.
- **Google Fonts** (Noto Sans), also loaded via `<link>` in `head.html`.
- No JS framework, no build step beyond Hugo Pipes (asset bundling/fingerprinting via
  `resources.Get` + `css.Build`). No npm dependencies currently in use.
- Deployed via GitHub Actions (`.github/workflows/hugo.yml`) to GitHub Pages.

## Repo layout

```
content/              Real site content (pages, posts) — this is what editors touch day to day
  _index.md            Homepage body (About section)
  activities/
  news/                Each post is a news item with a `date` front-matter field
  people/_index.md      People page wrapper; roster note lives in its front matter
data/people.yaml       The actual people roster (grouped: faculty / phd_students / campus_affiliates)
hugo.toml              Site config: params, main nav menu, footer link menu
themes/larc/           The theme — all templates, CSS, and theme-level assets live here
  layouts/              Hugo templates (baseof, home, page, section, people/list, partials/)
  assets/css/           variables.css (brand tokens + Bootstrap variable overrides) +
                         components/*.css (thin brand-specific layers on top of Bootstrap)
assets/images/          Project-level image assets (logo, hero photo) — referenced via
                        resources.Get "images/<file>" from templates
.github/workflows/      GitHub Actions deploy workflow
```

## Conventions established so far

- **Don't fabricate content.** Bios, news copy, and page text were migrated from the real
  old site (`iarg.si.umich.edu`, a Google Site — content is JS-rendered, so fetch it with a
  real browser/headless Chrome dump, not a raw `curl`/summarizing fetch tool, or you'll get
  a paraphrase instead of the real text). If exact source text isn't available, say so and
  ask rather than inventing plausible-sounding copy — this has bitten us once already
  (see git history around the People page).
- **Colors/typography** come from the U-M Library Design System
  (https://design-system.lib.umich.edu/) — Michigan blue `#00274C`, maize `#FFCB05`, plus
  the full neutral/teal/pink/green/orange/indigo scales. These are defined as CSS custom
  properties in `themes/larc/assets/css/variables.css`, which also overrides Bootstrap's
  own CSS variables (`--bs-primary`, `--bs-link-color`, `--bs-font-sans-serif`, etc.)
  rather than fighting Bootstrap's defaults with `!important`.
- **No fabricated photos.** Real headshots aren't in the repo yet; the People page uses
  initial-letter avatar circles as a placeholder rather than invented or stock photos.
- **Section separators**: prefer background-color shifts and spacing (`bg-light`, `py-5`)
  over hard rule/border dividers between page sections.
- Images go in `assets/images/` (project root, not inside the theme) and are referenced
  from templates with `resources.Get "images/<filename>"` so Hugo Pipes can fingerprint
  them.
- **When a Hugo (or Bootstrap, or any framework) function behaves unexpectedly, consult
  the official docs for that function first** — don't reverse-engineer the behavior by
  grepping generated HTML or trial-and-error rebuilding variants. Example: `relURL`/
  `relLangURL` with a leading slash resolve relative to the host root and silently drop
  any baseURL subpath (e.g. a GitHub Pages project URL like `/larc-website/`) — this is
  documented, not a bug to rediscover empirically. The fix was `site.Home.RelPermalink`
  instead of `"/" | relLangURL`. Once the docs confirm the fix, apply it directly; don't
  pad it out with a reflexive verification build for a trivial, doc-confirmed change.

## Local dev

```
hugo server          # dev server with live reload, http://localhost:1313
hugo --gc --minify   # production-equivalent build, outputs to public/
```

`public/` and `.hugo_build.lock` are gitignored — never hand-edit or commit built output.

## Before committing

- Run a plain `hugo --gc --minify` build and confirm it's clean (no warnings/errors) before
  handing off work — this has caught real template bugs (e.g. a deprecated template field,
  a Hugo-version mismatch between local and CI) early.
- Don't change the pinned `HUGO_VERSION` in the GH Actions workflow without also re-testing
  a full local build at that version — template syntax that works on a newer local Hugo
  install can silently fail on an older pinned CI version.

See `PLAN.md` for project status/scope and `TODO.md` for the current outstanding task list.
