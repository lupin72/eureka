---
name: lateral-alternatives
description: "Generate lateral ideas for a problem by listing deliberate alternatives for each element of the current approach, well past the first adequate one (de Bono's Alternatives). Use when the user asks for alternatives ideas on a brief, or wants a quick single-technique idea session that questions each piece of the usual way."
---

The Alternatives technique breaks the pattern of the obvious solution by refusing to stop at the first answer that works. The obvious solution is a bundle of elements, each chosen because it was the first adequate one; take each element, name what it is for, and keep listing other ways to serve that purpose after the adequate ones run out. The late alternatives, the ones you had to push for, are the lateral ones. Every idea comes from one alternative for one element, so that pair is the stimulus.

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

### 3. Name the elements

Break the Obvious solution, and the way things are done in the Current situation, into 4–6 elements: who acts, what they use, when it happens, where, through which channel, what triggers it. Name each element in a few words and give it a **fixed point**: the purpose it serves, stated without naming the element itself ("get the household to open the plan on Sunday", not "send the email").

Done when every element has a fixed point free of its current form.

### 4. Generate alternatives

For each element, list alternative ways to reach its fixed point:

1. Write down the adequate alternatives first, the ones that come easily. They clear the obvious out of the way.
2. Keep going for at least three more after the list feels finished. Change the actor, the resource, the moment or the scale; borrow how another field serves the same fixed point.
3. Mark the alternatives from the second round; they are where the ideas come from.

Turn the strongest second-round alternatives into ideas: what the user would do if that element worked that way. Keep the ideas that sit far from the Obvious solution and stay clear of Out of bounds. Judge feasibility lightly here; a later verifier tests it. When fewer than 5 survive, take a fixed point and push for three more alternatives.

### 5. Write the ideas file

Write `ideas/alternatives.md`:

- an `# Alternatives ideas` heading;
- an `Elements:` line followed by one list item per element, `- <element> (fixed point: <fixed point>)`, with its alternatives nested under it;
- 5–8 cards following the idea card contract, with the Technique field reading `Alternatives, alternative: \`<element> → <alternative>\``, the element named exactly as in the list, and the Movement saying how that alternative, applied to its fixed point, became the idea.

Done when every card carries all five fields and every card's element appears in the list.

### 6. Hand off

Tell the user the elements examined, list the card titles, give the session folder path, and offer to run `lateral-verify` on it to test each idea backwards from its end state. Leave verification to the user's answer.
