# Sources And Decisions

Last analyzed: 2026-06-05.

## Source Inventory

| Source | Trust | Contribution |
| --- | --- | --- |
| https://atroposjs.com/docs | High | Core docs, install/import guidance, DOM structure, options, methods, events, offsets. |
| https://atroposjs.com/docs/react | High | Official React wrapper usage and props examples. |
| https://atroposjs.com/docs/element | High | Official web component registration, attributes, events, slots, and `atroposRef`. |
| https://www.npmjs.com/package/atropos / npm metadata | High | Latest package version, exports, types, license, package shape. |
| https://raw.githubusercontent.com/nolimits4web/atropos/master/package/package.json | High | Published package exports, `type: module`, CSS entrypoints, Node engine, release date. |
| https://raw.githubusercontent.com/nolimits4web/atropos/master/src/atropos.js | High | Pointer/touch event behavior, `preventDefault`, `eventsEl`, `destroy`, document click handling. |
| https://raw.githubusercontent.com/nolimits4web/atropos/master/src/atropos.scss | High | `pointer-events: none` on shadow/highlight, `touch-action` classes. |
| https://unpkg.com/atropos@2.0.2/atropos.d.ts | High | Public core TypeScript contract. |
| https://unpkg.com/atropos@2.0.2/atropos-react.d.ts | High | Public React TypeScript contract. |
| https://unpkg.com/atropos@2.0.2/atropos-element.d.ts | High | Public web component TypeScript contract. |
| https://github.com/nolimits4web/atropos/blob/master/CHANGELOG.md | High | Version history, Vue/Svelte component removal, web component addition, type fix. |
| https://github.com/nolimits4web/atropos/issues/13 | Medium-high | Firefox buttons/links not clickable bug report and confirmations. |
| https://github.com/nolimits4web/atropos/issues/13#issuecomment-1085464288 | Medium | Community pointer-events workaround for Firefox click targeting. |
| https://github.com/nolimits4web/atropos/issues/13#issuecomment-1117839950 | Medium-high | More general pointer-events workaround and warning not to remove `preserve-3d`. |
| https://github.com/nolimits4web/atropos/issues/29 | Medium-high | Passive-listener Lighthouse warning tied to touch listener behavior. |
| https://github.com/nolimits4web/atropos/issues/43 | Medium-high | Open stale geometry bug after scrolling while hovered. |
| https://github.com/nolimits4web/atropos/pull/49 | Medium | Open, unreleased PR proposing a fix for scroll geometry drift. |
| https://github.com/nolimits4web/atropos/issues/46 | Medium-high | Nuxt 3 web component SSR `HTMLElement is not defined` report. |
| https://github.com/nolimits4web/atropos/discussions/44 | Medium | Remix CSS import issue and `?url` workaround. |
| https://github.com/nolimits4web/atropos/discussions/45 | Medium | React TypeScript prop mismatch report after v2.0.2. |
| https://github.com/nolimits4web/atropos/discussions/28 | Low-medium | Confirms users expect text/buttons inside Atropos, but solution details are thin. |

## Adopted Decisions

| Decision | Evidence |
| --- | --- |
| Use reference-backed layout, not one huge `SKILL.md`. | Skill needs optional details for API, frameworks, hit-testing, troubleshooting, and examples. |
| Do not add scripts in v1. | No stable deterministic repeated operation survived the deletion pass. |
| Current supported package entrypoints are core, React, element, and styles. | npm/package exports and changelog. |
| Treat Vue/Svelte components as legacy in v2. | Changelog says Vue and Svelte components were removed in 2.0.1, and v2 exports do not expose them. |
| Make click/tap safety a required first concern. | Issue #13, source pointer/touch handling, and frontend/fullstack analysis. |
| Separate Firefox hit-testing from mobile touch tap loss. | Firefox issue points to transformed layer targeting; source shows touch `preventDefault` behavior. |
| Do not blame built-in shadow/highlight as the default click blocker. | Atropos CSS gives `.atropos-shadow` and `.atropos-highlight` `pointer-events: none`. |
| Do not recommend removing `transform-style: preserve-3d`. | Issue #13 comment says it can allow interaction but breaks the effect. |
| Require client-only handling for `atropos/element` under SSR. | Web component source depends on browser globals; Nuxt issue reports `HTMLElement is not defined`. |

## Deferred Or Rejected

| Item | Status | Reason |
| --- | --- | --- |
| Reddit and broad forum advice | Deferred | No high-signal source was needed after official repo evidence; future update can add only reproducible, source-backed patterns. |
| Native mobile implementation guidance | Rejected | Atropos is an HTML/CSS/JS library, not a native UI library. |
| Global monkeypatch of Atropos source for bugs | Rejected | Safer to provide integration workarounds unless the project explicitly vendors or patches the library. |
| Full automation script | Rejected | No repeated fragile transform/validation task is stable enough yet. |

## Retrieval Stopping Rationale

The source mix includes official docs, npm/package metadata, current source, TypeScript declarations, changelog, open issues, open PRs, and official discussions. Additional broad searches were becoming lower-yield than turning confirmed behavior into runtime guidance.

