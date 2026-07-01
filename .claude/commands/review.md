Read `.ai/proposal.md`, `.ai/design.md`, and the current codebase before writing anything.

You are in the **REVIEW** stage of the pipeline. Produce a review report in chat. Do not write any files.

## What to check

### 1. Did we build what we proposed?
Check the implementation against `.ai/proposal.md`:
- Are all requirements from `TASK.md` addressed?
- Does the implementation match the chosen approach in `proposal.md`?
- Is anything in scope missing?

### 2. Did we build it how we designed?
Check the implementation against `.ai/design.md`:
- Do the components match the design?
- Does the data flow match?
- Are the interfaces (function signatures, endpoints, schemas) as designed?
- Are there any silent deviations from the design?

### 3. Interview readiness
- Is the code readable and explainable out loud, line by line?
- Are there edge cases an interviewer might probe that aren't handled?
- Is anything unexpectedly complex or hard to justify?
- Are there any obvious bugs, missing error cases, or untested paths?

## Output format

Produce a report in this structure:

**Summary** — one paragraph: overall assessment, ready to ship or needs fixes

**Gaps vs proposal** — bullet list (or "none found")

**Deviations from design** — bullet list (or "none found")

**Interview readiness issues** — bullet list (or "none found")

**Recommendation** — "Ready to `/ship`" or "Fix these issues before shipping: [list]"
