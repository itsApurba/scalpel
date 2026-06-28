# Example: Completely Remove Stripe Integration

## Scenario
The codebase has an old Stripe payment integration that is no longer used. We want to remove it **completely**.

## Before (Typical AI behavior without Scalpel)
- Deletes `stripe.ts` and `useStripe.ts`
- Leaves imports in `checkout.tsx` commented out
- Forgets to remove `STRIPE_SECRET_KEY` from `.env.example`
- Misses the webhook handler in `api/webhooks/stripe.ts`
- Leaves Stripe mentions in README and docs
- Leaves `@stripe/stripe-js` in `package.json`
- Leaves test files that import Stripe helpers

**Result**: Partial, messy removal. Tech debt increases.

## With Scalpel (Correct Approach)

### Step 1: Plan
Agent produces a full blast radius report:
- Files to delete: `lib/stripe.ts`, `hooks/useStripe.ts`, `api/webhooks/stripe.ts`, `components/StripeCheckout.tsx`
- Files to modify: `package.json`, `.env.example`, `README.md`, `docs/payments.md`, `app/checkout/page.tsx`
- Configs: Remove Stripe from feature flags / env validation
- Tests: Delete `tests/stripe.test.ts` and clean related tests

### Step 2: Execute
Clean removal performed in logical order.

### Step 3: Verify
- `npm run build` passes
- Relevant tests pass
- Final grep for "stripe" / "Stripe" across codebase returns only historical mentions in git history / CHANGELOG

## Key Differences

| Aspect                    | Normal AI          | Scalpel                  |
|---------------------------|--------------------|--------------------------|
| Completeness              | Partial            | 100%                     |
| Commented code left       | Often              | Never                    |
| Configs & env cleaned     | Usually misses     | Always                   |
| Docs updated              | Rarely             | Yes                      |
| Verification              | Weak               | Strong (build + grep)    |
| Long-term tech debt       | Increases          | Decreases                |

This is the standard Scalpel expects.