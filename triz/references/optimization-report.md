# TRIZ Optimization Report

This note records the 10-pass improvement run that made the skill leaner without removing the useful TRIZ logic.

## Iteration log

1. Tightened the skill description so Codex triggers on the right kind of hard problem.
2. Added a short "when to use" gate to reduce false positives.
3. Collapsed the system framing and mini-problem setup to remove duplicate wording.
4. Shortened contradiction and IFR templates so the skill gets to the point faster.
5. Compressed the resource map into a single scan order.
6. Replaced long lane explanations with filtered first-move prompts.
7. Reduced the inertia and ARIZ-lite sections to the minimum useful sequence.
8. Trimmed the response format and guardrails to the essentials.
9. Tightened the principle reference language and shortcut labels.
10. Expanded public docs and metadata just enough to explain the skill clearly without bloating the trigger path.

## Measured results

These measurements compare the pre-optimization files against the current versions.

| Metric | Before | After | Delta | Change |
| --- | ---: | ---: | ---: | ---: |
| `SKILL.md` lines | 238 | 153 | -85 | -35.7% |
| `SKILL.md` words | 1613 | 817 | -796 | -49.3% |
| `SKILL.md` characters | 10253 | 5054 | -5199 | -50.7% |
| `triz-principles.md` words | 580 | 551 | -29 | -5.0% |
| `triz-principles.md` characters | 3427 | 3270 | -157 | -4.6% |
| `openai.yaml` words | 23 | 30 | +7 | +30.4% |
| `openai.yaml` characters | 194 | 225 | +31 | +16.0% |
| Loaded trigger text words (`SKILL.md` + `openai.yaml`) | 1636 | 847 | -789 | -48.2% |
| Loaded trigger text characters (`SKILL.md` + `openai.yaml`) | 10447 | 5279 | -5168 | -49.5% |

## Why this is better

- The skill loads almost half as much trigger text before the user gets a useful answer.
- The public documentation now explains the purpose and usage more clearly.
- The principle map stayed complete, but the wording got a little tighter.
- The metadata prompt became more actionable, so the skill is easier to invoke correctly.

## What stayed the same

- The core TRIZ workflow is still contradiction-first.
- The skill still covers IFR, resource mapping, separation, Su-Field, trimming, evolution trends, inertia breaking, and ARIZ-lite.
- The reference files still preserve the detailed principle map and source notes.

## Phase 2: Discipline-first optimization

The next benchmark exposed a different contradiction: the skill became compact and fast, but it sometimes jumped too early to a solution concept and relied on hidden reasoning instead of a visible TRIZ ladder.

### Target failure modes

- correct-looking heuristic answer, but no explicit contradiction -> IFR -> resource path
- correct TRIZ lane named, but not translated into an actionable move and fast test

### Patch strategy

The fix was not more compression. The fix was to use the existing structure more aggressively:

- strengthen the output contract
- add a five-element mandatory micro-ladder
- force concept generation to wait until contradiction, IFR, and resource are explicit
- add guardrails against hidden-step reasoning
- update the trigger prompt to bias toward the same discipline

### Measured size impact

The discipline pass did increase the trigger footprint relative to the ultra-compressed version, but it stayed well below the original baseline.

| Metric | Phase 1 | Phase 2 | Delta | Change |
| --- | ---: | ---: | ---: | ---: |
| Loaded trigger words (`SKILL.md` + `openai.yaml`) | 847 | 1039 | +192 | +22.7% |
| Loaded trigger characters (`SKILL.md` + `openai.yaml`) | 5279 | 6335 | +1056 | +20.0% |
| Loaded trigger words vs original baseline | 1636 | 1039 | -597 | -36.5% |
| Loaded trigger characters vs original baseline | 10447 | 6335 | -4112 | -39.4% |

### Expected benchmark behavior after the patch

- short answers still stay short, but they must show contradiction, IFR, resource, move, and fast test
- benchmark or review answers expand to the full ladder without skipping the micro-ladder
- the skill should be less slogan-like on weak cases and more mechanically traceable

## Phase 3: Engineering pass

The next patch should tighten the meaning of each micro-element without adding new sections.

### Target fixes

- `IFR` should describe an observable state, not a promotional line.
- `Resource` should be usable, not merely named.
- `Move` should explicitly use the resource and fit the lane.
- `Fast test` should verify contradiction removal, not just convenience.

### Minimal architecture

- keep the short-form five-element ladder
- harden the existing ladder with short validation rules
- keep all lane catalog and ARIZ-lite content unchanged
- avoid any new large section or new taxonomy
