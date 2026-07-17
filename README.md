# Kordio documentation

Source for the Kordio docs site (`docs.kordio.io`), built with [Mintlify](https://mintlify.com).

Kordio is a double-entry ledger API for fintechs, payment processors, and platforms that move money. It is a SouthPay product: the API is served from `ledger.southpay.io` and webhook signature headers keep the `Southpay-` prefix.

## Layout

- `docs.json` — site config and navigation (two tabs: Guides, API Reference)
- `*.mdx` — guide pages, at the repo root
- `api-reference/openapi.yaml` — the OpenAPI 3.1 spec; endpoint pages are generated from it
- `logo/`, `images/`, `favicon.svg` — brand assets, sourced from the kordio-website repo

## Local preview

```bash
npm i -g mint
mint dev
```

## Deploy

Connect the repo to a Mintlify project pointed at the `docs.kordio.io` custom domain; pushes to `main` auto-deploy.
