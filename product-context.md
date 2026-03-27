# Product Context

Cross-cutting decisions that apply across all features. Every agent reads this file. Update it as decisions are made.

---

## Product Identity

**Product name**: Zeraki Finance — Instalment Plans & Fee Top-Up Credit
**One-line description**: Structured fee payment plans and embedded school fee credit built on top of Zeraki Finance's existing school subscription and paybill infrastructure.
**Primary platform**: Web (bursar and admin interface). Parent communication is SMS-first. Parent-facing app existence is unconfirmed — see OQ-05 in `features/1.0.1-zeraki-instalment-plans.md`.

---

## Global Navigation & Layout

- **Navigation type**: Zeraki Finance existing sidebar navigation — new features integrate as sections within the existing Finance module
- **Persistent elements**: Inherited from Zeraki Finance shell (header, school switcher, user menu)
- **Layout shell**: Zeraki Finance web app shell — all feature screens live inside the existing authenticated Finance module layout

---

## Shared Patterns

Patterns that recur across features. When a new feature uses one of these, reference it here instead of reinventing.

| Pattern | Description | First used in |
|---------|-------------|---------------|
| _Example: Auth gate_ | _Redirect unauthenticated users to login, return to original URL after_ | _1.0.1-customer-registration_ |

---

## Actor Registry

All actors across the product. Agents must use actors from this list — do not invent new actors without adding them here first.

| Actor | Role | First appeared in |
|-------|------|-------------------|
| Headteacher / School Admin | Opts the school into features via settings. Makes school-level policy commitments (e.g. "students on active plans will not be sent home"). | 1.0.1-zeraki-instalment-plans |
| Bursar | Creates and manages instalment plans. Monitors fee collection and plan adherence via the dashboard. Primary day-to-day operator of Zeraki Finance. | 1.0.1-zeraki-instalment-plans |
| Parent | Receives SMS notifications and reminders. Makes payments to the school's M-Pesa paybill as normal. Does not interact with Zeraki Finance directly (SMS-only, unless a parent app is confirmed). | 1.0.1-zeraki-instalment-plans |
| Lending Partner | Provides credit capital, holds the lending licence, bears default risk. Receives pre-qualified borrower data from Zeraki. Disburses directly to school paybill. (Pezesha is the candidate partner — not yet validated.) | 1.0.2-zeraki-fee-top-up-credit |

---

## Cross-Feature Dependencies

When Feature B depends on Feature A, record it here so agents can reference the dependency.

| Feature | Depends on | Nature of dependency |
|---------|-----------|---------------------|
| 1.0.2-zeraki-fee-top-up-credit (Path 2) | 1.0.1-zeraki-instalment-plans | Path 2 credit eligibility uses plan adherence data produced by Layer 1. Technical dependency. |
| 1.0.2-zeraki-fee-top-up-credit (Path 1) | Existing Zeraki Finance payment history | Path 1 credit eligibility uses multi-term fee payment history already in Zeraki Finance. Independent of Layer 1 technically, but Layer 1 ships first for strategic reasons. |

---

## Global Business Rules

Rules that apply across multiple features. Feature-specific rules live in their own spec.

- **SMS sender ID**: All SMS messages to parents are sent from the school's registered sender ID, not a Zeraki corporate sender ID. Parents see the school's name. This applies to all features.
- **Paybill**: Payments are always made to the school's existing M-Pesa paybill. No new payment channel is introduced for parents. This applies to all features.
- **Term scoping**: All plan and credit data is scoped to a specific school + term combination. Cross-term data is used for historical analysis only, not for active transaction management.
- **Loan language prohibition**: The word "loan" must not appear in any parent-facing entry communication (offers, initial screens). Credit nature is disclosed in the consent flow. Post-acceptance communications use neutral language ("fee top-up balance"). Applies to all Layer 2 surfaces.
- **Waterfall payment priority**: When a fee payment arrives for a student with an ACTIVE_REPAYMENT credit arrangement, the repayment share is deducted first. Layer 1 instalment plan allocation is applied to the remainder. Applies wherever both features coexist.

---

## Design Tokens (when established)

Shared visual decisions that all UI specs must respect.

- **Primary action color**: [TBD]
- **Destructive action color**: [TBD]
- **Border radius convention**: [TBD]
- **Spacing scale**: [TBD]
- **Typography scale**: [TBD]
