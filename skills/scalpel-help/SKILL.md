# scalpel-help — Scalpel Command Reference

Explain how to use Scalpel effectively.

## Available Commands
- `/scalpel` — Enable core Scalpel removal mode
- `/scalpel-plan <feature>` — Get a detailed removal plan first (recommended for anything non-trivial)
- `/scalpel-execute <feature>` — Perform the actual clean removal (after planning)
- `/scalpel-audit` — Scan the codebase for things worth removing
- `/scalpel-review` — Review a removal diff or PR
- `/scalpel-help` — This help message

## Recommended Workflow
1. Use `/scalpel-plan` first for anything bigger than a few files.
2. Review the plan.
3. Approve and call `/scalpel-execute`.
4. Let it verify everything.

## Philosophy Reminder
Scalpel's job is complete, safe removal — not speed. A clean deletion today saves hours of confusion later.

For full rules, see `AGENTS.md` in the root of this repo.