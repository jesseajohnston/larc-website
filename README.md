# LARC Website

This repo contains files for the website of the
Libraries, Archives, and Digital Curation research group
at the University of Michigan School of Information.
The site is migrating here and will be hosted as a Hugo site.
The site will serve at a UMSI URL when finished.

Contact: Jesse Johnston (jesseajohnston) and Lavinia Dunagan.

## Adding content

New news posts and DAIS talks start from archetypes in `archetypes/`.
Run these from the repo root, then edit the new file.

### News post

```sh
hugo new content news/my-post.md
```

Creates a file in `content/news/` with `title` and `date`. Replace the
generated title and write the post below the front matter.

### DAIS talk

```sh
hugo new content --kind dais activities/dais/2026-10-30-jane-doe.md
```

The `--kind dais` flag is required; without it Hugo uses the default archetype.
Name the file `YYYY-MM-DD-firstname-lastname.md`.

Fill in the front matter:

- `title`: speaker name.
- `date`: the talk date (not the file creation date). Talks sort by this within a term.
- `affiliation`: the speaker's institution.
- `term`: the academic term, such as `"Fall 2026"` or `"Winter 2027"`. Talks with the
  same `term` value are grouped under one heading, so spell it identically each time.

Optional fields are included commented out; uncomment the ones you need:

- `talkTitle`: title of the talk, shown in quotes.
- `eventDateDisplay`: replaces the formatted `date` when it needs to read differently,
  such as `"March 9-10, 2023"`.
- `acknowledgment`: small note shown at the end of the entry.
- `image`: talk graphic, a path under `assets/images/`, such as `"talks/202610_doe.png"`.
- `links`: a list of `label` and `url` pairs shown under the bio. Add as many as needed.

Write the speaker bio below the front matter.
