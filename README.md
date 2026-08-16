# Homeschool Compass — homeschooling, without the guesswork

English-language content site for United States homeschooling families, built on the
**Blog OS** static engine (the same engine as CertNorth and GridDojo).

The site's differentiator is **honest worldview labelling**: for every curriculum we
cover we report two separate facts — whether there is religious content in the
material, and whether the publisher is religious — each quoting the publisher's own
words, linked and dated. We tell families what a material carries; we never tell them
what to believe.

## What's here

- `platform/src/*` — the engine: build with a blocking quality gate, typed block
  renderer, tokens-driven templates (light/dark, WCAG AA validated), post-build checks.
- `platform/content/{site,taxonomy,authors,pages}.json` — site configuration.
- `platform/content/curriculum.json` — **the worldview dataset** (single source of
  truth). Schema and rules documented inside the file.
- `platform/content/articles/*.json` — the published articles.
- `platform/wrangler.jsonc` — Cloudflare deploy config (`name: "homeschool-compass"`).
- `.github/workflows/deploy.yml` — auto-deploy on push to `main` (needs repo secrets
  `CLOUDFLARE_API_TOKEN` + `CLOUDFLARE_ACCOUNT_ID`).
- `docs/protocolo-de-credibilidade.md` — **read this before publishing anything.**

## Build locally

```
cd platform
node src/build.js --force && node src/check.js
```

The gate blocks the build on quality violations; `check.js` verifies the output.

## The worldview gate (CUR-1 … CUR-5)

This engine differs from CertNorth's in one deliberate way: `build.js` validates
`content/curriculum.json` and **fails the build** unless every entry has

- `subject` — labels are per curriculum+subject, never per publisher (CUR-2)
- `contentWorldview` and `publisherAffiliation` as separate fields, each one of
  `christian` / `secular` / `unstated` (CUR-3)
- `worldviewSource` (URL), `worldviewQuote` (the publisher's literal sentence) and
  `verifiedOn` (YYYY-MM) — no source, no label (CUR-4)
- `scopeChecked` — what was actually verified, and what was not (CUR-5)

The build also warns when any label has gone 6+ months without re-verification.
This is the credibility protocol enforced by code rather than by good intentions.

## Deploy

Push to `main`; the Action builds, gates, checks and deploys to Cloudflare Workers.
Configure the two repo secrets first (Settings → Secrets and variables → Actions).

## Status

Live-ready foundation with the first six articles. Still pending, and deliberately
not faked: the registered domain and contact email, the `curriculum.json` entries
(each needs a publisher page read directly), and the State Laws pillar (each state
guide needs that state's own published rules read directly).
