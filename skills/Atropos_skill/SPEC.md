# Atropos_skill Specification

## Intent

Provide Codex with compact, source-backed Atropos.js expertise for implementation, debugging, and review. The skill should prevent common integration failures before they happen, especially broken clicks/taps around transformed Atropos scenes.

## Scope

In scope:
- Atropos v2 package usage for core JavaScript, React wrapper, and web component.
- Web, mobile web, hybrid WebView, SSR/client-only integration, CSS imports, TypeScript declarations, performance, accessibility, and known bugs.
- Source-backed workaround guidance for Firefox hit-testing and touch pointer behavior.

Out of scope:
- Native React Native, iOS, or Android implementations not rendered through web/HTML.
- Unsupported Vue/Svelte package wrappers in current v2 packages.
- Unverified community snippets that cannot be tied to official docs, package metadata, source, issues, discussions, or reproducible behavior.

## Users And Trigger Context

- Primary users: coding agents implementing or fixing Atropos.js in a project.
- Common requests: add Atropos, fix Atropos clicks, use Atropos in React/Next, make Atropos mobile-safe, debug SSR/CSS/type errors.
- Should not trigger for generic CSS transforms, unrelated animation libraries, or native-only mobile motion effects.

## Runtime Contract

- Required first actions: inspect stack, installed Atropos version, CSS import path, interactive controls, touch/mobile requirements, and SSR constraints.
- Required outputs: implementation or diagnosis that includes click/tap safety and verification steps.
- Non-negotiable constraints: do not recommend current Vue/Svelte package imports unless the local package exports prove they exist; do not remove `transform-style: preserve-3d` as a Firefox click fix; do not server-import `atropos/element`.
- Expected runtime references: `hit-testing-touch.md` for interactive scenes; `integration-guides.md` for SSR/framework work; `troubleshooting.md` for bug work.

## Source And Evidence Model

Authoritative sources:
- Official Atropos docs and docs pages.
- Published npm/package metadata for `atropos`.
- Official GitHub source, changelog, issues, PRs, and discussions.

Useful improvement sources:
- Confirmed bug reports with reproduction details.
- Community workarounds inside official GitHub issues/discussions.
- Local verification results from real project usage.

Data that must not be stored:
- Secrets, private customer data, private URLs, or unreleased app implementation details.

## Reference Architecture

- `SKILL.md` contains runtime routing, first actions, defaults, and verification gates.
- `references/` contains flat, task-specific runtime guides.
- `SOURCES.md` contains source inventory, decisions, gaps, and maintenance notes.
- `scripts/` and `assets/` are intentionally absent in v1.

## Validation

- Lightweight validation: run the Agent Skills structural validator on the skill directory.
- Manual validation: check every reference named in `SKILL.md` exists and is directly relevant.
- Holdout examples: React card with CTA, Next/SSR import, Firefox click-target bug, mobile tap reliability.
- Acceptance gates: the skill must explicitly mention Firefox hit-testing, touch `preventDefault` risk, SSR custom-element risk, and current Vue/Svelte removal.

## Known Limitations

- Atropos source and docs can move after v2.0.2; re-check npm and changelog before major updates.
- Some workarounds are source-backed or issue-backed but not official shipped fixes.
- Browser hit-testing differences require real browser verification when user-facing CTAs are involved.

## Maintenance Notes

- Update `SKILL.md` only when the default workflow, trigger strategy, or required first actions change.
- Update `SOURCES.md` when sources, evidence confidence, or version truth changes.
- Update `references/troubleshooting.md` when new bug reports or fixes affect implementation decisions.

