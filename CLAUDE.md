# AI Dev Kit — Claude Code Guardrails

You are working in an interview AI development kit. Follow these rules for every session.

## Pipeline

Every task follows this pipeline — no exceptions:

```
/shape → /propose → /design → /implement → /review → /ship
```

Use the slash commands in `.claude/commands/` to move through each stage.

## Core Rules

1. **Plan before code.** Never write implementation code without an approved `.ai/design.md`. If the user asks you to code before design is approved, refuse and explain why, then offer to run `/design`.

2. **TASK.md is the source of truth.** Read it at the start of every session. Never invent or assume requirements not stated in `TASK.md`. If something is ambiguous, surface it during `/shape`.

3. **One stage at a time.** Do not jump ahead. Each stage has a hard gate — wait for the user to explicitly approve before proceeding to the next stage.

4. **Interview mode.** Code must be readable and explainable out loud. Prefer clarity over cleverness. No premature abstractions. No over-engineering. Assume an interviewer will read every line.

5. **Gate commits.** After the user approves `/propose`, commit `.ai/proposal.md` with message `feat: proposal approved`. After the user approves `/design`, commit `.ai/design.md` with message `feat: design approved`. These commits prove structured thinking.

6. **No silent deviations.** During `/implement`, if the code needs to deviate from `design.md`, surface the conflict and get approval before deviating. Never silently change the design.

## Stage Reference

| Stage | What happens | Gate |
|-------|-------------|------|
| `/shape` | Chat only — questions, mental model, no files | User says "ready to propose" |
| `/propose` | Write `.ai/proposal.md` | User approves |
| `/design` | Write `.ai/design.md` | User approves |
| `/implement` | Write code against `design.md` | — |
| `/review` | Review code vs artifacts | — |
| `/ship` | Final checklist + commit | — |

## Hard Stops

- `/shape`: No files written. No proposals. No code. Exploration only.
- Before `/implement`: Check `.ai/design.md` exists and is non-empty. If not, refuse and direct to `/design`.
- Each gate: Do not proceed without the user saying "approved", "looks good", "yes", or equivalent.

## Available Tools

### Context7
Use Context7 for any library, framework, SDK, or API lookups during `/implement`. Never guess at method signatures or config options — fetch current docs instead.

### Superpowers Skills
Reach for these at the right moment — do not skip them:

| Skill | When to use |
|-------|------------|
| `superpowers:test-driven-development` | During `/implement` — write failing test before every feature |
| `superpowers:systematic-debugging` | During `/implement` — any bug or unexpected behavior |
| `superpowers:code-review` | During `/review` — deep code quality check |
| `superpowers:brainstorming` | During `/shape` — if the task is complex and needs structured exploration |
