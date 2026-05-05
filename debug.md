Systematically investigate and fix the bug or error described in $ARGUMENTS.

Follow this debugging workflow:

**Step 1 — Reproduce**
- Identify the exact error message, stack trace, or unexpected behavior
- Find the entry point (endpoint, function, component) where it manifests
- Note the conditions required to trigger it

**Step 2 — Locate**
- Trace the call path from the entry point to where it fails
- Read all relevant files in the call chain
- Look for: null/undefined access, off-by-one errors, wrong assumptions, race conditions, timezone/encoding issues, missing null checks

**Step 3 — Understand the root cause**
- State the root cause in one clear sentence before touching any code
- If multiple causes are possible, list them ranked by likelihood

**Step 4 — Fix**
- Make the minimal change that addresses the root cause
- Do not refactor surrounding code unless it directly caused the bug
- If a workaround is tempting but hides the real issue, say so and fix the real issue instead

**Step 5 — Verify**
- After the fix, trace through the same call path mentally to confirm the error condition is resolved
- Check for edge cases the fix might introduce
- Run any existing tests covering the affected area

End with a one-paragraph summary: what the bug was, why it happened, and what was changed.

If $ARGUMENTS is empty, ask the user to describe the bug or paste the error message.
