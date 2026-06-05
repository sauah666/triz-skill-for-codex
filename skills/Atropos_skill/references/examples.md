# Examples

Use this for copyable patterns and anti-pattern corrections.

## React Card With CTA And Touch Scroll

```tsx
'use client';

import Atropos from 'atropos/react';
import 'atropos/css';

export function PlanCard() {
  return (
    <Atropos className="plan-card-atropos" rotateTouch="scroll-y" shadowScale={1.03}>
      <div className="plan-card-bg" data-atropos-offset="-4" />
      <div className="plan-card-content" data-atropos-offset="4">
        <h2>Pro</h2>
        <p>For teams shipping production UI.</p>
        <a className="plan-card-link" href="/checkout">
          Choose plan
        </a>
      </div>
    </Atropos>
  );
}
```

Add the Firefox hit-testing workaround if the CTA is inside transformed layers:

```css
.plan-card-atropos.atropos .atropos-scale {
  pointer-events: none;
}

.plan-card-atropos.atropos .atropos-rotate,
.plan-card-atropos.atropos .atropos-inner,
.plan-card-atropos.atropos a,
.plan-card-atropos.atropos button {
  pointer-events: auto;
}
```

## Whole Card Link

Use this only when the whole card has one destination.

```tsx
import Atropos from 'atropos/react';
import 'atropos/css';

export function ArticleCard() {
  return (
    <Atropos component="a" href="/article" className="article-card" rotateTouch="scroll-y">
      <img src="/cover.jpg" alt="" data-atropos-offset="-3" />
      <span data-atropos-offset="5">Read article</span>
    </Atropos>
  );
}
```

Do not place another link or button inside this card.

## Vanilla With Cleanup

```js
import Atropos from 'atropos';
import 'atropos/css';

let atropos;

export function mountTiltCard(root) {
  const canHover = window.matchMedia('(hover: hover) and (pointer: fine)').matches;
  if (!canHover) return;

  atropos = Atropos({
    el: root,
    rotateTouch: false,
    shadowScale: 1.04,
  });
}

export function unmountTiltCard() {
  atropos?.destroy();
  atropos = undefined;
}
```

## Web Component Client Registration

```js
export async function registerAtroposElement() {
  if (typeof window === 'undefined') return;
  if (customElements.get('atropos-component')) return;

  const { default: AtroposComponent } = await import('atropos/element');
  customElements.define('atropos-component', AtroposComponent);
}
```

```html
<atropos-component class="feature-tilt" rotate-touch="scroll-y">
  <img src="/back.png" alt="" data-atropos-offset="-5" />
  <a href="/feature" data-atropos-offset="5">Open feature</a>
</atropos-component>
```

## Reduced Motion Gate

```js
const prefersReducedMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;
const canHover = window.matchMedia('(hover: hover) and (pointer: fine)').matches;

if (!prefersReducedMotion && canHover) {
  Atropos({ el: '.my-atropos' });
}
```

Keep content visible and actionable when Atropos is disabled.

## Anti-Pattern: Nested Interactive Controls

Bad:

```tsx
<Atropos component="a" href="/product">
  <button>Add to cart</button>
</Atropos>
```

Correct:

```tsx
<Atropos component="div" className="product-card" rotateTouch="scroll-y">
  <a href="/product">Details</a>
  <button>Add to cart</button>
</Atropos>
```

## Anti-Pattern: Server Importing The Web Component

Bad:

```js
import AtroposComponent from 'atropos/element';

customElements.define('atropos-component', AtroposComponent);
```

Correct:

```js
if (typeof window !== 'undefined') {
  const { default: AtroposComponent } = await import('atropos/element');
  customElements.define('atropos-component', AtroposComponent);
}
```

## Anti-Pattern: Treating Touch Tilt As Free

Bad:

```js
Atropos({ el: '.checkout-card', rotateTouch: true });
```

Correct when taps and vertical scroll matter:

```js
const canHover = window.matchMedia('(hover: hover) and (pointer: fine)').matches;
if (canHover) {
  Atropos({ el: '.checkout-card', rotateTouch: false });
}
```

Or isolate touch controls as described in `references/hit-testing-touch.md`.

