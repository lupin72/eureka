---
name: eureka
description: "Run a full lateral-thinking idea session on a brief: clarify it, pick 3–4 techniques, generate ideas in parallel, verify them backwards, and report a ranked shortlist. Use when the user wants new, non-obvious ideas for a problem, or names Eureka or `--all`."
---

Eureka turns a brief into a ranked shortlist of lateral ideas. It sets the obvious solution down as a baseline, runs several lateral-thinking techniques in isolation from each other, has every idea tested backwards from its end state by `lateral-verify`, and ranks what survives by how far it travels from the baseline. Isolation is the point: techniques that see each other's ideas converge, and a verifier that sees how an idea was born rationalises it.

Write these instructions' outputs in the language of the user's brief. The headings and field labels defined below are a contract read by other skills: keep them in English, and write everything under them in the brief's language.

## Technique selection table

This table is the only home of technique selection. One row per technique skill; `<technique>` (the ideas file name) is the skill name without its `lateral-` prefix.

| Technique | Skill | Summary | Pick when |
| --- | --- | --- | --- |
| Random Entry | `lateral-random-entry` | Draw a random concrete noun with the shell from the skill's bundled word list, list its properties, and force each property onto the problem until it moves to a usable idea. | The brief is stuck inside one frame or industry and needs an outside stimulus; works in any domain, so it is the default when few rows fit. |
| Provocation | `lateral-provocation` | Draw a provocation type (reversal, exaggeration, distortion, wishful thinking) with the shell, state deliberately unreasonable `PO` statements of that type about the problem, then use movement (extract a principle, focus on the difference, moment to moment, positive aspects, special circumstances) to reach usable ideas. | The brief rests on assumptions everyone in the field takes for granted (how things flow, who pays, what order things happen in), or the obvious solution is an incremental tweak of the status quo. |

## Session folder contract

```
eureka/<YYYY-MM-DD>-<slug>/
├── brief.md
├── ideas/
│   └── <technique>.md          # one per technique run, deduplicated
├── verification/
│   ├── <technique>.input.md    # the cards as the verifier saw them: no Movement
│   └── <technique>.md          # that file's verification section
├── verification.md             # all sections, assembled
└── report.md
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
- **Obvious solution**: the default answer anyone in the user's position would reach first. It is the baseline for lateral distance, so state it plainly and concretely.

`verification.md` and each `verification/<technique>.md` follow the verification file contract in `lateral-verify`: one `## ideas/<technique>.md` section per ideas file, one `### <card heading>` entry per card, each with exactly one Verdict (✅ / 🔧 / ❌).

## Idea card contract

Each ideas file starts with `# <Technique name> ideas` and holds 5–8 cards in this shape:

```markdown
## <n>. <Title>

**Description:** <2–3 sentences: what the idea is and how it works.>
**Technique:** <technique name>, <stimulus label>: `<stimulus>`
**Movement:** <the path from stimulus to idea: which property of the stimulus led where.>
**Problem it solves:** <one sentence tying the idea to the brief's Problem.>
```

A card that survives a merge lists every source in its Technique field, separated by `; `, and gains a line `**Convergence:** <the source technique names>`.

## Report contract

```markdown
# Report: <short title>

## Techniques

| Technique | Skill | Why |
| --- | --- | --- |
| <name> | `<skill>` | <why it suits this brief, or "named by the user" / "--all"> |

**Skipped:** <each wanted technique not installed, with its skill name; or "none">

## Shortlist

### <rank>. <Title>

**Card:** ideas/<technique>.md › <card heading exactly as in the ideas file>
**Source:** <source technique(s); "converged" when more than one>
**Verdict:** <the verdict line from verification.md>
**Why it ranks here:** <rationale: verdict, distance from the Obvious solution, convergence>
**Movement:** <the card's movement, from stimulus to idea>
**First step:** <one concrete action the user can take this week>

## Appendix

### <Title>

**Card:** ideas/<technique>.md › <card heading>
**Source:** <source technique(s)>
**Verdict:** <the verdict line from verification.md>
**Note:** <one line: the broken link and fix for 🔧, what it actually solves for ❌>
```

Every card in `ideas/` appears exactly once in the report, in the Shortlist or the Appendix, through its Card line.

## Process

### 1. Clarify

Create `eureka/<YYYY-MM-DD>-<slug>/` in the project root, taking the date from `date +%F` when a shell is available.

Map the user's brief onto Problem, Desired state, Current situation, Constraints and Out of bounds. Ask the user, in one message, only about the fields that are missing or ambiguous; a brief that fills all five runs without a single question, and Out of bounds counts as filled when the user said nothing is ruled out. Technique names and `--all` in the brief are selection instructions, not brief content.

Write `brief.md`, adding the Obvious solution yourself. Done when all six sections hold content drawn from the brief and the answers.

### 2. Select

Decide the wanted techniques:

- **`--all`**: every row of the selection table.
- **Named techniques**: the techniques the brief names, matched to table rows by name or skill name; they replace the automatic choice.
- **Otherwise**: 3–4 rows whose Pick when best fits this brief, each far from the others in how it moves.

Then check each wanted technique is installed: its skill appears among the skills available to you, or its `SKILL.md` exists next to this skill's folder (`<skill-dir>/../<skill>/SKILL.md`). A wanted technique that is not installed, or a named one with no table row, is skipped. When automatic selection loses rows this way, fill from the next-best installed rows; when fewer than three rows are installed, run every installed one.

Done when you hold the run list, each with a one-line reason tied to the brief, and the skipped list. Tell the user both before generating.

### 3. Generate

Spawn one sub-agent per technique in the run list, all in parallel, each with a fresh context window. Give each this prompt, filled in:

> Run the lateral-thinking technique **<Technique>** on the brief in `<session>/brief.md`. If you can invoke the skill `<skill>`, use it on that session folder. Otherwise apply the technique directly: <Summary>.
> Write 5–8 idea cards to `<session>/ideas/<technique>.md`, headed `# <Technique> ideas`, each card in this shape: <the card block from the idea card contract>.
> Keep the ideas far from the brief's Obvious solution and clear of its Out of bounds. Read only `brief.md`; leave the rest of the session folder alone. Skip any offer to verify: reply with the path you wrote and the card titles.

**Without sub-agents**, run the same prompt yourself, one technique at a time: write each technique's file before starting the next, and generate each from `brief.md` alone, leaving earlier ideas files unread.

Done when every technique in the run list has an ideas file with 5–8 cards carrying all five fields. Rerun a technique whose file falls short.

### 4. Deduplicate

Read every ideas file. Two cards are near-identical when realising one would realise the other: the same mechanism for the same people, whatever the wording. For each such group, keep the card from the technique listed first in the run list, merge the others' sources into its Technique field, add its Convergence line, fold the others' movements into its Movement, and delete the others from their files. Renumber headings within each file.

Done when no two remaining cards across files are near-identical. A file may drop below 5 cards here.

### 5. Verify

For each ideas file, write `verification/<technique>.input.md`: the same file with every `**Movement:**` line removed, all else unchanged. The verifier tests the idea, never its origin.

Spawn one `lateral-verify` sub-agent per input file, all in parallel, each with a fresh context window, using the skill's single-file mode:

> Use the skill `lateral-verify` in single-file mode. Brief: `<session>/brief.md`. Ideas file: `<session>/verification/<technique>.input.md`. Head the section `## ideas/<technique>.md` and write it to `<session>/verification/<technique>.md`. Read nothing else in the session folder.

Without sub-agents, run the same single-file verification yourself, one file at a time.

Assemble `verification.md`: a `# Verification` heading, then each `verification/<technique>.md` section in run-list order. Done when every card in `ideas/` has exactly one entry in `verification.md`.

### 6. Rank

Order every card:

1. **Adherence gate**: every ❌ goes to the Appendix.
2. **Chain state**: ✅ before 🔧.
3. **Lateral distance**: within each verdict, the further a card's end state sits from the Obvious solution (a different mechanism, actor or resource rather than a variant of it), the higher.
4. **Convergence** breaks remaining ties: more source techniques rank higher.

The Shortlist takes the top 5–10 cards of that order: all of them when fewer than 5 pass the gate, and stopping where the next card adds little beyond those above it. Everything else goes to the Appendix. Done when every card has a place.

### 7. Report

Write `report.md` following the report contract. Write each First step as an action the user could start this week within the Constraints. Then check: Shortlist size 5–10 (or every non-❌ card when fewer), no ❌ in it, ✅ entries before 🔧, and the Card lines cover every card in `ideas/` exactly once. Done when all four hold.

Then print a chat summary: the techniques run and skipped, the verdict counts, the shortlist titles with their verdicts, and the path to `report.md`.
