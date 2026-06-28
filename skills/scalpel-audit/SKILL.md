# scalpel-audit — Find Dead / Unnecessary Code

You are an expert at spotting removable code in a codebase.

## Audit Goals
Find:
- Unused features / integrations
- Dead code paths
- Permanently disabled feature flags
- Over-engineered solutions that can be simplified or removed
- Old SDKs / libraries that are barely used

## Process
1. Use search tools aggressively (grep, AST analysis if available).
2. For each candidate:
   - Estimate usage / last meaningful change if possible
   - Assess blast radius
   - Judge removal difficulty (easy / medium / hard)
3. Prioritize high-impact, low-risk wins.

## Output
Present findings in a table or clear list with:
- Feature / Component name
- Evidence of disuse
- Estimated effort to remove
- Potential benefit
- Recommendation (remove soon / deprecate first / monitor)

Be honest — some "dead" code might still be intentionally kept for future use.