# Scalpel Removal Protocol (Detailed)

This document expands on the ladder defined in `AGENTS.md`.

## Phase 0: Trigger & Understanding

When the user says something like:
- "Remove the old payment integration"
- "Delete the analytics SDK we don't use anymore"
- "Clean up the dead feature X"

**First action**: Deeply understand what the feature is and where it lives.

Read key files, trace data flow, understand why it exists and why it's being removed.

## Phase 1: Confirmation (Rung 1)

Ask / confirm:
- Is this feature truly unused?
- Has it been replaced by something else?
- Is there any chance we'll need parts of it again soon?

If uncertain → recommend planning a deprecation instead of immediate deletion.

## Phase 2: Blast Radius Mapping (Rung 2) — Critical

This is the most important phase.

Create a comprehensive list of everything that touches the feature:

### Checklist
- [ ] All source files that import or reference it
- [ ] API routes / server actions / tRPC procedures
- [ ] Frontend components and hooks
- [ ] Database schema (tables, columns, relations)
- [ ] Migrations (old + new cleanup migrations if needed)
- [ ] Environment variables and validation schemas (Zod, Joi, etc.)
- [ ] Configuration files and feature flag systems
- [ ] Package manager manifests (`package.json`, `Cargo.toml`, `pubspec.yaml`, `go.mod`, etc.)
- [ ] Tests (all levels)
- [ ] Documentation (README, Notion, Confluence, inline docs)
- [ ] CI/CD pipelines, GitHub Actions, Dockerfiles, deployment scripts
- [ ] Monitoring / logging / error tracking references
- [ ] Any generated code or fixtures

**Tool usage recommendation**: Use `grep`, `git grep`, IDE search, and AST tools when available.

## Phase 3: Risk Classification

| Risk Level | Description                          | Recommended Approach          |
|------------|--------------------------------------|-------------------------------|
| Low        | Pure leaf code, no data impact       | Direct atomic removal         |
| Medium     | Shared utilities, multiple callers   | Update callers first          |
| High       | Involves database or critical paths  | Staged removal + verification |
| Very High  | Core auth, payments, data migration  | Detailed plan + human approval |

## Phase 4: Execution Strategy

### Atomic Removal (Preferred)
One commit/PR that removes everything cleanly.

### Staged Removal
Use when risk is high:
1. Remove UI / API surface first (hide behind flag or return early)
2. Remove internal implementation
3. Remove data layer last
4. Final cleanup

## Phase 5: Post-Removal Verification

Mandatory checks:
1. Project builds successfully
2. Relevant test suites pass
3. No broken imports (TypeScript, ESLint, etc.)
4. **Final comprehensive search** for any remaining references to the removed feature
5. Manual testing of affected user flows (when possible)

## Phase 6: Documentation & Commit

Good commit message example:
```
chore: completely remove old Stripe integration

- Delete all Stripe-related code, configs, tests, and docs
- Remove @stripe/stripe-js and related env vars
- Verified: build + tests pass, no remaining references

Refs: #123
```

## Anti-Patterns to Avoid

- Commenting out instead of deleting
- Leaving "maybe useful later" code
- Forgetting to update documentation
- Skipping the final verification grep
- Removing things without understanding why they were there

---

**Remember**: A clean removal is a gift to future developers (including future you).