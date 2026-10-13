# AGENTS.md

Contract for every agent in this repo. Plain markdown. The closest `AGENTS.md` to a changed file wins. Codex merges nested files from the repo root downward and truncates the combined text at 32 KiB.

Keep this file to rules that apply everywhere. Put area procedure in a context skill, or in a nested `AGENTS.md` when a subtree has its own rules.

## Roles

The project bot (a Grok Bot for this project) owns this file and `context/`. It scopes work, writes the work item, and gives the go-ahead. Implementation belongs to an executor.

An executor is a Cursor cloud agent, or a local Claude Code or Codex session. It starts from the repo alone. The handoff is the work item plus the context skills that item names.

## Session start

1. Read this file. The last reconciled commit is the newest subject containing `[nap]` or `[deep-sleep]`. With none, use the root commit.
2. Read `git log <reconciled>..HEAD` and `git diff <reconciled>..HEAD`. State premise corrections before proposing or editing. Where a doc and the diff disagree, the diff wins.
3. The project owner's hands-on commits are deliberate. Ask before reverting one. (judgment)

Name the reconciled commit, and any premise correction, in the first note of the session.

## Where authority lives

| Concern | Authority |
| --- | --- |
| Intent and status | The tracker |
| Executable truth | This repo |
| Docs disagree with code | Code |

Tracker: files in `context/work/`. To externalize, name GitHub Issues, Linear, or another tracker in place of this sentence. Keep a repo work item when the handoff still has to live next to the code.

## Change classes

| Class | What | Who may ship |
| --- | --- | --- |
| 0 | Docs, copy, or checks, with no behavior change | Executor |
| 1 | Behavior a check already covers | Executor |
| 2 | New behavior, API, schema, or dependency the work item names | Executor, after status is `ready` |
| 3 | Secrets, auth, billing, production data, irreversible migration, or a change the item marks class 3 | Project owner |

State the class on the pull request. Class 3 waits for the project owner. (judgment: an unlabeled change is class 3)

## Work items

Specimen: `context/work/0001-example-work-item.md`. A real file name is an id, a hyphen, and a slug. Required fields: Status, Owner, Executor, Change class, Skills. Required sections: Outcome, Acceptance criteria, Handoff, Pickup, Result.

Status is `draft`, `ready`, `in-progress`, `blocked`, or `done`. `ready` is the go-ahead. An executor starts an item only at `ready`, fills Pickup at the start and Result at the end, and stays inside the item.

Add a field or a section when the handoff needs it. Keep the required ones until a deep sleep changes the check.

## Context skills

A context skill is a file under `context/` outside `context/work/`. A project may have many. Required sections: Who, When to load, How, Checks. Load a skill when its When matches the task. This file is the index:

| Skill | Load when |
| --- | --- |
| `context/example-operator.md` | The task changes agent docs, or you are copying this skill's shape |

## Nap and deep sleep

A nap ends the session. Reconcile each skill and work item the session touched with the commits. Commit with `[nap]` in the subject. Git is the state.

A deep sleep is the project owner's cleanup. Restructure and prune context skills and work items. Delete a file the owner marks dead. Commit with `[deep-sleep]` in the subject. Both stay in this repo: no vault path and no home-directory path.

A nap is complete when the touched work items match the commits. (judgment)

## Hard rules

A new rule names its incident and that incident's date. Land it in `scripts/check-agent-docs` or CI when a machine can decide. Otherwise mark the row (judgment). A rule with no incident does not get a row. (judgment: the incident is real)

Dates on the starter rows are the day this template recorded the rule. Replace a date with the original incident date when you have it.

| Rule | Incident | Check |
| --- | --- | --- |
| Exact name `AGENTS.md`, one per directory, no case-only twin | macOS folded agents.md and AGENTS.md into one file, recorded 2026-10-13 | `scripts/check-agent-docs` |
| Every `AGENTS.md` stays at or under 150 lines, aim 100 | Long instruction files were skipped or ignored, recorded 2026-10-13 | `scripts/check-agent-docs` |
| No absolute path and no home-directory path in agent docs | Home and vault paths in shared docs, recorded 2026-10-13 | `scripts/check-agent-docs` |
| `.gitignore` ignores `.env*` and keeps `.env.example` committable | Env files need ignoring before the first secret is saved, recorded 2026-10-13 | `scripts/check-agent-docs` |
| No session-state file; git holds session state | Status docs went stale while the repo moved, recorded 2026-10-13 | `scripts/check-agent-docs` |
| `CLAUDE.md` is the single line `@AGENTS.md` | A second instruction file drifted from the contract, recorded 2026-10-13 | `scripts/check-agent-docs` |
| Skills and work items keep the sections named above | Prose-only gates caught nothing, recorded 2026-10-13 | `scripts/check-agent-docs` |

## Verify

Run `scripts/check-agent-docs` before a nap and on every pull request. CI is `.github/workflows/agent-docs.yml`. Build and test commands live in the skill for that kind of work.
