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

Before opening a PR that touches anything under `.github/`, run
`gh pr list --state open` to confirm no in-flight PR is already
refactoring CI on the same files. Two parallel CI refactors both
end up stale — one of them lands, the other gets closed.

## Adding a custom domain

`n3ary.com` (apex) is already attached to this project as a custom
domain. `app.n3ary.com` is attached to the app's Pages project (`neary`).
The DNS apex is a proxied CNAME flattening to `website-b4a.pages.dev`,
and `app.n3ary.com` is a proxied CNAME to the app's deployment.

If you ever need to detach or re-attach a domain:

1. Cloudflare Pages → project → **Custom domains** to manage the
   project side.
2. The DNS zone (`n3ary.com`, hosted on Cloudflare) is in the
   `~/.config/n3ary/cloudflare.env`-scoped token. Use that token (or
   re-mint per the silent-scope-drop gotcha) to flip records.

> [!WARNING]
> Don't point the apex back at the app's Pages deployment without
> detaching it from the website project first — CF Pages can't have
> the same custom domain on two projects simultaneously.

## Vendored standards

The full org standards are at
[`n3ary/standards`](https://github.com/n3ary/standards). We don't vendor
them here — this repo is too small to need local copies.
