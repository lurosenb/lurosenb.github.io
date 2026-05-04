# Site Cleanup Plan

This plan identifies unnecessary files from the al-folio template that are unused by the live site, and outlines removals + config updates to reduce file bloat and fix SEO/indexing issues.

## Current Site Structure

**Active pages** (actually used):
- `_pages/about.md` - Homepage (`/`), contains all key content (bio, teaching, publications list, awards, service)
- `_pages/publications.md` - `/publications/` (nav: false, linked from about)
- `_pages/projects.md` - `/projects/` (nav: false)
- `_pages/hidden.md` - `/hidden/` (personal reference, already has noindex/sitemap:false)
- `_posts/` - 2 real blog posts (bus, cf-is-dp)
- `_news/` - 27 news items (all actively used)
- `_bibliography/papers.bib` - Publication data
- `blog/index.html` - Blog listing page

**Inactive/template pages** (to remove):
- `_pages/teaching.md` - Content is now on about page; generates orphan `/teaching/` URL that Google indexes
- `_pages/dropdown.md` - Fully commented out, serves no purpose
- `_archive/cv.md` - Has `nav: true` referencing `example_pdf.pdf` (template); CV is now a direct PDF link from about page
- `_archive/repositories.md` - Fully commented out
- `_archive/cartoons.md` - Standalone HTML page, not a Jekyll page, unused

---

## Phase 1: Remove Template Bloat Files

### 1a. Template example posts (`_backup_posts/`)
All 10 files are al-folio template demos, not real content:
- `2015-03-15-formatting-and-links.md`
- `2015-05-15-images.md`
- `2015-07-15-code.md`
- `2015-10-20-comments.md`
- `2015-10-20-math.md`
- `2018-12-22-distill.md`
- `2020-09-28-github-metadata.md`
- `2020-09-28-twitter.md`
- `2021-07-04-diagrams.md`
- `2022-02-01-redirect.md`

**Action:** Delete entire `_backup_posts/` directory.

### 1b. Template example images (`assets/img/`)
Numbered placeholder images and template screenshots:
- `1.jpg` through `12.jpg` (template gallery examples)
- `al-folio-preview.png` (template README preview)
- `code-screenshot.png`, `distill-screenshot.png`, `math-screenshot.png`, `photos-screenshot.png`, `projects-screenshot.png`, `publications-screenshot.png` (template demo screenshots)
- `prof_pic.jpg` (template default profile pic; site uses `lucas_photo.jpeg`)
- `publication_preview/brownian-motion.gif`, `publication_preview/wave-mechanics.gif` (template physics demo previews)
- `pagespeed.svg` (template README badge)

**Action:** Delete these files. Keep all `schoolbus/`, `cfisdp/`, `lucas_photo.jpeg`, `lil_guy.png`, and real `publication_preview/` images.

### 1c. Template data files
- `_data/cv.yml` - Contains Albert Einstein example data, not Lucas's CV
- `_data/coauthors.yml` - Contains template coauthors (Einstein, Schrodinger, etc.)

**Action:** Delete both files. The CV page referencing cv.yml is being removed. Coauthors could be re-added later with real data if needed.

### 1d. Template asset files
- `assets/bibliography/2018-12-22-distill.bib` - Bib for template distill post
- `assets/pdf/example_pdf.pdf` - Template example PDF

**Action:** Delete both.

### 1e. Outdated PDFs
- `assets/pdf/lucas_rosenblatt_cv_2023.pdf` - Superseded by oct 2025 version
- `assets/pdf/lucas_rosenblatt_cv_may_2025.pdf` - Superseded by oct 2025 version

**Action:** Delete outdated CVs. Keep only `lucas_rosenblatt_cv_october_2025.pdf`.

### 1f. Docker/CI files (template infrastructure)
- `Dockerfile` - For template development, not needed for GH Pages deploy
- `docker-compose.yml` - Same
- `docker-local.yml` - Same
- `.github/workflows/deploy-docker-tag.yml` - Docker Hub publishing (template maintainer use)
- `.github/workflows/deploy-image.yml` - Docker image CI (template maintainer use)
- `.github/FUNDING.yml` - Template funding links
- `.github/ISSUE_TEMPLATE/` - Template issue templates
- `.github/stale.yml` - Template stale bot config
- `bin/` - Template helper scripts (docker_build_image.sh, etc.)

**Action:** Delete all. Keep only `.github/workflows/deploy.yml` (the actual site deploy).

### 1g. Template meta files
- `CONTRIBUTING.md` - Template contributing guide
- `.all-contributorsrc` - Template contributors list
- `README.md` - 30KB template README (replace with minimal site README)

**Action:** Delete `CONTRIBUTING.md` and `.all-contributorsrc`. Replace `README.md` with a brief one.

---

## Phase 2: Remove Unused Pages

### 2a. Teaching page
- `_pages/teaching.md` generates `/teaching/` which Google indexes
- All teaching info is already on the about page

**Action:** Delete file. Add `/teaching/` to robots.txt disallow.

### 2b. Dropdown page
- `_pages/dropdown.md` - Entirely commented out

**Action:** Delete file.

### 2c. Archive directory
- `_archive/cv.md` - References template data, `nav: true` means it shows in nav
- `_archive/repositories.md` - Entirely commented out
- `_archive/cartoons.md` - Unused standalone HTML

**Action:** Delete entire `_archive/` directory.

---

## Phase 3: Configuration Updates

### 3a. `_config.yml` updates
- Remove `jekyll-diagrams` from plugins (only used by removed template posts)
- Remove `jekyll-twitter-plugin` from plugins (unused)
- Remove `jemoji` from plugins (unused)
- Remove `jekyll-imagemagick` from plugins (disabled anyway: `enabled: false`)
- Clean up `collections` if needed

### 3b. `Gemfile` updates
- Remove gems matching removed plugins

### 3c. `robots.txt` updates
- Add `Disallow: /teaching/` to prevent further indexing
- Add `Disallow: /cv/` to prevent further indexing

### 3d. Replace `README.md`
- Brief description of site and how to build locally

---

## Phase 4: Test Locally
- Install Ruby 3.2.x + Bundler
- `bundle install`
- `bundle exec jekyll serve`
- Verify homepage, publications, projects, blog, news all render correctly

---

## Phase 5: Document Changes
- Write `CHANGELOG.md` listing all removals and updates
