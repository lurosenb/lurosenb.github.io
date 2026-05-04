# Changelog

## 2026-05-04 - Site Cleanup

Major cleanup to reduce file bloat from the al-folio template and remove pages that should no longer be indexed by search engines.

### Removed - Template Example Content

- **`_backup_posts/`** (entire directory, 10 files) - Template demo posts (formatting, images, code, comments, math, distill, github-metadata, twitter, diagrams, redirect) that were never part of the live site.

### Removed - Template Placeholder Images

- `assets/img/1.jpg` through `12.jpg` - Numbered gallery placeholder images from template.
- `assets/img/al-folio-preview.png` - Template README screenshot.
- `assets/img/prof_pic.jpg` - Template default profile picture (site uses `lucas_photo.jpeg`).
- `assets/img/code-screenshot.png`, `distill-screenshot.png`, `math-screenshot.png`, `photos-screenshot.png`, `projects-screenshot.png`, `publications-screenshot.png` - Template demo screenshots.
- `assets/img/publication_preview/brownian-motion.gif`, `wave-mechanics.gif` - Template physics animation previews.
- `assets/img/pagespeed.svg` - Template README badge.

### Removed - Template Data Files

- `_data/cv.yml` - Contained Albert Einstein example CV data, not real content.
- `_data/coauthors.yml` - Contained template coauthors (Einstein, Schrodinger, etc.).

### Removed - Template Asset Files

- `assets/bibliography/2018-12-22-distill.bib` - Bibliography for removed template distill post.
- `assets/pdf/example_pdf.pdf` - Template example PDF.

### Removed - Outdated Files

- `assets/pdf/lucas_rosenblatt_cv_2023.pdf` - Superseded by October 2025 CV.
- `assets/pdf/lucas_rosenblatt_cv_may_2025.pdf` - Superseded by October 2025 CV.

### Removed - Unused Pages

- `_pages/teaching.md` - Teaching content is now on the about/home page. The `/teaching/` URL was being indexed by Google despite `nav: false`.
- `_pages/dropdown.md` - Entirely commented out, served no purpose.
- `_archive/` (entire directory) - Contained `cv.md` (using template Einstein data with `nav: true`), `repositories.md` (fully commented out), and `cartoons.md` (unused standalone HTML page).

### Removed - Template Infrastructure Files

- `Dockerfile`, `docker-compose.yml`, `docker-local.yml` - Docker setup for template development, not needed for GitHub Pages deployment.
- `.github/workflows/deploy-docker-tag.yml` - Docker Hub tag publishing workflow (template maintainer use only).
- `.github/workflows/deploy-image.yml` - Docker image CI workflow (template maintainer use only).
- `.github/FUNDING.yml`, `.github/ISSUE_TEMPLATE/`, `.github/stale.yml` - Template project management files.
- `bin/` (entire directory) - Template helper scripts (docker builds, deploys).
- `CONTRIBUTING.md` - Template contributing guide.
- `.all-contributorsrc` - Template contributors list.

### Updated - Configuration

- **`_config.yml`**: Removed unused plugins (`jekyll-diagrams`, `jekyll-twitter-plugin`, `jemoji`, `jekyll-imagemagick`), removed `imagemagick` and `jekyll-diagrams` config sections, removed deprecated `uglifier_args.harmony` option.
- **`Gemfile`**: Removed corresponding gems (`jekyll-diagrams`, `jekyll-twitter-plugin`, `jemoji`, `jekyll-imagemagick`, `mini_racer`).
- **`robots.txt`**: Added `Disallow` rules for `/teaching/`, `/cv/`, and `/repositories/` to signal search engines to stop indexing these removed pages.
- **`README.md`**: Replaced 30KB template README with a brief site-specific one.

### Kept (intentionally)

- All `_news/` items (27 active news entries).
- Both blog posts (`bus`, `cf-is-dp`).
- Distill layout, JS, and SCSS (used by the `cf-is-dp` blog post).
- `_pages/hidden.md` (personal reference page, already has `noindex`/`sitemap: false`).
- `_pages/projects.md` and `_pages/publications.md`.
- All real images: `schoolbus/`, `cfisdp/`, `lucas_photo.jpeg`, `lil_guy.png`, and publication previews.
- `_data/repositories.yml` and `_data/venues.yml` (actively used).
- `.github/workflows/deploy.yml` (the actual GitHub Pages deploy workflow).
