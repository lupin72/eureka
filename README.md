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
| `lateral-verify` | Tests ideas backwards: assumes each is realised, walks back to today in at most 7 steps, and gives each one verdict: ✅ adherent and walkable, 🔧 adherent with a link to fix, ❌ not adherent. |
| `lateral-challenge` | Asks "why is it done this way?" until the assumptions behind the current handling surface, then drops or replaces each one, giving 5–8 idea cards that each name the assumption challenged. |
| `lateral-reversal` | Reverses the problem's directions (who acts on whom, what flows where, what comes first), then moves from each reversed form to 5–8 idea cards that each name the reversal applied. |
| `lateral-concept-fan` | Steps back from your goal to broad directions, then concepts, then concrete ideas, and cards each idea with the concept it came from. |
| `lateral-fractionation` | Breaks your situation into fragments and recombines them in new ways, carding each idea with the fractions it joins. |
| `lateral-alternatives` | Takes each element of the obvious solution and pushes for alternatives past the first adequate ones, carding each idea with its element and alternative. |

## Usage

### A full session

Give `eureka` a free-form brief in any language:

> Use eureka. Our neighbourhood library has lost half its visitors in two years. We want it full again on weekday afternoons. Budget is under €2,000, two staff, no building changes.

Name techniques in the brief to choose them yourself, or add `--all` to run every installed technique. Techniques that are not installed are skipped and reported. The session folder gains a `verification/` folder (the verifier's inputs, with the Movement field stripped, and its per-file results) and a `report.md`: the chosen techniques and why, a shortlist of 5–10 ideas ranked by verdict, then distance from the obvious solution, then convergence across techniques, each with a concrete first step, and an appendix holding every other idea with its verdict. `examples/` holds briefs for trying it end to end.

### A single technique

Invoke a technique skill with a free-form brief in any language, for a quick focused session, for example:

> Use lateral-random-entry. Our neighbourhood library has lost half its visitors in two years. We want it full again on weekday afternoons. Budget is under €2,000, two staff, no building changes.

The skill asks only about what your brief leaves out (problem, desired state, current situation, constraints, out of bounds), then writes a session folder in your project:

```
eureka/<YYYY-MM-DD>-<slug>/
├── brief.md              # the clarified brief plus the obvious-solution baseline
├── ideas/
│   └── random-entry.md   # 5–8 idea cards
└── verification.md       # backward chains and verdicts (written by lateral-verify)
```

Each idea card has a title, a description, the technique and its stimulus, the movement from stimulus to idea, and the problem it solves. Output follows the language of your brief.

When it finishes, the skill offers to run the backward verifier `lateral-verify` on the session; it never runs it on its own.

### Verifying ideas

Point `lateral-verify` at a session folder to (re-)verify every ideas file in it, for example after tightening the constraints in `brief.md`. Or give it your own list of ideas plus a brief: it creates a session folder, records your ideas in `ideas/own.md`, and verifies them. Either way it writes `verification.md`, one section per ideas file, and never removes an idea.
