# Master of Illusion

Universal skill for convincing optical illusion of volume, depth, materiality, spatial presence, and subtle optical effects in 2D / 2.5D visuals.

I built this first for my own workflow, because I wanted a disciplined way to stop fake-looking effects from hijacking the actual job of the image. I am publishing it because the same system may be useful to other people building prompts, UI, illustration, compositing, or lightweight implementation work.

## What this is

This repository packages a Codex skill that helps future agents:
- create convincing depth and material reads without defaulting to heavy 3D
- keep light, shadow, and material cues coherent
- decide when optical effects are justified and when they are just noise
- keep visuals accessible, editable, and performant

## When to use it

Use this skill when the task involves:
- 2D or 2.5D images that need volume or presence
- UI elements that should feel physical but still stay usable
- illustration or product visualization that needs a disciplined material read
- VFX or compositing work that depends on layered cue control
- web implementation where heavy rendering is not worth the cost

## When not to use it

Do not use it as a shortcut for:
- random decorative polish
- project-specific art direction without a Context Adapter
- heavy 3D reconstruction when layered cues are enough
- generic "make it pop" requests

## What it contains

- [`SKILL.md`](SKILL.md): the actual skill logic and workflow
- [`research/`](research): domain notes for depth, light, material, effects, compositing, and implementation
- [`examples/`](examples): reusable templates for future project adapters, prompts, and QA

## How to use it

1. Read [`SKILL.md`](SKILL.md).
2. Fill out the [`examples/context_adapter_template.yaml`](examples/context_adapter_template.yaml) for the project at hand.
3. Use the visual or implementation prompt templates from [`examples/`](examples).
4. Audit the result with [`examples/qa_checklist.md`](examples/qa_checklist.md).

## Why this may be valuable

- It gives agents a reusable mental model for volume, materiality, and spatial presence.
- It keeps the visual stack grounded in perception instead of vibes.
- It helps separate shape, light, shadow, material, and effects so problems stay fixable.
- It keeps motion and runtime cost under control.
- It makes it easier to build convincing visuals that still behave like usable interfaces.

## Repository structure

- `SKILL.md`: core skill
- `README.md`: human-readable overview
- `LICENSE`: MIT license
- `CONTRIBUTING.md`: how to contribute
- `CODE_OF_CONDUCT.md`: community behavior expectations
- `SECURITY.md`: issue reporting guidance
- `FAQ.md`: common questions
- `research/`: deep reference notes
- `examples/`: reusable templates

## Forks and reuse

Forks, remixes, and practical reuse are welcome.
If this helps you, cool. If it helps you build something better, even better.

## Design rule

- effects are evidence, not decoration
- light and material must agree
- motion must serve meaning
- reduced-motion and performance are part of the visual contract

## License

MIT. See [`LICENSE`](LICENSE).
