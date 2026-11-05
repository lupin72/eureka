---
name: lateral-reversal
description: "Reversal: generate lateral ideas for a problem by reversing its directions (who acts on whom, what flows where, what comes first) and moving from the reversed form to usable ideas (de Bono). Use when the user asks for reversal or flip-it-around ideas on a brief, or wants to see the problem from the other side."
---

Reversal breaks the pattern of the obvious solution by turning the problem around. Every problem carries directions it takes for granted: who acts and who is acted on, which way things flow, what comes first, who seeks whom. Reverse one and the problem is seen from the other side. The reversed form is rarely the answer itself; it is a stepping stone, and the ideas come from the movement away from it.

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

### 3. Map the directions

From the Problem, the Current situation and the Obvious solution, write down the relationships the problem runs on, each as a short statement with a direction:

- **Who acts on whom**: the provider serves the user, the teacher teaches the student.
- **What flows where**: money, information, goods, effort, attention.
- **What comes first**: the order of steps, cause before effect.
- **Who seeks whom**: who has to come, find, ask or remember.
- **What is fixed and what moves**: the place, the time, the product, the person.

Done when you hold 6–10 directional statements covering at least three of these kinds.

### 4. Apply Reversal

1. Reverse each statement: swap actor and receiver, send the flow the other way, put the last step first, make the fixed thing move. Write the reversed form as a plain statement ("the students teach the teacher", "the exam comes before the lesson"), however absurd it sounds.
2. Treat each reversed form as a stepping stone: ask what would be true in that world, what it would take, and what part of it could work here. That path is the **movement**: follow it until it lands on something the user could do.
3. Keep the ideas that sit far from the Obvious solution and stay clear of Out of bounds. Judge feasibility lightly here; a later verifier tests it.

When the reversals yield fewer than 5 ideas, reverse the same statements a different way (another element swapped, a partial reversal) and repeat.

### 5. Write the ideas file

Write `ideas/reversal.md`: a `# Reversal ideas` heading, then 5–8 cards following the idea card contract, with the Technique field reading `Reversal, reversal applied: \`<reversed statement>\`` and the Movement starting from the original direction it reversed. Done when every card carries all five fields and names the reversal it applied.

### 6. Hand off

Tell the user the reversals applied, list the card titles, give the session folder path, and offer to run `lateral-verify` on it to test each idea backwards from its end state. Leave verification to the user's answer.
