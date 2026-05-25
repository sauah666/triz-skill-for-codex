# 06 Implementation, Motion, and Performance Strategy

## Purpose

This note defines how to build illusion-heavy visuals without wrecking performance, accessibility, or battery life.

## Core Concepts

- Perceived depth beats literal simulation.
- Cheap primitives first.
- Specialty effects are expensive.
- Motion is decoration, not meaning.
- Accessibility is part of the effect.

## Implementation Primitives

- CSS gradients
- pseudo-elements
- CSS variables
- transforms
- opacity
- masks
- blend modes
- backdrop-filter
- SVG filters
- feTurbulence
- feDisplacementMap
- canvas
- lightweight WebGL
- static asset baking
- pointer-driven CSS custom properties
- reduced-motion gating

## Practical Buckets

| Bucket | Use when | Typical examples | Notes |
|---|---|---|---|
| safe static asset | The effect is decorative, repeated, or should never animate | baked grain, highlight sprite, shadow plate | Best for repeated ornament |
| safe CSS | The effect can be expressed with layout and paint primitives | gradients, pseudo-elements, transforms, opacity, CSS variables | Default choice |
| safe SVG | The effect needs vector fidelity or isolated filtering | masks, clips, simple filters | Good for scalable art |
| safe with baked asset | The effect needs richness but not runtime synthesis | scanned texture, painted sheen, static smoke frame | Bake the expensive part |
| performance-sensitive | The effect may work, but cost can rise quickly | backdrop-filter, blend modes, large blurs, soft masks | Requires profiling |
| requires testing | The effect depends on device or browser context | animated filters, large parallax stacks, dense compositing | Must verify on real targets |
| avoid unless justified | The effect is expensive, fragile, or harmful by default | canvas-heavy scenes, WebGL ornament, turbulence loops | Use only when payoff is clear |

## Motion Policy

- Use motion to show state change, direction, activation, or simulated material response.
- Freeze non-essential motion in reduced-motion mode.
- Keep hover, focus, press, drag, and release understandable without animation.
- Prefer transforms and opacity over expensive layout-triggering motion.
- Use requestAnimationFrame for loops.

## What To Bake

- complex textures
- high-frequency noise
- repeated organic breakup
- static lighting that does not need to change
- expensive shadow or glow combinations
- ornamental details replicated many times

## What Should Not Be Animated

- core text readability
- contrast-critical overlays
- focus rings
- major layout geometry
- large full-screen textures
- essential meaning for reduced-motion users
- pointer-only affordances with no alternative state
- anything that causes nausea, flashing, or attention hijacking

## How To Preserve Accessibility And Meaning

- Keep the static state informative on its own.
- Use shape, contrast, spacing, and hierarchy to communicate the meaning.
- Provide visible focus and hover-independent states.
- Mirror interaction feedback with non-motion cues when needed.
- Replace loops with still frames in reduced-motion mode.

## Common Mistakes

- Using motion where a static cue would do better.
- Overusing blur, filters, or blend modes until contrast dies.
- Animating large areas when only a tiny accent needs to move.
- Building everything in canvas or WebGL because it feels fancy.
- Forgetting reduced-motion users.
- Making the interface pointer-only.

## What To Include In The Final Skill

- Safe primitive patterns.
- Fallback strategy.
- Accessibility rules.
- Performance triage rules.
- Motion policy.
- Baked-vs-runtime decision rules.
- Verification checklist.
- Escalation thresholds for specialty rendering.

## What To Exclude

- "Make it feel premium" style advice.
- Tool-specific setup for one project.
- Expensive rendering techniques without clear justification.
- Anything that treats accessibility as a bonus.

## Selected Sources

- [MDN: backdrop-filter](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/backdrop-filter)
- [MDN: CSS compositing and blending](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Compositing_and_blending)
- [MDN: mix-blend-mode](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/mix-blend-mode)
- [MDN: mask-image](https://developer.mozilla.org/en-US/docs/Web/CSS/mask-image)
- [MDN: CSS custom properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)
- [MDN: registering custom properties with @property](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Properties_and_values_API/Registering_properties)
- [MDN: requestAnimationFrame](https://developer.mozilla.org/en-US/docs/Web/API/Window/requestAnimationFrame)
- [MDN: WebGL best practices](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API/WebGL_best_practices)
- [web.dev: animations and performance](https://web.dev/animations-and-performance/)
- [web.dev: high-performance CSS animations](https://web.dev/articles/animations-guide)
- [web.dev: prefers-reduced-motion](https://web.dev/prefers-reduced-motion/)
- [web.dev: accessibility overview](https://web.dev/learn/design/accessibility/)
- [Microsoft Learn: reduced motion simulation](https://learn.microsoft.com/en-us/microsoft-edge/devtools-guide-chromium/accessibility/reduced-motion-simulation?source=recommendations)
