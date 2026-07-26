# Development guide

This file contains development and maintenance instructions for contributors. For routine content updates, start with [`README.md`](README.md).

## Scope

Keep this repository focused on the PAMI Lab website. Do not add theme demonstration content, generated output, or large media files unless the live site actually uses them.

## Content conventions

- Use UTF-8 Markdown and valid YAML front matter.
- Use ISO-style dates in news filenames and front matter.
- Keep reusable, structured information in `_data/*.yml`; keep prose in `_pages/`, `_projects/`, and `_news/`.
- Use relative Jekyll paths or `relative_url` for internal links.
- Give images descriptive filenames and store site images in `assets/img/`.
- Do not commit `_site/`, `.jekyll-cache/`, local Bundler files, or other generated output.

## Layout and theme changes

Prefer editing page content or data before changing layouts. When a layout, include, Sass file, or plugin must change, keep the change small and verify all pages that use it. Preserve the existing navigation order and the lab-focused language.

## Validation

Run the following before opening a pull request:

```bash
bundle exec jekyll build
```

For visual changes, also run `bundle exec jekyll serve --lsi` and inspect the home page, navigation, Projects, Publications, Members, Grants, Teaching, Collaborations, and News pages at desktop and mobile widths.

Check that:

- YAML and front matter parse successfully.
- Every referenced image, PDF, and link target exists or is intentionally external.
- New pages have the intended `permalink`, `nav`, and `nav_order` values.
- No demo content or generated files have been reintroduced.

## Pull requests

Use a concise title describing the content or site change. Explain which pages or data files were updated, include screenshots for visual changes, and mention the local build result.
