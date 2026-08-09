---
name: ceros-find-and-embed-an-experience
description: Walk a Ceros account from an API key down to the embed markup for a specific published experience, then place it on a host page.
api: Ceros Public API
base_url: https://rest.ceros.com
version: 2026-05-28-09-00
operations:
- getCurrentAccount
- getFolderTree
- listFolderExperiences
- getEmbedCodes
generated: '2026-08-09'
method: generated
source: openapi/ceros-public-api-openapi.yml, https://developers.ceros.com/guides/getting-started
---

# Find and embed a Ceros experience

The Ceros Public API has no lookup-by-name and no lookup-by-id. There is exactly one path from a
key to an embed, and it is four calls deep. Follow it in order.

## Before you start

Every request needs two headers:

```
Authorization: Bearer YOUR_API_KEY
x-ceros-api-version: 2026-05-28-09-00
```

Pin the version header. Omitting it floats you onto whatever Ceros ships next — and Ceros has
already removed operations between versions without notice.

## 1. Resolve the account

`getCurrentAccount` — `GET /accounts/current-account`

Takes no parameters. Returns `accountName` and `accountResourceId`. The key resolves to exactly
one account; there is no way to enumerate accounts. A missing or invalid key returns 401
(the live host answers `{"message":"UNAUTHORIZED"}`, not the `errors[]` envelope the spec
documents — handle both).

Keep `accountResourceId`. Every step below needs it.

## 2. Walk the folder tree

`getFolderTree` — `GET /accounts/{accountResourceId}/folder-tree`

- `depth` defaults to **2**. Set `depth=0` to get every level. If you take the default and the
  experience sits three folders down, you will not find it and the call will not tell you why.
- `folder` restricts the result to one branch (that folder, its descendants, and its ancestors for
  structure only).
- `expand=experiences,members` inlines experiences and member counts. Ceros calls these
  "expensive" and excludes them by default. If your goal is one experience, prefer step 3 over
  expanding here.

Each folder carries `resourceId`, plus `deletedAt` and `isAncestorDeleted`. Soft-deleted folders
are in the response — filter them out yourself.

404 means the account does not exist or the caller has no access to it.

## 3. List experiences in the folder

`listFolderExperiences` — `GET /folder/{folderResourceId}/experiences`

Note the singular `/folder/` — the other paths are plural. This trips people.

- `search` filters by name.
- `sort` is one of `alphabetical_a_to_z`, `alphabetical_z_to_a`, `last_created`, `last_updated`,
  `last_published`. Anything else is a **400**. Default is `last_created`.
- `page` is 1-based; `pageSize` defaults to and caps at **50**.
- Sub-folders are **not** traversed. One folder only.

The response has `paging.next` and `paging.previous` as absolute URLs — follow those rather than
rebuilding query strings.

Each experience carries `status`, one of `published`, `draft`, `deleted`, `unpublished`. Filter to
`published` before step 4 if the experience is Legacy.

Keep `resourceId`.

## 4. Get the embed codes

`getEmbedCodes` — `GET /experiences/{experienceResourceId}/embed-codes`

`isExport` is declared **required** with a default of `false` — send it explicitly rather than
relying on the default.

What comes back depends on the kind of experience:

- **Flex** experiences always return `fullHeightEmbedCode`, `scrollableEmbedCode` and
  `inlineEmbedCode`, and work **before** publishing. `experienceAlias` is an empty string.
- **Legacy** experiences must be published, and return only the snippet variants their layout
  supports — the others are absent, not empty.

`viewUrl` and `assetBaseUrl` are the serving URLs. With `isExport=true` they are rewritten as
paths relative to a self-hosted HTML export — Legacy experiences only.

404 here means the experience is deleted, unpublished, or (Legacy only) has never been published.

## 5. Place the embed

The snippet is an aspect-ratio wrapper `div`, an `iframe.ceros-experience`, and a
`scroll-proxy.min.js` script tag. Insert it verbatim; the script handles cross-frame scroll.

## Shortcut: you already have the public URL

If you have the experience's public URL and only need embed markup, skip the API entirely:

```
GET https://view.ceros.com/oembed?url=<experience-url>&format=json
```

Public, unauthenticated, returns the same embed HTML plus title and dimensions. `format=xml`
returns 501. An unresolvable URL returns 400 `Invalid Request`; omitting `url` returns the player
404 page.

## Things the API will not do for you

- No retries guidance and no idempotency key — but every operation here is a GET, so retry freely.
- No rate limits are published. Back off on your own schedule; there is no `429` documented and no
  rate-limit header to read.
- No request-id header, so correlate on your side before you need to open a support ticket.
