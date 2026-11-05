---
name: lateral-six-hats
description: "Generate lateral ideas for a problem with de Bono's Six Thinking Hats used as a generator: the Green Hat produces raw ideas, then White, Red, Black and Yellow refine each one. Use when the user asks for Six Hats ideas on a brief, or wants raw creative ideas already shaped by facts, gut feeling, risks and benefits."
---

Six Hats here is a generator. The Green Hat produces raw ideas; White, Red, Black and Yellow then reshape each idea before it is written down. The four refining hats change the idea; they never judge it. Judging belongs to a later backward verifier, so every card leaves this skill as a better idea, never as a scored one.

Write these instructions' outputs in the language of the user's brief. The headings and field labels defined below are a contract read by other skills: keep them in English, and write everything under them in the brief's language. The hat names in the Technique and Movement fields stay in English too.

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

### 3. Green Hat: generate seeds

Wear only the Green Hat: alternatives, provocations, possibilities. Write 10–12 raw seeds, each one line, deliberately far from the Obvious solution and clear of Out of bounds. Quantity and distance matter here; nothing is assessed yet.

### 4. Refine each seed with the other hats

Take the seeds that sit furthest from the Obvious solution and pass each through four hats, in order. Each hat adds one change to the idea:

- **White** (facts): what facts in the brief, or checkable general facts, does the idea rest on or ignore? Reshape it to use the facts available in the Current situation.
- **Red** (gut): how would the people involved feel about it on first contact? Reshape it so the first contact draws them in.
- **Black** (risks): where could it go wrong under the Constraints? Reshape it to design the risk out.
- **Yellow** (benefits): where is its greatest value? Reshape it to make that value the centre of the idea.

Every hat output is a change to the idea, so the refinement ends on a revised idea rather than an assessment. When the Black Hat finds a risk it cannot design out, keep the seed and write the risk into the refined idea's Description as an open condition; dropping seeds is the Green Hat's choice alone.

Done when 5–8 seeds have passed through all four hats.

### 5. Write the ideas file

Write `ideas/six-hats.md`: a `# Six Hats ideas` heading, then 5–8 cards following the idea card contract:

- **Description**: the refined idea, as it stands after the Yellow Hat.
- **Technique**: `Six Hats, Green Hat seed: \`<the raw seed, one line>\``.
- **Movement**: one line, `White: <change>; Red: <change>; Black: <change>; Yellow: <change> → <how the seed became the refined idea>`.

Done when every card carries all five fields, its Technique names the Green Hat seed, and its Movement holds all four hats on a single line.

### 6. Hand off

List the card titles, give the session folder path, and offer to run `lateral-verify` on it to test each idea backwards from its end state. Leave verification to the user's answer.
