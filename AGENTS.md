# Agent Guidelines — jukebox03.github.io

Personal academic site of Junseop Byun, built on the [al-folio](https://github.com/alshedivat/al-folio) v1.x Jekyll starter.

## Critical: baseurl

**`baseurl` in `_config.yml` MUST stay empty.**

This site is served from `https://jukebox03.github.io` — the domain root. Upstream al-folio's own docs say the baseurl must be `/al-folio`, because *their* demo lives at `alshedivat.github.io/al-folio`. That instruction does not apply here, and following it silently breaks every stylesheet, image, and link on this site.

Build locally with a plain `bundle exec jekyll build` — never pass `--baseurl`.

## Where content lives

| What | Where |
| --- | --- |
| Front page (bio, profile photo block) | `_pages/about.md` |
| Navigation tabs | `nav:` / `nav_order:` in each `_pages/*.md` |
| Projects | `_projects/*.md` — ordered by `importance:` |
| CV (renders the `/cv/` page) | `_data/cv.yml` — `rendercv` schema |
| CV PDF download | `assets/pdf/CV_JunseopByun.pdf`, linked from `_data/socials.yml` and `_pages/cv.md` |
| Social / contact links | `_data/socials.yml` |
| GitHub cards on `/repositories/` | `_data/repositories.yml` |
| Publications | `_bibliography/papers.bib` — the tab is currently `nav: false` in `_pages/publications.md` |

Upstream's demo pages (people, teaching, bookshelf, submenus, plugins, blog) and the demo `_posts`, `_teachings`, `_books`, and bibliography entries were **deleted**, not hidden. Restore any of them from git history if wanted.

## The projects page filters by category

`site.enable_project_categories` is **on by gem default** — it is not in `_config.yml`. When `_pages/projects.md` also carries `display_categories`, the page renders one section per listed category and shows only projects whose `category:` matches. A mismatch renders empty category headings and no cards, with no error.

`display_categories` is currently removed from `_pages/projects.md`, so all projects render in one grid ordered by `importance:`. If you add it back, every value must match a `category:` used in `_projects/*.md`.

## `nav: false` hides a tab; it does not remove the page

A page with `nav: false` still builds and is still served at its permalink, and search engines can still index it. To actually retire a page, delete the file.

Deleting a page is also not always safe on its own: `_pages/profiles.md` named `about_einstein.md` in its front matter, and the gem's `profiles.liquid` layout `include`s that file by name. Deleting only `about_einstein.md` broke the build with `Could not locate the included file`. **After deleting any content file, grep the repo for its basename** — front matter in one page can reference a file in another.

## This is a thin starter, not a theme

Layouts, includes, Sass, and JavaScript live in the `al_folio_*` **gems**, not in this repo. There is deliberately no `_layouts/`, `_includes/`, or `_sass/` directory here.

To change how something *renders*, first try `_config.yml` feature flags and `_data/*.yml`. Only create a local `_layouts/` or `_includes/` override when config and content genuinely cannot express the change — an override shadows the gem and will not receive upstream fixes.

## Deployment

`.github/workflows/deploy.yml` is the only workflow. On push to `main` it builds with Jekyll and pushes `_site/` to the `gh-pages` branch, which GitHub Pages serves. Upstream's other 20-odd maintainer workflows (visual regression, CodeQL, Docker publishing, release automation) were removed — they only make sense in the al-folio repo itself. Recover any of them from git history if ever needed.

Requirements for the deploy to work, both already configured:

- Settings → Actions → General → Workflow permissions = **Read and write**
- Settings → Pages → Source = **Deploy from a branch** → `gh-pages` / `(root)`

## Local preview

Requires Ruby with DevKit. Not currently installed on the author's machine — edits are verified by pushing and letting the Action build.

```bash
bundle install
bundle exec jekyll serve   # http://localhost:4000/
```
