# Product Context

Cross-cutting decisions that apply across all features. Every agent reads this file. Update it as decisions are made.

---

## Product Identity

**Product name**: [TBD]
**One-line description**: [TBD]
**Primary platform**: [Web / Mobile / Desktop / Cross-platform]

---

## Global Navigation & Layout

Describe the shared navigation structure, persistent UI elements, and page layout patterns that all features must respect.

- **Navigation type**: [Top nav / Sidebar / Tab bar / None yet]
- **Persistent elements**: [Header, footer, notification area, etc.]
- **Layout shell**: [Describe the outer container that all feature screens live inside]

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
| _Example: Customer_ | _End user who purchases products_ | _1.0.1-customer-registration_ |

---

## Cross-Feature Dependencies

When Feature B depends on Feature A, record it here so agents can reference the dependency.

| Feature | Depends on | Nature of dependency |
|---------|-----------|---------------------|
| _Example: 1.0.3-checkout_ | _1.0.1-customer-registration_ | _User must be authenticated to check out_ |

---

## Global Business Rules

Rules that apply across multiple features. Feature-specific rules live in their own spec.

- _None yet_

---

## Design Tokens (when established)

Shared visual decisions that all UI specs must respect.

- **Primary action color**: [TBD]
- **Destructive action color**: [TBD]
- **Border radius convention**: [TBD]
- **Spacing scale**: [TBD]
- **Typography scale**: [TBD]
