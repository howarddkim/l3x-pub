# Archive — glassmorphism site (2026)

**This branch is not published.** GitHub Pages serves `main` only, so nothing here is
reachable from l3x.info. It exists so the retired design can be recovered if we ever
want it back.

## What this is

A verbatim snapshot of `nexus/website/` as it stood at nexus commit `42a162d`, i.e. the
last state before the site moved out to this repo. Nothing has been edited.

| File | What it is |
| --- | --- |
| `index.html` | The **glassmorphism** landing page — Inter/Outfit, frosted panels, glowing background orbs, blue/violet accents. Retired when the site moved. |
| `privacy.html`, `terms.html` | The legal pages in the same glassmorphism styling, before their tarmac re-skin. |
| `css/styles.css` | The glassmorphism stylesheet (the only thing that ever styled the pages above). |
| `js/main.js` | Nav scroll state + reveal-on-scroll for those pages. |
| `index-v2.html` | The tarmac "Boarding Pass" page as it looked pre-move. On `main` this became `index.html`. |
| `assets/hero.png`, `assets/logo.png`, `assets/watch.png` | Art used **only** by the glassmorphism landing page. Dropped from `main`; 1.9 MB. |
| `assets/app_logo.jpg`, `assets/l3x_*.png` | Still in use on `main`, kept here so this snapshot stands alone. |

## Why it was retired

The app moved to the tarmac / boarding-pass design language (tarmac black, bone, signal
amber; Archivo + IBM Plex Mono). The glassmorphism site no longer resembled the product
it was selling.

## How to get it back

```bash
git checkout archive/glassmorphism        # look at it
python3 -m http.server 8000               # or serve it locally
```

To restore a single file onto `main` without switching branches:

```bash
git checkout archive/glassmorphism -- css/styles.css
```
