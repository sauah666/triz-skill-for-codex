---
name: Atropos_skill
description: Expert Atropos.js integration guidance for Codex. Use when building, fixing, reviewing, or optimizing Atropos.js 3D parallax hover/tilt effects in web apps, React, Next.js, vanilla JavaScript, web components, Vue/Nuxt via custom elements, mobile web/WebView, touch interactions, SSR builds, CSS imports, performance, accessibility, or known Atropos bugs including buttons/links not responding, Firefox hit-testing, touch tap loss, scroll geometry drift, passive-listener warnings, and TypeScript wrapper issues.
---

# Atropos.js Integration

Use this skill to implement or debug Atropos.js without breaking clicks, taps, scroll, SSR, or accessibility.

## First Actions

1. Inspect the target stack: framework, rendering mode, package version, CSS pipeline, and whether the scene contains links, buttons, inputs, popovers, or routed navigation.
2. Prefer current supported entrypoints: core `atropos`, React `atropos/react`, or web component `atropos/element`.
3. Treat Vue and Svelte component docs as legacy unless the installed package version proves otherwise; v2 removed packaged Vue/Svelte components.
4. If interactive controls are inside or above Atropos, open `references/hit-testing-touch.md` before writing code.
5. If the app uses SSR, app routers, Nuxt, Remix, or delayed hydration, open `references/integration-guides.md` before choosing imports.
6. If diagnosing a bug, open `references/troubleshooting.md` before changing code.

## Reference Routing

| Need | Open |
| --- | --- |
| Exact package exports, options, DOM structure, CSS classes, methods, and events | `references/api-surface.md` |
| React, Next.js, SSR, Remix, Vue/Nuxt custom element, CSS import, and lifecycle choices | `references/integration-guides.md` |
| Buttons/links not clickable, Firefox hit-testing, touch tap loss, `eventsEl`, `rotateTouch`, mobile scroll | `references/hit-testing-touch.md` |
| Known bug symptoms, likely cause, source-backed fixes, and verification checks | `references/troubleshooting.md` |
| Copyable implementation patterns and anti-pattern corrections | `references/examples.md` |

## Implementation Defaults

1. Install/import Atropos CSS exactly once.
2. Use React wrapper for React unless SSR or type tooling makes vanilla/client-only simpler.
3. Use vanilla core when the app needs explicit lifecycle control or exact DOM ownership.
4. Use web component only on the client; do not import `atropos/element` during server evaluation.
5. Keep the Atropos root non-interactive when the card has multiple controls. Use a single interactive root only when the whole card is one link.
6. Never nest an anchor/button inside another interactive root.
7. For touch/mobile pages, do not assume `rotateTouch: false` alone protects taps. Atropos still listens for touch `pointerdown`; isolate `eventsEl`, disable Atropos on coarse pointers, or stop pointerdown propagation on controls and verify on a real device.
8. Add reduced-motion handling at the app level; Atropos has no built-in reduced-motion policy.

## Known Click/Tap Rule

Always account for the known Atropos click/tap failure modes:

- Firefox can mis-target transformed Atropos layers so buttons/links appear dead. Use the scoped pointer-events workaround in `references/hit-testing-touch.md`; do not remove `transform-style: preserve-3d` because that breaks the effect.
- On touch devices, Atropos calls `preventDefault()` on touch pointer paths. If controls do not tap reliably, isolate or disable touch tilt rather than polishing CSS blindly.
- Built-in shadow/highlight overlays are not the primary suspect because Atropos CSS sets them to `pointer-events: none`.

## Verification Checklist

Before calling the task complete:

1. Verify desktop hover/leave behavior in Chrome and Firefox when possible.
2. Verify every link/button/input inside the Atropos scene with mouse and keyboard.
3. Verify tap behavior on a real or emulated touch device.
4. Verify page scroll while the pointer is over an active card.
5. Verify SSR/build output if the framework has server rendering.
6. Verify reduced-motion fallback keeps content usable.

