# Scalpel

> **Cut clean. Leave nothing behind.**  
> The best deletion is the one done completely and safely.

Makes your AI coding agent perform **surgical removal** of unnecessary features, integrations, and dead code.

Inspired by [ponytail](https://github.com/DietrichGebert/ponytail) — but focused on complete, clean deletion instead of minimal addition.

## Why Scalpel?

Most AI agents suck at removing things. They leave commented-out code, miss references in configs/tests/docs/CI, and create more technical debt than they remove.

**Scalpel** turns the agent into a precise, slightly ruthless senior engineer who only removes code when it can be done cleanly and completely.

## Core Philosophy

- **Completely remove or don't touch it**
- Understand the full blast radius before cutting
- Safety and verification are non-negotiable
- No commented-out corpses or "maybe later" dead code
- Prefer one clean atomic removal over many partial ones

## Installation & Setup

Scalpel works in two main ways:

### 1. Portable Rules (Works Everywhere — Recommended to Start)

Copy the core rules into your project:

```bash
# Option A: Copy AGENTS.md into your project root
curl -o AGENTS.md https://raw.githubusercontent.com/itsApurba/scalpel/main/AGENTS.md
```

Or simply tell your AI:
> "Follow the Scalpel rules from https://github.com/itsApurba/scalpel/blob/main/AGENTS.md"

This works great with:
- **Claude Code / Claude Desktop**
- **Cursor**
- **Windsurf**
- **Cline**
- **GitHub Copilot**
- **Hermes Agent** and other custom agents
- **Gemini CLI** / Antigravity

### 2. Native Slash Commands (Claude Code, Codex, Copilot CLI, etc.)

Because Scalpel includes proper `commands/` and `skills/` folders (modeled after ponytail), many hosts can load it as a plugin.

**Claude Code:**
```
/plugin marketplace add itsApurba/scalpel
/plugin install scalpel
```

**Codex:**
```
/plugins → Add from repository → itsApurba/scalpel
```

**GitHub Copilot CLI:**
```
copilot plugin marketplace add itsApurba/scalpel
copilot plugin install scalpel
```

After installing, you should get native slash commands like `/scalpel-plan`, `/scalpel-execute`, etc.

> **Note**: Full marketplace/plugin support is still early. The portable `AGENTS.md` method above is currently the most reliable.

### 3. Editor-Specific Rules

- **Cursor**: Add `AGENTS.md` content to `.cursor/rules/scalpel.mdc`
- **Windsurf / Cline**: Use `.windsurf/rules/` or `.clinerules/`
- **Continue.dev**: Load `AGENTS.md` as context

### 4. Custom / Self-Hosted Agents (Hermes, Warp, etc.)

Load these files as persistent skills/context:
- `AGENTS.md` (core rules)
- `skills/scalpel/SKILL.md`
- `skills/scalpel-plan/SKILL.md` (and others as needed)

## Usage

### Recommended Workflow

1. **Plan first** (especially for anything non-trivial)
   ```
   /scalpel-plan remove the old Stripe integration completely
   ```

2. Review the plan the agent produces.

3. **Execute** once you're happy
   ```
   /scalpel-execute remove the old Stripe integration completely
   ```

4. Let it verify (build + tests + final reference search).

### Available Commands

| Command              | Description                                      |
|----------------------|--------------------------------------------------|
| `/scalpel`           | Enable core Scalpel removal mode                 |
| `/scalpel-plan`      | Create a detailed, safe removal plan             |
| `/scalpel-execute`   | Perform the actual clean removal                 |
| `/scalpel-audit`     | Scan codebase for dead/unused features           |
| `/scalpel-review`    | Review a removal diff or PR for completeness     |
| `/scalpel-help`      | Show command reference + philosophy              |

### The Scalpel Removal Protocol

After understanding the feature, the agent follows this structured ladder:

1. **Confirm it's truly unnecessary** (evidence-based)
2. **Map the complete blast radius** (every file, import, config, test, doc, env var, CI step...)
3. **Classify impact & risk**
4. **Choose strategy** (atomic vs staged)
5. **Execute cleanly** (no commented code)
6. **Verify aggressively** (build + tests + final grep)
7. **Document** what was removed

Full details: [`docs/removal-protocol.md`](docs/removal-protocol.md)

## Examples

See [`examples/remove-stripe-integration.md`](examples/remove-stripe-integration.md) for a full before/after comparison of a typical messy removal vs a proper Scalpel removal.

## Roadmap

- [x] Core `AGENTS.md` + Removal Protocol
- [x] `commands/` + `skills/` for native slash command support
- [ ] Full plugin manifests + lifecycle hooks (Claude Code, Codex)
- [ ] Better static analysis integration for `/scalpel-audit`
- [ ] More stack-specific examples (Frappe, Flutter, FastAPI, etc.)
- [ ] Benchmarks on real removal tasks

## Contributing

PRs are very welcome! Especially:
- Better examples for different tech stacks
- Improved rules for specific frameworks
- Plugin adapter implementations
- More skills (debt tracking, etc.)

## License

MIT (same as ponytail)

---

**The best code is the code you delete cleanly.**

Made with the same "lazy senior dev but for removal" energy as ponytail.