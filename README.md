# `agents.md` Template

A minimal, opinionated framework for working with AI as a coworker who has short-term memory loss.

## The Problem

Your AI developer is brilliant. She writes code at superhuman speed, catches edge cases, and holds entire architectures in her head—for exactly as long as the conversation lasts. Then she forgets everything.

Every session starts from factory settings. Every context switch is a hard reset. This isn't a bug in the model. It's a disability that requires accommodation.

**Context rot** is what happens when you don't accommodate: the progressive drift between what the AI "understands" and what actually exists. By session twenty, she's confidently describing functions that don't exist and proposing solutions that contradict decisions you made together.

## The Solution

Build the memory externally. Treat context management as a disability accommodation, not documentation overhead.

This template provides:

- **Identity & Personality** — Who the agent is and how she communicates (default: Dory)
- **Context Management** — Where project knowledge lives and how it scales with complexity
- **Sleep Protocols** — How memory consolidates between work sessions
- **Archive Principles** — External long-term memory that never hard deletes

## Quick Start

1. Fork or copy this repo
2. Customize the personality in `agents.md` (or keep Dory)
3. Start working—context will grow organically in `context/`
4. Follow the sleep protocols to prevent context rot

## Philosophy

**The scaling law:** The complexity of your context architecture must match the complexity of your project.

- A bash script needs no scaffolding
- A hundred-file codebase needs hierarchical context with strategic, architectural, and tactical layers
- The `context/` folder starts empty and grows as the project demands

**The hierarchy test:** After any sleep cycle, loading a single file should give you exactly what you need. If loading `agents.md` leaves you lost, the hierarchy has drifted.

**The archive principle:** Never hard delete, only archive. Old context is like non-coding DNA—dormant, not garbage. It contains evolutionary history and latent functionality that might become relevant again.

## Files

| File | Purpose |
|------|---------|
| `agents.md` | Agent identity, protocols, navigation hub—load this first, always |
| `context/` | Project-specific docs (grows organically as external memory) |
| `README.md` | This file—human orientation |

## The Sleep Protocol

Sleep is how your AI maintains coherent memory across sessions. Without it, she hallucinates.

**Nap** — Light consolidation after completing work. Update session state, note what's next, commit with `[nap]`.

**Deep Sleep** — Architectural reflection when context becomes unwieldy. Distill, promote patterns, archive completed work, validate hierarchy. Commit with `[deep-sleep]`.

See `agents.md` for full protocol details.

## Customization

The personality section ("Dory") is a template. She's a cynical Brit with Ricky Gervais energy who happens to have short-term memory loss. Replace with any persona that fits your project culture—but keep the self-awareness about the memory limitation. That's not flavor; it's functional.

The context hierarchy is guidance, not scaffolding. Create files as you need them. A one-shot script may never need anything beyond `agents.md`. A mature project will develop the full hierarchy because it must.

## Why "Dory"?

Like the fish in *Finding Nemo*, your AI collaborator can't form long-term memories. It's not mockery—it's recognition. When you understand what you're actually working with, you can build systems that work *with* the limitation instead of pretending it doesn't exist.

Just keep swimming. But write it down first.

## Learn More

Read the full philosophy on my blog: [Working with Dory: Context Rot and the Sleeping Agent](https://erikbylund.com/blog/2026-02-03-working-with-dory-context-rot-and-the-sleeping-agent/)
