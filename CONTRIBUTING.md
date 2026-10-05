# Contributing

Thanks for helping keep the LARC site up to date. This covers the common content
edits — for anything about how the site is built, see `AGENTS.md`.

## How to contribute

1. Make your changes on a new branch (not directly on `main`).
2. Open a pull request against `main`.
3. Once it's reviewed and merged, the site rebuilds and redeploys automatically via
   GitHub Actions — no extra steps needed.

All of the edits below can be made directly in GitHub's web editor if you don't want to
clone the repo locally — click the pencil icon on the file, make your change, and it'll
prompt you to open a PR.

## Add or replace a photo for your bio snippet

1. Add the image file to `assets/images/people/`. Use a lowercase, underscore-separated
   filename based on the person's name, e.g. `william_bishop.jpg`.
2. Open `data/people.yaml`, find that person's entry, and add (or update) the `photo`
   field with just the filename:

   ```yaml
   - name: William Bishop
     bio: "Former University Librarian at University of Michigan..."
     photo: "william_bishop.jpg"
     links: []
   ```

If no `photo` value is added, the site automatically shows a UMSI logo
placeholder instead.

## Change a bio

Open `data/people.yaml`, find the person under their group (`faculty`, `phd_students`,
or `campus_affiliates`), and edit the `bio` field directly. It's a single-line quoted
string — keep it on one line and make sure it stays wrapped in double quotes.

## Add a Google Scholar (or other) link

Each person has a `links` list. Add a new entry with a `label` (what the link text says)
and a `url`:

```yaml
- name: William Bishop
  bio: "..."
  photo: "william_bishop.jpg"
  links:
    - label: "Google Scholar"
      url: "https://scholar.google.com/citations?user=XXXXXXX"
    - label: "UMSI faculty page"
      url: "https://www.si.umich.edu/people/william-bishop"
```

If your person entry doesn't have any links, the `links` field will look like `links: []`
— replace that with the list format above.

Links show up on the People page in the order they're listed, separated by a middle dot.
