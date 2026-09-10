# AIK P2012 / P2013

Statiska sidor för AIK Innebandy P2012 och P2013 — planering, taktik och serietabeller
från Stockholms IBF. Publiceras med GitHub Pages.

## Struktur

```
index.html                                    Startsida med navigering
assets/site.css                               Gemensam stil för navigeringssidorna
assets/aik-logo.png                           AIK:s klubbmärke (används på startsidan)
taktik/index.html                             Taktik — navigering
training/index.html                           Träning — navigering
itelligence/index.html                        Itelligence — navigering
itelligence/pojkar-2012-stockholm-2025-26.html  Alla 8 Pantamera-serier P2012, 2025/26
itelligence/pojkar-2013-stockholm-2025-26.html  Alla 7 Pantamera-serier P2013, 2025/26
```

Alla interna länkar är relativa och pekar på `index.html` explicit, så sidorna fungerar
både direkt från disk (`file://`) och via GitHub Pages.

## Lägga till en sida

Kopiera kortmallen som ligger i kommentar i `taktik/index.html` och länka den nya filen
från rätt navigeringssida. Nya sidor länkar in `assets/site.css` (`../assets/site.css`
från en undermapp) för att matcha resten.

## Publicera

```sh
git init && git add . && git commit -m "AIK P2012/P2013 pages"
gh repo create AIKPages --public --source=. --push
```

Aktivera sedan Pages på `main` / root i repots inställningar. Sidan hamnar på
`https://<användarnamn>.github.io/AIKPages/`.
