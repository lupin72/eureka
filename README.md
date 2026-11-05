# Eureka

Lateral-thinking idea generation skills for any agent host that supports `SKILL.md` skills, with any model.

## Install

```sh
npx skills add lupin72/eureka
```

## Skills

All skills live under `skills/lateral-thinking/`.

| Skill | What it does |
| --- | --- |
| `eureka` | The entry point. Clarifies your brief, picks 3–4 techniques that suit it, runs each in its own sub-agent, verifies every idea backwards, and reports a ranked shortlist. |
| `lateral-random-entry` | Forces your problem to collide with a random word drawn from a bundled list of ~2000 concrete nouns, and turns the collision into 5–8 idea cards. |
| `lateral-provocation` | States deliberately unreasonable `PO` statements about your problem, of a type drawn at random (reversal, exaggeration, distortion, wishful thinking), and uses movement to turn them into 5–8 idea cards. |
| `lateral-scamper` | Runs what exists today through Substitute, Combine, Adapt, Modify, Put to another use, Eliminate and Reverse, and writes 5–8 idea cards, each naming its operator. |
| `lateral-six-hats` | Generates raw ideas with the Green Hat, reshapes each with White, Red, Black and Yellow (no verdicts), and writes 5–8 idea cards showing the seed and its refinement. |
| `lateral-challenge` | Asks "why is it done this way?" until the assumptions behind the current handling surface, then drops or replaces each one, giving 5–8 idea cards that each name the assumption challenged. |
| `lateral-reversal` | Reverses the problem's directions (who acts on whom, what flows where, what comes first), then moves from each reversed form to 5–8 idea cards that each name the reversal applied. |
| `lateral-concept-fan` | Steps back from your goal to broad directions, then concepts, then concrete ideas, and cards each idea with the concept it came from. |
| `lateral-fractionation` | Breaks your situation into fragments and recombines them in new ways, carding each idea with the fractions it joins. |
| `lateral-alternatives` | Takes each element of the obvious solution and pushes for alternatives past the first adequate ones, carding each idea with its element and alternative. |
| `lateral-verify` | Tests ideas backwards: assumes each is realised, walks back to today in at most 7 steps, and gives each one verdict: ✅ adherent and walkable, 🔧 adherent with a link to fix, ❌ not adherent. |

## How a session runs

Give `eureka` a free-form brief in any language:

> Use eureka. Our neighbourhood library has lost half its visitors in two years. We want it full again on weekday afternoons. Budget is under €2,000, two staff, no building changes.

1. **Clarify.** It maps the brief onto five fields (problem, desired state, current situation, constraints, out of bounds), asks in one message about only the fields you left out, and writes `brief.md` with the obvious solution added as a baseline. A brief that fills all five runs without a question.
2. **Select.** It picks 3–4 techniques whose strengths fit the brief and tells you which and why. Name techniques in the brief to choose them yourself, or add `--all` to run all nine. Techniques that are not installed are skipped and reported.
3. **Generate.** Each technique runs in its own sub-agent with a fresh context, so techniques never see each other's ideas, and writes 5–8 idea cards to its own file. On hosts without sub-agents the techniques run one after another, each written before the next starts.
4. **Deduplicate.** Near-identical cards from different techniques merge into one that keeps every source and is marked as converged. The other cards stay in their files, marked with the card they were merged into, and are left out of verification and ranking.
5. **Verify.** `lateral-verify` runs once per ideas file, in parallel, on a copy of the cards with the Movement removed, so it tests the idea rather than how it was reached. It assumes each idea is realised, walks back to today in at most 7 steps, and gives one verdict: ✅ adherent and walkable, 🔧 adherent with a link to fix, ❌ not adherent.
6. **Rank.** ❌ ideas go to the appendix; the rest are ordered ✅ before 🔧, then by distance from the obvious solution, then by convergence across techniques.
7. **Report.** It writes `report.md` (the techniques and why, a shortlist of 5–10 ideas each with its movement and a concrete first step, and an appendix holding every other idea with its technique and verdict) and prints a summary in chat. The only exception to the 5-idea minimum: when fewer than 5 ideas pass the adherence gate, the shortlist holds all of them.

Every output follows the language of your brief.

## Session folder

Every session lives in a dated folder in your project. A full `eureka` session writes:

```
eureka/<YYYY-MM-DD>-<slug>/
├── brief.md                    # the five fields plus the obvious-solution baseline
├── ideas/
│   └── <technique>.md          # 5–8 idea cards per technique; duplicates marked, never removed
├── verification/
│   ├── <technique>.input.md    # the live cards as the verifier saw them, Movement removed
│   └── <technique>.md          # that file's backward chains and verdicts
├── verification.md             # all verification sections, assembled
└── report.md                   # techniques, ranked shortlist, appendix
```

Each idea card has a title, a description, the technique and its stimulus (a random word, a `PO` statement, a challenged assumption, …), the movement from stimulus to idea, and the problem it solves.

A standalone technique run writes only `brief.md` and `ideas/`; a standalone verifier run adds `verification/` and `verification.md`.

## Using a skill on its own

### A single technique

Invoke a technique skill with a free-form brief for a quick focused session, for example:

> Use lateral-random-entry. Our neighbourhood library has lost half its visitors in two years. We want it full again on weekday afternoons. Budget is under €2,000, two staff, no building changes.

It clarifies the brief the same way, writes its ideas file, then offers to run `lateral-verify` on the session; it never runs it on its own.

### Verifying ideas

Point `lateral-verify` at a session folder to (re-)verify every ideas file in it, for example after tightening the constraints in `brief.md`. Or give it your own list of ideas plus a brief: it creates a session folder, records your ideas in `ideas/own.md`, and verifies them. Either way it writes the stripped inputs and one section per ideas file under `verification/`, assembles them into `verification.md`, and never removes an idea. An existing `report.md` is then stale: ask `eureka` to rank and report that session again.

## Examples

`examples/` holds three briefs from different domains (a product, a non-profit, a personal problem in Italian) and, under `examples/reference/`, the session each produced, including one `--all` run. Run `eureka` on a brief and compare your session with its reference.
