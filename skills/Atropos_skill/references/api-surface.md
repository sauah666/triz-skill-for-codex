# API Surface

Use this when you need exact Atropos.js package, option, DOM, CSS, event, or method facts.

## Current Package Truth

| Fact | Value |
| --- | --- |
| Package | `atropos` |
| Latest verified version | `2.0.2` |
| Release date in package metadata | 2023-07-04 |
| Module type | ESM |
| License | MIT |
| Node engine in package metadata | `>= 12.0.0` |
| Current supported runtime entrypoints | `atropos`, `atropos/react`, `atropos/element` |
| Style entrypoints | `atropos/css`, `atropos/css/min`, `atropos/atropos.css`, `atropos/atropos.min.css`, `atropos/scss`, `atropos/less` |

## Core Usage

```js
import Atropos from 'atropos';
import 'atropos/css';

const instance = Atropos({
  el: '.my-atropos',
  activeOffset: 40,
  shadowScale: 1.05,
});

// Destroy during teardown.
instance.destroy();
```

## Required Vanilla DOM Shape

```html
<div class="atropos my-atropos">
  <div class="atropos-scale">
    <div class="atropos-rotate">
      <div class="atropos-inner">
        <!-- content -->
      </div>
    </div>
  </div>
</div>
```

Atropos looks up `.atropos-scale`, `.atropos-rotate`, and `.atropos-inner` inside the root. Missing structure usually means the effect fails or behaves oddly.

## Options

| Option | Type | Default | Use |
| --- | --- | --- | --- |
| `el` | `HTMLElement | CSSSelector` | none | Root Atropos element. |
| `eventsEl` | `HTMLElement | CSSSelector` | `el` | Pointer/touch event target. Use for shared hover zones or to isolate gestures. |
| `alwaysActive` | `boolean` | `false` | Keep entered/active state without hover. |
| `activeOffset` | `number` | `50` | Z offset while active. |
| `shadowOffset` | `number` | `50` | Shadow Z offset. |
| `shadowScale` | `number` | `1` | Shadow scale. |
| `duration` | `number` | `300` | Transition duration in ms. |
| `rotate` | `boolean` | `true` | Enable rotation. |
| `rotateTouch` | `boolean | 'scroll-x' | 'scroll-y'` | `true` | Touch rotation and touch-action mode. See `hit-testing-touch.md`. |
| `rotateXMax` | `number` | `15` | Max X rotation. |
| `rotateYMax` | `number` | `15` | Max Y rotation. |
| `rotateXInvert` | `boolean` | `false` | Invert X rotation. |
| `rotateYInvert` | `boolean` | `false` | Invert Y rotation. |
| `stretchX` | `number` | `0` | X stretch when using `eventsEl`. |
| `stretchY` | `number` | `0` | Y stretch when using `eventsEl`. |
| `stretchZ` | `number` | `0` | Z stretch when using `eventsEl`. |
| `commonOrigin` | `boolean` | `true` | Shared transform origin for multiple elements with one `eventsEl`. |
| `shadow` | `boolean` | `true` | Inject/use shadow element. |
| `highlight` | `boolean` | `true` | Inject/use highlight element. |
| `onEnter` | `() => void` | `null` | Enter callback. |
| `onLeave` | `() => void` | `null` | Leave callback. |
| `onRotate` | `(x, y) => void` | `null` | Rotation callback. |

## Instance

| Property | Use |
| --- | --- |
| `el` | Root element. |
| `isActive` | Current active state. |
| `destroyed` | Destroy state. |
| `params` | Resolved options. |
| `destroy()` | Remove event listeners and cleanup marker. Always call on manual teardown. |

## Data Attributes

| Attribute | Use |
| --- | --- |
| `data-atropos-offset="5"` | Move element by percentage of its size at max rotation. Positive appears closer; negative appears farther. |
| `data-atropos-opacity="0;1"` | Interpolate opacity from first to second value as rotation increases. |

## CSS Classes To Know

| Class | Meaning |
| --- | --- |
| `.atropos` | Root; has perspective and transform context. |
| `.atropos-scale` | Scaled/transformed wrapper. |
| `.atropos-rotate` | Rotated wrapper. |
| `.atropos-inner` | Content wrapper; `overflow: hidden` by default. |
| `.atropos-shadow` | Auto-created/used shadow layer; `pointer-events: none`. |
| `.atropos-highlight` | Auto-created/used highlight layer; `pointer-events: none`. |
| `.atropos-rotate-touch` | Adds `touch-action: none`. |
| `.atropos-rotate-touch-scroll-y` | Adds `touch-action: pan-y`. |
| `.atropos-rotate-touch-scroll-x` | Adds `touch-action: pan-x`. |

