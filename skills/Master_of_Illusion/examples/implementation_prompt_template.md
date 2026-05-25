# Implementation Prompt Template

Implement [TARGET_OBJECT] using [IMPLEMENTATION_STACK].

Goal:
Create a lightweight 2D / 2.5D illusion of [DEPTH_READING] and [MATERIAL_READING].

Layer stack:
1. [BASE_SILHOUETTE_LAYER]
2. [THICKNESS_LAYER]
3. [CONTACT_SHADOW_LAYER]
4. [CAST_SHADOW_LAYER]
5. [AMBIENT_OCCLUSION_LAYER]
6. [MATERIAL_BODY_LAYER]
7. [TEXTURE_LAYER]
8. [EDGE_LIGHT_LAYER]
9. [HIGHLIGHT_LAYER]
10. [OPTICAL_EFFECT_LAYER]
11. [INTERACTION_RESPONSE_LAYER]

Interaction states:
- idle: [IDLE_BEHAVIOR]
- hover: [HOVER_BEHAVIOR]
- focus: [FOCUS_BEHAVIOR]
- press: [PRESS_BEHAVIOR]
- drag: [DRAG_BEHAVIOR]
- release: [RELEASE_BEHAVIOR]
- invalid: [INVALID_BEHAVIOR]
- reduced motion: [REDUCED_MOTION_BEHAVIOR]

Implementation constraints:
- performance budget: [PERFORMANCE_BUDGET]
- asset budget: [ASSET_BUDGET]
- browser support: [BROWSER_SUPPORT]
- accessibility: [ACCESSIBILITY_REQUIREMENTS]
- forbidden techniques: [FORBIDDEN_TECHNIQUES]

Audit:
Run Master_of_Illusion quality gates before finalizing.
