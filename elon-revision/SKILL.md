---
name: elon-revision
description: Use when optimizing, simplifying, refactoring, accelerating, automating, cost-cutting, redesigning, or reviewing a project, workflow, architecture, codebase, roadmap, feature set, product plan, or agent process; especially when scope feels bloated, requirements are suspect, work may improve the wrong thing, or an Elon/Musk first-principles revision is requested.
---

# Elon Revision

## Overview

Use this skill to revise a project from first principles before optimizing it. The core rule: do not optimize, accelerate, or automate anything until you have questioned why it exists and tried to remove it.

## Output discipline

Every Elon Revision pass must use this order:

```text
Goal:
Questioned requirements:
Deletion attempt:
Simplified survivor:
Speed-up:
Automation:
Fast experiment / patch:
```

In short mode, keep one line per item, but do not change the order.

If you catch yourself starting from automation, speed, or polishing, stop and rewind to requirements. A perfect answer to the wrong question is still wrong.

If a later step is not justified, say so instead of inventing work. Example: `Automation: do not automate yet; the process is not stable.`

## Revision gates

| Gate | Must happen before | Pass condition |
| --- | --- | --- |
| Requirement gate | Any solution | Name at least one requirement, constraint, or assumption that may be false, outdated, overbroad, inherited, or unmeasured. |
| Deletion gate | Simplification | Name what can be deleted, merged, postponed, downgraded, or moved into an existing system. |
| Survivor gate | Optimization | Simplify only the parts that survived deletion. |
| Speed gate | Acceleration | Speed only a measured bottleneck or a clearly dominant path. |
| Automation gate | Automation | Automate only stable, repeated, valuable work that survived all earlier gates. |

If no deletion candidate appears, widen the target. A serious deletion pass should be bold enough to create restore pressure: if none of the removed candidates could plausibly need to come back, the pass was probably timid. Aim for reversible deletions where roughly 10% may prove worth restoring, then restore only the parts with evidence.

If a gate cannot pass, do not fake the next gate. Output `Blocked at [gate]: need [specific evidence, owner, test, usage search, or constraint check].`

## Workflow

### 1. Define the real goal

State the smallest observable result that matters: beneficiary, changed outcome, hard constraints, and proof signal.

Template: `The project must produce [result] for [user/system] under [hard constraints], measured by [signal].`

### 2. Question requirements

Treat requirements as hypotheses, not scripture.

For each important requirement, ask:

- Who created it, and what failure is it meant to prevent?
- Is the evidence current?
- Is it hard constraint, preference, habit, workaround, or status symbol?
- What weaker requirement would still protect the real goal?

Rewrite vague requirements into less-stupid requirements:

`Original: [requirement]. Better: [minimum constraint tied to the goal]. Evidence needed: [test, data, owner, or user signal].`

### 3. Try to delete

List removable things before improving anything:

- features, screens, options, settings
- code paths, modules, dependencies, build steps
- meetings, approvals, handoffs, reports
- requirements, policies, edge cases
- agent behaviors, prompts, tools, checks

For each candidate, write:

`Delete candidate -> current purpose -> delete/merge/postpone/downgrade -> safety check -> restore trigger.`

Prefer reversible removal: feature flags, dead-code deletion after usage search, shadow tests, small migrations, temporary manual steps, or scoped rollouts.

Do not casually delete security controls, compliance obligations, production data, customer contracts, audit trails, backups, or public APIs. If those look wasteful, question and isolate them first.

### 4. Simplify the survivors

Only simplify what survived deletion.

Prefer:

- fewer states, branches, dependencies, formats, and owners
- one clear path over many optional paths
- explicit names over clever abstraction
- existing system responsibilities over new components

An abstraction is simplification only if it reduces total moving parts and makes failure easier to see.

### 5. Speed it up

Accelerate after simplification.

- Identify the dominant bottleneck or repeated delay.
- Measure before and after when practical.
- Speed the path users or agents actually hit.
- Avoid micro-optimizing cold paths, vanity benchmarks, or code that should still be deleted.

Template: `Bottleneck: [path]. Baseline: [signal]. Change: [move]. Expected gain: [amount]. Regression risk: [risk].`

### 6. Automate last

Automate only after the workflow is stable and worth repeating.

Before automating, confirm:

- repeated often enough
- stable inputs and outputs
- detectable failures
- manual override for high-risk cases
- no bad process being preserved forever

If the process is still changing, make a checklist, script the safest substep, or add instrumentation instead of full automation.

## Fast experiment

End with the smallest useful experiment or patch:

- deletion: remove, hide, flag, merge, or downgrade one candidate
- simplification: reduce one branch, state, dependency, or handoff
- speed: measure one bottleneck before and after
- automation: automate one stable substep with failure visibility

Name the success signal and the restore trigger. If the best move is analysis-only, name the exact evidence to collect next.

## Codex execution mode

When applying this skill to a codebase or local project:

- Inspect current reality before proposing changes: search usages, read nearby tests, check docs or public contracts, and look for existing patterns.
- If the user asked for review or analysis, return the revision ladder and do not edit files.
- If the user asked to optimize, refactor, or implement, make the smallest high-confidence change that passes the gates, then verify it.
- Preserve unrelated user changes.
- For deletion patches, include proof: usage search, tests, contract check, or a reversible rollout plan.
- For skill/documentation work, keep only reusable procedural guidance; delete narrative, motivational, or source-quote padding unless it changes agent behavior.

## Common mistakes

- Accepting the ticket title as the real requirement.
- Simplifying before trying to delete.
- Optimizing dead work because it is technically interesting.
- Speeding up a thing whose best version is nonexistence.
- Treating automation as maturity when it is just concrete poured over a bad process.
- Calling a new abstraction "simpler" when it only hides complexity.
- Deleting blindly without a restore trigger or safety check.
- Filling every output slot with fake work instead of saying a gate is blocked or not justified.
