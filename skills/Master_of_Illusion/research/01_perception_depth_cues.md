# 01 Perception, Depth Cues, and Optical Illusion

## Purpose

This note explains how flat images create perceived depth, how figure-ground separation works, and which cues usually matter most when the goal is convincing 2D or 2.5D illusion.

## Core Findings

- Depth from a flat image is an inference, not a measurement.
- The visual system combines multiple monocular cues instead of trusting one trick.
- Occlusion is one of the strongest cues because it answers "what is in front of what?"
- Relative size, relative height, linear perspective, texture gradient, shading, shadow, blur, and motion parallax all contribute.
- Figure-ground and Gestalt grouping happen before a viewer fully reads "depth."
- Single-view illusions work only when the cue stack stays consistent from one viewpoint.

## Useful Terminology

- **Monocular cue**: depth cue available from one view.
- **Occlusion / interposition**: if A blocks B, A is closer.
- **Relative size**: smaller retinal size often reads as farther away when the object is familiar.
- **Relative height**: on a ground plane, higher placement often reads as farther away.
- **Linear perspective**: parallel lines converge toward a vanishing point.
- **Texture gradient**: texture density increases with distance.
- **Aerial perspective**: distant forms lose contrast and often become hazier.
- **Shading**: light-dark variation that helps the eye read curvature.
- **Cast / contact shadow**: shadow placement anchors the object and explains distance from the surface.
- **Motion parallax**: nearer elements shift faster than farther elements when the viewer moves.
- **Figure-ground**: what reads as object versus backdrop.
- **Border ownership**: which side of an edge belongs to the object.
- **Anamorphosis**: a deliberately distorted image that only resolves from one viewpoint.
- **Forced perspective**: a physical scaling trick that exploits perspective.
- **Trompe-l'oeil**: an image that aims to fool the eye into seeing real space or objects.

## How Flat Images Create Depth

- Occlusion is a strong spatial claim. If one shape cuts over another, the top shape reads as nearer.
- Relative size works because the viewer expects familiar objects to keep a roughly stable physical size.
- Relative height and perspective help define a ground plane.
- Texture gradient lets the eye infer recession when texture elements get smaller or denser with distance.
- Shading and shadows help the viewer infer surface orientation and object separation.
- Blur and haze weaken local detail and can read as distance.
- Motion parallax is powerful for interactive or moving views because near and far layers shift differently.
- Figure-ground grouping makes the scene feel layered instead of pasted flat shapes.

## How Single-View Illusion Works

- A fixed-view illusion works by making one viewpoint internally consistent.
- Anamorphic art and forced perspective align cues so they only "click" from the intended position.
- Trompe-l'oeil usually combines overlap, shadow, edge treatment, perspective, and material detail.
- The illusion breaks when the viewer moves and the fake spatial logic no longer holds.

## Object / Background Separation

- The visual system first asks what belongs together, then what is in front of what.
- Gestalt cues such as proximity, similarity, continuity, closure, symmetry, and common region bind parts into one object.
- Figure-ground cues include convexity, lower region, symmetry, border continuity, and prior expectation.
- Background usually receives less attention and weaker memory than figure regions.
- Edge treatment is critical. If border ownership is ambiguous, the object feels weak or pasted on.

## Common Illusion-Breaking Mistakes

- Contradictory perspective lines or vanishing points.
- Shadows pointing against the presumed light source.
- Scale relationships that do not make sense together.
- Too little occlusion, so layers feel pasted.
- No hierarchy of blur, contrast, or detail.
- Flat or ambiguous edges that weaken border ownership.
- Texture that does not change with distance.
- Surface detail that is too clean or too uniform.
- In UI, too many depth tricks at once, which turns the interface noisy instead of legible.

## What To Include In The Final Skill

- A cue library that maps each depth cue to the inference it creates.
- A simple rule that depth must be built from multiple agreeing cues.
- Guidance for static images and interactive UI.
- Warnings about cue conflicts and viewpoint drift.
- A short list of cues that usually earn the most value per cost.

## What To Exclude

- Any claim that one cue is always the strongest in every scene.
- Project-specific art direction.
- Heavy 3D tricks when a layered 2D cue stack is enough.
- Shallow "make it feel deep" advice without cue logic.
- Hardcoded composition recipes that will not generalize.

## Selected Sources

- [Webvision: The Perception of Depth](https://www.ncbi.nlm.nih.gov/books/NBK11512/?report=reader)
- [Depth Cues in the Human Visual System](https://www.hitl.washington.edu/projects/knowledge_base/virtual-worlds/EVE/III.A.1.c.DepthCues.html)
- [Figure-ground mechanisms, Gestalt principles, and background vs figure attention](https://link.springer.com/article/10.3758/s13414-022-02511-5)
- [Figure and ground in the visual cortex](https://pure.johnshopkins.edu/en/publications/figure-and-ground-in-the-visual-cortex-v2-combines-stereoscopic-c-4/)
- [Illusory occlusion affects stereoscopic depth perception](https://www.nature.com/articles/s41598-018-23548-3)
- [Ames / anamorphosis / forced perspective overview](https://scholarworks.uni.edu/behrens_videos/10/)
