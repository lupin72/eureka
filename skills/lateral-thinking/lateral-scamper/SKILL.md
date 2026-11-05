---
name: lateral-scamper
description: "SCAMPER: generate lateral ideas for a problem by running the current solution through the seven operators (Substitute, Combine, Adapt, Modify, Put to another use, Eliminate, Reverse). Use when the user asks for SCAMPER ideas on a brief, or wants to rework an existing product, process or service."
---

SCAMPER moves away from the obvious solution by taking what already exists apart and pushing each piece through seven operators: Substitute, Combine, Adapt, Modify, Put to another use, Eliminate, Reverse. Every operator is a fixed question, so the stimulus is the operator, not the model's taste: an idea that no operator produced is a pattern, not a movement.

Write these instructions' outputs in the language of the user's brief. The headings and field labels defined below are a contract read by other skills: keep them in English, and write everything under them in the brief's language. The operator names in the Technique field stay in English too.

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
**Movement:** <the path from stimulus to idea.>
**Problem it solves:** <one sentence tying the idea to the brief's Problem.>
```

## Process

### 1. Set up the session

If the user pointed at an existing session folder that holds a `brief.md`, use it and go to step 3.

Otherwise create `eureka/<YYYY-MM-DD>-<slug>/` in the project root, taking the date from the shell (`date +%F`) when one is available.

### 2. Clarify the brief

Map the user's brief onto the five fields (Problem, Desired state, Current situation, Constraints, Out of bounds). Then ask the user, in one message, only about the fields that are missing or ambiguous. A brief that fills all five runs without a single question; Out of bounds counts as filled when the user said nothing is ruled out.

Write `brief.md`, adding the Obvious solution yourself. Done when all six sections hold content drawn from the brief and the answers.

### 3. Break the situation into elements

List 6–10 concrete elements of what exists today, drawn from the Current situation and the Obvious solution: who is involved, what they use, the steps they go through, when and where it happens, what it costs, what it produces. Name each element specifically ("the Sunday planning screen", not "the UI").

### 4. Apply the operators

Run all seven operators, each as its question against the elements it bites on:

| Operator | Question |
| --- | --- |
| Substitute | What element could be swapped for another person, material, place, rule or moment? |
| Combine | What element could merge with another element, or with something outside the situation? |
| Adapt | What solution from another field, era or species already handles a problem shaped like this one, and how would it fit here? |
| Modify | What element could be made much bigger, smaller, more frequent, rarer, faster or slower? |
| Put to another use | What element, asset or by-product could serve a different purpose or a different audience? |
| Eliminate | What element could be removed entirely, and what would the situation look like without it? |
| Reverse | What order, direction or role could be flipped: last step first, user as provider, inside out? |

Each operator applied to an element is a **movement**: follow the answer forward until it lands on something the user could do. Keep the ideas that sit far from the Obvious solution and stay clear of Out of bounds; a mere tweak of the Obvious solution is not a lateral idea. Judge feasibility lightly here; a later verifier tests it.

Done when every operator has produced at least one candidate, and the 5–8 you keep span at least four different operators.

### 5. Write the ideas file

Write `ideas/scamper.md`: a `# SCAMPER ideas` heading, then 5–8 cards following the idea card contract, with the Technique field reading `SCAMPER, operator: \`<operator>\`` (the operator name exactly as in the table) and the Movement naming the element the operator was applied to and where that led. Done when every card carries all five fields and names exactly one operator.

### 6. Hand off

Tell the user the operators used, list the card titles, give the session folder path, and offer to run `lateral-verify` on it to test each idea backwards from its end state. Leave verification to the user's answer.
