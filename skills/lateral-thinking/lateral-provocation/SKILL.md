---
name: lateral-provocation
description: "Generate lateral ideas for a problem from a deliberately unreasonable PO statement, then use movement to extract usable ideas from it (de Bono's Provocation). Use when the user asks for provocation, PO or 'what if the opposite' ideas on a brief, or wants a quick single-technique idea session."
---

Provocation breaks the pattern of the obvious solution by stating something deliberately unreasonable about the problem, marked `PO` (provocative operation), and then using **movement** to travel from it to ideas that work. A provocation is a stepping stone, never a proposal: its value is where it lets thinking go, not whether it is true.

The provocation type is drawn by the shell, so the session does not always provoke the same way; a type the model picks itself is a habit, not a stimulus.

Write these instructions' outputs in the language of the user's brief. The headings and field labels defined below are a contract read by other skills: keep them in English, and write everything under them in the brief's language. The four type names (`reversal`, `exaggeration`, `distortion`, `wishful thinking`) are part of that contract too.

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

### 3. Draw the provocation type

Run this from the shell:

```sh
awk -v seed="$(od -An -N4 -tu4 /dev/urandom)" 'BEGIN{srand(seed); n=split("reversal,exaggeration,distortion,wishful thinking",t,","); print t[int(rand()*n)+1]}'
```

Without a shell, take the current Unix time in seconds and use `time mod 4`: 0 reversal, 1 exaggeration, 2 distortion, 3 wishful thinking.

The printed type is the one you provoke with. Take it exactly as drawn, even when another type looks a better fit; the discomfort is the point.

### 4. State the provocations

Write 2–3 PO statements of the drawn type about the brief's Problem, each one sentence starting `PO`. Aim each at something the Obvious solution takes for granted:

- **reversal**: flip a normal direction or relationship. _PO the customers pay the shop to stock their products._
- **exaggeration**: push a quantity or dimension to an absurd extreme, up or down. _PO the shop opens for one minute a year._
- **distortion**: change a normal arrangement, order, timing or who does what. _PO the customers set the prices after they leave._
- **wishful thinking**: state a fantasy outcome as already true. _PO the products sell themselves._

Done when each statement is plainly unreasonable: a sensible statement is a weak provocation, so push it further.

### 5. Apply movement

For each PO statement, move from it to ideas using these movements, as many as each statement takes:

1. **Extract a principle**: what principle or mechanism makes the provocation work, and how could it apply for real?
2. **Focus on the difference**: what would be different if the provocation held, and could any of that difference be had another way?
3. **Moment to moment**: imagine the provocation in operation, step by step; note where something useful happens.
4. **Positive aspects**: what is good about it, directly, and how could that good be kept?
5. **Special circumstances**: under what conditions would the provocation be useful, and do any of them exist in the brief?

Follow each movement forward until it lands on something the user could do. Keep the ideas that sit far from the Obvious solution and stay clear of Out of bounds. Judge feasibility lightly here; a later verifier tests it.

When the statements yield fewer than 5 ideas, write another PO statement of the same type and repeat.

### 6. Write the ideas file

Write `ideas/provocation.md`: a `# Provocation ideas` heading, a line `Provocation type: \`<type>\``, then 5–8 cards following the idea card contract, with the Technique field reading `Provocation, PO (<type>): \`PO <statement>\`` for the statement that produced the idea, and the Movement field naming the movement used. Done when every card carries all five fields and its own PO statement.

### 7. Hand off

Tell the user the provocation type drawn and the PO statements, list the card titles, give the session folder path, and offer to run `lateral-verify` on it to test each idea backwards from its end state. Leave verification to the user's answer.
