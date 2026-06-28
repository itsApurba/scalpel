# Scalpel

> **Cut clean. Leave nothing behind.**  
> The best deletion is the one done completely and safely.

Makes your AI coding agent perform **surgical removal** of unnecessary features, integrations, and dead code.

Inspired by [ponytail](https://github.com/DietrichGebert/ponytail) — but for deletion instead of addition.

## Why Scalpel?

Most AI agents are terrible at removing things. They:
- Leave commented-out code
- Miss references in configs, tests, docs, CI
- Do partial cleanups that create tech debt
- Are scared to delete

**Scalpel** turns the agent into a precise surgeon.

## Core Philosophy

- **Completely remove or don't touch it**
- Understand the full blast radius before cutting
- Prefer one clean removal over ten small ones
- Safety and verification are non-negotiable
- No "we might need it later" dead code

## Quick Install

### Claude Code / Codex / Copilot CLI
Just add the rules (works immediately):

```bash
# In your project, create or append to AGENTS.md or use the rules below
```

Or copy `AGENTS.md` from this repo into your project's rules.

### Cursor / Windsurf / Cline / Other Editors
Add to your rules/settings:
- Use the content from `AGENTS.md`

### Hermes Agent / Custom Agents
Load `AGENTS.md` as persistent context or as a skill.

### Full Plugin Support (coming soon)
Future versions will include proper plugin manifests like ponytail.

## Usage

### Basic Commands (tell the agent)

```
/scalpel-plan remove the old Stripe integration completely
/scalpel-execute remove the analytics SDK we no longer use
/scalpel-audit find potentially dead features in this codebase
/scalpel-review review this removal diff for completeness
```

### Recommended Flow

1. **Plan first** → `/scalpel-plan <feature>`
2. Review the plan
3. **Execute** → `/scalpel-execute <feature>`
4. Verify tests + build pass

## The Scalpel Removal Protocol

After fully understanding the feature, the agent follows this ladder:

1. **Confirm it's truly unnecessary** (evidence-based)
2. **Map the complete blast radius** (every file, import, config, test, doc, env var, CI step...)
3. **Classify impact** (leaf code vs shared vs data layer)
4. **Choose strategy** (atomic vs staged removal)
5. **Execute the cut** cleanly
6. **Verify aggressively** (tests, build, final grep, smoke tests)
7. **Document** what was removed

Full details in `docs/removal-protocol.md`.

## Examples

See `examples/` folder for real before/after removal cases (e.g. removing a payment gateway).

## Roadmap

- [ ] Full plugin support for Claude Code, Codex, etc. (like ponytail)
- [ ] `/scalpel-audit` skill with static analysis integration
- [ ] Better blast radius visualization
- [ ] Benchmarks on real removals
- [ ] Support for common stacks (React, FastAPI, Frappe, Flutter, etc.)

## Contributing

PRs welcome. Especially:
- Better examples
- Improved rules for specific tech stacks
- Plugin implementations

## License

MIT — same as ponytail.

---

**The best code is the code you delete cleanly.**  
Made with the same energy as ponytail, but for cleanup.