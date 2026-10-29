# Ceros

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Ceros is an experiential content platform used by marketing, design and agency teams to build interactive, no-code web content — microsites, landing pages, interactive reports, infographics, pitch decks and embeddable experiences — in a browser design studio and publish them to a CDN. Its developer surface is three separate things. A small read-only REST Public API at rest.ceros.com walks accounts, folders, experiences and embed codes behind a bearer API key, versioned by dated snapshots selected with the x-ceros-api-version header. A browser-side Flex Experience SDK, delivered as an ES module from the Ceros CDN, scripts a published experience at runtime — setting text, controlling media and states, toggling visibility and navigating pages. And a public oEmbed 1.0 endpoint on view.ceros.com, together with first-party connectors for Adobe Experience Manager, Contentful, Optimizely and WordPress, places an experience inside another platform. Ceros also operates MarkUp, its visual commenting and collaboration product.

**Areas:** Content Management · Interactive Content · Digital Experience · Embed · oEmbed · CMS Integration · Marketing · Design · No-Code · Content Delivery · Media and Publishing · SDK

## Ceros on APIs.io

Everything profiled for Ceros is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/ceros/](https://apis.io/providers/ceros/)** — or go straight to one of the APIs or properties below.

### APIs (6)

- [Ceros Accounts API](https://apis.io/apis/ceros/ceros-accounts-api/) — The accounts API from Ceros — 1 operation(s) for accounts.
- [Ceros Embed Codes API](https://apis.io/apis/ceros/ceros-embedcodes-api/) — The embedCodes API from Ceros — 1 operation(s) for embedcodes.
- [Ceros Experience API](https://apis.io/apis/ceros/ceros-experience-api/) — The experience API from Ceros — 1 operation(s) for experience.
- [Ceros Experience Page API](https://apis.io/apis/ceros/ceros-experiencepage-api/) — The experiencePage API from Ceros — 6 operation(s) for experiencepage.
- [Ceros Folders API](https://apis.io/apis/ceros/ceros-folders-api/) — The folders API from Ceros — 1 operation(s) for folders.
- [Ceros o Embed API](https://apis.io/apis/ceros/ceros-o-embed-api/) — The o Embed API from Ceros — 1 operation(s) for o embed.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [ceros-mcp.yml](https://apis.io/servers/ceros/ceros-mcp-yml/)

#### Examples (1)

Example requests and responses.

- [Ceros Oembed Response](https://apis.io/examples/ceros/ceros-oembed-response/)

#### Collections (6)

Postman and Open Collection request collections.

- [Ceros Accounts API](https://apis.io/collections/ceros/open-ceros-accounts-api/)
- [Ceros Embed Codes API](https://apis.io/collections/ceros/open-ceros-embedcodes-api/)
- [Ceros Experience API](https://apis.io/collections/ceros/open-ceros-experience-api/)
- [Ceros Public Experience Page API](https://apis.io/collections/ceros/open-ceros-experiencepage-api/)
- [Ceros Folders API](https://apis.io/collections/ceros/open-ceros-folders-api/)
- [Ceros Oembed API](https://apis.io/collections/ceros/open-ceros-oembed-api/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Ceros Public Api Overlay](https://apis.io/overlays/ceros/ceros-public-api-overlay/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Ceros Authentication](https://apis.io/security/ceros/ceros-authentication/)
- [Ceros Domain Security](https://apis.io/security/ceros/ceros-domain-security/)
- [Ceros Trust Center](https://apis.io/security/ceros/ceros-trust-center/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.ceros.com/)
- [Documentation](https://developers.ceros.com/overview)
- [Getting started](https://developers.ceros.com/guides/getting-started)
- [API reference](https://developers.ceros.com/api/public/ceros-public-api)
- [Pricing](https://www.ceros.com/pricing/)
- [Sign up](https://www.ceros.com/demo-request/)
- [Support](https://www.ceros.com/contact/)
- [Blog](https://www.ceros.com/blog/)
- [Terms of service](https://www.ceros.com/terms-and-conditions/)
- [Privacy policy](https://www.ceros.com/privacy-policy/)
- [GitHub](https://github.com/ceros)
- [Status](https://status.ceros.com/)

## API Evangelist rating

**Kin Score 52.9** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 71.4 |
| Contract quality | 54.0 |
| Contract governance | 4.5 |
| Operational transparency | 50.0 |
| Developer ergonomics | 66.1 |
| Access clarity | 52.6 |

**Agent readiness 22.3** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | partial |
| Rate Limit Signal | — |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | partial |
| Operation Distinctiveness | distinct |

**Regulatory alignment 29.4** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/ceros/](https://apis.io/providers/ceros/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Ceros: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/ceros/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
