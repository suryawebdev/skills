Write a thorough pull request description for the current branch's changes.

Steps:
1. Run `git log --oneline $(git merge-base HEAD main 2>/dev/null || git merge-base HEAD master 2>/dev/null)..HEAD` to list all commits on this branch
2. Run `git diff $(git merge-base HEAD main 2>/dev/null || git merge-base HEAD master 2>/dev/null)..HEAD --stat` to see the full file change summary
3. Read the most significant changed files to understand what actually changed
4. Check for any related test files to understand what was tested

Then produce a PR description in this exact format:

---
## Summary
[2–4 bullet points describing WHAT changed and WHY — focus on intent, not mechanics]

## Changes
[Bulleted breakdown by area, e.g. "**Backend:** ...", "**Frontend:** ...", "**Database:** ..."]

## Testing
[Checkbox list of what was tested — include both manual and automated]
- [ ] ...
- [ ] ...

## Notes
[Anything reviewers should know: migration steps, env var changes, feature flags, known limitations. Omit section if nothing notable.]

🤖 Generated with [Claude Code](https://claude.com/claude-code)
---

If $ARGUMENTS is provided, treat it as the PR title or ticket number and incorporate it.

Write as if a senior engineer is explaining their work to a teammate. No fluff.
