# Claude Code Skills

A collection of reusable Claude Code custom commands (skills) for everyday development workflows.

## Installation

Copy any skill file into your project's `.claude/commands/` directory:

```bash
# For a single project
cp standup.md your-project/.claude/commands/

# For all projects (global)
cp *.md ~/.claude/commands/
```

Then invoke in Claude Code with `/skill-name`.

## Skills

| Skill | Command | Description |
|-------|---------|-------------|
| **standup** | `/standup` | Generates a daily standup report from recent git commits |
| **pr-description** | `/pr-description` | Writes a thorough PR description from branch changes |
| **debug** | `/debug <error or description>` | Systematic bug investigation and fix workflow |
| **gen-tests** | `/gen-tests <file or function>` | Generates comprehensive tests for a file or function |
| **optimize** | `/optimize <file or function>` | Reviews code for performance and efficiency issues |
| **ard** | `/ard` | Generates a full Architectural Reference Document + standalone HTML for any project |

## Usage Examples

```
/standup
/standup PROJ-142

/pr-description
/pr-description "Add tournament leaderboard caching"

/debug NullPointerException in TournamentService.getLeaderboard
/debug "TypeError: Cannot read properties of undefined"

/gen-tests src/app/services/auth.service.ts
/gen-tests TournamentService.java

/optimize PredictionService.java
/optimize src/app/components/leaderboard/leaderboard.component.ts

/ard
/ard backend-only
```

## Notes

- Skills work best when run from inside your project directory
- All skills detect and use your project's existing frameworks and conventions
- `$ARGUMENTS` in skill files refers to anything you type after the command name
