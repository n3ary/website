# n3ary/website — Agent guide

Read this once per session before making changes.

## What lives here

A **single static HTML page** that introduces the n3ary org. No build step.
No bundler. No framework. The static file *is* the site.

## Working tree rules

- **Default branch is `main`.** Linear history. Squash / rebase merge only.
- **Edit `index.html` and `404.html` in place.** Don't introduce a build pipeline.
- Brand assets (`assets/`) are sourced from [`n3ary/branding`](https://github.com/n3ary/branding).
  Re-pull them when the brand evolves. Don't hand-edit SVGs.
- Tone, per the [n3ary brand manual](https://github.com/n3ary/branding/blob/main/docs/concepts/brand-manual.md):
  - **Direct, not clever.** "Find your stop" beats "Discover your journey."
  - **Specific, not generic.** "Live vehicle in 38 seconds" beats "Coming soon."
  - **Confident, not loud.** The mark does the talking; copy is plain.

## Deploy

Workflow at `.github/workflows/deploy.yml` ships `index.html`, `404.html`,
`assets/`, and `_headers` to the Cloudflare Pages project `website` on
every push to `main`. The Pages project serves at `website.n3ary.com`.

If a deploy is failing: read the GH Actions log first, then check
Cloudflare Pages → `website` → Deployments.

## Adding a custom domain

The plan is to attach `n3ary.com` (apex) to this project and move the app
to `app.n3ary.com`. When the time comes:

1. In Cloudflare Pages → `website` → **Custom domains** → add `n3ary.com`.
2. The DNS records (CNAME for `n3ary.com`, then `app` for the app) get added
   automatically if the zone is on Cloudflare.
3. The app repo (`n3ary/app`) will need its `_redirects` or Netlify-to-
   Pages config updated to serve from the subdomain.

This is a one-person, afternoon job once the domain is on Cloudflare.

## Vendored standards

The full org standards are at
[`n3ary/standards`](https://github.com/n3ary/standards). We don't vendor
them here — this repo is too small to need local copies.
