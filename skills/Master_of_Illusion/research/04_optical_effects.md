# 04 Optical Effects System

## Purpose

This note defines optical effects as evidence of material and light behavior, not as decoration.

## Core Rule

An optical effect is justified only when it follows from:
- angle of view
- thickness
- wavelength
- coherence
- surface microstructure
- internal scattering
- absorption
- emission
- light source shape and direction

If the effect only makes the image louder, remove it.

## Effect Vocabulary

- **Refraction**: light bends because the material changes light speed.
- **Transmission**: light passes through with tint, blur, or attenuation.
- **Fresnel behavior**: reflectivity rises at grazing angles.
- **Thin-film interference**: layered surfaces create angle-dependent color shifts.
- **Iridescence**: color changes with view angle due to structure or film effects.
- **Bloom / glow**: bright values spill into nearby pixels.
- **Caustics**: focused light patterns from refraction or reflection.
- **Chromatic aberration**: lens or system separates colors slightly.
- **Dispersion**: wavelength-dependent refraction splits light by color.
- **Subsurface scattering**: light enters a material, scatters inside, and exits nearby.
- **Translucency**: light passes through but is blurred and weakened.
- **Holography**: view-dependent interference or reconstruction pattern.

## What Each Effect Implies

| Effect | What it implies | When to avoid |
|---|---|---|
| Refraction | Transparent or semi-transparent medium with a different refractive index | Opaque matte materials |
| Transmission | Material lets light through | Dense, blocking objects |
| Fresnel | Smooth surface with angle-dependent reflectivity | Chalky, dusty, deeply rough surfaces |
| Thin-film | A real layered coating or film | Generic rainbow paint |
| Iridescence | Microstructure or angle-dependent spectral response | Rainbow styling with no angle logic |
| Bloom / glow | Intense emission or sensor spread around bright values | Universal beautifier |
| Caustics | A curved or refractive surface focuses light onto another surface | Random squiggles with no source path |
| Chromatic aberration | Lens/system artifact | Premium filter on the subject |
| Dispersion | Wavelength separation in a refractive medium | Materials that cannot split colors |
| SSS | Translucent volume with internal scatter | Hard opaque surfaces |
| Translucency | Thin or scattering material that admits light | Full-opacity materials |
| Holography | Coherent-light-like view dependence | Anything merely shiny and colorful |

## Common Misuse Patterns

- Rainbow gradients without angle dependence.
- Bloom everywhere because it looks nice.
- Caustics with no refractive cause.
- Chromatic aberration used as a prestige filter.
- SSS on hard opaque materials.
- Holography for any shiny rainbow surface.
- Multiple optical effects stacked until material identity turns to mush.

## Step-by-Step Procedure

1. Identify the material first.
2. Identify the light situation.
3. Choose only the effects the material/light pair can justify.
4. Place the effect where the physics would occur.
5. Reduce effect strength until it supports the read.
6. Check whether the effect still makes sense from another angle or lighting setup.
7. Remove any effect that cannot survive that check.

## What To Include In The Final Skill

- A short material-to-effect decision rule.
- The effect-to-condition map.
- A rule that effects must be physically justified.
- A warning against rainbow, glow, and aberration abuse.
- A simple plausibility checklist.

## What To Exclude

- Artist-specific presets.
- Software-specific node graphs.
- Exotic edge cases that require specialist optics knowledge.
- Heavy physics derivations.
- Pure style recipes disconnected from material/light behavior.

## Selected Sources

- [Fresnel reflectance](https://www.graphics.cornell.edu/~westin/misc/fresnel.html)
- [Refraction of light](https://www.hyperphysics.phy-astr.gsu.edu/hbase/geoopt/refr.html)
- [Dispersion](https://labs.phys.utk.edu/mbreinig/phys222core/modules/m7/dispersion.html)
- [Thin-film interference](https://openbooks.lib.msu.edu/collegephysics2/chapter/thin-film-interference-2/)
- [Iridescence / structural color](https://mechse.illinois.edu/news/blogs/mechanics-structural-color)
- [Subsurface scattering](https://courses.washington.edu/arch481/1.Tapestry%20Reader/4.Rendering/b.Scattering/0.default.html)
- [Caustics](https://graphics.ucsd.edu/~henrik/images/caustics.html)
- [Chromatic aberration](https://micro.magnet.fsu.edu/primer/java/aberrations/chromatic/index.html)
- [Holography](https://pressbooks.online.ucf.edu/osuniversityphysics3/chapter/holography/)
- [Bloom / lens flare as imaging artifact](https://blogs.oregonstate.edu/amillionlittlecores/2022/04/21/post-processing/)
