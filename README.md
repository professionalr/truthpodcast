# The Truth Podcast — truth-podcast.com

Static site for The Truth Podcast. No build step, no dependencies, no framework.
Open `index.html` in a browser and it runs.

## Files

```
index.html          entire site — all six pages, styles and scripts
CNAME               custom domain for GitHub Pages
.nojekyll           tells Pages to serve files as-is
robots.txt
sitemap.xml
assets/
  logo.jpg          680px logo — hero, page headers, footer
  logo-mark.png     150px mark — header, apple-touch-icon
  favicon.ico       multi-size favicon
  og-cover.jpg      1200x630 social share card
```

## Pages

Routing is hash-based, so every page is one file and GitHub Pages serves it
without any 404 rewrite rules.

| Route | Page |
|---|---|
| `#/` | Home — hero, episode log, articles, platforms |
| `#/episodes` | Full episode log |
| `#/articles` | Articles |
| `#/mirrors` | BitChute / Brighteon mirrors |
| `#/quest` | $QUEST token |
| `#/subscribe` | Platforms + contact |

## Editing content

All content lives in three arrays at the bottom of `index.html`.
Add an episode by adding one line — the page rebuilds itself.

```js
const EPISODES = [ {t:"Title", src:"Rumble", u:"https://..."}, ... ];
const ARTICLES = [ {t:"Title", d:"Aug 9, 2023", r:"8 min", u:"https://..."}, ... ];
const FEED     = [ {n:"Spotify", k:"Audio", u:"https://..."}, ... ];
```

Episodes are numbered automatically from the length of the array, newest first.

## Brand tokens

Taken from the logo artwork. Defined once in `:root`.

| Token | Value | Use |
|---|---|---|
| `--void` | `#000000` | Page background — matches the logo's own background |
| `--volt` | `#76FB04` | Primary green |
| `--volt-dim` | `#4FBE03` | Mid green |
| `--moss` | `#1C6800` | Deep green, dividers |
| `--rule` | `#1D2A19` | Green-tinted hairlines |
| `--paper` | `#E6E9E5` | Body text |
| `--dim` | `#778573` | Secondary text |

Type: Archivo (display, expanded weights), IBM Plex Sans (body), IBM Plex Mono (labels).
Major headings use the `.chrome` class — a gradient-clipped metallic fill matching
the logo's lettering.

## Deploying

1. Push to `main`.
2. Settings → Pages → Source: `main`, folder `/ (root)`.
3. Settings → Pages → Custom domain: `truth-podcast.com` → Save.
4. Wait for the certificate, then tick **Enforce HTTPS**.

DNS at your registrar:

```
A     @     185.199.108.153
A     @     185.199.109.153
A     @     185.199.110.153
A     @     185.199.111.153
CNAME www   professionalr.github.io
```

## Open TODOs

- [ ] Mirror titles on `#/mirrors` are placeholders
- [ ] `$QUEST` page is structure only — no contract address, chain, supply or date
- [ ] Add a risk / not-financial-advice disclaimer before `$QUEST` goes live
- [ ] Article links still point at the old Wix posts — migrate or keep redirecting
- [ ] Replace `hello@truth-podcast.com` with the real inbox
