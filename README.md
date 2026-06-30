# portfolio

Personal portfolio site of Arthur Cesare-Herriau — a static HTML/CSS page
served via GitHub Pages.

🌐 **Live:** https://arthur.thurbeen.eu/

## Stack

- Plain HTML + CSS (no build step, no framework)
- Deployed to GitHub Pages via GitHub Actions ([`.github/workflows/deploy.yaml`](.github/workflows/deploy.yaml))

## Structure

```
index.html      Home page
thoughts.html   Thoughts / posts
style.css       Styles
img/            Images & favicon
CNAME           Custom domain for GitHub Pages
```

## Local preview

Any static file server works, e.g.:

```sh
python -m http.server 8000
# then open http://localhost:8000
```

## Deploy

Pushes to `main` trigger the workflow, which publishes the repository root to
GitHub Pages at the custom domain configured in `CNAME`.
