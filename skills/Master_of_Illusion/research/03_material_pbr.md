# 03 Material Perception and PBR-Informed 2.5D Rendering

## Purpose

This note turns material perception into a practical cue system for 2D / 2.5D illusion without requiring full 3D by default.

## Core Vocabulary

- **Shitsukan**: perceived material quality or feel.
- **Gloss**: perceived shininess or reflectance behavior.
- **Roughness**: how spread out the highlight reads.
- **Metallic**: whether the object reads as metal-like or dielectric.
- **Translucency**: light passes through but is scattered or softened.
- **Wetness**: a cue bundle involving gloss, chroma, highlight behavior, and surface context.
- **Sheen**: soft grazing response common in cloth or fibers.
- **Anisotropy**: directionally stretched reflection, common in brushed or fibrous surfaces.
- **Subsurface scattering**: light enters the body and exits elsewhere.
- **Fresnel**: angle-dependent increase in reflectance at grazing view.

## Cue Relationships

- Material perception is a bundle of signals, not one magical knob.
- Gloss depends on highlight behavior and surrounding context.
- Roughness is not the same as geometric bumpiness.
- Wetness often reads through stronger gloss, altered chroma, stain distribution, and context.
- Translucency sits between surface and volume.
- Softness and hardness are mostly haptic, but the eye infers them from edge behavior, deformation, and light spread.
- A physically correct material can still look wrong if the cue balance is off.

## Useful PBR Concepts

- **Base color / albedo**: non-shaded color cue.
- **Roughness**: strongest simple control for highlight spread.
- **Metallic**: separates metal-like tinted reflection from dielectric behavior.
- **IOR / Fresnel**: explains why edges often look shinier.
- **Normal / bump / displacement**: helps sell micro-structure.
- **Clearcoat / coat**: top layer for varnish, lacquer, wet film, and car paint.
- **Transmission / SSS**: useful for glass, skin, wax, milk, plastic, fruit.
- **Sheen**: useful for cloth, fibers, dust, velvet-like edge glow.
- **Anisotropy**: useful for brushed metal and directional textures.

## General Material Description Schema

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

## How Material Cues Sell Volume And Materiality

- Material cues help the viewer distinguish metal from glass, skin from wax, matte from glossy, and hard from soft.
- Edge behavior tells the eye how light wraps around the form.
- Roughness controls highlight spread and therefore perceived polish.
- Transmission and SSS suggest internal depth.
- Microtexture keeps the surface from reading as a computer-flat sticker.
- Fresnel behavior helps the material stay alive at grazing angles.

## Step-by-Step Usage Procedure

1. Name the material family.
2. Decide whether the surface is opaque, translucent, or transparent.
3. Choose the roughness / gloss regime.
4. Decide whether metallic behavior is allowed.
5. Decide whether a clearcoat or top layer is needed.
6. Add microtexture only after the body read is correct.
7. Add transmission, SSS, or anisotropy only when the material needs them.
8. Check whether the material still reads correctly under different lighting.
9. Remove any cue that contradicts the intended material family.

## Common Mistakes

- Treating gloss as one physical knob instead of a perceptual result.
- Using roughness as a synonym for bumpiness.
- Darkening albedo to fake wetness.
- Overusing opacity to fake translucency.
- Ignoring Fresnel, so the surface looks dead at the edges.
- Using colored specular on non-metals without reason.
- Mixing metalness values so badly that the material turns muddy.
- Assuming a correct PBR setup guarantees a correct perceptual read.

## What To Include In The Final Skill

- A material cue map that explains what each cue tells the viewer.
- A concise PBR-influenced decision path for 2D / 2.5D work.
- The YAML schema above.
- Guidance for when approximation is enough.
- Guidance for when real 3D or shader work becomes justified.

## What To Exclude

- Single-number material dogma.
- Heavy shader theory that does not affect cue choice.
- One-off stylization recipes.
- Anything that ignores context and lighting.

## Selected Sources

- [Material Perception - Annual Reviews](https://www.annualreviews.org/doi/10.1146/annurev-vision-102016-061429)
- [The perception of gloss: A review](https://www.sciencedirect.com/science/article/pii/S0042698914002594)
- [Shitsukan - the Multisensory Perception of Quality](https://brill.com/view/journals/msr/33/7/article-p737_3.xml)
- [Tactual perception of material properties](https://www.sciencedirect.com/science/article/pii/S0042698910004967)
- [The visual perception of wetness](https://eprints.soton.ac.uk/482855/1/2023_VisualWetness_JSS.pdf)
- [On the Nature of Perceptual Translucency](https://diglib.eg.org/items/f3f6a6c4-edad-4492-a06c-5a2bb0270c2b)
- [Principled BSDF - Blender Manual](https://docs.blender.org/manual/en/4.4/render/shader_nodes/shader/principled.html)
