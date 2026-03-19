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
