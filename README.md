# Zilin Yang

Personal website: https://zilinyang.com

Static HTML and CSS, hosted on GitHub Pages. No dependencies or build step.

## Edit content

- `index.html`: name, navigation, and the About, Research, Projects, and Contact sections. About, Research, and Projects are intentionally blank; Contact uses email and Douyin icon links without visible addresses or handles. The Douyin icon links directly to the user-provided profile URL. HTML comments mark insertion points.
- `style.css`: layout, colors, typography, and responsive styles.
- `assets/portrait.jpg`: user-provided homepage portrait from `112018.JPG`.

## Local preview and Git

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

Open http://127.0.0.1:8000. Stop the server with Ctrl+C.

This directory is the Git working copy. Make changes locally, preview them, then commit and push to `main`:

```sh
git add index.html style.css assets README.md
git commit -m "Update personal website"
git push origin main
```

## GitHub Pages

Repository Settings → Pages → Deploy from a branch → `main` → `/ (root)`.

## Custom domain

The primary domain is `zilinyang.com`, registered with GoDaddy, with DNS managed by Cloudflare on the Free plan. GitHub Pages serves the site using the tracked `CNAME` file.

See [domain configuration](docs/domain-setup.md) for DNS records, preserved service records, redirects, and HTTPS setup.

## Search indexing

`robots.txt` allows crawling and points to `sitemap.xml`. The sitemap lists the canonical homepage. Keep the Google verification meta tag in `index.html` to retain Search Console ownership. The homepage includes a GitHub contact icon and ProfilePage/Person structured data connecting the site to `yang-zilin`.

On 2026-11-13, the URL-prefix property `https://zilinyang.com/` was verified through the HTML meta tag in Google Search Console. The sitemap was submitted and returned `Success`, with one discovered page. The initial URL inspection reported `URL is unknown to Google` and no previous crawl; this is an indexing snapshot, not a live status. Search Console ownership verification and sitemap submission do not guarantee indexing or ranking.

The live URL test subsequently returned `URL is available to Google`, `Page can be indexed`, and one valid Profile page item. The indexing request succeeded: `Indexing requested`, with the URL added to a priority crawl queue. GitHub profile name/website updates were not applied: the CLI lacks the `user` scope, and Safari was signed into `juyujing`, not `yang-zilin`.
