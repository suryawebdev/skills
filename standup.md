Generate a concise daily standup report based on recent git activity in this repository.

Steps:
1. Run `git log --oneline --since="yesterday" --author="$(git config user.name)" 2>/dev/null || git log --oneline -10` to get recent commits
2. Run `git diff --stat HEAD~5 HEAD 2>/dev/null` to see files changed
3. Run `git status` to capture any in-progress work
4. Check for any open TODO comments in recently changed files

Then produce a standup report in this format:

---
**Yesterday**
- [summarize commits as human-readable accomplishments, not raw commit messages]

**Today**
- [infer logical next steps based on in-progress changes and open TODOs]

**Blockers**
- [list any merge conflicts, failing tests, or unresolved TODOs found — "None" if clean]
---

Keep each bullet tight — one line. No filler. Sound like a developer talking to their team, not a bot summarizing git history.

If $ARGUMENTS is provided, treat it as additional context (e.g. a ticket number or feature name) and weave it into the report.
