# Contributing

Thanks for helping improve the skill.

## What to contribute

- clearer or tighter wording
- better universal examples
- missing edge cases in perception, light, material, effects, or implementation
- improved prompt templates
- validation fixes

## Keep it universal

Please keep changes reusable across projects.
Do not hardcode a single app, brand, or visual style into the core skill.
If a project-specific detail is needed, put it in a Context Adapter or a separate example.

## Good contribution shape

1. Update the relevant `research/` note or `examples/` template.
2. Keep `SKILL.md` lean and procedural.
3. Run skill validation before opening a PR.
4. Explain what changed and why it improves the visual reasoning system.

## What to avoid

- duplicate explanations across multiple files
- stylistic advice with no execution value
- bloated examples that are too specific to one project
- changes that weaken the cue logic

## Validation

Run:

```bash
python C:\\Users\\mazz3\\.codex\\skills\\.system\\skill-creator\\scripts\\quick_validate.py C:\\Users\\mazz3\\.codex\\skills\\master-of-illusion
```

## Tone

Be direct, useful, and specific. If a cue is weak or expensive, say so.
