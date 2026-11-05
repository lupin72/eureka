---
name: lateral-random-entry
description: "Generate lateral ideas for a problem by forcing a connection with a genuinely random word (de Bono's Random Entry). Use when the user asks for random-word or random-entry ideas on a brief, or wants a quick single-technique idea session."
---

Random Entry breaks the pattern of the obvious solution by forcing the problem to collide with a word nobody chose. The word is drawn from the bundled `nouns.txt` by the shell, so the stimulus is genuinely unpredictable; a word the model picks itself is a pattern, not a stimulus.

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

### 3. Draw the random word

Run this from the shell, with `<skill-dir>` the folder holding this SKILL.md:

```sh
awk -v seed="$(od -An -N4 -tu4 /dev/urandom)" 'BEGIN{srand(seed)} {w[NR]=$0} END{print w[int(rand()*NR)+1]}' <skill-dir>/nouns.txt
```

Without a shell, take the current Unix time in seconds, compute `(time mod line count) + 1`, and use that line of `nouns.txt`.

The printed word is the stimulus, whatever it is. Take it exactly as drawn; its distance from the problem is the point.

### 4. Apply Random Entry

1. List 8–12 concrete properties of the word: its parts, functions, behaviours, settings, the people around it, what goes wrong with it.
2. Lay each property against the brief's Problem and ask what it would mean for the problem to work that way. Each forced connection is a **movement**: follow it forward until it lands on something the user could do.
3. Keep the ideas that sit far from the Obvious solution and stay clear of Out of bounds. Judge feasibility lightly here; a later verifier tests it.

When the word yields fewer than 5 ideas, draw a second word with the same command and repeat; card each idea with the word that produced it.

### 5. Write the ideas file

Write `ideas/random-entry.md`: a `# Random Entry ideas` heading, a line `Random word: \`<word>\`` (list every word drawn), then 5–8 cards following the idea card contract, with the Technique field reading `Random Entry, random word: \`<word>\``. Done when every card carries all five fields.

### 6. Hand off

Tell the user the word drawn, list the card titles, give the session folder path, and offer to run `lateral-verify` on it to test each idea backwards from its end state. Leave verification to the user's answer.
