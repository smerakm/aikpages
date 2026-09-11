# AIKPages

Static navigation site for AIK Innebandy P2012/P2013, published with GitHub Pages at
https://smerakm.github.io/aikpages/ (lowercase — the capitalised URL 404s).

## Layout

```
index.html              hub: Planeringsark / Kalender / Träning / Taktik / Itelligence
assets/site.css         shared shell for every nav page
assets/aik-logo.png     club crest, vendored (do not hotlink the CDN)
taktik/  training/  itelligence/    section pages, each an index.html
itelligence/pojkar-20{12,13}-*.html  pre-existing data tables — own theme, leave alone
training/ovningar.html  övningsbank — partly generated, see below
assets/ovningar/        exercise schemas, copied out of .trainingFiles by the generator
tools/build_ovningar.py generator for training/ovningar.html
.trainingFiles/         source of truth for the exercises — gitignored, never published
```

## Övningar

`training/ovningar.html` is generated from `.trainingFiles/`, one subfolder per exercise
holding a `description.md` (H1 name, image link, `## Flags ##`, `## Description ##`) and
its schema image. `.trainingFiles/config.md` lists the valid categories.

```
python3 tools/build_ovningar.py           # rewrite the page, sync assets/ovningar/
python3 tools/build_ovningar.py --check    # exit 1 if the page is out of date
```

The script rewrites only the regions between `<!-- BEGIN:toc -->`, `<!-- BEGIN:chips -->`
and `<!-- BEGIN:cards -->` markers — the CSS, the filter JS and the prose around them are
hand-edited in that file as usual. It refuses to write if an exercise names a category
missing from `config.md` or points at a missing image.

Because `.trainingFiles/` is gitignored, the images it copies into `assets/ovningar/` are
the only ones Pages ever sees; the script also deletes assets whose exercise is gone.
It applies two display-only transforms: a capital first letter and an en dash in the
heading. Everything else is verbatim, so fix the Swedish in `description.md`, not in HTML.

## Conventions

- Swedish UI text, written with HTML entities (`&auml;` `&ouml;` `&aring;`), not literal characters.
- Nav pages share `assets/site.css` (`../assets/site.css` from a subfolder). No dark mode —
  the gold `#af9664` background is a fixed brand choice.
- Internal links name the file (`taktik/index.html`, not `taktik/`) so the site works from
  disk and from Pages alike.
- External links get `target="_blank" rel="noopener"`.
- Google Drive links carry a `Behörighet krävs` badge and a padlock icon instead of an
  arrow. That is signalling only — access control is Google's.
- `.nojekyll` is intentional; Pages serves the tree verbatim.

## Note

The repo is public, so the Google Sheet/Slides URLs are readable in page source. The
documents stay permission-gated, but don't add links that shouldn't be discoverable.
