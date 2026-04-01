# Zeraki Pledge & Credit

A two-layer product built on top of Zeraki Finance that turns informal verbal fee pledges into structured instalment plans — and uses the behavioural data those plans generate to offer eligible parents affordable school fee credit through an embedded lending partner.

---

## The Problem

When a parent can't pay full school fees on Day 1 of term, they negotiate verbally at the school gate. The bursar records the commitment in a notebook. When the parent misses the informal deadline, the child gets sent home.

Zeraki Finance already has a pledge feature — but it's a digital notebook entry, not a workflow. There's no structured plan, no automated tracking, no adherence monitoring. Parents who need to bridge the gap borrow from Tala or shylocks at 15–20% monthly interest.

---

## The Product

### Layer 1 — Instalment Plans
Turns the existing pledge record into a real payment plan: scheduled instalments, automated SMS reminders, adherence tracking, and a bursar dashboard showing expected vs. actual fee collection. Included in the existing Zeraki Finance school subscription.

**School value**: fees arrive faster, bursars stop chasing parents with a notebook.
**Parent value**: structured flexibility, child never sent home, no gate negotiation.

### Layer 2 — Fee Top-Up Credit
Uses multi-term payment history from Layer 1 (and existing Zeraki Finance data) to identify credit-eligible parents. Eligible parents receive a "fee support" offer — credit disbursed directly to the school's paybill at ~5% flat, repaid automatically through a waterfall built into the parent's existing fee payment flow.

**Parent value**: affordable credit vs. 15%+ monthly from digital lenders, no new repayment behaviour required.
**Zeraki value**: data and distribution fee per arrangement, zero credit risk.

---

## How the Waterfall Works

1. Parent accepts a fee top-up offer (two-step explicit consent)
2. Lending partner (e.g. Pezesha) disburses directly to the school's paybill
3. School is made whole — child stays in school
4. As the parent pays future fees to the same paybill, Zeraki's system automatically splits each payment: lender's repayment share → B2B transfer to partner; remainder → stays with school
5. Parent repays by doing exactly what they always do: paying school fees

---

## Credit Eligibility

Two groups qualify for Layer 2:

| Group | Signal |
|---|---|
| Long-term payer | Strong multi-term payment history in Zeraki Finance (average payment speed score ≥ 90) |
| Layer 1 adherent | On an instalment plan with 75%+ payment adherence before a late-term disruption |

The model distinguishes **deviation from pattern** — a parent with 6 clean terms and one crisis term is statistically low-risk. This is the data insight Tala and standalone lenders cannot replicate.

---

## Business Model

| Layer | Revenue |
|---|---|
| Layer 1 | None — included in existing school subscription. Strategic value: moat, stickiness, data generation. |
| Layer 2 | 1–2% data and distribution fee per credit arrangement. Zeraki holds zero credit risk. |

At 1,000 schools opted in, ~50 arrangements per term at KES 4,000 average: **KES 9M/year**. Full 4,000-school penetration: **KES 36M/year**. Scales further with geographic expansion.

This is a high-margin recurring line within Zeraki's subscription business — not the entire revenue model.

---

## Competitive Moat

Zeraki's position as the data and distribution layer is protected by four things that cannot be replicated independently:

1. **Distribution** — 4,000+ schools built over 10 years through teacher-facing tools, not a lending product
2. **Operational data** — multi-term payment history, pledge fulfilment records, and plan adherence data generated as a byproduct of daily bursar use
3. **School trust** — SMS messages arrive from the school's sender ID; parents see the school, not the platform
4. **Settlement infrastructure** — paybill integration already exists for fee receipting; the waterfall requires no new integrations

A lender cannot replicate all four without becoming a school management company.

---

## Success Metrics

**90-day go/no-go metric**: Plan adherence rate
**Target**: 65%+ of parents on a Layer 1 plan make all scheduled payments on time
**Gate**: Below 40% — fix Layer 1 before investing in Layer 2

---

## Pipeline Status

| Stage | File | Status |
|---|---|---|
| Brainstorm | `brainstorms/zeraki-pledge-credit.md` | ✅ Complete |
| Feature Spec — Layer 1 | `features/1.0.1-zeraki-instalment-plans.md` | ✅ Complete |
| Feature Spec — Layer 2 | `features/1.0.2-zeraki-fee-top-up-credit.md` | ✅ Complete |
| BDD Spec — Layer 1 | `specs/1.0.1-zeraki-instalment-plans.md` | ✅ Complete |
| BDD Spec — Layer 2 | `specs/1.0.2-zeraki-fee-top-up-credit.md` | ✅ Complete |
| User Journey — Layer 1 | `journeys/1.0.1-zeraki-instalment-plans.md` | ✅ Complete |
| User Journey — Layer 2 | `journeys/1.0.2-zeraki-fee-top-up-credit.md` | ✅ Complete |
| UI Spec — Layer 1 | `ui-specs/1.0.1-zeraki-instalment-plans.md` | ✅ Complete |
| UI Spec — Layer 2 | `ui-specs/1.0.2-zeraki-fee-top-up-credit.md` | ✅ Complete |
| Technical Spec — Layer 1 | `tech-specs/1.0.1-zeraki-instalment-plans.md` | ✅ Complete |
| Technical Spec — Layer 2 | `tech-specs/1.0.2-zeraki-fee-top-up-credit.md` | ✅ Complete |

The full pipeline is complete. All specs are ready for engineering handoff.

---

## Key Open Questions Before Engineering Handoff

The following questions must be resolved before development begins. Each blocks a specific part of the implementation.

### Blocks Layer 2 entirely
1. **Pezesha partnership** — validate structural fit, API contract, and commercial terms (fee rate, disbursement flow, repayment data exchange) in a direct conversation before building any Layer 2 infrastructure. This is the single most critical unvalidated assumption in the product.

### Blocks Layer 2 go-live
2. **Consent text legal review** — two-step progressive disclosure flow with version tracking is designed (OQ-13); consent version 1.0 cannot go live without sign-off against CBK Digital Credit Provider Regulations 2022 and Kenya Data Protection Act 2019.
3. **Regulatory classification** — confirm Zeraki's role under the same regulations. Zeraki is the data and routing layer, not the lender — but this must be formally confirmed.

### Blocks Layer 2 reliability
4. **Child transfer detection** — AT_RISK state with lending partner notification and bridging SMS is designed (OQ-10); the remaining dependency is the detection mechanism (withdrawal event in Zeraki Finance vs. inactivity-based detection).

### Blocks Layer 1 go-live
5. **Inbound SMS infrastructure** — confirm whether Zeraki has an existing inbound SMS short code or long number, and whether it is shared across schools or per-school (OQ-06). Path B (PLAN and BAL keywords) depends on this.
6. **Parent app existence** — confirm whether the Zeraki parent app is an existing product or a new build (OQ-05). Path A (app-initiated plan requests) is a significant scope addition if it requires a new build.
