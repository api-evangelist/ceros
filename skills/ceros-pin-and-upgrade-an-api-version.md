---
name: ceros-pin-and-upgrade-an-api-version
description: Pin a Ceros Public API integration to a dated version, and safely move it forward — including checking whether the operations you depend on still exist.
api: Ceros Public API
base_url: https://rest.ceros.com
operations:
- getCurrentAccount
- getFolderTree
- listFolderExperiences
- getEmbedCodes
generated: '2026-08-09'
method: generated
source: https://developers.ceros.com/guides/versioning, openapi/ceros-public-api-openapi.yml, openapi/ceros-public-api-2026-02-25-openapi.yml
---

# Pin and upgrade a Ceros API version

## How Ceros versions

Versions are dated snapshots, `YYYY-MM-DD-HH-MM`. You select one per request:

```
x-ceros-api-version: 2026-05-28-09-00
```

Ceros's stated policy: a new version is cut "when a change would otherwise break existing
integrations", and shipped versions are "permanent snapshots that don't change as the API
evolves". There is no deprecation policy, no `Sunset` header, and no published support window for
old versions.

Omitting the header puts you on the latest version. Do not do this in production.

## The versions published today

| Version | Operations |
|---|---|
| `2026-05-28-09-00` (current) | 4 |
| `2026-02-25-12-00` | 11 |
| `2026-02-17-08-00` | 8 |
| `2025-12-10-09-11` | 8 |

## The upgrade check that matters

Do not assume a newer version is a superset. It has already not been one.

Version `2026-02-25-12-00` documents eleven operations. The current version documents **four**.
These seven are in the older reference and absent from the current one:

- `createPage` — `POST /experiences/{experienceResourceId}/pages`
- `deletePage` — `DELETE /experiences/{experienceResourceId}/pages/{pageId}`
- `duplicatePage` — `POST /experiences/{experienceResourceId}/pages/{pageId}/duplicate`
- `batchUpdatePage` — `POST /experiences/{experienceResourceId}/pages/{pageId}/batch-update`
- `applyPageTemplate` — `POST /experiences/{experienceResourceId}/pages/{pageId}/apply-template`
- `getAllExperiencePages` — `GET /experiences/{experienceResourceId}/pages`
- `getCmlForSelector` — `GET /experiences/{experienceResourceId}/pages/{pageId}/cml-for-selector`

That is every write operation the API ever had. No deprecation notice, no sunset date and no
migration note accompanies the removal.

## Procedure

1. **Inventory your calls.** List the operationIds your integration actually uses.
2. **Open the target version's reference.**
   `https://developers.ceros.com/api/public/<version>/ceros-public-api`. The version selector at
   the top of the reference is the only version history Ceros publishes.
3. **Confirm each operationId is still present.** If one is missing, it is gone from that version
   — treat it as a breaking change and stay pinned until you have a replacement.
4. **Diff the shapes you consume.** Parameters and response fields change between versions;
   compare field-by-field against the version you are on.
5. **Move the header, one environment at a time.** Change `x-ceros-api-version` in staging, run
   your integration tests, then production.
6. **Watch the 400s.** Validation failures return `errors[].cause[]` with `path`, `expected` and
   `received` — that is where a changed shape surfaces first.

## What to hold onto

Keep your pinned version in configuration, not in code, so a rollback is a deploy of one value.
There is no way to ask the API which version answered a request — no version echo header is
documented or observed — so log the version you sent alongside every request yourself.
