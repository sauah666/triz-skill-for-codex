# Troubleshooting

Use this when Atropos is installed but behavior is broken.

## Symptom Matrix

| Symptom | Likely cause | Fix |
| --- | --- | --- |
| Buttons/links inside Atropos do not click in Firefox | Transformed layer hit-testing bug, issue #13 | Apply scoped pointer-events workaround from `hit-testing-touch.md`; verify Firefox. |
| Mobile taps on buttons/links fail or need repeated taps | Touch `pointerdown` bubbles to Atropos and `preventDefault()` runs | Disable Atropos on coarse pointers, isolate `eventsEl`, or stop touch pointerdown propagation on controls. |
| Page cannot scroll smoothly on touch | `rotateTouch: true` gives `touch-action: none` and Atropos prevents touch movement while rotating | Use `rotateTouch: 'scroll-y'` for vertical pages, `'scroll-x'` for horizontal surfaces, or disable touch tilt. |
| Lighthouse warns about passive listeners | Atropos uses touch listeners that may call `preventDefault()`; issue #29 is open | Treat as known tradeoff; reduce touch use or disable Atropos on touch if scroll perf matters. |
| Hover math is wrong after scrolling while pointer stays over card | Open geometry bug issue #43; PR #49 not released | Force reset on scroll, avoid active hover during scroll, or patch/vendor only with project approval. Verify current package before patching. |
| Web component throws `HTMLElement is not defined` | `atropos/element` evaluated during SSR | Import/register only on client. |
| Remix or similar cannot resolve `atropos/css` | Bundler CSS export handling | Try `atropos/atropos.css`, or URL import such as `atropos/atropos.css?url`. |
| React TypeScript says `activeOffset` or other Atropos props do not exist | Wrong import, stale package declarations, or unresolved type discussion #45 | Confirm `import Atropos from 'atropos/react'`, installed version, and declaration resolution before adding a narrow type shim. |
| Vue/Svelte import path fails in v2 | Vue/Svelte package components removed in v2.0.1 | Use web component client-only, vanilla core, or local wrapper. |
| Visual effect missing or flat | CSS missing or DOM structure wrong | Import Atropos CSS and verify `.atropos > .atropos-scale > .atropos-rotate > .atropos-inner`. |
| Content is clipped | `.atropos-inner` has `overflow: hidden` | Move popovers outside Atropos, use portals, or adjust structure carefully. |
| Popping/glare/scale jumps with shared `eventsEl` | Open issue #19 reports popping in multi-component collections | Reduce shared `eventsEl` complexity, lower offsets/stretches, or test per-card event targets. |

## Debug Order

1. Confirm package version and entrypoint.
2. Confirm CSS is loaded.
3. Confirm DOM/wrapper structure.
4. Confirm no duplicate Atropos instance exists on the root.
5. Confirm interactive elements use a safe pattern from `hit-testing-touch.md`.
6. Confirm touch/scroll expectations and `rotateTouch`.
7. Confirm SSR/client-only import boundaries.
8. Reproduce in Firefox and a touch environment if user-facing controls are involved.

## Patch Discipline

Prefer app-level integration fixes before changing library code.

Patch or vendor Atropos only when:

1. The project already vendors dependencies or accepts patch-package.
2. The bug is reproduced locally.
3. The patch is tied to an upstream issue/PR.
4. The project has browser regression tests for the changed behavior.

For issue #43, PR #49 adds scroll and pointer tracking in source, but it is not in the latest verified npm package. Do not claim the package contains that fix until npm/changelog proves it.

