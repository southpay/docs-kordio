# Documentation project instructions

## About this project

- Mintlify docs site for Kordio, published at docs.kordio.io
- Pages are MDX with YAML frontmatter; configuration lives in `docs.json`
- Two products, two tabs, two OpenAPI specs. Neither is the default.

## Structure

- `/agents/*` is spend control. Paths mirror the API namespace `/v1/agent/*`.
- `/ledger/*` is the ledger API.
- Root holds only the chooser (`index.mdx`), `positioning.mdx`, and `changelog.mdx`.
- Shared code lives in `/snippets`. Shared prose does not exist: auth, errors and
  webhooks are genuinely different per product and are written per product.
- Every URL that has ever been published needs a `redirects` entry in `docs.json`
  if it moves. Error `docs_url` values are baked into live API responses.

## Voice

Write like the existing pages. Declarative, opinionated, specific.

- **No em dashes or en dashes.** Not one. Use a period, a comma, a colon, a
  semicolon, or parentheses. This is the single most common regression.
- No emojis anywhere.
- No unicode arrows in prose. Write "moves from `pending` to `completed`".
- Straight quotes only.
- Active voice, second person, sentence case headings.
- One idea per sentence. Vary sentence length.
- State the limit as plainly as the feature. Pages that say what Kordio does not
  guarantee are the ones readers trust.
- Do not announce what a section will do. Do it.
- Do not restate a heading in the first line under it.

## Page contract

- Frontmatter order: `title`, `sidebarTitle`, `description`, `icon`, `keywords`.
  `sidebarTitle` is required whenever `title` runs past two words.
- `description` is one clause, under 100 characters.
- `icon` must be a valid Lucide name and unique within its tab.
- `keywords` are wire-format tokens (field names, error codes, paths), not concepts.
- Exactly one lede paragraph between frontmatter and the first `##`.
- Max two callouts per page, never adjacent. `Warning` means you will lose money or
  corrupt data. `Note` is a surprise that costs an hour. `Info` is scope or routing.
- Say a thing once. The money-is-a-string rule lives at
  `/ledger/concepts#integer-minor-units`; everywhere else is one sentence and a link.
- Every page ends with `## Next steps`: two or four cards, never three, every card
  with an `href`.
- A `<Card>` without an `href` is a bug. Use `###` headings for definition lists.
- Show the response for every request you show. Title code fences with the language
  (`cURL`, `TypeScript`, `Python`) or the status (`201 Created`).
- Never put an elided identifier in a request body. Chain with shell variables.
- Every `$VAR` in a code fence must be defined in a `/snippets/env-*.mdx` file or
  inline on the same page.
- Cross-tab links name the destination product in the label, because clicking one
  replaces the whole sidebar.
- Error-code headings are an API contract: one `###` per code, matching the code
  string exactly, unique across the whole site, never renamed without a redirect.

## Accuracy

Both OpenAPI specs are hand-maintained and nothing syncs them to the code. After
changing routes or serializers in `kordio-api` or `southpay-ledger`, patch the
matching spec here in the same change. Verify claims against the source rather than
against the previous version of the docs.

Do not document packaging or pricing specifics. Point at Billing in the console.
