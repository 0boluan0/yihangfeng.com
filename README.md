# yihangfeng.com

The source for [yihangfeng.com](https://yihangfeng.com), the personal website of Yihang Feng. It presents research, software projects, education, and contact details on a single page.

## Stack

- Semantic HTML
- Plain CSS
- No framework, package manager, build step, database, or server code

## Preview locally

From the repository root, run:

```bash
python3 -m http.server 8000
```

Then open [http://localhost:8000](http://localhost:8000).

## Update content

- Edit page copy, links, and section order in `index.html`. Sections are numbered 01–04 in both the section headings and the "On this page" list; keep them in sync.
- Edit colors, spacing, typography, and responsive rules in `styles.css`.
- Update the `<title>`, description, Open Graph tags, and JSON-LD in the `<head>` of `index.html` when the site's positioning changes.
- Keep `sitemap.xml` in sync when adding public pages, and update its `<lastmod>`.

## Add a research item or project

Copy an existing `<article class="entry">` block in the Research or Projects section of `index.html`. Replace the title, verified link, description, metadata line, and tags. The handwritten `<p class="entry-note">` is optional; only use it for a concrete fact. Do not add results or links that cannot be verified.

## Cache busting

Cloudflare tells browsers to cache CSS, images, and PDFs for up to four hours. `index.html` and `404.html` therefore reference these files with a version query, for example `/styles.css?v=20261013`.

When you change `styles.css`, `favicon.svg`, or `assets/files/cv.pdf`, update the `?v=` value everywhere it appears so returning visitors get the new file immediately.

## Replace the CV

The CV links point to the public PDF at:

```text
assets/files/cv.pdf
```

Replace that file to publish a new version, then bump its `?v=` value. The public copy leaves out the phone number; export it that way from the source document too. Visitors download it as `Yihang-Feng-CV.pdf`.

## Social preview image

`assets/images/og.png` (1200 × 630) is used by Open Graph and Twitter cards. Regenerate it if the name or headline changes.

## Deployment

Cloudflare Pages serves this repository as a static site from the repository root. There is no build command or generated output directory, so every committed file is publicly reachable. `_redirects` sends repository-only files such as this README back to the homepage; keep internal notes out of the repository.

The production branch is `main`. Every push to `main` triggers an automatic Cloudflare Pages deployment for:

- [yihangfeng.com](https://yihangfeng.com)
- [www.yihangfeng.com](https://www.yihangfeng.com) (should redirect to the apex domain; see below)

A deployment is atomic and global: when the Cloudflare Pages check on the commit reports success, every edge location serves the new version. HTML is not cached at the edge, so no cache purge is needed.

`www` → apex redirect cannot be configured from this repository. In the Cloudflare dashboard, add a Redirect Rule for `www.yihangfeng.com` that sends a 301 to `https://yihangfeng.com` with the path and query string preserved.
