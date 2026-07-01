Read `TASK.md` before writing anything.

You are in the **PROPOSE** stage of the pipeline. Write `.ai/proposal.md`.

## What to write

`.ai/proposal.md` must contain:

1. **Problem** — restate the task in your own words (2-4 sentences). Show you understand it.
2. **Constraints** — bullet list of all constraints and requirements from `TASK.md`
3. **Approaches considered** — 2-3 approaches with brief trade-offs (2-3 sentences each)
4. **Chosen approach** — which approach you recommend and the key reason why
5. **Out of scope** — what you are explicitly not building in this task

## Process

1. Write `.ai/proposal.md` with all five sections above
2. Present the proposal to the user in chat — summarize the key decision
3. Ask: "Does this proposal look right? Approve to proceed to design."
4. Wait for explicit approval (user says "approved", "yes", "looks good", or equivalent)
5. On approval, run:
   ```bash
   git add .ai/proposal.md
   git commit -m "feat: proposal approved"
   ```
6. Tell the user: "Proposal committed. Run `/design` to write the technical design."

## Hard stop

Do NOT write design.md. Do NOT proceed to the design stage. Do NOT write any code.
Wait for approval before doing anything else.
