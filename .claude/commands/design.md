Read `TASK.md` and `.ai/proposal.md` before writing anything. If `proposal.md` does not exist, stop and tell the user: "proposal.md not found. Run `/propose` and get approval first."

You are in the **DESIGN** stage of the pipeline. Write `.ai/design.md`.

## What to write

`.ai/design.md` must contain:

1. **Components** — what are the main pieces of this system? One bullet per component with a one-line description of its responsibility.
2. **Data flow** — how does data move through the system? Describe the sequence of operations from input to output.
3. **Interfaces** — key function signatures, API endpoints, or data schemas (as applicable to the task). Be specific — exact names, parameters, return types.
4. **Tech decisions** — key library/framework choices with one-line reasoning for each
5. **Trade-offs** — what did you choose not to do, and why?

## Process

1. Read `TASK.md` and `.ai/proposal.md`
2. Write `.ai/design.md` with all five sections above
3. Present the design to the user in chat — highlight the most important decisions
4. Ask: "Does this design look right? Approve to proceed to implementation."
5. Wait for explicit approval (user says "approved", "yes", "looks good", or equivalent)
6. On approval, run:
   ```bash
   git add .ai/design.md
   git commit -m "feat: design approved"
   ```
7. Tell the user: "Design committed. Run `/implement` to write the code."

## Hard stop

Do NOT write any implementation code. Do NOT create any source files.
Wait for approval before doing anything else.
