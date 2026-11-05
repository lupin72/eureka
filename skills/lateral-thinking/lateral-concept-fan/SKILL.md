---
name: lateral-concept-fan
description: "Generate lateral ideas for a problem by stepping back from its goal to broad directions, then concepts, then concrete ideas (de Bono's Concept Fan). Use when the user asks for concept-fan ideas on a brief, or wants a quick single-technique idea session that widens the approaches considered."
---

The Concept Fan breaks the pattern of the obvious solution by refusing to start from it. The obvious solution is one concrete idea serving one concept; stepping back up the fan to the purpose, then fanning out through other directions and concepts, reaches ideas that never compete with it head-on. Every idea in the fan is reached from a concept, so the concept is the stimulus.

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

### 3. Build the fan

Work right to left, from the purpose to the ideas:

1. **Purpose**: the brief's Desired state in one line. If it already names a method ("more people using the reminders"), step back once more to what that method is for.
2. **Directions**: 3–5 broad approaches to the purpose, each a different mechanism or actor, not a variant of another. Write the Obvious solution's direction down and give it no further concepts; every other direction is the fan's real territory.
3. **Concepts**: for each remaining direction, 2–3 general methods of moving in it, each stated as a way of doing things ("make the household, not the user, the customer").
4. **Ideas**: for each concept, the concrete actions the user could take. A concept can serve as a new starting point: when it is still abstract, fan it again before landing on ideas.

Done when every concept holds at least one concrete idea and at least three directions carry concepts.

### 4. Choose the ideas

Keep 5–8 ideas spread across directions, preferring those far from the Obvious solution and clear of Out of bounds. Judge feasibility lightly here; a later verifier tests it. When fewer than 5 survive, add a direction and fan it.

### 5. Write the ideas file

Write `ideas/concept-fan.md`:

- a `# Concept Fan ideas` heading;
- a `Fan:` line followed by the fan as a nested list: `- Purpose: <purpose>`, under it each `- Direction: <direction>`, under each its `- Concept: <concept>`;
- 5–8 cards following the idea card contract, with the Technique field reading `Concept Fan, concept: \`<concept>\``, the concept named exactly as in the fan, and the Movement tracing purpose → direction → concept → idea.

Done when every card carries all five fields and every card's concept appears in the fan.

### 6. Hand off

Tell the user the directions explored, list the card titles, give the session folder path, and offer to run `lateral-verify` on it to test each idea backwards from its end state. Leave verification to the user's answer.
