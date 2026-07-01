# AI Dev Kit — Agent Guardrails

These rules apply to all AI assistants working in this repository (Cursor, GitHub Copilot, etc.).

## Pipeline

This project uses a structured development pipeline:

```
/shape → /propose → /design → /implement → /review → /ship
```

Do not skip stages. Do not write code before a technical design exists.

## Core Rules

1. **Never write implementation code without `.ai/design.md` existing and approved.** If asked to code before a design exists, ask the user to complete the design stage first.

2. **`TASK.md` is the task brief.** Read it to understand what is being built. Do not invent requirements.

3. **`.ai/proposal.md` is Gate 1.** The problem and approach are locked here. Do not contradict it.

4. **`.ai/design.md` is Gate 2.** The technical design is locked here. Follow it exactly. Surface conflicts rather than silently deviating.

5. **Interview mode.** Every line of code may be read aloud in an interview. Write clearly. No clever tricks. No unnecessary abstractions.

6. **One stage at a time.** Respect the pipeline. Each stage produces one artifact. Each artifact requires user approval before the next stage begins.

## Artifacts

- `TASK.md` — task brief (input, not generated)
- `.ai/proposal.md` — Gate 1 artifact
- `.ai/design.md` — Gate 2 artifact
