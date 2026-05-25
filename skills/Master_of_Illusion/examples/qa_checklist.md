# QA Checklist

## Perception
- [ ] The object reads quickly.
- [ ] The depth cues agree with one another.
- [ ] Figure-ground separation is clear.
- [ ] The silhouette supports the intended read.

## Shadow
- [ ] Contact shadow anchors the object.
- [ ] Cast shadow direction is correct.
- [ ] Shadow softness matches the light story.
- [ ] AO stays local and subtle.

## Lighting
- [ ] One light story is consistent across states.
- [ ] Fill reveals form without flattening it.
- [ ] Rim and backlight separate only when needed.
- [ ] Highlights match curvature and view angle.

## Material
- [ ] The material family is clear.
- [ ] The cue bundle does not contradict itself.
- [ ] Roughness / gloss / metallic / transmission read coherently.
- [ ] Microtexture supports scale instead of noise.

## Optical Effects
- [ ] Every effect has a physical reason.
- [ ] No effect is used as a generic beautifier.
- [ ] Bloom, glow, and aberration are not overused.
- [ ] The effect survives the angle / thickness / light check.

## Interaction
- [ ] Hover, focus, press, drag, release, and invalid states make sense.
- [ ] Shadow and light respond to interaction coherently.
- [ ] Pointer-only states have keyboard and touch equivalents.
- [ ] Reduced-motion preserves meaning.

## Tone
- [ ] The visual tone matches the adapter.
- [ ] The object does not drift into a different aesthetic.
- [ ] The effect serves the user action, not spectacle.

## Performance
- [ ] The implementation stays within budget.
- [ ] The effect is cheap enough for the target platform.
- [ ] Heavy filters are justified or removed.
- [ ] The image remains acceptable on mobile.

## Accessibility
- [ ] Contrast remains usable.
- [ ] Focus is visible.
- [ ] Motion reduction is supported.
- [ ] Semantic meaning survives without motion.

## Simplification
- [ ] The effect can be simplified without breaking the read.
- [ ] Excess layers have been removed.
- [ ] The final result is clearer than the raw stack.
