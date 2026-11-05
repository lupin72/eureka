# Eureka

Lateral-thinking idea generation skills: an orchestrator (`eureka`), nine technique generators (`lateral-*`) and a backward verifier (`lateral-verify`).

## Keeping skills in sync

Each skill is self-contained, so some text is deliberately duplicated. When you change one copy, change every copy:

- **A technique** is described in three places: its own `SKILL.md`, its row's Summary in the selection table of `eureka/SKILL.md`, and its row in the README skills table.
- **The shared contracts** (session folder, `brief.md` sections and their definitions, idea card) are repeated in every `SKILL.md`; `eureka` and `lateral-verify` also share the verification file contract, including the canonical Verdict lines and the Merged into rule. Keep them in sync, word for word where the wording is shared.

## Agent skills

### Issue tracker

Issues and specs live in GitHub Issues for `lupin72/eureka` (via `gh`). See `docs/agents/issue-tracker.md`.

### Triage labels

Default five-role vocabulary (`needs-triage`, `needs-info`, `ready-for-agent`, `ready-for-human`, `wontfix`). See `docs/agents/triage-labels.md`.

### Domain docs

Single-context: `GLOSSARY.md` and `docs/adr/` at the repo root. See `docs/agents/domain.md`.
