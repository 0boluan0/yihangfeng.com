# yihangfeng.com

The source for [yihangfeng.com](https://yihangfeng.com), the personal website of Yihang Feng. It presents a concise biography, selected projects, research and technical interests, and contact details.

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

- Edit page copy, links, and section order in `index.html`.
- Edit colors, spacing, typography, and responsive rules in `styles.css`.
- Update SEO metadata in the `<head>` of `index.html` when the site's positioning changes.
- Keep `sitemap.xml` in sync when adding public pages.

## Add a project

Copy an existing `<article class="project-card">` block in the Selected Projects section of `index.html`. Replace the project name, verified repository URL, description, status, and technology tags. Do not add results or links that cannot be verified.

## Replace the CV

The Download CV link points to the public PDF at:

```text
assets/files/cv.pdf
```

Replace that file to publish a new version. Keep the filename unchanged, or update the link in `index.html`.

## Deployment

Cloudflare Pages serves this repository as a static site from the repository root. There is no build command or generated output directory.

The production branch is `main`. Every push to `main` triggers an automatic Cloudflare Pages deployment for:

- [yihangfeng.com](https://yihangfeng.com)
- [www.yihangfeng.com](https://www.yihangfeng.com)
