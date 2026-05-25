# 05 Layered Compositing Pipeline

## Purpose

This note defines how to build the illusion of believable volume, materiality, depth, and contact by keeping shape, material, light, shadow, atmosphere, effects, and interaction separable until the final composite.

## Core Principles

- Layered causality: each cue gets its own control point when possible.
- Depth is not one thing: silhouette, perspective, occlusion, thickness, shadow, and atmospheric loss are different jobs.
- Shape, material, light, and effects are different jobs.
- The illusion comes from cue stacking, not from one magic pass.
- Comp must preserve editability.
- AOVs are control surfaces, not decoration.

## Pass Vocabulary

- **Beauty / Combined**: the fully shaded render.
- **AOV / custom pass**: auxiliary output for a targeted comp task.
- **Light group**: grouped lighting contribution.
- **Cryptomatte**: robust object/material selection.
- **Shadow catcher**: receives shadow only.
- **AO**: local softness where geometry blocks ambient light.
- **Z / depth**: distance information.
- **Mist / depth haze**: atmosphere and separation.
- **Normal pass**: surface orientation.
- **Material body**: the visible mass of the object before effects.
- **Interaction response**: how the object changes when it touches other things.

## Universal Pass System

1. Context intake
2. Camera / viewpoint
3. Base silhouette
4. Perspective distortion
5. Thickness / bevel
6. Contact shadow
7. Cast shadow
8. Ambient occlusion
9. Material body
10. Color behavior
11. Texture / micro-noise
12. Rim / edge light
13. Specular highlights
14. Optical effects
15. Interaction response
16. Final simplification

## How To Bake Depth Into Layers

- Use Z or Mist for fog, atmospheric fade, or defocus.
- Use discrete near / mid / far bands when painterly separation is enough.
- Project textures onto planes or cards when 2.5D parallax is needed.
- Bake ambient occlusion or other static shading when runtime cost matters.
- Split artwork into shape, shadow, highlight, and effect layers for relightable 2D art.

## Common Mistakes

- Relying on beauty only.
- Using raw Z for everything.
- Flattening too early.
- Recombining passes in the wrong order.
- Using brittle ID masks instead of Cryptomatte.
- Mixing shape, material, light, and effects in one layer.
- Overusing AO until the frame looks dirty.
- Letting mist destroy local contrast where clarity matters.

## What To Include In The Final Skill

- A clear rule for separating shape, material, light, shadow, and effects.
- The universal pass system above.
- Guidance for beauty vs AOVs vs custom passes.
- Cryptomatte as the default selection system.
- Shadow catcher use cases.
- Depth handling guidance for Z, Mist, normals, and card-based depth.
- Recombination order rules.

## What To Exclude

- Full compositing recipes for every software package.
- Heavy theory that does not change decisions.
- One-off stylization tricks.
- Advice that encourages flattening depth into one universal mask.
- Brittle workflows that break under motion or recomposite.

## Selected Sources

- [Blender Passes](https://docs.blender.org/manual/en/latest/render/layers/passes.html)
- [Blender Cryptomatte](https://docs.blender.org/manual/en/latest/compositing/types/mask/cryptomatte.html)
- [Blender Matte Nodes](https://docs.blender.org/manual/en/3.4/compositing/types/matte/index.html)
- [Blender Ambient Occlusion Node](https://docs.blender.org/manual/en/latest/render/shader_nodes/input/ao.html)
- [Blender Shadow Catcher](https://docs.blender.org/manual/en/3.0/render/cycles/object_settings/object_data.html)
- [Foundry Nuke Cryptomatte](https://learn.foundry.com/nuke/content/reference_guide/keyer_nodes/cryptomatte.html)
- [Autodesk Arnold AOVs](https://help.autodesk.com/cloudhelp/ENU/AR-DevGuide/files/plugins/shaders/arnold_dev_guide_shading_lighting_av_aovs_html.html)
- [Autodesk Camera Map Per Pixel Map](https://help.autodesk.com/cloudhelp/2017/ENU/3DSMax/files/GUID-DBA6ABCC-86FC-47F9-841D-29D8A84086A6.htm)
