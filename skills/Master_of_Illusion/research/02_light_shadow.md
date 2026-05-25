# 02 Light, Shadow, and Spatial Believability

## Purpose

This note turns light and shadow into a disciplined cue system for 2D / 2.5D volume, grounding, and material read.

## Vocabulary

- **Shape-from-shading**: form inferred from brightness changes.
- **Key light**: main light direction and main volume model.
- **Fill light**: softens contrast and reveals hidden form.
- **Rim light**: separates form from background.
- **Backlight**: light from behind that clarifies outline or translucency.
- **Negative fill**: removes light to restore mass and shape.
- **Bounce light**: light reflected from nearby surfaces.
- **Reflection card**: controlled reflection shape used to define glossy surfaces.
- **Form shadow**: shadow caused by the surface turning away from light.
- **Core shadow**: darkest part of the form shadow.
- **Cast shadow**: shadow projected onto another surface.
- **Contact shadow**: tiny dark anchor where object meets surface.
- **Ambient occlusion**: local crowding darkness in cavities and overlaps.
- **Penumbra**: softened shadow edge.
- **Shadow softness**: softness clue from source size and separation.
- **Shadow offset**: the gap and direction between object and cast shadow.

## Shadow Types And Their Role

- Cast shadows are strong cues for layout, separation, and motion inference.
- Form shadows reveal curvature and plane breaks.
- AO and contact shadows make objects feel grounded and physically present.
- Shadow softness and blur tell the eye about light size and distance from the receiver.
- Shadow direction consistency is critical. If shadows disagree, the form collapses.

## Lighting Setups That Matter

- **Matte surfaces**: use a soft key and gentle fill. Broad gradients usually read better than hard glare.
- **Reflective surfaces**: use diffusers, flags, and reflection cards. You are often lighting the reflection, not the object.
- **Transparent surfaces**: use backlight or edge light plus controlled background contrast.
- **Translucent surfaces**: use transmitted light through the object and soft side fill.
- **UI / 2.5D objects**: use one clear key direction, faint fill, a restrained contact shadow, and a small AO pass.

## Practical Recipes

- Soft product card: large soft key, opposite bounce, tiny soft contact shadow.
- Sculpted matte object: medium key, negative fill on shadow side, optional narrow rim.
- Reflective bottle or metal: broad diffusers left and right, black flags to carve edges, tiny kicker.
- Clear glass or acrylic: backlight through diffusion, dark cards for edge definition, careful front fill.
- Translucent material: stronger backlight than front light, soft side fill, visible thickness variation.

## How Light And Shadow Build Believability

- Volume appears when the viewer sees a believable turn from light into shadow.
- Materiality appears when highlights, shadow density, and edge crispness match the surface type.
- Contact shadows anchor the object to the scene.
- Cast shadows explain height and the direction of the light source.
- Fill and bounce should reveal form, not erase it.
- Rim and backlight should separate, not decorate.

## Step-by-Step Usage Procedure

1. Name the material first.
2. Choose the spatial story.
3. Pick one key light direction and keep it fixed.
4. Build form shadow and core shadow.
5. Add cast shadow and contact shadow.
6. Add fill or bounce only where form becomes unreadable.
7. Add rim or backlight only when separation is needed.
8. Add reflection cards or specular detail only if the material deserves them.
9. Animate shadow changes together with elevation or interaction state.
10. Check every state against the same light map.

## Common Mistakes

- Contradictory shadow directions.
- Missing contact shadows.
- AO that is too dark or too wide.
- Form shadow treated as a decorative gradient.
- Transparent material shaded like opaque plastic.
- Reflection cards used on dull surfaces.
- Shadow offset that ignores elevation or light angle.
- Shadow animation that jitters independently from the object.
- Rim light used like a glow tax instead of a spatial cue.

## What To Include In The Final Skill

- Cue-to-inference mapping for each light/shadow term.
- A layering order for static and interactive visuals.
- Rules for contact, cast, form, and occlusion shadows.
- Guidance for transparent and translucent surfaces.
- A coherence checklist for all interaction states.

## What To Exclude

- Full physical-lighting simulation when the task only needs convincing cues.
- One-off recipes tied to a single app or engine.
- Decorative blur or glow that does not help spatial reading.
- Advice that lets shadows wander independently of the object.

## Selected Sources

- [Perception of shape from shading](https://www.nature.com/articles/331163a0)
- [The perception of cast shadows](https://www.sciencedirect.com/science/article/pii/S1364661398012042)
- [Ambient Occlusion glossary](https://helpx.adobe.com/substance-3d-designer/using/glossary)
- [Ambient Occlusion baker](https://experienceleague.adobe.com/en/docs/substance-3d/bakers/bakers-settings/ambient-occlusion)
- [Product photography lighting guide](https://www.bhphotovideo.com/explora/photography/tips-and-solutions/raise-your-product-photography-game-with-the-right-gear)
- [Photographing glass: transparent glass lighting](https://blog.cmog.org/2018/photographing-glass-lighting-techniques-transparent-glass-objects)
- [NIST lab photography guide PDF](https://www.nist.gov/system/files/documents/2022/07/05/OSAC%202021-S-0027%20Standard%20Guide%20for%20Laboratory%20Photography%20-%20REGISTRY%20VERSION.pdf)
