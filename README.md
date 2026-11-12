# Zilin Yang

Personal website: https://yang-zilin.github.io

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

## Future custom domain

Planned domain: `zilinyang.com`, registered with GoDaddy. DNS will later move to Cloudflare.

No `CNAME` file is active yet, so the GitHub Pages address stays usable during setup.

When ready:

1. Add the domain to Cloudflare and copy all existing DNS records, including any email records.
2. Change nameservers at GoDaddy to the exact pair assigned by Cloudflare.
3. Point the apex `@` to GitHub Pages using A records `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, and `185.199.111.153`.
4. Set `www` CNAME to `yang-zilin.github.io`. Keep website records DNS-only while GitHub validates DNS and issues its certificate.
5. Verify domain ownership in GitHub account Settings → Pages using GitHub's assigned TXT record.
6. Set repository Settings → Pages → Custom domain to `zilinyang.com`, which creates the `CNAME` file.
7. Wait for the certificate, enable Enforce HTTPS, and verify both apex and www.

Do not replace existing email or unrelated DNS records without reviewing them.
