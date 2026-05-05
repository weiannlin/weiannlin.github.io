# Wei-Ann Lin Academic Website

This repository contains the source for [weiannlin.github.io](https://weiannlin.github.io), the academic website of Wei-Ann Lin.

The site is built with Jekyll and GitHub Pages, based on the Academic Pages template and customized for a journal-like visual identity: cream paper background, brick-red accents, serif typography, academic profile pages, teaching materials, and interactive statistics demos.

## Project Focus

The site currently serves four main purposes:

- Present biography, publications, talks, courses, and contact information.
- Host course and teaching pages for statistics, computer experiments, and Gaussian-process methodology.
- Develop short Teaching Topics articles designed for web reading.
- Pair selected teaching articles with interactive demos that make statistical concepts visible.

## Important Directories

- `_pages/`: top-level site pages, including the homepage, demos, publications, talks, courses, and archive pages.
- `_biography/`: biography collection content.
- `_courses/`: course pages.
- `_publications/`: publication entries.
- `_talks/`: talk and presentation entries.
- `_teaching_topics/`: longer teaching articles. Some entries may be unpublished while under development.
- `_layouts/`: Jekyll layouts, including the custom `topic` layout for Teaching Topics.
- `_includes/`: reusable Liquid fragments.
- `_sass/`: site styling, including the custom journal aesthetic.
- `assets/`: CSS, JavaScript, fonts, and webfont assets.
- `images/`: site images, profile images, favicons, and screenshots.
- `files/`: downloadable PDFs, slides, and BibTeX files.
- `markdown_generator/`: legacy Academic Pages helper scripts and notebooks for generating markdown entries.

## Current Content Direction

The near-term direction is to turn existing lecture material into concise, polished web articles under Teaching Topics. These articles should be readable on their own, but also connect to interactive demos where useful.

The first visible thread is probability accumulation:

- PMF to CDF
- PDF to CDF
- Mixed distributions

Future topics are expected to include foundational ideas in statistics, computer experiments, and Gaussian processes.

## Local Development

Install Ruby dependencies:

```bash
bundle install
```

Serve locally:

```bash
bundle exec jekyll serve -l -H localhost
```

The site will be available at:

```text
http://localhost:4000
```

If dependencies need to be installed locally instead of system-wide:

```bash
bundle config set --local path 'vendor/bundle'
bundle install
```

## Docker Development

The repository also includes a Docker setup inherited from Academic Pages:

```bash
docker compose up
```

The development server should then be available at `localhost:4000`.

## JavaScript Assets

The source JavaScript file is:

```text
assets/js/_main.js
```

The minified bundle is:

```text
assets/js/main.min.js
```

To rebuild the minified bundle after JavaScript changes:

```bash
npm install
npm run build:js
```

Many interactive demo pages currently use page-local HTML, CSS, and JavaScript inside `_pages/demos-*.md`.

## Publishing Workflow

Typical update flow:

```bash
git status
bundle exec jekyll build
git add <changed-files>
git commit -m "Describe the update"
git push origin master
```

GitHub Pages builds the public site from the `master` branch.

## Notes For Future Editing

- Keep the journal aesthetic consistent: cream background, brick-red accent, serif type, restrained rules, and clean academic spacing.
- Prefer Teaching Topics that are shorter than lecture notes but richer than a glossary entry.
- Use interactive demos to explain a concept only when the interaction clarifies the mathematics.
- Clean up inherited Academic Pages sample content gradually when it is no longer needed.
- Avoid committing generated `_site/` changes unless the deployment strategy changes.

## Template Lineage

This site began from [Academic Pages](https://academicpages.github.io/), itself based on Minimal Mistakes. The current repository has been customized substantially for Wei-Ann Lin's academic profile and teaching materials.
