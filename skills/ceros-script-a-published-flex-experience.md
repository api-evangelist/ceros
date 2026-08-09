---
name: ceros-script-a-published-flex-experience
description: Use the Ceros Flex Experience SDK to drive a published experience from JavaScript — set text, control media and states, toggle visibility and navigate pages.
api: Flex Experience SDK
sdk: https://assets.ceros.site/js/flex-experience-sdk.js
generated: '2026-08-09'
method: generated
source: https://developers.ceros.com/flex-experience-sdk/getting-started, https://developers.ceros.com/flex-experience-sdk/delivery-modes, https://developers.ceros.com/flex-experience-sdk/reference/capabilities, https://developers.ceros.com/flex-experience-sdk/limits
---

# Script a published Ceros Flex experience

The Flex Experience SDK is a browser ES module. It reaches into an experience a designer already
built and published, and drives the components they tagged. It does not create anything, and
nothing it does survives a reload.

## Load it

There is nothing to install. Which import you use depends on where the experience runs.

On a Ceros-hosted page (Standalone / iframe player), a bare specifier resolves through Ceros's
import map:

```js
import { connect } from '@ceros/flex-experience-sdk'
```

On your own page (Flex SSR or Flex Inline), import the absolute CDN URL:

```js
import { connect } from 'https://assets.ceros.site/js/flex-experience-sdk.js'
```

The `@ceros` npm scope is empty — the bare specifier is not an npm package and will not resolve in
a bundler. Requires a 2023-or-later browser (Chrome/Edge 89+, Safari 16.4+, Firefox 108+).

## Connect

```js
const experience = await connect()          // waits for readiness
// or
const experience = wrap(element)            // skips the readiness check
```

`connect(experienceRoot?, options?)` resolves to a Component handle once the experience is ready
and accepts an optional container element and timeout. `SDK_VERSION` is exported for version
checks. The SDK is **not** attached to `window.flexSdk` — you must import it.

## Find components

```js
const headline = experience.findByLocator(/* locator */)
const cards    = experience.findByTag(/* tag */)
```

Lookups do not wait and do not stay live. A handle you took before new content rendered will not
update itself — re-run the lookup after anything that changes the DOM.

## Drive them

| Namespace | Methods |
|---|---|
| `text` | `setText(text)`, `getText()` |
| `media` | `play()`, `pause()` |
| `states` | `activate(name)`, `deactivate(name)`, `toggle(name)`, `list()`, `current()` |
| `visibility` | `show()`, `hide()`, `isHidden()` |
| `pages` | `list()`, `current()`, `goTo(page)`, `next()`, `previous()` |

Each namespace is available on the component types that support it, or on the experience object
itself.

## Reconnect on navigation

Delivery mode changes how navigation behaves:

- **Standalone** navigates with a full page load — your script runs again from scratch.
- **Flex Inline** and **Flex SSR** swap pages in place. Nothing reloads, so listen for
  `flex.page.change` and re-connect and re-find your components when it fires.

In Inline and SSR modes Ceros does not render custom head/body HTML for you — analytics, fonts and
meta tags are your page's job.

## Limits worth knowing before you design around it

- Runtime-only. Changes do not persist after reload; there is no write-back to the experience.
- Published experiences only. The SDK does not work inside the Flex editor.
- It cannot add or remove components — only drive ones the designer placed.
- HTML text and animation events are not yet exposed.

Full list: https://developers.ceros.com/flex-experience-sdk/limits
