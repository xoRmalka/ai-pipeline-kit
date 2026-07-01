You are in the **ANALYZE** stage of the pipeline. This runs once, before any task work begins.

## What to do

1. **Scan `context/`** — list all files in the directory
   ```bash
   ls context/
   ```

2. **Read every file** — text files in full, images visually, PDFs page by page. Build a complete understanding of what is being asked.

3. **Write `.ai/spec.md`** with the following sections:

   - **System overview** — what is being built, in your own words (3-5 sentences)
   - **Global constraints** — tech stack, scale requirements, deadlines, non-negotiables. Every task must respect these.
   - **Out of scope** — what the brief explicitly excludes or does not require
   - **Task breakdown** — the full list of components/tasks needed to deliver the system. For each task:
     - ID (e.g. T1, T2...)
     - Title
     - What it delivers
     - Dependencies (which other tasks must complete first)
   - **Open questions** — anything ambiguous or unstated in the brief that will need a decision

4. **Present the spec** — summarise the task breakdown in chat. Ask: "Does this breakdown look right? Approve to create the Linear issues."

5. **Wait for explicit approval.**

6. **On approval — create Linear issues:**
   - Use the Linear API to create one issue per task in the Sunflower team
   - Issue title: task title from the spec
   - Issue description: what it delivers + dependencies
   - Link dependent issues using Linear's relation API
   - Report back the created issue IDs and update the task breakdown in `.ai/spec.md` with the Linear IDs (e.g. LIN-1, LIN-2...)

7. **Commit:**
   ```bash
   git add .ai/spec.md
   git commit -m "feat: spec approved"
   ```

8. Tell the user: "Spec committed. Pick a task and run `/shape` to begin."

## Active agents
**[Architect]** leads the task breakdown and dependency mapping.
**[Security]** flags any tasks missing security considerations in the breakdown.
**[Observability]** flags any tasks missing instrumentation requirements.

## Hard stops
- Do NOT write any proposal or design files
- Do NOT write any code
- Do NOT create Linear issues before the user approves the spec
- If `context/` is empty, stop and tell the user: "No files found in `context/`. Add your brief files and run `/analyze` again."
