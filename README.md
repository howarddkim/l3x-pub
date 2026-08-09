# l3x-pub

Marketing site for **L3X** — served by GitHub Pages at **https://l3x.info**.

Moved out of the app repo (`howarddkim/l3x`, formerly `nexus/website/`) so the site
can be published and iterated on without touching the Flutter build.

## Layout

```
index.html      landing page — "Boarding Pass" concept, self-contained <style> block
privacy.html    privacy policy
terms.html      terms of service
css/styles.css  styles for privacy + terms only (index.html carries its own)
js/main.js      nav/scroll behaviour for privacy + terms
assets/         app_logo.jpg, l3x_macro.png, l3x_meso.png, l3x_micro.png
CNAME           l3x.info — GitHub Pages custom domain
.nojekyll       serve files as-is, no Jekyll build step
```

`index.html` is the tarmac / boarding-pass design that matches the shipping app
(tarmac black `#0b0c0e`, bone `#f2efe9`, signal amber `#ffb100`; Archivo display +
IBM Plex Mono data). The earlier glassmorphism landing page was retired in the move,
along with its unused art (`hero.png`, `logo.png`, `watch.png`).

**Known mismatch:** `privacy.html` and `terms.html` still wear the retired
glassmorphism design (Inter/Outfit via `css/styles.css`). They need a tarmac
re-skin to match `index.html`.

## Deploying

Push to `main`. GitHub Pages builds from the branch root — there is no build step.

## Local preview

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000.

## DNS (apex domain, at the registrar)

`l3x.info` is an apex domain, so it needs A/AAAA records — not a CNAME:

| Type | Name | Value |
| --- | --- | --- |
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |
| AAAA | `@` | `2606:50c0:8000::153` |
| AAAA | `@` | `2606:50c0:8001::153` |
| AAAA | `@` | `2606:50c0:8002::153` |
| AAAA | `@` | `2606:50c0:8003::153` |
| CNAME | `www` | `howarddkim.github.io.` |

Once the records resolve, GitHub issues the Let's Encrypt certificate automatically
and **Enforce HTTPS** can be switched on in Settings → Pages.
