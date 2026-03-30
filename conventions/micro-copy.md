# Micro-copy Conventions

Shared voice, tone, and copy patterns that all journey and UI spec agents must follow for consistency across features.

---

## Voice & Tone

- **Voice**: [TBD — e.g. Professional but approachable / Casual and direct / Formal and precise]
- **Person**: [TBD — e.g. Second person ("You") / First person ("I/My")]
- **Tense for CTAs**: [TBD — e.g. Imperative ("Create account") / First-person ("Create my account")]

---

## CTA Patterns

| Action Type | Pattern | Example | Avoid |
|------------|---------|---------|-------|
| Create/Submit | Verb + Object | "Create account" | "Submit", "OK", "Done" |
| Destructive | Verb + Object (explicit) | "Delete project" | "Delete", "Remove", "Yes" |
| Cancel | "Cancel" or navigate away | "Cancel" | "Go back", "Never mind" |
| Confirm | Restate the action | "Yes, delete project" | "Confirm", "OK" |

---

## Error Message Pattern

```
[What happened] + [Why, if useful] + [What to do next]
```

- "That email is already registered. Try signing in instead."
- "Password must be at least 8 characters."
- NOT: "Error", "Something went wrong", "Invalid input"

---

## Empty State Pattern

```
[What would be here] + [How to get started]
```

- "No projects yet. Create your first project to get started."
- NOT: "Nothing to display", "Empty", "No data"

---

## Loading State Pattern

- Use skeleton screens for content areas, spinners only for actions
- Never show raw "Loading..." text

---

## Established Copy (add as features are built)

| Context | Copy | Used in |
|---------|------|---------|
| _Example: Email validation error_ | _"Please enter a valid email address"_ | _1.0.1-customer-registration_ |
| Credit offer SMS | `[School]: Based on [Student]'s payment record, you may qualify for fee support this term. Reply FEES to see your offer, or ignore to skip.` | J3, 1.0.2 |
| AT_RISK notification SMS | `[School]: Your fee top-up balance for [Student] remains outstanding. The credit partner may contact you about the remaining balance.` | J8, 1.0.2 |
| Consent Step 1 SMS | `[School] fee top-up: [Student]'s payment history will be shared with our credit partner. Repayments reported to credit bureaus. Reply YES to continue or NO to cancel.` | J3, 1.0.2 |
| Consent Step 2 SMS | `Confirm: KES [amount] fee top-up for [Student]. ~KES [amount]/[week or month] from your future fee payments. Reply CONFIRM to accept.` | J3, 1.0.2 |
| Offer accepted / disbursed SMS | `[School]: KES [amount] fee top-up confirmed for [Student] and credited to the school. Repayment starts from your next fee payment. Pay to [paybill] as usual.` | J2, J3, 1.0.2 |
| Waterfall payment applied SMS | `[School]: KES [amount] received for [Student]. KES [repayment] applied to fee top-up. Remaining: KES [balance]. School fees: KES [fee_credit] credited.` | J6, 1.0.2 |
| Waterfall — full payment to repayment edge | `[School]: KES [amount] received for [Student]. Full amount applied to your fee top-up balance. Remaining: KES [balance]. School balance unchanged this payment.` | J6 edge, 1.0.2 |
| Credit completed SMS | `[School]: Your fee top-up for [Student] is fully repaid. Thank you for keeping your commitment.` | J7, 1.0.2 |
| Offer expired SMS | `[School]: Your fee top-up offer for [Student] has expired. Contact the school if you still need support.` | J5, 1.0.2 |
| Disbursement failed SMS | `[School]: We could not process your fee top-up at this time. Please contact the school for assistance.` | J10, 1.0.2 |
| Layer 1 dependency gate (Layer 2 blocked) | `Please enable Instalment Plans first. Fee Top-Up Credit requires instalment plan data to assess eligibility for some parents.` | J1, 1.0.2 |
| School credit risk clarification | `The school takes no financial risk. The lending partner provides the credit and holds the default risk.` | J1, 1.0.2 |
