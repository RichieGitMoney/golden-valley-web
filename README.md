# Golden Valley Web — marketing site

Single-page marketing site for Golden Valley Web: AI-powered web design,
automation, and local SEO for small businesses across California's Central
Valley and beyond.

## Structure

- `index.html` — the entire site (self-contained: inline CSS + JS, Google Fonts
  loaded from the CDN, no build step)

## Local preview

Just open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server 8000
```

## Hosting (GitHub Pages)

Settings → Pages → Build and deployment → Deploy from a branch → `main` / `root`.
The site is served at `https://<user>.github.io/golden-valley-web/`.

To use a custom domain, add a `CNAME` file containing the domain and configure
DNS per GitHub's instructions.
