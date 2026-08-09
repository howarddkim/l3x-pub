# l3x-pub

Marketing site for **L3X** — served by GitHub Pages at **https://l3x.info**.

Moved out of the app repo (`howarddkim/l3x`, formerly `nexus/website/`) so the site
can be published and iterated on without touching the Flutter build.

## Layout

```
index.html      landing page — "Boarding Pass" concept
privacy.html    privacy policy          ─┐ the document sheet:
terms.html      terms of service        ─┘ legal copy printed on bone
css/site.css    SHARED — palette tokens, base type, nav, footer, document sheet
assets/         app_icon.png (+ favicon/touch sizes), l3x_macro/meso/micro.png
favicon.ico     32 + 64 px, so the browser's root probe resolves
CNAME           l3x.info — GitHub Pages custom domain
.nojekyll       serve files as-is, no Jekyll build step
```

Every page is the tarmac / boarding-pass design that matches the shipping app —
tarmac black `#0b0c0e`, bone `#f2efe9`, signal amber `#ffb100`; Archivo display +
IBM Plex Mono for data.

**`css/site.css` is the single source of truth** for the palette, page chrome and
the document sheet. Page-specific styling stays inline in the page that needs it
(`index.html` keeps its hero, boarding pass and departures board). Change a colour
once, in `site.css` — do not fork these rules into a page.

On a bone surface, raw amber and red wash out, so printed documents use the
AA-contrast variants `--amber-ink` and `--stamp-red`. Same rule the app follows.

`assets/app_icon.png` is the shipping iOS app icon (1024², from
`nexus/ios/Runner/Assets.xcassets/AppIcon.appiconset/`). **If the app icon changes,
re-copy it and regenerate the derived sizes:**

```bash
sips -Z 180 assets/app_icon.png --out assets/apple-touch-icon.png
sips -Z 64  assets/app_icon.png --out assets/favicon-64.png
sips -Z 32  assets/app_icon.png --out assets/favicon-32.png
```

## The retired design

The original glassmorphism site — landing page, pre-re-skin legal pages, its
stylesheet, script and art — is preserved verbatim on the **`archive/glassmorphism`**
branch, which Pages does not serve. See `ARCHIVE.md` there.

```bash
git checkout archive/glassmorphism
```

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
