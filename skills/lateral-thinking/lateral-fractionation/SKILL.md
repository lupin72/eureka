---
name: lateral-fractionation
description: "Generate lateral ideas for a problem by breaking the situation into parts and recombining them in new ways (de Bono's Fractionation). Use when the user asks for fractionation ideas on a brief, or wants a quick single-technique idea session that rearranges what they already have."
---

Fractionation breaks the pattern of the obvious solution by dissolving the situation it was built for. The obvious solution treats the problem as one block with one known shape; cut the block into fragments, and the fragments can be put back together in arrangements the block never suggested. The fragments need not be the "true" components: any cut that yields pieces you can hold separately will do, and an unusual cut yields unusual pieces. Every idea is a recombination, so the fractions it joins are the stimulus.

Write these instructions' outputs in the language of the user's brief. The headings and field labels defined below are a contract read by other skills: keep them in English, and write everything under them in the brief's language.

## Session folder contract

Every Eureka skill reads and writes one session folder in the user's project:

```
eureka/<YYYY-MM-DD>-<slug>/
├── brief.md
└── ideas/
    └── <technique>.md
```

`<slug>` is 2–5 kebab-case words naming the problem. `brief.md` has exactly these sections:

```markdown
# Brief: <short title>

## Problem
## Desired state
## Current situation
## Constraints
## Out of bounds
## Obvious solution
```

- **Problem**: what is wrong or wanted, in one or two sentences.
- **Desired state**: the end point; what is true once the problem is solved.
- **Current situation**: the start point; resources, assets and context available today.
- **Constraints**: budget, time, skills, people, rules the solution must respect.
- **Out of bounds**: solutions or paths the user has ruled out ("none stated" is a valid answer).
- **Obvious solution**: the default answer anyone in the user's position would reach first. It is the baseline that later judges how lateral an idea is, so state it plainly and concretely.

## Idea card contract

Each ideas file starts with `# <Technique name> ideas` and holds 5–8 cards in this shape:

```markdown
## <n>. <Title>

**Description:** <2–3 sentences: what the idea is and how it works.>
**Technique:** <technique name>, <stimulus label>: `<stimulus>`
**Movement:** <the path from stimulus to idea: which property of the stimulus led where.>
**Problem it solves:** <one sentence tying the idea to the brief's Problem.>
```

## Process

### 1. Set up the session

If the user pointed at an existing session folder that holds a `brief.md`, use it and go to step 3.

Otherwise create `eureka/<YYYY-MM-DD>-<slug>/` in the project root, taking the date from the shell (`date +%F`) when one is available.

### 2. Clarify the brief

Map the user's brief onto the five fields (Problem, Desired state, Current situation, Constraints, Out of bounds). Then ask the user, in one message, only about the fields that are missing or ambiguous. A brief that fills all five runs without a single question; Out of bounds counts as filled when the user said nothing is ruled out.

Write `brief.md`, adding the Obvious solution yourself. Done when all six sections hold content drawn from the brief and the answers.

### 3. Fractionate

Take the situation of the brief (the Problem plus the Current situation) and cut it:

1. Split it into 2–3 parts along one line: by actor, by moment in time, by asset, by step of the process.
2. Split each part again into 2–3 smaller fragments, along a different line from the first cut where you can.
3. Make one more pass along a cut nobody in the user's position would make (by emotion, by place, by what each piece costs), adding its fragments to the list.

Name each fraction in a few words, concrete enough to picture. Done when you hold 10–16 fractions from at least two different cuts.

### 4. Recombine

Put fractions together in ways the current situation keeps apart:

- **Join** two or three fractions that never meet today, and ask what arrangement would make them one.
- **Detach** a fraction from the block it lives in and attach it to a different one.
- **Reorder** fractions in time: what happens if the last one comes first.

Each recombination that lands on something the user could do is an idea. Keep the ideas that sit far from the Obvious solution and stay clear of Out of bounds. Judge feasibility lightly here; a later verifier tests it. When fewer than 5 survive, cut along a new line and recombine again.

### 5. Write the ideas file

Write `ideas/fractionation.md`:

- a `# Fractionation ideas` heading;
- a `Fractions:` line followed by the fractions as a nested list, each part with its fragments under it;
- 5–8 cards following the idea card contract, with the Technique field reading `Fractionation, fractions: \`<fraction> + <fraction>\`` (every fraction the idea joins, named exactly as in the list, separated by ` + `), and the Movement saying how the recombination was made and why it produced the idea.

Done when every card carries all five fields and every card's fractions appear in the list.

### 6. Hand off

Tell the user the cuts made, list the card titles, give the session folder path, and offer to run `lateral-verify` on it to test each idea backwards from its end state. Leave verification to the user's answer.
