---
name: triz
description: Use when the user wants to solve a hard design, engineering, process, service, or strategy problem with TRIZ/ТРИЗ; expose technical or physical contradictions; define the Ideal Final Result (IFR); map resources; and force a short but explicit ladder of contradiction -> IFR -> resource -> move -> fast test.
metadata:
  short-description: Solve hard problems with TRIZ
---

# TRIZ

Use this skill when a normal fix creates a new problem.

## Core rule

Start with the contradiction, not the idea.

Do not jump from framing to a solution concept. In short mode, the answer must still show `contradiction -> IFR -> resource -> move -> fast test`.

## When to use

- improving A makes B worse
- the same element must be opposite at once
- the function is missing, weak, or harmful
- the system is bloated
- you need a future-state roadmap
- brainstorming keeps looping

## Output discipline

Every answer must contain these five micro-elements in this order:

1. Contradiction
2. IFR
3. Resource
4. Move
5. Fast test

For benchmark, review, or high-stakes tasks, also show:

1. Problem frame
2. Mini-problem
3. Lane
4. Recommended path

## Workflow

### 1) Frame the system

- Say what it does, for whom, and what breaks.
- Define system, subsystem, supersystem, operating zone, and operational time.
- Template: `System does X for Y, but under C it causes Z.`

### 2) Write the mini-problem

- Reduce the story to the smallest blocked interaction.
- Template: `We need [useful action], but in the operating zone/time this causes [harm] or fails because [blockage].`

### 3) State contradictions

- Technical: `If we improve [A], [B] gets worse.`
- Physical: `Element [E] must be [A] and not-[A].`
- Write both when possible; the physical version is usually sharper.
- If you cannot state a contradiction yet, stop and reframe. Do not propose a move first.

### 4) Define IFR

- `The system itself delivers [result] without worsening [named contradiction side].`
- `The IFR must be observable, not promotional.`
- `The troublesome element disappears.`
- `The need disappears.`

### 5) Map resources

- Internal: parts, waste, by-products, unused properties
- Field: heat, pressure, vibration, gravity, magnetism, flow, software, information, attention
- Time: before, during, after, idle time
- Space: gaps, surfaces, boundaries, interfaces
- External: environment, neighbors, cheap materials
- Supersystem: upstream/downstream processes, infrastructure, nearby actors
- Rule: prefer existing, free, or low-cost resources.
- A resource is valid only if it names a usable property or action that can power the move.

### 6) Lock the ladder before concept generation

Before generating moves, make sure the answer already contains:

- one contradiction
- one IFR
- at least one concrete resource

If any of the three is missing, do not move to solution concepts yet.
If the resource cannot power a move, reframe the resource.
If the IFR does not answer the contradiction, rewrite the IFR.

### 7) Pick a TRIZ lane

#### Technical contradiction

Use filtered inventive principles, not a raw list. Start with:

- Segmentation
- Extraction
- Local Quality
- Asymmetry
- Merging
- Dynamics
- Another Dimension
- Feedback
- Convert Harm into Benefit
- Generate concrete moves only after naming the contradiction, the IFR, and at least one usable resource.

#### Physical contradiction

Try, in order:

1. time separation
2. space separation
3. scale or hierarchy separation
4. condition or state separation
5. material or field substitution
6. changing the game so the contradiction disappears

Questions:

- different times?
- different places?
- different scales?
- different conditions?
- can another substance or field satisfy one side?

#### Su-Field / standard solutions

Model the problem as `S1 - F - S2`.

Check whether the field is missing, weak, too strong, or harmful; whether a third element helps; or whether the interaction should move to another level.

#### Trimming / idealization

Ask:

- what useful function does this part provide?
- who else can provide it?
- can the part serve itself?
- can the supersystem take over?
- can the need disappear?

Preferred order: remove, merge, reassign, substitute, add only if needed.

#### Trends of evolution

Use for roadmaps and redesign.

Look for:

- increasing ideality
- dynamization
- supersystem shift
- macro to micro shift
- better feedback
- uneven development
- more substance-field use
- rhythm harmonization

### 8) Break inertia if stuck

- Size-Time-Cost
- Smart Little People
- Extreme IFR
- reverse viewpoint
- boundary shift

### 9) Escalate to ARIZ-lite if still stuck

1. Define the initial problem and hierarchy
2. Locate operating zone and operational time
3. Write the mini-problem
4. Write the technical contradiction
5. Convert it into a physical contradiction and IFR-1
6. Map resources
7. Generate concepts from separation, Su-Field, effects, or system transition
8. Translate back to a concrete concept
9. Verify the contradiction is actually gone

### 10) Evaluate concepts

Rank by:

- contradiction removed
- ideality increased
- existing resources used
- complexity reduced
- harmful effects contained
- cheap test available

If two concepts tie, choose the one that removes a part or uses an existing resource.
The recommended path must name one move and one fast test, not just a correct TRIZ genre.
The fast test must check both the improved side and the non-worsened side of the contradiction.

## Response format

### Required micro-ladder

- Contradiction: [improve X, but Y worsens]
- IFR: [existing system/resource] delivers [result] without worsening [Y]
- Resource: [existing thing] -> [usable property/action]
- Move: [TRIZ lane/mechanism] -> [concrete change]
- Fast test: prove [X] improves while [Y] does not worsen

### Full ladder for benchmark, review, or complex tasks

- Problem frame
- Mini-problem
- Lane
- Contradiction
- IFR
- Resource
- 2-5 moves
- Recommended path
- Fast test

Short mode may compress wording, but it may not skip the five micro-elements.

## Guardrails

- Do not dump 40 principles without filtering.
- Do not jump from contradiction to a move without explicit IFR and resource.
- Do not add a new subsystem before checking the current system and supersystem.
- Do not stay abstract; every abstract move must return as a concrete concept.
- Do not overfit the contradiction matrix to non-engineering problems.
- Do not rely on hidden reasoning to cover missing TRIZ steps; show the five micro-elements explicitly.
- Do not stop at naming the right lane; translate it into an actionable move.
- Blind compression that weakens method reliability is a harmful move.
- Do not write an IFR that sounds promotional or magical.
- Do not name a resource unless the move explicitly uses it.
- Do not use a move that could fit any problem without modification.
- Do not use a fast test that checks convenience only.

## References

- [references/triz-principles.md](references/triz-principles.md) for the full principle map and selection shortcuts.
- [references/source-notes.md](references/source-notes.md) for the source map used to synthesize this skill.
