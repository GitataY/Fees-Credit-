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

---

## Friction Resolution Patterns

Standard ways to resolve common friction points. Reference these instead of reinventing.

| Friction Type | Resolution Pattern | Example |
|--------------|-------------------|---------|
| _Form anxiety_ | _Show progress, validate inline, explain why data is needed_ | _"3 of 4 steps complete"_ |
| _Irreversible action_ | _Confirmation dialog restating the action and consequences_ | _"Delete project 'Acme'? This cannot be undone."_ |
| _Waiting/loading_ | _Skeleton screen + time estimate if >3s_ | _"Setting up your workspace..."_ |
| _Permission confusion_ | _Explain what role is needed and who can grant it_ | _"Only workspace admins can invite members. Contact [admin name]."_ |

---

## "After" Patterns

Standard ways to describe the real-world outcome. Keep these grounded and specific.

| After Type | Description | Anti-pattern |
|-----------|-------------|-------------|
| Task completion | Actor returns to their prior context with the task done | "User closes the tab" (too shallow) |
| Status change | Something in actor's world is now different | "Account created" (system state, not actor outcome) |
| Handoff | Actor tells someone else the thing is done | "Admin goes back to email" (no outcome) |

---

## Established Journeys (add as features are built)

Track common journey arcs so new features can reference them.

| Journey Arc | Description | Used in |
|------------|-------------|---------|
