# antcolony10086.github.io

Personal academic website for **Jian Lu / 鲁建** — EE undergraduate at Xinjiang University, applying for graduate admission in the Agent / multimodal LLM direction.

Live site: <https://antcolony10086.github.io/>

## What's where

- `_config.yml` — global site config (name, repo, social links)
- `_pages/about.md` — homepage hero + News + summary
- `_pages/portfolio.html` + `_portfolio/*.md` — project cards (4 flagship projects)
- `_pages/publications.html` + `_publications/*.md` — paper list
- `_pages/cv.md` — full CV (markdown)
- `_pages/awards.md` — awards
- `_data/navigation.yml` — top nav (Projects / Publications / Awards / CV)
- `images/profile.png` — avatar (replace any time)
- `images/proj-*.png` — project card illustrations
- `files/lujian_cv.pdf` — downloadable CV PDF

## How to update

### Replace your CV PDF
```
cp /path/to/your/new-resume.pdf files/lujian_cv.pdf
git add files/lujian_cv.pdf && git commit -m "update CV" && git push
```

### Replace your avatar
Drop a square PNG/JPG (recommended 400×400) at `images/profile.png` and push.

### Add a project
Create a new `_portfolio/NN-name.md` (copy structure from `01-label.md`).
The `excerpt:` field's `<img>` tag is what shows on the project list page — point it to a card image under `images/`.

### Add a paper
Create `_publications/YYYY-slug.md` with `category: manuscripts` (or `conferences` / `books` per `_config.yml`).

### Replace placeholder benchmarks (`TBD`)
Search for `TBD` across the repo as benchmark numbers land:
```
grep -rn "TBD" _portfolio _pages
```

## Build / preview

GitHub Pages builds Jekyll in the cloud — **no local build is required**. Push to `main` and the site is live in 1–2 minutes.

If you want a local preview:
```
gem install bundler && bundle install
bundle exec jekyll serve
# open http://localhost:4000
```
(Requires Ruby 3.x; the system Ruby on macOS is too old.)

## Deployment

Already configured: GitHub Pages serves the `main` branch root of <https://github.com/AntColony10086/AntColony10086.github.io>.

If Pages is not enabled yet:
**Settings → Pages → Source: "Deploy from a branch" → Branch: `main` / `(root)` → Save.**

## Credits

Built on the [academicpages](https://github.com/academicpages/academicpages.github.io) Jekyll template (which is itself a fork of [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/)).
