# Kordio documentation

Source for the Kordio docs site (`docs.kordio.io`), built with [Mintlify](https://mintlify.com).

Kordio is a double-entry ledger API for fintechs, payment processors, and platforms that move money. The API is served from `api.kordio.io`.

## Layout

- `docs.json` — site config and navigation (two tabs: Guides, API Reference)
- `*.mdx` — guide pages, at the repo root
- `api-reference/openapi.yaml` — the OpenAPI 3.1 spec; endpoint pages are generated from it
- `logo/`, `images/`, `favicon/` — brand assets, sourced from the Kordio frontend and website repos

## Local preview

```bash
npm i -g mint
mint dev
```

## Deploy

Connect the repo to a Mintlify project pointed at the `docs.kordio.io` custom domain; pushes to `main` auto-deploy.
