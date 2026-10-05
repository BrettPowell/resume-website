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

## Before going live

The canonical URLs, share tags (`og:url`, `og:image`), `robots.txt` and `sitemap.xml` use `https://resume-website.pages.dev`. Replace it with the real domain once it is known:

```bash
grep -rl 'resume-website.pages.dev' public | xargs sed -i '' 's#https://resume-website.pages.dev#https://YOUR-DOMAIN#g'
```
