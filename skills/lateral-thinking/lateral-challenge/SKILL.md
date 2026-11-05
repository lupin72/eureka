---
name: lateral-challenge
description: "Generate lateral ideas for a problem by challenging the assumptions behind how it is handled today (de Bono's Challenge: \"why is it done this way?\"). Use when the user asks for challenge or assumption-busting ideas on a brief, or wants to question the way things are currently done."
---

Challenge breaks the pattern of the obvious solution by questioning why things are done the way they are. It is not criticism: the current way is not judged wrong, only treated as one way among others. Every feature of the current handling rests on an assumption that was once a good reason, a habit or an accident; drop or replace the assumption and a different path opens.

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

### 3. Surface the assumptions

Describe how the problem is handled today, from the Current situation and the Obvious solution: who does what, for whom, where, when, in what order, with which tools, paid by whom, and measured how. For each feature ask "why is it done this way?", and ask "why?" again of the answer; the assumption is what the answers take for granted.

Write each one as a plain statement the user would nod at ("dinners are planned for a whole week at once", "the app is used by one person per household"). Done when you hold 8–12 assumptions, spread across actors, timing, place, resources and purpose, and none of them restates a Constraint or Out of bounds: those are the user's rules, and they stay.

### 4. Apply Challenge

For each assumption, try both moves:

- **Drop it**: what if this were no longer needed or true? What does the problem look like without it?
- **Replace it**: what else could fill the role it plays? Name a concrete alternative.

Each move is a **movement**: follow it forward until it lands on something the user could do. Keep the ideas that sit far from the Obvious solution and stay clear of Out of bounds. Judge feasibility lightly here; a later verifier tests it.

When the assumptions yield fewer than 5 ideas, go back to step 3, ask "why?" one level deeper of the most fertile ones, and repeat.

### 5. Write the ideas file

Write `ideas/challenge.md`: a `# Challenge ideas` heading, then 5–8 cards following the idea card contract, with the Technique field reading `Challenge, assumption challenged: \`<assumption>\`` and the Movement saying whether the assumption was dropped or replaced, and with what. Done when every card carries all five fields and names the assumption it challenged.

### 6. Hand off

Tell the user the assumptions challenged, list the card titles, give the session folder path, and offer to run `lateral-verify` on it to test each idea backwards from its end state. Leave verification to the user's answer.
