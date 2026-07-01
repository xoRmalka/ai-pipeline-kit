You are in the **SHIP** stage of the pipeline. Run a final checklist, then produce a submission summary.

## Checklist

Run each check and report pass/fail:

1. **proposal.md exists**
   ```bash
   test -s .ai/proposal.md && echo "PASS" || echo "FAIL: .ai/proposal.md missing"
   ```

2. **design.md exists**
   ```bash
   test -s .ai/design.md && echo "PASS" || echo "FAIL: .ai/design.md missing"
   ```

3. **TASK.md is filled in** (not just the blank template)
   ```bash
   grep -q "<!-- Paste the full interview task description here -->" TASK.md && echo "FAIL: TASK.md still blank" || echo "PASS"
   ```

4. **README explains how to run the project**
   Check manually: does README.md contain instructions for running the code?

5. **No uncommitted changes**
   ```bash
   git status --short && echo "(empty = PASS)"
   ```

## If all checks pass

1. If the git status check above shows a clean workspace (empty output), commit:
   ```bash
   git commit --allow-empty -m "feat: ship — task complete"
   ```
   If the workspace is dirty, stop here: "Uncommitted changes detected. Commit or stash your changes, then run `/ship` again."

2. Print submission summary in this format:

---
**Submission Summary**

**What was built:** [1 paragraph — what the project does and how to use it]

**Key technical decisions:**
- [decision 1 and why]
- [decision 2 and why]
- [...]

**Out of scope:** [bullet list of what was not built]

**How to run:**
[exact commands to install dependencies and run the project]
---

## If any check fails

List what's missing and stop. Do not commit. Tell the user what to fix before running `/ship` again.
