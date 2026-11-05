---
name: lateral-verify
description: "Test ideas by backward verification: assume each idea is realised, walk back step by step to today, and give each a verdict (walkable, link to fix, or off-problem). Use when the user wants an Eureka session folder verified or re-verified, or wants their own list of ideas tested against a brief."
---

Lateral ideas are justified in hindsight, so this skill tests them in hindsight. It assumes each idea has already happened and walks backwards to the user's situation today, checking that the end point solves the brief's problem and that every step back respects the brief's constraints. It annotates every idea with exactly one verdict and keeps every idea: an idea that looks impossible is a lead, and losing it silently is the one unrecoverable error.

Write these instructions' outputs in the language of the user's brief. The headings and field labels defined below are a contract read by other skills: keep them in English, and write everything under them in the brief's language.

## Session folder contract

Every Eureka skill reads and writes one session folder in the user's project:

```
eureka/<YYYY-MM-DD>-<slug>/
├── brief.md
├── ideas/
│   └── <technique>.md
├── verification/
│   ├── <technique>.input.md    # the live cards as the verifier saw them: no Movement
│   └── <technique>.md          # that file's verification section
├── verification.md             # all sections, assembled
└── report.md                   # eureka's ranked report, built from verification.md
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

Each ideas file starts with `# <Technique name> ideas` and holds cards in this shape:

```markdown
## <n>. <Title>

**Description:** <2–3 sentences: what the idea is and how it works.>
**Technique:** <technique name>, <stimulus label>: `<stimulus>`
**Movement:** <the path from stimulus to idea.>
**Problem it solves:** <one sentence tying the idea to the brief's Problem.>
```

After deduplication a card may list several source techniques and carry a `**Convergence:**` line. A card that carries a `**Merged into:** ideas/<technique>.md › <card heading>` line is a duplicate represented by the card it names: it gets no verification entry. A **live card** is one without that line. The card may arrive with the Movement field already stripped.

## Verification file contract

`verification.md` holds one `##` section per ideas file, headed by its path relative to the session folder, and one `###` entry per live card, headed by the card's heading text exactly as written in the ideas file, in the same order:

```markdown
# Verification

## ideas/<technique>.md

### <n>. <Title>

**Verdict:** <one canonical verdict line, below>
**Adherence:** <does the realised end state solve the brief's Problem? One or two sentences.>
**Backward chain:**

1. <the idea, realised>
2. <what must be true just before step 1>
3. <…until a step achievable today>

**Broken link:** <🔧 only: step number, and the constraint it breaks>
**Possible fix:** <🔧 only: one concrete change that would mend that link>
**Actually solves:** <❌ only: the problem this idea does solve>
```

Each entry carries exactly one Verdict line, in its canonical form: emoji and label verbatim, in English like the field labels, whatever the brief's language. The three canonical forms are `✅ Adherent and walkable`, `🔧 Adherent, link to fix` and `❌ Not adherent`; nothing else goes on the line. Broken link and Possible fix appear on every 🔧 entry and only there; Actually solves appears on every ❌ entry and only there.

## The test

Read each card's Title, Description and Problem it solves. The test is of the idea as it stands, never of its origin: skip the Technique stimulus and Movement lines, and write every verdict, chain and fix in terms of the idea and the brief alone.

### Adherence

Picture the idea fully realised. Ask whether that end state delivers the brief's Desired state for the brief's Problem, as the brief states it rather than as the card's "Problem it solves" claims it. An idea that solves a neighbouring problem, or solves this one only for someone else, is not adherent.

### Backward chain

Step 1 is the idea, realised. Each next step answers "what must be true just before this?". Stop at the first step that is achievable today with the resources in Current situation; that step closes the chain.

- **Cap**: 7 steps. When step 7 is still not achievable today, end the chain there and write `Chain too long` as the Broken link.
- **Each step** is one concrete state of the world (a thing built, a person agreed, a sum raised), small enough to check against the Constraints.
- **Each link** is checked against Constraints and Out of bounds. Judge feasibility from the brief first, then general knowledge; where a web lookup is available, use it for checkable facts (prices, rules, whether something exists).
- **First broken link**: the link the user would hit first walking forward from today, which is the highest-numbered broken step.

### Verdict

Exactly one per idea, decided in this order:

1. ❌ **Not adherent**: the end state misses the brief's Problem. Write Actually solves.
2. 🔧 **Adherent, link to fix**: some link breaks a constraint or touches Out of bounds, or the chain is too long. Write Broken link (step number and constraint) and Possible fix.
3. ✅ **Adherent and walkable**: every link holds and the chain reaches today within 7 steps.

## Process

### 1. Find the input

- **Session folder**: the user names or points at a folder holding `brief.md` and `ideas/`. Verify every file in `ideas/`. Existing `verification/` files and `verification.md` are replaced: this is a re-run, typically after the user tightened the brief.
- **Own ideas**: the user supplies a list of ideas plus a brief. Create `eureka/<YYYY-MM-DD>-<slug>/` in the project root (date from `date +%F` when a shell is available). Map the brief onto Problem, Desired state, Current situation, Constraints and Out of bounds, ask the user in one message only about the fields that are missing or ambiguous, and write `brief.md`, adding the Obvious solution yourself. Then write `ideas/own.md` headed `# Own ideas`, one card per idea in the user's order: the user's wording as Title and Description, Technique `Own idea`, Movement `not given`, and Problem it solves from the user's words or, failing that, from the Description. From here on it is a session folder.
- **Single file**: a caller names one ideas file and an output path. Verify only the live cards of that file and write its section, in the verification file format, to that path. Steps 2 and 4 do not apply.

Done when you hold a `brief.md` with all six sections and every ideas file to verify.

### 2. Strip the inputs

Session folder only. For each `ideas/<technique>.md`, write `verification/<technique>.input.md`: the same file with every card that carries a Merged into line left out and every `**Movement:**` line removed, all else unchanged. From here on read the cards from these input files, so the verdicts rest on the idea alone. Done when every ideas file has its input file.

### 3. Verify every card

Run the test on each live card of each input file, in file order, and write that file's section, headed `## ideas/<technique>.md`, to `verification/<technique>.md` (in single-file mode, to the caller's output path). Then count: the `###` entries equal the live cards in that ideas file, and every heading matches. Done when the counts match for every file and every entry has Verdict, Adherence and Backward chain, plus the fields its verdict requires.

### 4. Assemble

Session folder only. Write `verification.md`: a `# Verification` heading, then each `verification/<technique>.md` section, in the order of the Techniques table in `report.md` when one exists, otherwise in file-name order. Done when every live card in `ideas/` has exactly one entry in `verification.md`.

### 5. Report

Tell the user the path of `verification.md`, the verdict counts (✅ / 🔧 / ❌), and the titles of the ✅ ideas. When the session folder holds a `report.md`, say that it is now stale, since its ranking rests on the previous verdicts, and offer to rebuild it by running `eureka`'s Rank and Report steps on this session folder. Leave the ideas files untouched.
