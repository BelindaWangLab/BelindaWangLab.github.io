# Belinda Wang Lab Website

This is the public GitHub Pages/Jekyll source for the Belinda Wang Lab website.

This folder should contain only files that are safe to publish on GitHub.

## Public Site Structure

- `_config.yml`: site metadata and domain settings.
- `_data/navigation.yml`: top navigation.
- `_includes/site-footer.html`: public footer text and source attribution links.
- `_data/publications.json`: curated publication metadata.
- `_people/*.md`: public lab member and alumni profiles.
- `_posts/*.md`: public news items.
- `assets/`: public CSS, logos, icons, and image assets.
- `assets/img/publications/`: public publication thumbnail images.
- `assets/img/share-card.png`: public link-preview image for shared URLs.
- `assets/img/share-card.svg`: editable source for the link-preview image.
- `favicon.svg`, `apple-touch-icon.png`, and `apple-touch-icon.svg`: browser tab and saved-link icons.
- `index.md`, `research.md`, `publications.md`, `people.md`, `news.md`, `contact.md`, `support.md`: public pages.

Do not put internal Google Docs, Google Sheets, unpublished PDFs, raw form responses, collaborator notes, draft thumbnails, or working image files in this folder. Keep those in sibling folders such as `../content-inputs/` and `../private/`. Only final, public-ready assets should go in `assets/`.

## Preview Locally

If Ruby 3 and Bundler are available:

```bash
bundle install
bundle exec jekyll serve
```

Then open `http://127.0.0.1:4000`.

The included GitHub Actions workflow already uses Ruby 3.3, so GitHub Pages can build this even if an older system Ruby is installed locally.

## Publish On GitHub Pages

1. Create the GitHub repository `BelindaWangLab/BelindaWangLab.github.io`.
2. Push this folder to the repository's `main` branch.
3. In GitHub, go to Settings -> Pages.
4. Set Source to GitHub Actions.
5. The included workflow in `.github/workflows/pages.yml` will build and deploy the site.

For a user or organization site URL like `https://username.github.io`, name the repository `username.github.io`.

For `belindawanglab.com`, see `DOMAIN_SETUP.md`.

## Reference Lineage

The three reference sites use or cite the same broad GitHub Pages/Jekyll lab-site pattern:

- Capra Lab: `http://capralab.org/`
- Coyote-Maestas Lab: `https://www.wcoyotelab.com/`
- Fraser Lab research page: `https://fraserlab.com/research/`
