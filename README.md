# agentsmd

Starter for a new repository whose agents share one contract. The project bot scopes work and gives the go-ahead. An executor implements it from the repo alone, whether that executor is a Cursor cloud agent or a local Claude Code or Codex session.

## Start

1. Create a git repository from this template, or copy these files into a new repository and commit them. The first commit is the start of the project.
2. In `AGENTS.md`, set the tracker sentence. The default tracker is `context/work/`.
3. Create the project bot, a Grok Bot whose job is project manager. It owns `AGENTS.md` and `context/`. It writes work items and marks them `ready`. Implementation belongs to an executor.
4. Duplicate `context/example-operator.md` for each kind of work the project takes on. Add a row to the skill index in `AGENTS.md`. The number of skills grows with the project.
5. Copy `context/work/0001-example-work-item.md` for the first real item. Leave the specimen at `draft`, or delete it once a real item has replaced it and nothing still links to it.
6. Run `scripts/check-agent-docs`.

## Handoff

The bot writes the handoff into the repo. The executor picks it up from the repo. The two do not need a side channel.

1. The bot writes the context skill the work needs, when that skill is not already there.
2. The bot adds `context/work/` plus an id, a hyphen, and a slug. It fills Outcome, Acceptance criteria, and Handoff, then sets Status to `ready`. That status is the go-ahead.
3. An executor takes the item:
   - a Cursor cloud agent, or
   - the project owner, locally, in Claude Code or Codex.
4. The executor reads `AGENTS.md`, then the log and diff since the last reconciled commit. That commit is the newest subject containing `[nap]` or `[deep-sleep]`, or the root commit when none exists.

   ```
   git log <reconciled>..HEAD
   git diff <reconciled>..HEAD
   ```

   It reads the work item and the skills named on it, writes Pickup, does the work, and opens a pull request. The body comes from `.github/pull_request_template.md`.
5. The agent that ends the session reconciles the skills and work items with the commits and makes a `[nap]` commit.

Claude Code loads `CLAUDE.md`, which points at `AGENTS.md`. Codex and Cursor read `AGENTS.md`. A cloud agent and a local session see the same files.

On Erik's projects the project owner is Erik. Class 3 waits for him. Ask him before reverting a commit he made by hand.

## Nap and deep sleep

A nap is the end of a session. The subject contains `[nap]`. The commit reconciles context skills and work items with what the session actually changed. Git is the session state.

A deep sleep is the project owner's cleanup. It restructures and prunes context skills and work items, then commits with `[deep-sleep]` in the subject. The files stay in this repository.

## Layout

| Path | Purpose |
| --- | --- |
| `AGENTS.md` | Contract. Every session reads it. |
| `CLAUDE.md` | Pointer Claude Code follows into `AGENTS.md`. |
| `context/example-operator.md` | Specimen context skill. |
| `context/work/0001-example-work-item.md` | Specimen work item. |
| `.github/pull_request_template.md` | What changed, how to verify, change class, evidence. |
| `scripts/check-agent-docs` | Checks this contract. |
| `.github/workflows/agent-docs.yml` | Runs that check in CI. |
| `.gitignore` | Ignores `.env*` and keeps `.env.example` committable. |

## Check

```
scripts/check-agent-docs
```

The script checks the `AGENTS.md` line budget (aim 100, hard max 150), that referenced paths exist, that every instruction file is uppercase `AGENTS.md` with no case-only twin, and that these docs contain no absolute or home-directory path. It also checks the skill and work-item sections, the hard-rule table, and the env ignore rules. Remove `scripts/check-agent-docs` and `.github/workflows/agent-docs.yml` together if a project replaces them.

## References

- [AGENTS.md](https://agents.md) is plain markdown. The closest file to the work wins.
- [Codex](https://developers.openai.com/codex/guides/agents-md) merges nested instruction files from the repository root downward and truncates the combined text at 32 KiB.
- [Claude Code](https://code.claude.com/docs/en/best-practices) keeps the instruction file short. Linters and CI enforce what a machine can decide.
