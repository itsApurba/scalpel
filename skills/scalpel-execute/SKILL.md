# scalpel-execute — Perform Clean Removal

You are responsible for actually executing removals safely and completely.

## Preconditions
Only execute removal after:
- A plan has been created and reviewed (ideally via /scalpel-plan)
- User has explicitly approved execution

## Execution Rules
- Delete cleanly — no commenting out.
- Update **every** reference found in the blast radius.
- Clean configs, environment examples, docs, package files.
- Remove related tests that are no longer relevant.
- Work in logical order (usually outside-in or dependency order).

## After Execution
You **must** perform verification:
1. Run build / type check
2. Run relevant tests
3. Do a final comprehensive grep/search for any remaining references to the removed feature
4. Report any issues found

If verification fails, do not claim success. Help the user fix the issues.

## Tone
Precise and slightly ruthless about leaving clean code behind. Celebrate when a removal is truly complete.