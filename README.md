# portfolio

Personal portfolio site of Arthur Cesare-Herriau — a static HTML/CSS page
served via GitHub Pages.

🌐 **Live:** https://arthur.thurbeen.eu/

## Stack

- Plain HTML + CSS + a little vanilla JS (no build step, no framework)
- Doom game-UI theme ported from [thurbox.thurbeen.eu](https://thurbox.thurbeen.eu/) — warm
  charcoal, Doom-red accent, phosphor-green links, pixel bevels, HUD status bar,
  MAP-xx level dividers, CRT scanlines + vignette. Dark only, zero border radius.
- Self-hosted fonts (Inter, JetBrains Mono, Press Start 2P) — no third-party requests
  for typography
- Deployed to GitHub Pages via GitHub Actions ([`.github/workflows/deploy.yaml`](.github/workflows/deploy.yaml))

## Structure

```
index.html      Single-page site
style.css       Styles
assets/fonts/   Self-hosted woff2 (latin subset)
img/            Images & favicon
CNAME           Custom domain for GitHub Pages
```

## Keeping the theme in sync with thurbox

The design tokens and chrome rules are copied from `thurbox/website/css/`
(`variables.css`, `base.css`, `components.css`, `landing.css`). When that site's theme
changes, re-port: the token block at the top of `style.css`, the game-terminal chrome
(square status LED + beveled header, no macOS traffic lights), the CRT sweep on panels,
and the `h2` MAP-xx divider.

## Bluesky feed

The "Latest posts" section fetches posts client-side from the public AT Protocol
AppView — no auth, no third-party embed script, no tracking:

```
https://public.api.bsky.app/xrpc/app.bsky.feed.getAuthorFeed?actor=magicletur.eurosky.social
```

Reposts are filtered out, the six most recent original posts are rendered, and the
section degrades to a link to bsky.app if the API is unreachable or JS is disabled.
Change `BSKY_HANDLE` / `BSKY_LIMIT` at the top of the feed script in `index.html`
to adjust.

## Local preview

Any static file server works, e.g.:

```sh
python -m http.server 8000
# then open http://localhost:8000
```

## Deploy

Pushes to `main` trigger the workflow, which publishes the repository root to
GitHub Pages at the custom domain configured in `CNAME`.
