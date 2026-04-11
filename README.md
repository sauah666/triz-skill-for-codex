# TRIZ Skill for Codex

This repository packages a Codex skill for solving hard product, engineering, process, service, and strategy problems with TRIZ-style inventive thinking.

## What this is for

TRIZ is most useful when a normal fix creates a new problem:

- faster, but weaker
- safer, but slower
- simpler, but less capable
- more automated, but less controllable

The skill turns that tradeoff into a contradiction, then forces a short but explicit ladder: contradiction, IFR, resource, move, fast test.

## Theory base

This skill is not a fresh invention from scratch. It is a compact Codex-friendly synthesis of classical TRIZ and practitioner training material.

The core TRIZ idea is simple: do not settle for a compromise if the system can be changed so the contradiction disappears or is separated by time, space, condition, or hierarchy.

What this repo keeps from that theory:

- contradiction-first framing
- Ideal Final Result thinking
- resource analysis before adding new parts
- separation principles
- Su-Field logic
- trimming and idealization
- trends of system evolution
- a lightweight ARIZ-style sequence

The short ladder in `triz/SKILL.md` is the execution layer on top of that theory base.

## Status

This repository is a public experiment in making TRIZ usable inside a compact Codex skill. The goal is to keep the method disciplined without turning the trigger into a fat theory dump.

Expect the wording, examples, and benchmark notes to evolve as the skill gets tested on harder cases.

## What the skill does

When `triz/SKILL.md` is triggered, Codex will:

1. frame the system and the real pain point
2. write the technical or physical contradiction
3. define the Ideal Final Result
4. map existing resources before inventing new parts
5. choose the right TRIZ lane
6. generate concrete solution concepts
7. recommend the fastest useful experiment

Even in short mode, the answer must still show:

- contradiction
- IFR
- resource
- move
- fast test

## Who it is for

This repo is aimed at people who want a compact TRIZ helper, not a giant theory dump:

- product teams
- architects
- engineers
- agents doing worker-style implementation or design support

It is especially useful when the task is really a dilemma, not a vague brainstorm.

## Model fit

The skill is intentionally short and deterministic enough to stay useful on compact worker models. In practice that means it should remain comfortable on smaller reasoning budgets, including lightweight models in the `5.4 mini` class.

That said, the skill is not magic. If the task is a broad roadmap, a messy cross-team strategy call, or a problem that is not really a contradiction yet, a stronger model may still help with framing.

## Open license

This project is MIT licensed. In plain English, that means you can use it, copy it, modify it, publish it, and build on top of it, including for commercial work, as long as you keep the copyright and license notice.

There is no warranty. If you use it, you own the outcome.

## What is included

- `triz/SKILL.md` - the skill logic and workflow
- `triz/agents/openai.yaml` - trigger metadata for Codex surfaces
- `triz/references/triz-principles.md` - compact principle map
- `triz/references/source-notes.md` - source map and synthesis notes
- `triz/references/optimization-report.md` - the optimization history and benchmark notes
- `FAQ.md` - short human-readable answers about fit and usage

## Contributing

Contributions are welcome, especially if they make the skill more reliable, clearer, or easier to benchmark.

Good contributions include:

- sharper examples
- counterexamples that expose weak TRIZ moves
- tighter wording in the short ladder
- better public documentation
- benchmark cases that show where the method still slips

If you open a PR, keep it small and explain what changed and why.

## How to use it

Place the `triz/` folder where Codex discovers skills, then ask for it directly.

## Installation

This repo is not a package with a build step. To install the skill, copy or clone the `triz/` folder into your Codex skills directory.

Typical location on Windows:

```text
C:\Users\<you>\.codex\skills\triz
```

Typical location on macOS or Linux:

```text
~/.codex/skills/triz
```

After the folder is in place, restart Codex so it picks up the new skill. Then call it with `[$triz](./triz/SKILL.md)` or ask for TRIZ-style problem solving directly.

Examples:

```text
Use $triz to reduce onboarding friction without making the flow longer.
```

```text
Use $triz to redesign this process so it is faster and safer at the same time.
```

## Repository structure

```text
.
|-- README.md
|-- FAQ.md
|-- LICENSE
|-- .gitignore
|-- .env.example
`-- triz/
    |-- SKILL.md
    |-- agents/
    |   `-- openai.yaml
    `-- references/
        |-- triz-principles.md
        |-- optimization-report.md
        `-- source-notes.md
```

## Optimization pass

This skill was first refined to reduce context load, then refined again to restore stronger method discipline without blowing the size back up.

The report with the actual before/after metrics lives in [`triz/references/optimization-report.md`](triz/references/optimization-report.md).

## Publication notes

- License: MIT
- No secrets or private data are bundled
- No runtime dependencies are required
- The repository is documentation-first, so a fresh clone should be easy to inspect and reuse

## Sources

This skill is a synthesis of classical and training-oriented TRIZ material. The external PDFs are referenced, but not copied into the repository. See [`triz/references/source-notes.md`](triz/references/source-notes.md) for the bibliography and notes on what each source contributed.

## Search terms

People looking for this repo may search for:

- TRIZ
- contradiction-first problem solving
- Ideal Final Result
- resource analysis
- inventive problem solving
- ARIZ-lite
- product architecture
- process design
- service design

## License

MIT. See [`LICENSE`](LICENSE).
