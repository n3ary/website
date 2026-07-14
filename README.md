# n3ary/website

The static marketing site for the [n3ary](https://github.com/n3ary) org.
Two views: a customer-facing home at the apex [n3ary.com](https://n3ary.com)
and a developer-facing page at [n3ary.com/developers/](https://n3ary.com/developers/).
The app lives at [app.n3ary.com](https://app.n3ary.com).

## What's here

| File | Purpose |
|---|---|
| `index.html` | Customer-facing home page. What the app does, in user terms. |
| `developers/index.html` | Developer-facing page. The data pipeline, the adapter contract, the infrastructure. |
| `404.html` | Friendly not-found page served by Cloudflare Pages on miss. |
| `_headers` | Cache + security headers. |
| `assets/` | Brand logo, favicon, social preview. Synced from [`n3ary/branding`](https://github.com/n3ary/branding). |
| `.github/workflows/deploy-marketing.yml` | Cloudflare Pages deploy on every push to `main`. |
| `.github/workflows/pr-check.yml` | PR validation (shared n3ary/actions base, ASCII check). |

There is no build step. The site is the static file. Edit `index.html`,
commit, push — the workflow takes it from there.

## Live deployment

- **Apex**: <https://n3ary.com> — the marketing site
- **App**: <https://app.n3ary.com> — the SvelteKit PWA (separate Cloudflare Pages project)
- **Cloudflare Pages project**: `website` (auto-creates on first deploy — the workflow handles it)
- **Custom domain**: `n3ary.com` attached to the `website` project; DNS apex is a CNAME flattening to `website-b4a.pages.dev`
- **Deploys on**: every push to `main`

The deploy workflow uses `secrets.CLOUDFLARE_API_TOKEN` and
`secrets.CLOUDFLARE_ACCOUNT_ID`. Add them via
**Repo → Settings → Secrets and variables → Actions** before the first
push.

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