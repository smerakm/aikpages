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
```

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
