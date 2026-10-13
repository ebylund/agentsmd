# 0001 Example work item

Specimen only. Status stays `draft`, so this file is not a go-ahead. Copy it for real work. Add a field or a section when a handoff needs it, and keep every required field and section until a deep sleep updates `scripts/check-agent-docs`.

Executor starts as `unassigned`. On pickup, set it to the tool or person doing the work: `cursor-cloud`, `claude-code`, `codex`, or a name.

- Status: draft
- Owner: project-bot
- Executor: unassigned
- Change class: 0
- Skills: context/example-operator.md

## Outcome

A later work item can be picked up from the repo alone: who wants the work, who executes it, when it may start, and what the next agent records.

## Acceptance criteria

- [ ] The copy names a real outcome.
- [ ] Status is `ready` before an executor starts.
- [ ] Pickup names the commit the executor started from, and any premise correction.
- [ ] `scripts/check-agent-docs` exits 0 when the session edits agent docs.

## Handoff

The project bot fills this section before setting Status to `ready`.

- Constraints: this specimen is not work. Leave it in `draft`.
- Out of scope: product code, until a real item exists.
- Repo facts the executor cannot guess: none.

## Pickup

The executor fills this section at the start, sets Executor to who picked the item up, and sets Status to `in-progress`.

- Started from commit:
- Premise corrections:

## Result

The executor fills this section when the work is finished, before the nap.

- Pull request:
- Checks run:
- Left undone:
