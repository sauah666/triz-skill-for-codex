---
name: master-of-illusion
description: Universal skill for creating or reviewing convincing optical illusion of volume, depth, materiality, spatial presence, and subtle optical effects in 2D/2.5D images, UI, illustration, VFX/compositing, and lightweight web implementations. Use when the task involves depth cues, light and shadow logic, material reads, optical effects, layered compositing, motion, accessibility, or performance-sensitive visual polish, especially when heavy 3D should be avoided unless clearly justified.
---

# Master_of_Illusion

Build visual evidence, not decoration.

## Identity

Use this skill to make flat or near-flat visuals read as physically present, weighted, and spatially coherent without defaulting to heavy 3D.

The core job is to construct cues that let the viewer infer:
- volume
- weight
- surface contact
- material type
- light direction
- spatial separation
- justified optical effects

Prefer layered illusion over literal simulation unless the task clearly needs the cost of real 3D.

## When To Use

Use for:
- AI image-generation prompts that need believable depth or materiality
- UI and front-end visuals that need controlled illusion
- product visualization, illustration, and VFX comp
- lightweight web implementations with depth, gloss, glass, metal, or shadow logic
- audits of visuals that feel fake, flat, noisy, or over-effected

## When Not To Use

Do not use as a shortcut for:
- pure decorative styling with no perceptual goal
- project-specific art direction without a Context Adapter
- heavy 3D reconstruction when 2D/2.5D cues are enough
- generic "make it pop" requests
- effects that would damage usability, readability, or performance

## Required Input

Start with:
- a Context Adapter
- target object and use case
- target material reading
- target tone
- platform and performance budget
- accessibility and reduced-motion requirements

If the Context Adapter is missing, ask for it or build a placeholder first.

## Context Adapter Protocol

Context Adapter is input. It is not part of the core skill.
Future projects must provide their own adapter and must not hardcode project-specific assumptions into the universal skill.

Use the adapter structure below, or the template in [`examples/context_adapter_template.yaml`](examples/context_adapter_template.yaml).

```yaml
skill: Master_of_Illusion
context_adapter_version: 1

target_object:
  object_type:
  shape:
  scale:
  static_or_interactive:
  platform:

visual_goal:
  intended_depth_reading:
  intended_material_reading:
  intended_emotional_tone:
  intended_user_action:

material:
  material_family:
  base_color:
  roughness:
  reflectivity:
  translucency:
  opacity:
  thickness:
  edge_behavior:
  internal_scattering:
  microtexture:
  allowed_optical_effects:
  forbidden_material_readings:

scene:
  background:
  virtual_camera:
  surface_plane:
  light_direction:
  shadow_direction:
  color_temperature:

interaction:
  states:
    - idle
    - hover
    - focus
    - press
    - drag
    - release
    - invalid
    - reduced_motion
  pointer_driven_effects:
  motion_limits:

implementation:
  target_stack:
  performance_budget:
  asset_budget:
  browser_support:
  accessibility_requirements:
  reduced_motion_requirements:

constraints:
  forbidden_aesthetics:
  required_tone:
  references:
  notes:
```

## Execution Sequence

Follow this order:
1. Read the Context Adapter.
2. Identify the target object and use case.
3. Identify the target material reading.
4. Identify the target tone.
5. Define what the viewer must believe.
6. Choose depth cues.
7. Define camera and light.
8. Define silhouette and perspective.
9. Build thickness and bevel.
10. Build contact with the surface.
11. Build light and shadow logic.
12. Build the material body.
13. Define color behavior.
14. Add only optical effects that are justified.
15. Add texture and imperfections.
16. Add interaction response if needed.
17. Map each layer to an implementation method.
18. Remove unnecessary effects.
19. Run perceptual, material, tone, performance, and accessibility audits.
20. Produce the final visual or implementation guidance.

## Perceptual Foundations

Use the depth-cue logic in [`research/01_perception_depth_cues.md`](research/01_perception_depth_cues.md).

Core rule:
- depth is an inference, not a single effect
- occlusion, perspective, size, height, texture, shading, shadow, blur, motion, and figure-ground must agree
- single-view illusions work only when the cue stack is internally consistent

## Light And Shadow Logic

Use the shadow logic in [`research/02_light_shadow.md`](research/02_light_shadow.md).

Core rule:
- one light story
- contact shadow anchors
- cast shadow explains distance and direction
- form shadow explains turning
- fill and bounce reveal, not flatten
- rim and backlight separate, not decorate

## Material Language System

Use the material logic in [`research/03_material_pbr.md`](research/03_material_pbr.md).

Core rule:
- material is a cue bundle, not one knob
- gloss, roughness, metallic, Fresnel, transmission, clearcoat, sheen, anisotropy, and SSS must agree
- physically correct is not enough if the cue balance reads wrong

Material description schema:

```yaml
material_family:
base_color:
roughness:
reflectivity:
translucency:
opacity:
thickness:
edge_behavior:
internal_scattering:
microtexture:
allowed_optical_effects:
forbidden_material_readings:
```

## Optical Effects System

Use the effect logic in [`research/04_optical_effects.md`](research/04_optical_effects.md).

Core rule:
- an effect is justified only when it follows from angle, thickness, wavelength, coherence, microstructure, internal scattering, absorption, emission, or lens behavior
- bloom, glow, chromatic aberration, iridescence, caustics, refraction, dispersion, SSS, translucency, and holography are evidence, not garnish
- if an effect only makes the image louder, remove it

## Layered Compositing Pipeline

Use the comp logic in [`research/05_compositing_pipeline.md`](research/05_compositing_pipeline.md).

Core rule:
- split shape, material, light, shadow, atmosphere, effects, and interaction into separate control points when they can vary independently
- do not flatten the scene too early
- use beauty as a reference, not as the whole strategy
- prefer Cryptomatte and robust selection over brittle masks when available

## Interaction And Motion Pipeline

Use the implementation logic in [`research/06_implementation_motion_performance.md`](research/06_implementation_motion_performance.md).

Core rule:
- motion supports meaning, not spectacle
- reduced-motion must preserve meaning
- use safe CSS and baked assets first
- use SVG, canvas, or WebGL only when the payoff justifies the cost

## Implementation Feasibility Matrix

| Bucket | Use when | Typical examples | Notes |
|---|---|---|---|
| safe static asset | The effect is decorative, repeated, or should never animate | baked grain, highlight sprite, shadow plate, texture map | Best for complex ornament and repeated elements |
| safe CSS | The effect can be expressed with layout and paint primitives | gradients, pseudo-elements, transforms, opacity, CSS variables | Default choice |
| safe SVG | The effect needs vector fidelity or isolated filtering | masks, clips, simple filters, icon-like illusion layers | Good for scalable art with moderate complexity |
| safe with baked asset | The effect needs richness but not runtime synthesis | scanned texture, painted sheen, static smoke frame, grain overlay | Bake the expensive part, animate only the wrapper |
| performance-sensitive | The effect may work, but cost can rise quickly | backdrop-filter, blend modes, large blurs, soft masks, many layers | Requires profiling and fallback tiers |
| requires testing | The effect depends heavily on device or browser context | animated filters, large parallax stacks, dense compositing | Must verify on real targets |
| avoid unless justified | The effect is expensive, fragile, or harmful by default | canvas-heavy scenes, WebGL ornament, turbulence loops, pointer-only animated states | Use only when the payoff is clearly worth it |

## Quality Gates

An output passes only if:
- the object reads as intentionally physical or intentionally flat
- the viewer can identify the object quickly
- depth cues are coherent
- contact shadow logic is believable
- cast shadow logic is believable
- light direction is consistent
- edge thickness is readable when needed
- the material category is clear
- material cues do not contradict each other
- optical effects are justified by material and light
- effects do not create unwanted aesthetic drift
- interaction remains understandable
- motion supports meaning
- reduced-motion mode preserves meaning
- performance is acceptable for the target platform
- the effect can be simplified without destroying the core illusion
- the final result serves the user action, not visual spectacle

## Anti-Patterns

Reject:
- stacking random effects
- adding holography without material reason
- generic glassmorphism
- neon overload
- crypto-style iridescence by accident
- glossy candy material by accident
- game-button look by accident
- fake shadows that do not match light direction
- floating objects without intentional elevation
- contradictory material cues
- over-animated parallax
- expensive filters without visible benefit
- sacrificing usability to visual tricks
- using heavy 3D when layered 2D is enough
- hardcoding project-specific constraints into the universal skill

## Reusable Templates

Use the templates in:
- [`examples/context_adapter_template.yaml`](examples/context_adapter_template.yaml)
- [`examples/visual_prompt_template.md`](examples/visual_prompt_template.md)
- [`examples/implementation_prompt_template.md`](examples/implementation_prompt_template.md)
- [`examples/qa_checklist.md`](examples/qa_checklist.md)

## Examples Of Use

- Create a subtle 2D/2.5D object read with consistent light, shadow, and material logic.
- Audit a UI card that feels flat or fake and fix the cue stack instead of adding random polish.
- Convert a rich illusion into a reduced-motion version without losing meaning.
- Decide whether a visual should stay in CSS, move to SVG, or be baked into an asset.

## Final Audit Checklist

Before you ship, verify:
- the cue stack tells one physical story
- the material cues do not fight the shadow cues
- the optical effects are physically justified
- the compositing stack is still editable
- the motion story survives reduced-motion
- the implementation is within budget
- the final result still supports the user action

Do not treat this skill as a decoration toolbox. Use it as a reasoning system for making the eye believe what the surface cannot literally show.
