# AI Pipeline Kit

A structured, stage-gated development pipeline for Claude Code (and other AI assistants) that enforces design-before-code discipline and a virtual panel of senior engineer personas.

## What it does

Instead of asking an AI to "just build it", this kit enforces a structured pipeline where every task goes through analysis, proposal, design review, and implementation — with explicit human approval at each gate.

The result: AI-generated code that is traceable to a written design, reviewed by multiple specialist perspectives, and shipped with consistent quality.

## Pipeline

```
/analyze → [ Linear tasks created ] → per task:
/shape → /propose → /design → /implement → /review → /ship
```

| Stage | Output | Gate |
|-------|--------|------|
| `/analyze` | `.ai/spec.md` + Linear issues | User approves spec |
| `/shape` | Shared mental model (chat only) | User says "ready to propose" |
| `/propose` | `.ai/proposal.md` | User approves |
| `/design` | `.ai/design.md` | User approves |
| `/implement` | Code, following `design.md` exactly | — |
| `/review` | Code review vs artifacts | — |
| `/ship` | Final checklist + commit | — |

**`/analyze` runs once per project.** All other stages repeat per Linear task.

## Agent Panel

At each stage, a relevant subset of these personas is active and their perspectives are surfaced explicitly in the output:

| Agent | Expertise | Active during |
|-------|-----------|---------------|
| Principal System Architect | Distributed systems, OpenSpec contracts, ADRs | `/shape`, `/propose`, `/design` |
| Senior Backend Engineer | Node.js, TypeScript, TDD, clean API design | `/implement`, `/review` |
| Cybersecurity Specialist | Input validation, rate limiting, cheat prevention | `/design`, `/implement`, `/review` |
| DevOps Engineer | Docker, Kubernetes, AWS | `/design`, `/ship` |
| Observability Engineer | Structured logging, metrics, tracing, alerting | `/design`, `/implement`, `/review` |
| Principal Code Reviewer | Cross-cutting correctness and design fidelity | `/review` |

## Getting started

### 1. Drop your brief into `context/`

Add any combination of `.md`, `.pdf`, `.txt`, `.png`, `.jpg`, or `.yaml` files that describe what you're building.

```
context/
  my-brief.md
  architecture-diagram.png
  api-requirements.yaml
```

### 2. Run `/analyze`

```
/analyze
```

The AI reads every file in `context/`, writes `.ai/spec.md`, presents a task breakdown, and — on your approval — creates Linear issues for each task.

### 3. Work through each task

Pick a Linear issue and run the pipeline stages in order:

```
/shape      ← understand the task, surface unknowns
/propose    ← lock the problem and approach
/design     ← lock the technical design
/implement  ← code it
/review     ← review against the artifacts
/ship       ← final checklist and commit
```

## Directory structure

```
.
├── context/            ← Drop brief files here before /analyze
├── .ai/                ← Generated artifacts (spec, proposal, design)
│   ├── spec.md
│   ├── proposal.md
│   └── design.md
├── docs/
│   ├── openspec.yaml   ← API contract (generated during /design)
│   └── adr/            ← Architecture decision records
├── .claude/
│   ├── commands/       ← Slash command definitions
│   └── agents/         ← Agent persona definitions
├── CLAUDE.md           ← Rules for Claude Code
└── AGENTS.md           ← Rules for other AI assistants (Cursor, Copilot, etc.)
```

## Core rules

1. **No code without a design.** The AI will refuse to write implementation code if `.ai/design.md` doesn't exist and isn't approved.
2. **One stage at a time.** Each stage has a hard gate. The AI waits for explicit approval before moving forward.
3. **No silent deviations.** If implementation needs to diverge from `design.md`, the conflict is surfaced and requires approval.
4. **Gate commits are mandatory.** Approving `/propose` triggers a commit of `proposal.md`. Approving `/design` triggers a commit of `design.md`. These commits prove structured thinking happened.

## Compatibility

The pipeline is designed for **Claude Code** (`CLAUDE.md`) but the guardrails in `AGENTS.md` apply to any AI assistant that respects agent instruction files — including Cursor and GitHub Copilot.
