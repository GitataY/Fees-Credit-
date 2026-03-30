# Journey Patterns

Recurring UX patterns that the UX Journey Designer must reference for consistency across features.

---

## Trigger Patterns

Common real-world triggers that bring actors into features. Reuse these across journeys for consistency.

| Trigger Type | Description | Example |
|-------------|-------------|---------|
| _Example: External notification_ | _Actor receives email/Slack/push notification_ | _"Customer receives email invite from admin"_ |
| _Example: Self-initiated_ | _Actor decides to do something proactively_ | _"Admin opens dashboard to check team status"_ |
| _Example: System-prompted_ | _Product surfaces a need_ | _"Banner appears: 'Complete your profile to unlock features'"_ |
| Self-initiated (in-person handoff) | Actor takes a product action immediately following a real-world conversation — partial attention, time pressure | Bursar creates plan after in-person conversation (J4, 1.0.1) |
| System-prompted (approval queue) | Product surfaces a work queue the actor needs to process | Bursar processes approval queue (J5, 1.0.1) |
| Inbound SMS keyword | Actor sends a keyword to initiate a self-service flow — zero navigation, zero auth | Parent sends PLAN or BAL keyword (J3, J10, 1.0.1) |
| System-prompted (unexpected offer) | Actor receives an unsolicited offer from the product — trust must be established before comprehension. School sender ID is the primary trust signal. Notification must surface legitimacy before content. | Parent receives credit offer notification (J2, J3, 1.0.2) |

---

## Friction Resolution Patterns

Standard ways to resolve common friction points. Reference these instead of reinventing.

| Friction Type | Resolution Pattern | Example |
|--------------|-------------------|---------|
| _Form anxiety_ | _Show progress, validate inline, explain why data is needed_ | _"3 of 4 steps complete"_ |
| _Irreversible action_ | _Confirmation dialog restating the action and consequences_ | _"Delete project 'Acme'? This cannot be undone."_ |
| _Waiting/loading_ | _Skeleton screen + time estimate if >3s_ | _"Setting up your workspace..."_ |
| _Permission confusion_ | _Explain what role is needed and who can grant it_ | _"Only workspace admins can invite members. Contact [admin name]."_ |
| Commitment anxiety (non-destructive) | Show the commitment prominently before the confirm action; include it in post-activation confirmation | School opt-in commitment statement (J1, 1.0.1) |
| Abstract configuration (structure vs. value) | Explain calculation method inline where the actor may confuse structure with value | Template amount explanation: "amounts calculated per student at request time" (J1, 1.0.1) |
| Waiting after submission (no SLA) | Surface expected processing time as a soft indicator ("Bursars typically review within 1 school day") | Parent waiting for plan approval (J2, 1.0.1) |
| Silent session expiry (SMS) | Consider a session-expiry SMS so actors can restart; weigh against notification noise | 10-minute SMS session expiry (J3, 1.0.1) |
| Alert fatigue (bulk system events) | Evaluate digest vs. per-item alerts for high-volume scheduled jobs | Multiple missed instalment alerts sent simultaneously (J9, 1.0.1) |
| Destructive action on active record | Use secondary action position (not primary CTA); restate the action in the confirm button | Cancel Plan (J12, 1.0.1) |
| Credit disclosure anxiety (CRB framing) | "Reported to credit bureaus" triggers avoidance for parents associating CRB with blacklisting. Reframe proactively: CRB reporting builds credit history when repayments are honoured; consequences are negative only on missed payments. Consider an expandable "What does this mean?" if abandonment is high. | Consent Step 1 (J2, J3, 1.0.2) |
| Waterfall split confusion | Parent pays fees and sees less than full amount credited to school — feels like a shortfall. Root cause: expectation was not set at acceptance. Mitigation: in-app callout at acceptance showing how the split works before the first payment is made. SMS wording should lead with total debt reduced, not with "school balance unchanged." | J6 (1.0.2); set up in J2/J3 |
| Financial commitment with paybill routing | When a school opt-in involves routing (not just enabling), surface a concrete before/after example alongside the commitment: "lending partner disburses → school gets cash; future fee payments → school returns lender's share." Distinguish routing from ownership of credit risk. | J1 (1.0.2) |

---

## "After" Patterns

Standard ways to describe the real-world outcome. Keep these grounded and specific.

| After Type | Description | Anti-pattern |
|-----------|-------------|-------------|
| Task completion | Actor returns to their prior context with the task done | "User closes the tab" (too shallow) |
| Status change | Something in actor's world is now different | "Account created" (system state, not actor outcome) |
| Handoff | Actor tells someone else the thing is done | "Admin goes back to email" (no outcome) |
| SMS as receipt | A system event SMS serves as the actor's record of a real-world transaction | "Plan approved" (system state only) |
| Self-service deflection | A successful SMS self-service response is an inbound phone call that didn't happen | "Parent saw the balance" (no deflection framing) |
| Active record + passive oversight | Actor completes a transaction; dashboard reflects the change without requiring navigation | "Bursar recorded payment; dashboard updated" |
| Passive waterfall repayment | Actor makes no new decisions after accepting credit; system automatically allocates each payment; SMS receipt after each waterfall event confirms the split. Expectation set at acceptance is the key UX lever — not the waterfall SMS itself. | J6, J7 (1.0.2) |

---

## Established Journeys (add as features are built)

Track common journey arcs so new features can reference them.

| Journey Arc | Description | Used in |
|------------|-------------|---------|
| School feature opt-in with commitment | Admin enables a feature by accepting a displayed commitment — templates or configuration required before save | J1, 1.0.1-zeraki-instalment-plans |
| Parent SMS self-service (keyword → schedule → confirm) | Multi-step SMS flow initiated by keyword, with session timeout and re-entry path | J3, 1.0.1-zeraki-instalment-plans |
| Bursar approval queue (approve / adjust / decline / bulk approve) | Work queue with three per-item actions and a bulk action; processes parent-initiated requests | J5, 1.0.1-zeraki-instalment-plans |
| In-person plan creation (partial attention, time pressure) | Bursar creates a record during or immediately after a face-to-face conversation | J4, 1.0.1-zeraki-instalment-plans |
| Two-step consent (disclosure + confirmation) | Step 1: data sharing and CRB disclosure; Step 2: amount and repayment confirmation. Both steps must allow back/dismiss freely — consent validity depends on freely given confirmation. Applicable to any credit or data-sharing flow. | J2, J3, 1.0.2-zeraki-fee-top-up-credit |
| System-initiated credit offer (app + SMS dual path) | Offer delivered via push notification + in-app banner (app path) and offer SMS + keyword reply (SMS path). Same two-step consent applies on both paths; SMS path has compression constraints and session timeout risk. | J2, J3, 1.0.2-zeraki-fee-top-up-credit |
