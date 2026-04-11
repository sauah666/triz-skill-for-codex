# Contributing

Thanks for improving the TRIZ skill.

This repository is a public experiment, so sharp feedback is useful. If the skill fails on a real benchmark, that is a bug report, not a personal insult.

## What to keep in mind

- Keep the skill text in English.
- Keep `triz/SKILL.md` procedural and lean.
- Put denser background notes in `triz/references/`.
- Keep `triz/agents/openai.yaml` aligned with the skill name and tone.
- Do not paste copyrighted source text from books or PDFs into the repo. Summarize in your own words.
- Do not add secrets, private URLs, or internal-only context.

## Good changes

- tighter workflow steps
- clearer examples
- better prompt text
- cleaner references
- better publication docs
- stronger benchmark cases
- small fixes that improve short-mode reliability

## Before opening a PR

- run the repository audit script again
- check the README still explains what the repo does and how to use it
- verify the repo does not depend on hidden local state
- mention whether your change helps the short ladder, the public docs, or the benchmark behavior

## Style

- Prefer short, direct prose
- Prefer concrete examples over abstract advice
- Keep edits small and reviewable
- Do not paste source text from copyrighted books or PDFs
