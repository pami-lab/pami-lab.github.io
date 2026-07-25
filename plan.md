## Plan: PAMI Lab Site Migration

Convert the existing personal al-folio site into a lab-centered website with seven core pages (Home, Projects, Publications, Members, Grants, Teaching, Collaborations), while preserving low-maintenance update flows. Reuse existing publication and news pipelines, add structured data files for Members and Grants, and keep Collaborations simple via Markdown.

**Steps**
1. Phase 1 - Home and navigation foundation
2. Update site identity fields in /workspaces/ntcuong2103.github.io/_config.yml (title/description/contact wording) for PAMI Lab branding.
3. Add a dedicated home layout at /workspaces/ntcuong2103.github.io/_layouts/lab_home.html by reusing the same rendering patterns from about layout (profile + content + news include), but with lab-focused sections and explicit news block. This keeps Home independent from personal CV/about semantics.
4. Rewrite /workspaces/ntcuong2103.github.io/_pages/about.md as the Home page content (permalink /) for PAMI Lab and enable homepage news rendering via front matter flags expected by the chosen layout. Depends on step 3.
5. Normalize top navigation to lab scope by setting nav and nav_order in page front matter so menu order is Home, Projects, Publications, Members, Grants, Teaching, Collaborations. Hide CV and Repositories from top menu by setting nav false in their page front matter (pages remain reachable by URL). Can run in parallel with step 4 once page targets are finalized.

6. Phase 2 - Lab content pages and maintainable data
7. Members page: create /workspaces/ntcuong2103.github.io/_data/members.yml with grouped sections for PI, Current Students (grouped by level), and Alumni (grouped by Master/Bachelor), plus fields for Name and Personal Page (current students) and Name/Thesis Title/Graduation Year (alumni).
8. Members rendering: create /workspaces/ntcuong2103.github.io/_pages/members.md and render grouped tables from members.yml using Liquid loops; keep table schema simple and explicit so updates are data-only. Depends on step 7.
9. Grants page: create /workspaces/ntcuong2103.github.io/_data/grants.yml as dedicated structured records and create /workspaces/ntcuong2103.github.io/_pages/grants.md that renders entries in a table or compact cards. This decouples lab grants from CV formatting. Can run in parallel with steps 7-8.
10. Collaborations page: create /workspaces/ntcuong2103.github.io/_pages/collaborations.md as plain Markdown list sections (institutions, industry, international partners), intentionally no YAML to keep editing friction minimal.
11. Teaching page: keep /workspaces/ntcuong2103.github.io/_pages/teaching.md and refactor text to lab-facing course/supervision wording while preserving simple Markdown table updates.
12. Projects and Publications pages: keep existing pipeline and update descriptive text/front matter only as needed. Projects remain collection-driven from /workspaces/ntcuong2103.github.io/_projects/*.md; Publications remain bib-driven from /workspaces/ntcuong2103.github.io/_bibliography/papers.bib and /workspaces/ntcuong2103.github.io/_pages/publications.md.

13. Phase 3 - Workflow guarantees and verification
14. Add short maintainer notes in /workspaces/ntcuong2103.github.io/README.md (or a dedicated lab-maintenance section) documenting update rules:
15. News update flow: add a markdown file in /workspaces/ntcuong2103.github.io/_news/.
16. Publication update flow: add/update entry in /workspaces/ntcuong2103.github.io/_bibliography/papers.bib and adjust /workspaces/ntcuong2103.github.io/_pages/publications.md only if grouping/filter rules need edits.
17. Members update flow: edit /workspaces/ntcuong2103.github.io/_data/members.yml.
18. Grants update flow: edit /workspaces/ntcuong2103.github.io/_data/grants.yml.
19. Collaborations/Teaching update flow: edit corresponding markdown page.
20. Verify local build and navigation behavior with existing local Jekyll workflow to ensure all new pages render and table data displays correctly.

**Relevant files**
- /workspaces/ntcuong2103.github.io/_config.yml — site identity and collection/menu behavior dependencies.
- /workspaces/ntcuong2103.github.io/_includes/header.html — reference for nav ordering and nav flag behavior.
- /workspaces/ntcuong2103.github.io/_layouts/about.html — reusable pattern for profile/content/news structure.
- /workspaces/ntcuong2103.github.io/_includes/news.html — existing news rendering include for homepage and /news page.
- /workspaces/ntcuong2103.github.io/_pages/about.md — home content source at permalink /.
- /workspaces/ntcuong2103.github.io/_pages/publications.md — publication rendering by year via jekyll-scholar.
- /workspaces/ntcuong2103.github.io/_bibliography/papers.bib — publication source of truth.
- /workspaces/ntcuong2103.github.io/_pages/projects.md — projects landing page using collection includes.
- /workspaces/ntcuong2103.github.io/_projects/ — project entry files.
- /workspaces/ntcuong2103.github.io/_pages/teaching.md — existing teaching page to retain.
- /workspaces/ntcuong2103.github.io/_data/members.yml — new structured members source.
- /workspaces/ntcuong2103.github.io/_data/grants.yml — new structured grants source.
- /workspaces/ntcuong2103.github.io/_pages/members.md — new members page.
- /workspaces/ntcuong2103.github.io/_pages/grants.md — new grants page.
- /workspaces/ntcuong2103.github.io/_pages/collaborations.md — new collaborations page.
- /workspaces/ntcuong2103.github.io/README.md — maintenance instructions for future updates.

**Verification**
1. Run local Jekyll build/serve using the repository’s documented workflow and confirm no build errors.
2. Confirm top navigation shows exactly: Home, Projects, Publications, Members, Grants, Teaching, Collaborations; CV and Repositories absent from menu.
3. Confirm Home page renders latest news items from /workspaces/ntcuong2103.github.io/_news/ and links to /news/ entries as expected.
4. Add one temporary test news markdown item in _news and verify it appears, then remove it.
5. Add one temporary test BibTeX entry in papers.bib and verify it appears in Publications under the intended year grouping, then remove it.
6. Edit one member record in members.yml and verify page updates without template edits.
7. Edit one grant record in grants.yml and verify page updates without template edits.
8. Spot-check mobile layout for members/grants tables to ensure readability (Bootstrap table-responsive where needed).

**Decisions**
- Dedicated lab home layout will be created (not reusing default about layout directly).
- Members will be maintained in YAML and displayed as grouped tables.
- Current Students will show Name and Personal Page, grouped by level.
- Alumni will show Name, Thesis Title, Graduation Year, grouped by Master/Bachelor.
- Grants will use dedicated /_data/grants.yml.
- Collaborations will be a simple markdown-maintained page.
- CV and Repositories will be hidden from top navigation but not deleted.

**Further Considerations**
1. Members grouping format recommendation: Option A keeps explicit groups in YAML (most readable for manual editing), Option B stores flat rows with level/type tags (easier to filter/sort in Liquid).
2. Publications grouping recommendation: keep current fixed years list initially for stable display, then optionally auto-generate year headings later if publication volume grows.
3. Home visual depth recommendation: keep layout changes structural and content-first now; defer major styling/theme redesign to a separate pass to reduce migration risk.