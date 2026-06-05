# Integration Guides

Use this when choosing Atropos integration by framework, SSR mode, or CSS pipeline.

## Choose The Entry Point

| Stack | Default | Notes |
| --- | --- | --- |
| Vanilla/browser-managed DOM | `atropos` | Own lifecycle and call `destroy()`. |
| React SPA | `atropos/react` | Official wrapper; import CSS once. |
| Next.js / React SSR | Client component using `atropos/react` | Keep Atropos out of server components. |
| Web component | `atropos/element` | Register only on client. |
| Vue/Nuxt v2 package expectations | Do not import `atropos/vue` in v2 | Vue/Svelte package components were removed in v2; use web component client-only or vanilla. |
| Svelte v2 package expectations | Do not import `atropos/svelte` in v2 | Treat old Svelte docs as legacy unless installed exports prove otherwise. |
| Remix CSS pipeline | Try CSS URL import if `atropos/css` fails | `atropos/atropos.css?url` was reported as a workaround. |

## React

```jsx
import Atropos from 'atropos/react';
import 'atropos/css';

export function ProductCard() {
  return (
    <Atropos className="product-tilt" rotateTouch="scroll-y">
      <img src="/product.png" alt="" data-atropos-offset="-4" />
      <div data-atropos-offset="6">
        <h2>Product</h2>
        <a href="/buy">Buy</a>
      </div>
    </Atropos>
  );
}
```

React wrapper supports Atropos options plus HTML attributes and wrapper customization props: `component`, `rootChildren`, `scaleChildren`, `rotateChildren`, `scaleClassName`, `rotateClassName`, and `innerClassName`.

## Next.js And React SSR

Use a client component for Atropos UI.

```tsx
'use client';

import Atropos from 'atropos/react';
import 'atropos/css';

export function TiltCard() {
  return <Atropos rotateTouch="scroll-y">{/* content */}</Atropos>;
}
```

Rules:

1. Do not use Atropos in a server component.
2. Import global Atropos CSS in the app-level CSS entry if the framework requires global CSS there.
3. If using `atropos/element`, dynamically import/register it only on the client.
4. If build tooling reports CSS export errors, try `atropos/atropos.css` or a framework-specific URL stylesheet import.

## Vanilla

Use vanilla when you need exact DOM/lifecycle control.

```js
import Atropos from 'atropos';
import 'atropos/css';

let instance;

export function mount() {
  instance = Atropos({
    el: '.my-atropos',
    rotateTouch: 'scroll-y',
  });
}

export function unmount() {
  instance?.destroy();
  instance = undefined;
}
```

Rules:

1. Create the required DOM structure before calling `Atropos(...)`.
2. Call `destroy()` when removing the element or remounting.
3. Avoid initializing twice on the same root; the source guards with `el.__atropos__`.

## Web Component

```js
if (typeof window !== 'undefined' && !customElements.get('atropos-component')) {
  const { default: AtroposComponent } = await import('atropos/element');
  customElements.define('atropos-component', AtroposComponent);
}
```

```html
<atropos-component class="my-atropos" active-offset="40" rotate-touch="scroll-y">
  <img src="/bg.png" alt="" data-atropos-offset="-5" />
  <a href="/details" data-atropos-offset="5">Details</a>
</atropos-component>
```

Rules:

1. Register only in the browser; SSR can throw `HTMLElement is not defined`.
2. Use kebab-case attributes for component options.
3. Use DOM events `enter`, `leave`, and `rotate`.
4. Access the underlying instance as `element.atroposRef` after initialization.

## Vue, Nuxt, And Svelte

Do not assume current Atropos v2 package wrappers exist for Vue or Svelte. The changelog says Vue and Svelte components were removed in v2.0.1.

Use one of these instead:

1. Web component with client-only registration.
2. Vanilla core inside a mounted/client-only lifecycle hook.
3. A local wrapper component that owns DOM structure and teardown.

Nuxt rule: keep `atropos/element` imports inside client-only plugin code and verify the build does not evaluate `HTMLElement` on the server.

## CSS Import Fallbacks

Try in this order:

1. `import 'atropos/css';`
2. `import 'atropos/atropos.css';`
3. Framework URL pattern, for example Remix-style `import atroposCss from 'atropos/atropos.css?url';` and return it from the route links API.

Do not silently omit CSS; missing Atropos CSS often looks like broken transforms, missing perspective, or unusable layout.

## TypeScript Notes

Atropos v2.0.2 shipped a type resolver compatibility fix, but a later official discussion reports React prop mismatches. If TypeScript says props like `activeOffset` do not exist:

1. Confirm installed `atropos` is `2.0.2` or newer.
2. Confirm import is `atropos/react`, not `atropos`.
3. Confirm package manager did not resolve stale declarations.
4. Prefer a narrow local type shim only after verifying package version and imports.

