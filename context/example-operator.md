# Example operator

Specimen context skill. Duplicate this file for a real kind of work, name the copy from the work item, and add that path to the index in `AGENTS.md`.

## Who

An executor changing the agent contract, a context skill, a work item, the doc check, or the README.

## When to load

The work item names this skill, or the change touches `AGENTS.md`, `CLAUDE.md`, `context/`, `.github/pull_request_template.md`, or `scripts/check-agent-docs`.

## How

1. Read the work item's Handoff before editing.
2. Keep root `AGENTS.md` at or under 100 lines. Procedure for one kind of work stays in a skill.
3. A new hard rule names the incident and its date, then lands in `scripts/check-agent-docs` when a machine can decide it.
4. Add a skill by copying this file. Index the new path from `AGENTS.md` in the same change.
5. Run `scripts/check-agent-docs` before the nap.

## Checks

- `scripts/check-agent-docs` exits 0.
- A hard rule with no incident date does not land. (judgment)
