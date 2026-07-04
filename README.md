# n3ary/website

The static, single-page marketing site for the
[n3ary](https://github.com/n3ary) org. Lives at `website.n3ary.com`, with
[n3ary.com](https://n3ary.com) as the planned apex once we move the app
under `app.n3ary.com`.

## What's here

| File | Purpose |
|---|---|
| `index.html` | The single page. Dark-mode by default, brand-colored, system-font. |
| `404.html` | Friendly not-found page served by Cloudflare Pages on miss. |
| `_headers` | Cache + security headers. |
| `assets/` | Brand logo, favicon, social preview. Synced from [`n3ary/branding`](https://github.com/n3ary/branding). |
| `.github/workflows/deploy.yml` | Cloudflare Pages deploy on every push to `main`. |

There is no build step. The site is the static file. Edit `index.html`,
commit, push — the workflow takes it from there.

## Live deployment

- **Domain**: <https://website.n3ary.com>
- **Cloudflare Pages project**: `website`
- **Deploys on**: every push to `main`

The deploy workflow uses `secrets.CLOUDFLARE_API_TOKEN` and
`secrets.CLOUDFLARE_ACCOUNT_ID`. Add them via
**Repo → Settings → Secrets and variables → Actions** before the first
push. Wrangler auto-creates the Pages project on first deploy.

## Brand

| Asset | Source |
|---|---|
| Logo (SVG) | `assets/neary-logo.svg` — from [`n3ary/branding/src/logo/`](https://github.com/n3ary/branding/tree/main/src/logo) |
| Wordmark (SVG) | `assets/neary-wordmark.svg` — same source |
| Favicon | `assets/favicon.ico` — from [`n3ary/branding/dist/`](https://github.com/n3ary/branding/tree/main/dist) |
| Apple touch icon | `assets/apple-touch-icon.png` (180 × 180) — from same |
| Social preview | `assets/social/social-preview.png` (1280 × 640) — from same |

When the brand evolves, regenerate these locally or re-pull from the
branding repo. Don't hand-edit the SVGs.

## Cross-references

- [`n3ary/branding`](https://github.com/n3ary/branding) — brand manual, source SVGs, palette.
- [`n3ary/standards`](https://github.com/n3ary/standards) — org governance.

## License

MIT.
