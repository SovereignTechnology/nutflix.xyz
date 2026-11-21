# nutflix.xyz

Landing page for **nutflix.xyz** — a single static `public/index.html` with no
build step, no JS and no dependencies.

The page describes the product, explains each Nutflix repository in plain
language with a link to its code on GitHub, shows how the repositories fit
together, and lists the NFX protocol suite and the current status.

It is public-safe by design. The only addresses on it are public ones: the
GitHub repositories and the web player at `web.nutflix.xyz`. It deliberately
contains no IPs and no internal infrastructure details.

## What the page lists

| Repository | Card |
|------------|------|
| `SovereignTechnology/nfx` | The open standard, and the Rust engine that runs it |
| `SovereignTechnology/nutflix-pear` | The desktop app |
| `SovereignTechnology/nutflix-runtime` | The app with no download server (pre-alpha) |
| `SovereignTechnology/nutflix-nsite` | The web player, published on Nostr |
| `SovereignTechnology/nutflix.xyz` | This site |

When a repository is added, or one changes state (a first release, the nsite
going live), edit its card and its status pill. The page names no version
numbers, so a release needs no edit: it links to each Releases page instead.
The protocol list follows the table in nfx's `spec/README.md`.

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
block, so the site stays a one-file deployable. The file itself loads nothing
else: no scripts, no web fonts and no images. (On the live site Cloudflare adds
its Web Analytics beacon at the edge.)

The colours are the Nutflix app's own (`--nf-color-*` in nutflix-pear's
`packages/ui`). The page is dark by default and follows the reader's
`prefers-color-scheme` to a light variant; check both after a change.

## License

AGPL-3.0 — see [LICENSE](LICENSE).
