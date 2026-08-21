# jukebox03.github.io

Personal academic site of **Junseop Byun** — Computer Science and Engineering, Seoul National University.

Live at **<https://jukebox03.github.io>**.

Built on the [al-folio](https://github.com/alshedivat/al-folio) Jekyll starter (MIT).

## Editing

| To change | Edit |
| --- | --- |
| Front page bio | `_pages/about.md` |
| A project | `_projects/*.md` |
| The CV page | `_data/cv.yml` |
| The CV PDF | replace `assets/pdf/CV_JunseopByun.pdf` |
| Contact links | `_data/socials.yml` |
| GitHub cards | `_data/repositories.yml` |

Push to `main` and GitHub Actions builds the site to the `gh-pages` branch, which GitHub Pages serves. A deploy takes roughly two minutes.

See [`AGENTS.md`](AGENTS.md) for the full layout and the `baseurl` caveat.
