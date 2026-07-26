# PAMI Lab website

This repository contains the website for the Pattern Analysis and Machine Intelligence (PAMI) Lab at Vietnamese-German University. It is a Jekyll site hosted on GitHub Pages.

## Updating the website

Most updates only require editing Markdown or YAML files. After editing, commit the changes and push them to `master`; GitHub Actions builds and deploys the site automatically.

| What you want to change | Edit |
| --- | --- |
| Home page text | [`_pages/about.md`](_pages/about.md) |
| Members and alumni | [`_data/members.yml`](_data/members.yml) |
| Grants | [`_data/grants.yml`](_data/grants.yml) |
| Teaching | [`_pages/teaching.md`](_pages/teaching.md) |
| Collaborations | [`_pages/collaborations.md`](_pages/collaborations.md) |
| Projects | Add or edit a Markdown file in [`_projects/`](_projects/) |
| Publications | Add BibTeX entries to [`_bibliography/papers.bib`](_bibliography/papers.bib) |
| News | Add a dated Markdown file in [`_news/`](_news/) |
| Site title, links, and social profiles | [`_config.yml`](_config.yml) |

### Add a project

Create a file such as `_projects/handwritten-math.md` with front matter like this:

```yaml
---
layout: page
title: Handwritten mathematics recognition
description: A short description shown on the Projects page.
importance: 1
category: work
---
```

Write the project description below the closing `---`. Use images from `assets/img/` when needed.

### Add news

Create a file in `_news/` whose name starts with the date, for example `2026-08-01-new-award.md`:

```yaml
---
layout: post
date: 2026-08-01 09:00:00+0000
title: A short announcement title
inline: false
related_posts: false
---
```

Add the announcement text below the front matter.

### Add a publication

Add a normal BibTeX record to [`_bibliography/papers.bib`](_bibliography/papers.bib). Include the publication year and, where appropriate, `selected={true}`, `pdf`, `code`, or `url` fields. The Publications page groups records by year.

## Local preview

With Ruby and Bundler installed:

```bash
bundle install
bundle exec jekyll serve --lsi
```

Open <http://localhost:4000>. Alternatively, use Docker:

```bash
docker compose up
```

Before pushing, check the local site and make sure links, images, YAML indentation, and dates are correct. Development and contribution conventions are documented in [`AGENTS.md`](AGENTS.md).

## Repository map

- `_pages/`, `_projects/`, and `_news/` contain editable page content.
- `_data/` contains structured records used by pages.
- `_layouts/`, `_includes/`, `_sass/`, and `_plugins/` contain site presentation and Jekyll implementation.
- `assets/` contains site images, stylesheets, and JavaScript.
- `.github/workflows/` contains the deployment workflow.

## License

The site uses the al-folio theme. See [`LICENSE`](LICENSE) for the repository license.
