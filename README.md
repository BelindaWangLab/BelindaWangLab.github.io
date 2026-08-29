# Belinda Wang Lab Website

Public GitHub Pages/Jekyll source for [belindawanglab.com](https://belindawanglab.com).

## Site Structure

Top-level files:

- `_config.yml`: site settings.
- `.gitignore`: files Git should ignore.
- `index.md`, `research.md`, `publications.md`, `people.md`, `news.md`, `contact.md`, `support.md`: main pages.
- `404.html`: not-found page.
- `CNAME`: custom domain for GitHub Pages.
- `DOMAIN_SETUP.md`: domain setup notes.
- `Gemfile`: Ruby/Jekyll dependencies.
- `README.md`: this file.
- `favicon.ico`: browser/search fallback icon.
- `preview*.html`: local preview pages, ignored by Git.

Folders:

- `.github/`: GitHub Actions deployment workflow.
- `_data/`: navigation and publication data.
- `_includes/`: reusable header and footer pieces.
- `_layouts/`: page templates.
- `_people/`: lab member and alumni records.
- `_posts/`: news posts.
- `assets/`: CSS, images, icons, logos, and publication thumbnails.

## Preview Locally

```bash
bundle install
bundle exec jekyll serve
```

Then open `http://127.0.0.1:4000`.

## Publish

Push changes to `main`. GitHub Actions builds and deploys the site.

For domain notes, see `DOMAIN_SETUP.md`.
