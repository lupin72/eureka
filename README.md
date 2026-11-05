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
| `lateral-random-entry` | Forces your problem to collide with a random word drawn from a bundled list of ~2000 concrete nouns, and turns the collision into 5–8 idea cards. |

## Usage

Invoke a skill with a free-form brief in any language, for example:

> Use lateral-random-entry. Our neighbourhood library has lost half its visitors in two years. We want it full again on weekday afternoons. Budget is under €2,000, two staff, no building changes.

The skill asks only about what your brief leaves out (problem, desired state, current situation, constraints, out of bounds), then writes a session folder in your project:

```
eureka/<YYYY-MM-DD>-<slug>/
├── brief.md              # the clarified brief plus the obvious-solution baseline
└── ideas/
    └── random-entry.md   # 5–8 idea cards
```

Each idea card has a title, a description, the technique and its stimulus, the movement from stimulus to idea, and the problem it solves. Output follows the language of your brief.

When it finishes, the skill offers to run the backward verifier `lateral-verify` on the session; it never runs it on its own.
