# resume-website

Brett Powell's personal site and resume, served as static files by Cloudflare.

## Layout

- `public/` is everything that gets published. There is no build step.
  - `index.html`, `Management.html`, `OnAI.html`, `Influences.html` are self-contained page bundles (fonts, React and page content are packed inside each file).
  - `Brett-Powell-Resume.pdf` is the downloadable resume.
  - `og-image.png`, `favicon.svg`, `favicon-32.png`, `apple-touch-icon.png` are the share preview and icons.
  - `_headers`, `404.html`, `robots.txt`, `sitemap.xml` are Cloudflare and crawler support files.
- `wrangler.jsonc` tells Cloudflare to serve `public/` as static assets.

## Deploy

Cloudflare (Workers & Pages, connected to this repo):

- Build command: leave empty
- Deploy command: `npx wrangler deploy`
- Root directory: `/`

Or from a terminal with Node.js installed:

```bash
npx wrangler deploy
```

## Domain

The site is served at https://bretteepowell.com. `wrangler.jsonc` attaches it as a Workers custom domain on deploy, which requires the `bretteepowell.com` zone to be in the same Cloudflare account. Canonical links, share tags (`og:url`, `og:image`), `robots.txt` and `sitemap.xml` all use this domain.
