# Hit Testing And Touch

Use this before adding Atropos to any scene with links, buttons, inputs, routing, or mobile touch.

## Mental Model

Atropos has two separate failure classes:

| Failure class | Evidence | Typical symptom |
| --- | --- | --- |
| Firefox transformed-layer hit-testing | Issue #13 and comments | Desktop links/buttons inside Atropos appear dead in Firefox. |
| Touch pointer default prevention | Source code | Mobile taps/clicks can be suppressed because touch `pointerdown` reaches Atropos and `preventDefault()` runs. |

Do not collapse these into one vague "overlay steals clicks" bug. Built-in `.atropos-shadow` and `.atropos-highlight` already use `pointer-events: none`.

## Required Interactive Design Choice

Choose one pattern before coding:

| Situation | Pattern |
| --- | --- |
| Whole card is one destination | Make the Atropos root the single link or render root as an anchor. Do not put nested links/buttons inside. |
| Card has multiple CTAs or controls | Keep Atropos root as a non-interactive `div`; put real controls inside. |
| Controls must work on touch devices | Isolate touch events from controls or disable Atropos for coarse pointers. |
| Shared hover zone for several cards | Use `eventsEl`, but keep controls from bubbling touch `pointerdown` into it unless verified. |

## Firefox Click Workaround

Known issue: Firefox can target the wrong transformed layer, making buttons/links inside Atropos unclickable. Use a scoped pointer-events override.

```css
/* Scope to the affected Atropos card, not the whole app. */
.my-atropos.atropos .atropos-scale {
  pointer-events: none;
}

.my-atropos.atropos .atropos-rotate,
.my-atropos.atropos .atropos-inner,
.my-atropos.atropos a,
.my-atropos.atropos button,
.my-atropos.atropos input,
.my-atropos.atropos select,
.my-atropos.atropos textarea,
.my-atropos.atropos [role='button'] {
  pointer-events: auto;
}
```

If `auto` does not reproduce the community fix in Firefox, test `pointer-events: all` on `.atropos-rotate`; the GitHub issue workaround used `all`. Keep it scoped.

Do not use this workaround:

```css
.atropos-rotate,
.atropos-scale {
  transform-style: flat;
}
```

Removing `transform-style: preserve-3d` may make clicks easier to target but breaks the 3D effect.

## Mobile Tap Protection

Source behavior to remember:

1. Atropos listens to `pointerdown` on `eventsEl`.
2. For non-mouse `pointerdown`, it calls `preventDefault()`.
3. For touch movement, it can call `preventDefault()` again while rotating.
4. `rotateTouch: true` adds `touch-action: none`.
5. `rotateTouch: 'scroll-y'` adds `touch-action: pan-y`.
6. `rotateTouch: 'scroll-x'` adds `touch-action: pan-x`.

Safe defaults:

| Goal | Default |
| --- | --- |
| Vertical scrolling page | `rotateTouch: 'scroll-y'` |
| Horizontal scrolling surface | `rotateTouch: 'scroll-x'` |
| Tap reliability is more important than touch tilt | Disable Atropos on coarse pointers, or isolate `eventsEl` away from controls. |
| Desktop-only decorative tilt | Initialize only when `(hover: hover) and (pointer: fine)` matches. |

Do not assume `rotateTouch: false` fully protects taps. The pointerdown listener still exists and can call `preventDefault()` before rotation is skipped.

## Event Isolation Patterns

Use one of these when controls lose taps:

1. Desktop-only tilt:

```js
const canHover = window.matchMedia('(hover: hover) and (pointer: fine)').matches;
if (canHover) {
  Atropos({ el: '.my-atropos' });
}
```

2. Separate non-interactive gesture region:

```js
Atropos({
  el: '.my-atropos',
  eventsEl: '.my-atropos-gesture-layer',
  rotateTouch: 'scroll-y',
});
```

Ensure `.my-atropos-gesture-layer` does not cover controls unless click-through CSS and device tests prove it is safe.

3. Stop touch pointerdown before it bubbles to Atropos:

```jsx
<button
  onPointerDownCapture={(event) => {
    if (event.pointerType !== 'mouse') event.stopPropagation();
  }}
>
  Buy
</button>
```

Use this as an app-level workaround, then test tap, focus, keyboard, and analytics handlers.

## Verification

Check all of these before shipping:

1. Firefox desktop: every button/link inside the card receives clicks.
2. Chrome desktop: hover still rotates after pointer-events workaround.
3. Touch device: tapping controls triggers exactly once.
4. Touch device: vertical page scroll still works if expected.
5. Keyboard: tab order and Enter/Space activation still work.

