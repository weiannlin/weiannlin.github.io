# Wei-Ann Lin Academic Website

This repository contains the source for [weiannlin.github.io](https://weiannlin.github.io), the academic website of Wei-Ann Lin.

The site began from the Academic Pages template and has since been customized into a personal academic website with a journal-like visual identity, bilingual academic profile pages, teaching materials, notes, and interactive probability/statistics demos.

This README is a repository overview. It is not part of the public site navigation.

## Site Structure

The public website is organized around the following sections.

- **Home and About** introduce academic background, research interests, and selected industrial collaboration areas.
- **Biography** gives a structured academic profile.
- **Publications** collects journal articles, conference papers, and related research outputs.
- **Talks** records invited talks, conference talks, contributed presentations, and scheduled talks.
- **Courses** lists teaching-related course pages.
- **Teaching Topics** hosts topic-based web articles, currently centered on probability theory and statistical foundations.
- **Demos** provides interactive demonstrations linked to selected teaching topics.
- **Notes** replaces the earlier generic blog role and is used for research notes, project updates, and software-development progress.

## Teaching Topics

Teaching Topics is the main long-term teaching component of the site. Articles are written as concise web versions of lecture material rather than direct lecture-note copies. The goal is to keep mathematical definitions, theorems, examples, and proof ideas while making each topic readable as a standalone webpage.

The current probability sequence is organized by chapter and topic. Chapter 1 covers random experiments, sample spaces, events, event families, probability assignment, probability rules, conditional probability, total probability, Simpson's paradox, Bayes' rule, and independence. Chapter 2 is planned to begin with random variables and distribution functions.

The writing direction is to connect rigorous probability/statistics content with modern examples and interactive demos whenever the interaction genuinely clarifies the mathematics.

## Demos

Interactive demos are kept as focused teaching companions, not as standalone games. Current demos include PMF to CDF, PDF to CDF, mixed distributions, the Monty Hall problem, Bayesian updating for rapid tests, and Simpson's paradox mixing.

Most demos are implemented as page-local HTML, CSS, and JavaScript inside `_pages/demos-*.md`, so they can be revised together with the corresponding explanatory page.

## Repository Layout

- `_pages/` contains top-level pages such as Home, About, Talks, Courses, Notes, Teaching Topics, and Demos.
- `_teaching_topics/` contains topic-based teaching articles.
- `_biography/`, `_courses/`, `_publications/`, and `_talks/` contain collection entries.
- `_layouts/` and `_includes/` contain Jekyll layouts and reusable Liquid fragments.
- `_sass/`, `assets/`, and `images/` contain styling, scripts, fonts, figures, and site images.
- `files/` contains downloadable PDFs, slides, BibTeX files, and related public files.
- `markdown_generator/` contains legacy Academic Pages helper scripts retained from the original template.

## Editing Principles

- Preserve the site's journal-like visual style, including cream paper background, brick-red accents, restrained rules, and serif typography.
- Keep Teaching Topics concise enough for web reading but mathematically precise enough to support serious course use.
- Use demos only when the interaction improves understanding.
- Keep unpublished drafts marked as unpublished until they are ready for the public Teaching Topics index.
- Avoid committing generated `_site/` files.

## Template Lineage

This site began from [Academic Pages](https://academicpages.github.io/), which is based on Minimal Mistakes. The current repository has been substantially customized for Wei-Ann Lin's academic profile, teaching materials, and interactive probability/statistics content.
