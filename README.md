# DRAKONeditor+

Free, browser-based DRAKON diagram editor (PWA) with **rule checking**, **import/export** and offline use.

> Independent project, not affiliated with or endorsed by Stepan Mitkin. DRAKON Editor, DrakonHub and Drakon.Tech are his products; "DRAKON" is the name of the visual language itself.

## Origin

Built on [DrakonWidget](https://github.com/stepan-mitkin/drakonwidget) by Stepan Mitkin (Unlicense / public domain). The widget core (`libs/drakonwidget.js`, `dtsrc/`) is kept as upstream; this repository adds modules around it. Upstream README: [docs/DrakonWidget-upstream-README.md](docs/DrakonWidget-upstream-README.md).

## Differences from upstream

| Area | Folder | What it adds |
|---|---|---|
| Rule validation | `validation/` | Engine, 18 base rules (12 structure + 6 content), editable `rules-config.js`, Report / Strict / Off panel, generic rule kinds `mentions` and `diagramField` |
| Export | `export/` | PNG, SVG (with embedded diagram JSON), `.drakon` JSON |
| Import | `import/` | `.drakon` / JSON / SVG with embedded JSON, render check |
| PWA | `manifest.webmanifest`, `sw.js`, `pwa/` | Installable, works offline after first visit |
| Branding | `images/`, `pwa/` | Own icons (upstream branding images removed) |

Upstream pull request for the same modules: https://github.com/stepan-mitkin/drakonwidget/pull/10 (kept open; if merged upstream, this repo will re-base onto it).

## Product line

- **DRAKONeditor+** (this repo, free, public)
- **DRAKONstudio** (paid tier, private): project library, rule-pack manager, AI conversion, document export, licence check. It consumes this editor as a pinned dependency; no paid logic lives here.

## Run / test / deploy

```
npm test                 # validation + import tests
npx serve .              # or open index.html through any static server (service worker needs http/https)
npx wrangler deploy      # Cloudflare Workers static assets (wrangler.toml, .assetsignore) -> https://drakoneditor-p.inventship.workers.dev/
```

`.github/workflows/deploy.yml` runs tests and deploys on push to `main` when the `CLOUDFLARE_API_TOKEN` (and `CLOUDFLARE_ACCOUNT_ID`) repository secrets exist; without them the deploy step is skipped.

## Licence

Unlicense (public domain), same as upstream. See [LICENSE](LICENSE) and [NOTICE.md](NOTICE.md).
