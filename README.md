# nutflix.xyz

Landing page for **nutflix.xyz** — a single static `index.html` with no build
step, no JS and no dependencies.

The page is public-safe by design: it describes the product, the two tracks
(Nutflix demo / NFX redesign), the NFX-01…12 protocol suite and the current
milestone status. It deliberately contains no hostnames, IPs or internal
infrastructure details.

## Remotes

| Remote   | URL | Role |
|----------|-----|------|
| `origin` | `ssh://git@sovit.xyz:2222/sovtech/nutflix.xyz.git` | GitLab (private, source of truth) |
| `github` | `git@github.com:SovereignTechnology/nutflix.xyz.git` | GitHub (public, feeds Cloudflare Pages) |

## Cloudflare Pages

1. Cloudflare dashboard → Workers & Pages → Create → Pages → Connect to Git.
2. Select `SovereignTechnology/nutflix.xyz`, production branch `main`.
3. Framework preset: **None**. Build command: **empty**. Build output
   directory: `/` (root).
4. Custom domain: `nutflix.xyz` (add the CNAME; DNS is already on Cloudflare).

No environment variables, no build configuration — every commit to `main`
deploys.

## Editing

Open `index.html` in a browser; that is the whole preview environment. The
favicon is an inline SVG data URI and all styling is a single `<style>` block,
so the site stays a one-file deployable.

## License

AGPL-3.0 — see [LICENSE](LICENSE).
