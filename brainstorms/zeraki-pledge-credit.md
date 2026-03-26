# Product Plan: Zeraki Pledge & Credit
**Date**: 2026-03-26
**Version**: 1.0
**Type**: New Feature for Zeraki Finance
**Mode**: Devil's Advocate

---

## 1. Executive Summary

Zeraki Finance already records parent fee pledges — verbal commitments made at the school gate that are logged as digital notebook entries with no workflow, no tracking, and no consequence. This product has two sequenced layers. Layer 1 turns that inert record into a structured instalment plan system: parents commit to a payment schedule, Zeraki tracks adherence automatically, and children stay in school as long as the plan is being honoured. Layer 2 uses the multi-term behavioural data Layer 1 generates to offer eligible parents affordable fee credit through an embedded lending partner — disbursed directly to the school's paybill at ~5% flat, repaid automatically through a waterfall built into the parent's existing fee payment flow.

The product solves a precise problem: the cash flow gap between when fees are due and when parents can pay, which today forces schools to send children home and forces parents to borrow from digital lenders at 15–20% monthly interest. Zeraki takes zero credit risk, earns a data and distribution fee per credit arrangement, and deepens its moat in every school that opts in.

---

## 2. Problem & Opportunity

### 2.1 The Problem

| Dimension | Description |
|---|---|
| School cash flow problem | Schools collect 20–35% of fees in Week 1 but owe teacher salaries, food suppliers, and operational costs by mid-month. The fee trickle — 55–70% by Week 4, 85–95% by end of term — creates a structural cash flow gap that drives the sent-home cycle. |
| Parent payment timing problem | Most parents cannot pay full fees on Day 1. The gap is typically a timing mismatch (salary arrives week 3, fees due week 1), not an inability to pay. Parents eventually pay — but the path to payment involves gate negotiation, bursar notebook entries, child sent home 2–3 days, and informal borrowing at predatory rates. |
| Zeraki pledge feature gap | Zeraki Finance already tracks pledges — but it is a digital notebook, not a workflow. There is no structured plan, no automated tracking, no adherence monitoring, no consequence when a deadline is missed, and no data signal generated. The feature exists but does nothing. |
| Predatory lending market gap | Parents who need to bridge the fee gap borrow from Tala, Shylocks, or M-Shwari at 15–20% monthly interest. A parent borrowing KES 5,000 repays KES 6,000+ within 30 days. No purpose-built, affordable school fee credit product exists in the Kenyan market. |

### 2.2 The Opportunity

| Factor | Detail |
|---|---|
| Target market | Kenya (primary); Uganda and additional Zeraki expansion markets (subsequent phases) |
| Addressable segment | Parents at Zeraki Finance-enabled schools who cannot pay full fees on Day 1 of term — estimated 50–80% of the parent population at any given school |
| Market signal | The verbal pledge system has existed for decades. Zeraki already has a pledge feature adopted by bursars. Tala and digital lenders are actively used for fee gaps — demonstrable demand for the credit product exists, just served badly. |
| Why now | Zeraki Finance has sufficient school penetration (4,000+ schools) to make a lending partner arrangement commercially viable. Layer 1 infrastructure (paybill integration, fee receipting, SMS parent contact) already exists. The data moat is buildable without new integrations. |

---

## 3. Target Users

### 3.1 Bursar / School Finance Officer

| Dimension | Detail |
|---|---|
| Who they are | The person responsible for fee collection, receipting, and financial reporting at the school. Uses Zeraki Finance daily for receipting and expense tracking. Trusted by the headteacher to manage cash flow. |
| Current workflow | Records verbal pledges in a notebook or as a simple Zeraki entry. Sends children home when deadlines pass. Has no system for tracking who has a plan, whether payments are on schedule, or which parents are about to miss. Manually chases parents via phone. |
| Key frustrations | No visibility into expected cash flow. No structured way to honour a parent's commitment without a notebook. No leverage beyond sending the child home. |
| What success looks like | Can see every active instalment plan, each parent's adherence status, and projected fee collection for the term — from a single dashboard. Spends less time chasing. More fees arrive earlier. |

### 3.2 Parent (Fee Gap — Timing Mismatch)

| Dimension | Detail |
|---|---|
| Who they are | A parent whose salary, business income, or family remittance arrives after fees are due. Has the intention and eventual means to pay. Typically resolves the gap within days through informal borrowing or partial payment. |
| Current workflow | Negotiates verbally at the school gate. Pays what they can. Borrows from a relative, chama, or digital lender to cover the gap. Child may be sent home 2–3 days while this is resolved. |
| Key frustrations | Gate negotiation is humiliating. Digital lenders are expensive. A 2–3 day disruption costs the parent a lost work day and the child missed class. |
| What success looks like | Commits to a structured plan before term starts. Child never sent home. No gate negotiation. No Tala loan. |

### 3.3 Parent (Fee Gap — Crisis Term)

| Dimension | Detail |
|---|---|
| Who they are | A parent with a strong multi-term payment history who hits a genuine crisis — hospital bill, job loss, emergency — in a specific term. Has demonstrated creditworthiness through behaviour but cannot bridge this term's gap through normal means. |
| Current workflow | Same as 3.2 but the informal borrowing options are exhausted or insufficient. May resort to high-interest digital lending or keep the child home longer while funds are sourced. |
| Key frustrations | Nowhere to access affordable, purpose-appropriate credit. Strong payment history counts for nothing with Tala. No way to signal trustworthiness to a lender. |
| What success looks like | Receives a "fee top-up" offer based on their track record. Credit is disbursed directly to the school — no diversion risk, no cash handling. Repays automatically through their normal fee payment flow. Child stays in school. |

---

## 4. Value Proposition

### 4.1 For Schools (Bursars / Headteachers)

> **Core promise:** Your fees arrive faster and your bursar stops chasing parents with a notebook.

| Value driver | How it is delivered |
|---|---|
| Faster fee collection | Layer 2 credit disbursements compress the fee collection timeline. Instead of waiting until Week 8–10 for late fees to trickle in, the school is closer to whole by Week 5. A "Total disbursed to school this term" figure in the bursar dashboard makes this concrete. |
| Structured payment visibility | Layer 1 replaces notebook entries with active instalment plans — the bursar sees every plan, adherence status, and next expected payment in one view. |
| Reduced admin burden | Automated SMS reminders go to parents from the school's sender ID. The bursar's only action is opting in at the start of term. No manual chasing. |
| No new product to sell | Layer 1 is part of the existing Zeraki Finance subscription. Layer 2 is opt-in via a settings toggle. The school does not pitch loans to parents. |

### 4.2 For Parents

> **Core promise:** Keep your child in school without borrowing at 15% monthly interest.

| Value driver | How it is delivered |
|---|---|
| Structured flexibility | Layer 1 converts a verbal commitment into a clear plan with scheduled payments, SMS reminders, and a mutual understanding that the child stays in school while the plan is honoured. |
| Affordable credit for crisis terms | Layer 2 offers fee credit at ~5% flat vs. 15–20% monthly from digital lenders — purpose-locked to the school's paybill, never touching the parent's M-Pesa. |
| Invisible repayment | Repayment is built into the parent's existing fee payment flow via waterfall allocation. No new repayment behaviour required. |
| Dignity | No gate negotiation. No humiliation. The offer comes through the school's channel, framed as fee support based on payment history — not a loan application. |

### 4.3 Platform-Level Value Proposition

Zeraki is the only platform that can deliver purpose-locked school fee credit because it already sits between the school's paybill, the parent's payment history, and the child's enrolment record. A lender cannot replicate this without becoming a school management company. Remove Zeraki from this model and the product does not exist.

---

## 5. Competitive Landscape

### 5.1 Competitor Overview

| Competitor | Category | Key Limitation |
|---|---|---|
| Tala / M-Shwari / Branch | General-purpose digital lenders | 15–20% monthly interest; no purpose-locking; disbursed to parent M-Pesa (diversion risk); no school relationship; no education-specific underwriting |
| Shylocks / informal lenders | Informal credit | Predatory rates; no formal structure; social cost; no reporting upside for borrower |
| Bank school fee loans | Formal credit | High friction; collateral requirements; not designed for KES 3,000–10,000 ticket sizes; no paybill integration |
| Pezesha (standalone) | Embedded lending platform | Has the credit infrastructure but no school distribution, no fee payment data, no school trust relationship — this is why they are a partner candidate, not a competitor |

### 5.2 Feature Comparison Matrix

| Feature | Zeraki Pledge & Credit | Tala / Digital Lenders | Bank Loans |
|---|:---:|:---:|:---:|
| Purpose-locked to school paybill | ✅ Yes | ❌ No | 🟡 Partial |
| ~5% flat fee (vs 15%+ monthly) | ✅ Yes | ❌ No | 🟡 Varies |
| Underwriting from school fee history | ✅ Yes | ❌ No | ❌ No |
| Automatic waterfall repayment | ✅ Yes | ❌ No | ❌ No |
| No new parent behaviour required | ✅ Yes | ❌ No | ❌ No |
| Structured instalment plans (Layer 1) | ✅ Yes | ❌ No | ❌ No |
| School cash flow improvement | ✅ Yes | ❌ No | ❌ No |

### 5.3 Positioning

The moat is a combination of four things that cannot be replicated individually: 10 years of school distribution (4,000+ schools through teacher-facing tools), operational data generated as a byproduct of daily bursar use, school trust earned through Zeraki's existing relationships, and paybill settlement infrastructure already integrated for fee receipting. A lender can replicate one of these. They cannot replicate all four without becoming a school management company — which is not their business.

---

## 6. Business Model

| Revenue stream | How it works |
|---|---|
| Layer 1 — Instalment plans | Included in existing Zeraki Finance school subscription. No direct revenue. Strategic value: deepens school relationship, increases platform stickiness, generates the behavioural data that makes Layer 2 viable. |
| Layer 2 — Data and distribution fee | 1–2% of disbursed amount per credit arrangement (or flat fee per arrangement). Zeraki earns for delivering pre-qualified borrowers with verified behavioural data and providing settlement infrastructure. Zeraki holds zero credit risk — the lending partner provides capital and bears defaults. |

**Illustrative economics:**
- 500-student school, 50 credit arrangements per term, average KES 4,000 disbursed
- KES 200,000 disbursed per school per term → Zeraki earns ~KES 3,000
- 1,000 schools opted in → KES 3M per term → **KES 9M per year**
- Full 4,000-school penetration → **KES 36M per year**
- Revenue is high-margin and recurring — Zeraki takes no capital risk and marginal infrastructure cost once Layer 1 exists

**Key assumptions**: School opt-in rate reaches 25%+ of the base (1,000/4,000). Pezesha or equivalent partner agrees to the revenue share structure. Average loan size and take-up rate hold at assumed levels. Geographic expansion (Uganda, additional markets) unlocks further scale — but M-Pesa paybill infrastructure dependencies must be resolved per market before the model ports.

---

## 7. Success Metrics & Validation

### Leading Indicators
| Metric | Why it matters & target |
|---|---|
| Layer 1 plan adherence rate | The single 90-day go/no-go metric. Measures the percentage of parents on an instalment plan who make all scheduled payments on time. Validates Layer 1 PMF, data quality for Layer 2 underwriting, and school trust simultaneously. **Target: 65%+ at 90 days.** |
| School opt-in rate | Percentage of pilot schools that enable Layer 1 via settings toggle in Term 1. Low opt-in means the bursar value proposition is not landing. |
| Layer 2 offer acceptance rate | Percentage of eligible parents who accept a fee top-up offer. Validates parent willingness to use the product and the "fee support" framing. |

### Lagging Indicators
| Metric | Why it matters |
|---|---|
| Sent-home reduction rate | The ultimate outcome metric — percentage reduction in children sent home for fee arrears at pilot schools. Hard to measure cleanly (depends on school behaviour) but directionally important. |
| Layer 2 default rate | Validates the underwriting model. Should be materially lower than general digital lending defaults if the multi-term history signal is real. |
| School-to-school referral rate | Whether headteachers recommend Zeraki Finance to peer schools based on Layer 1/2 outcomes — the organic growth signal. |

### Change Course Thresholds
- **Below 40% plan adherence at 90 days**: Do not invest in Layer 2. Fix Layer 1 first — diagnose whether parents are signing up for plans they cannot keep, plan structures do not match real income timing, or schools are not honouring the "on a plan means stays in school" commitment.
- **Below 10% school opt-in in pilot**: The bursar value proposition is not clear enough or requires active selling the product cannot support. Revisit onboarding and the settings toggle UX.
- **Pezesha (or equivalent) partnership not agreed by end of Layer 1 pilot**: Do not build Layer 2 payment infrastructure. Run Layer 1 as a standalone feature while the partnership is validated.

---

## 8. Assumptions & Open Questions

### Assumptions

- [ ] A lending partner (Pezesha or equivalent) will accept Zeraki's payment history as a primary credit signal and disburse at ~5% flat — **this is the single most critical unvalidated assumption in the entire plan**
- [ ] 65% plan adherence is an achievable threshold — no benchmark data exists for this yet
- [ ] Schools will opt in at sufficient rates (25%+) when presented with the "faster fee collection" value proposition
- [ ] Parents at pilot schools have sufficient digital literacy and M-Pesa access to operate within the consent and payment flows
- [ ] The multi-term history signal is a genuine predictor of credit performance (deviation vs. pattern thesis) — to be validated through Layer 2 early cohorts
- [ ] The waterfall repayment model is technically feasible within Zeraki Finance's existing paybill integration without significant re-engineering

### Open Questions

- [ ] What is the legal structure of the data-sharing arrangement between Zeraki and the lending partner under Kenya's Data Protection Act 2019? Does Zeraki need to register as a credit information provider?
- [ ] Does Zeraki need any CBK registration or license to operate as a credit referral or origination platform under the Digital Credit Providers Regulations 2022?
- [ ] What is the exact revenue share / fee structure Pezesha would accept? Is a per-arrangement fee or percentage more viable for the partner?
- [ ] What happens to the waterfall when a child transfers schools mid-repayment? Who is responsible for collecting the outstanding loan amount?
- [ ] How does the model adapt for markets without M-Pesa paybill infrastructure (e.g. Guinea)? Does it require a separate integration strategy per market?
- [ ] What minimum tenure on Zeraki Finance does a school need before its data is creditworthy enough to power Layer 2? (Constrains addressable market at launch)

### Risks

- **Lending partner dependency**: The entire Layer 2 business model depends on one class of partner agreeing to terms Zeraki does not control. If no partner accepts the revenue share, Layer 2 does not exist. Mitigation: validate Pezesha structural fit in parallel with Layer 1 pilot.
- **Consent UX trust gap**: The "fee top-up" entry language and the explicit CRB-disclosure consent screen create a tone mismatch that could feel like a bait-and-switch to parents. If first-touch language is soft and the consent screen is formal, trust erodes at the moment of conversion. This is a design problem, not a reason to kill the product — but it must be resolved before launch.
- **School compliance with the plan**: The "on a plan means stays in school" commitment is the parent's core incentive to adhere. If schools send children home anyway (because the bursar doesn't trust the plan or the headteacher overrides), plan adherence collapses and the credit signal is worthless. Requires explicit school-side commitment as part of opt-in.
- **Adverse selection in Layer 2**: The parents most likely to need credit in a crisis term are also the ones whose current-term data looks worst. The multi-term history model mitigates this — but only for parents who have been in the Zeraki system long enough to have a history. New Zeraki schools have no data depth.
- **Revenue ceiling at current scale**: KES 36M/year at full 4,000-school penetration is meaningful margin but not business-defining revenue. The scale thesis depends on geographic expansion into markets where the M-Pesa waterfall model may not port without significant adaptation.
- **Regulatory evolution**: Kenya's fintech regulatory environment is active. CBK Digital Credit Provider Regulations 2022 are recent. Zeraki's role as data provider, credit referrer, and payment router may attract regulatory scrutiny as the product scales.

---

## 9. Decisions Log

### D1: Layer 1 generates no direct revenue

| | |
|---|---|
| **Decision** | Layer 1 (structured instalment plans) is included in the existing Zeraki Finance school subscription at no additional charge |
| **Rationale** | Layer 1's value to Zeraki is strategic: it deepens the school relationship, generates the behavioural data that makes Layer 2 viable, and increases platform stickiness. Charging for it creates an adoption barrier that undermines the data moat. |
| **Implication** | Layer 1 must be justified on strategic grounds, not as a standalone revenue line. If Layer 2 never materialises, Layer 1's ROI must be evaluated on retention and churn reduction alone. |

### D2: Zeraki takes zero credit risk

| | |
|---|---|
| **Decision** | Zeraki's role is data provider and distribution layer. The lending partner (e.g. Pezesha) provides capital, holds the lending license, and bears all default risk. |
| **Rationale** | Taking credit risk requires capital, a CBK lending license, and loss provisioning — none of which are Zeraki's core competency. The embedded lending model (platform + licensed lender) gives Zeraki high-margin revenue without balance sheet exposure. |
| **Implication** | Zeraki's Layer 2 revenue is capped by partner terms. Zeraki cannot unilaterally adjust interest rates or credit limits. Long-term, if the model proves out, Zeraki could explore a deeper fintech structure — but this is explicitly not in scope for this phase. |

### D3: Waterfall repayment over active collection

| | |
|---|---|
| **Decision** | Loan repayment is captured automatically by splitting incoming fee payments through Zeraki's paybill integration — not through active collection from parent, school, or lender |
| **Rationale** | Active collection requires a collections function, erodes school and parent relationships, and replicates cost the lender already bears. The waterfall works because the parent's strongest incentive (child in school) is directly tied to continued fee payment — making repayment a byproduct of normal behaviour. |
| **Implication** | The waterfall is contingent on the child remaining enrolled at the same school. Child transfer or dropout breaks the collection mechanism. This is mitigated by small loan sizes (KES 3,000–10,000) and CRB listing as backstop. |

### D4: Multi-term history as primary credit signal

| | |
|---|---|
| **Decision** | Credit eligibility is based on multi-term payment history, not current-term adherence alone. Two eligible groups: (a) 6+ terms of consistent on-time payment history; (b) Layer 1 plan with 75%+ adherence before a late-term disruption. |
| **Rationale** | Current-term data collapses precisely when credit is most needed (crisis term). Multi-term history identifies deviation vs. pattern — a parent with 6 clean terms and one bad term is structurally different from a serial defaulter. This is the data insight Tala and standalone lenders cannot replicate. |
| **Implication** | New Zeraki schools with less than 2 years of data cannot power Layer 2 until data depth is built. This constrains the addressable market at launch and means Layer 2 adoption lags Layer 1 adoption by at least 1–2 years at newly onboarded schools. |

### D5: 65% adherence as the Layer 2 go/no-go threshold

| | |
|---|---|
| **Decision** | If Layer 1 plan adherence reaches 65%+ at 90 days in the pilot, proceed to Layer 2 investment. Below 40%, fix Layer 1 before spending on Layer 2. |
| **Rationale** | Adherence rate is the single number that simultaneously validates Layer 1 PMF, Layer 2 data quality, and school growth (headteacher recommendations). It is measurable from day one and is a leading indicator for every downstream outcome. Revenue is too small and adoption is vanity if parents do not follow through. |
| **Implication** | The 65% threshold is an assumed benchmark — no comparable data exists. The pilot must surface whether this is realistic before it becomes a formal gate. |

### D6: "Fee top-up" framing with explicit consent

| | |
|---|---|
| **Decision** | The product is marketed to parents as "fee support" based on payment history, not as a loan. The word "loan" does not appear in the entry experience. However, the consent flow is explicit and two-step: parents are told their fee history will be shared with a credit partner, that repayment may be reported to a credit bureau, and must confirm twice (YES then CONFIRM for SMS). |
| **Rationale** | "Loan" triggers anxiety and comparison-shopping with Tala. "Fee support" frames the offer as the school helping the parent — more accurate to the product's actual design and more likely to convert. Regulatory compliance is met through explicit consent, not through entry language. |
| **Implication** | The tone shift between entry language and consent screen is a real trust risk. UX design must ensure the transition feels like progressive disclosure ("here's how it works") rather than a reveal ("actually it's a loan"). This must be prototyped and tested before launch. |

---

## What This Is Not

- **A general-purpose lending product**: Credit is purpose-locked to school fees only. Zeraki is not building a fintech super-app or competing with mobile money platforms.
- **A product Zeraki capitalises itself**: Zeraki holds no loan book, provides no capital, and takes no default risk. The lending infrastructure belongs to the partner.
- **An automated Layer 1-to-Layer 2 pipeline**: Layer 1 and Layer 2 are distinct opt-ins. Signing up for an instalment plan does not automatically make a parent credit-eligible or enrol them in the credit product. These are separate consent events.
- **A collections business**: The school does not chase Pezesha's debt. Zeraki does not operate a collections function. The waterfall handles repayment passively. CRB listing is the backstop — not active recovery.
- **Ready for geographic expansion in Phase 1**: Uganda, Guinea, and other target markets are a stated direction, not a Phase 1 commitment. The M-Pesa paybill waterfall model requires per-market infrastructure validation before the model is portable.

---

## Next Step
When satisfied with this plan, hand it to the **Specs Writer** to produce the Feature Spec (`features/zeraki-pledge-credit.md`) and BDD Spec (`specs/zeraki-pledge-credit.md`) and begin the pipeline.
