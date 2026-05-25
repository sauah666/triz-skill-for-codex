# Visual Generation Prompt Template

Create a [OUTPUT_TYPE] of [OBJECT_TYPE].

Object:
- shape: [SHAPE]
- scale: [SCALE]
- viewpoint: [CAMERA_ANGLE]
- depth reading: [DEPTH_READING]

Material:
- material family: [MATERIAL_FAMILY]
- base color: [BASE_COLOR]
- roughness: [ROUGHNESS]
- translucency: [TRANSLUCENCY]
- reflectivity: [REFLECTIVITY]
- edge behavior: [EDGE_BEHAVIOR]
- internal scattering: [INTERNAL_SCATTERING]
- microtexture: [MICROTEXTURE]

Lighting:
- key light: [KEY_LIGHT]
- fill light: [FILL_LIGHT]
- rim light: [RIM_LIGHT]
- shadow behavior: [SHADOW_BEHAVIOR]
- ambient occlusion: [AO_BEHAVIOR]

Optical effects:
- allowed: [ALLOWED_OPTICAL_EFFECTS]
- intensity: [EFFECT_INTENSITY]
- forbidden: [FORBIDDEN_OPTICAL_EFFECTS]

Composition:
- background: [BACKGROUND]
- figure-ground relation: [FIGURE_GROUND]
- visual tone: [VISUAL_TONE]

Constraints:
- avoid: [FORBIDDEN_AESTHETICS]
- must preserve: [REQUIRED_QUALITIES]
- output format: [OUTPUT_FORMAT]
