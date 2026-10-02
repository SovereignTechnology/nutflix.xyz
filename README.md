# nutflix.xyz

Landing page for **nutflix.xyz** — a single static `public/index.html` with no
build step, no JS and no dependencies.

The page is public-safe by design: it describes the product, the two tracks
(Nutflix demo / NFX redesign), the NFX-01…12 protocol suite and the current
milestone status. It deliberately contains no hostnames, IPs or internal
infrastructure details.

## Remotes

| Remote   | URL | Role |
|----------|-----|------|
| `origin` | `ssh://git@sovit.xyz:2222/sovtech/nutflix.xyz.git` | GitLab (private, source of truth) |
| `github` | `git@github.com:SovereignTechnology/nutflix.xyz.git` | GitHub (public, feeds Workers Builds) |

## Deployment

Served by the Cloudflare Worker **`nutflix-xyz`** (static assets) on the
`Sovereign IT` account, custom domain `nutflix.xyz`. Only `public/` is
deployed — `.git`, `README.md`, `LICENSE` and `wrangler.jsonc` are never
uploaded. (An early deploy shipped the repo root and served `.git` at the site
root; fixed 2026-10-02.)

Manual deploy, from a checkout:

```sh
npx wrangler deploy
```

Autodeploy (once): Cloudflare dashboard → Workers & Pages → **`nutflix-xyz`** →
Settings → **Builds** → Connect → GitHub → `SovereignTechnology/nutflix.xyz`,
production branch `main`, **deploy command `npx wrangler deploy`**, build
command empty. Every push to `main` then deploys.

## Editing

Open `public/index.html` in a browser; that is the whole preview environment.
The favicon is an inline SVG data URI and all styling is a single `<style>`
block, so the site stays a one-file deployable.

## License

AGPL-3.0 — see [LICENSE](LICENSE).
