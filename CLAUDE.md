## Drift Detection Rule

Whenever a `features/*.md` file is modified (by you or the user), immediately:

1. Check if corresponding files exist in `specs/`, `journeys/`, and `ui-specs/` with the same filename
2. For each that exists, read it and identify which sections are affected by the change
3. Generate a **drift report** in `sync-reports/[name].md` that lists:
   - What changed in the feature file
   - Which sections in each downstream file are affected
   - Whether the change is mechanical (rename, add field) or requires human judgment (flow redesign, new actor)
4. Present the drift report to the user and ask which downstream files to update

**Do NOT auto-edit downstream files.** Many feature changes require human judgment about how they affect journeys and UI specs. The drift report makes the impact visible so the user can decide what to update and in what order.

For mechanical changes (e.g. renaming a field, fixing a typo), the user may approve a batch update. For structural changes (e.g. adding a new flow, changing an actor), the user should re-run the relevant downstream agent.

**Never consider a feature file edit "done" until the drift report has been generated and presented.**

## Pipeline Stage Order

The pipeline runs in strict order: `brainstorms/` → `features/` + `specs/` → `journeys/` → `ui-specs/` → `tech-specs/`

**Stage entry requirements:**
| Stage | Agent | Required input |
|-------|-------|---------------|
| Stage 1 | Specs Writer | A `brainstorms/[name].md` brief |
| Stage 2 | UX Journey Designer | `features/[name].md` |
| Stage 3 | UI Spec Designer | `journeys/[name].md` |
| Stage 4 | Technical Spec Writer | `ui-specs/[name].md` + `features/[name].md` |

**If a required input does not exist, stop and redirect — do not proceed, do not auto-create.**
Tell the user exactly which file is missing and which agent produces it.

Example: user asks the UX Journey Designer to work on a feature but no `features/[name].md` exists → respond: "I need a Feature Spec before I can design the journey. Please run the Specs Writer on your brainstorm brief first to produce `features/[name].md`."

`brainstorms/` files are not covered by the Drift Detection Rule. The user controls when a brief moves to Stage 1.

## Cross-Feature Context

Every agent must read these shared files before producing output:

| File | Purpose | Who updates it |
|------|---------|---------------|
| `product-context.md` | Shared navigation, actors, dependencies, global rules | All agents — update when new cross-cutting decisions are made |
| `design-system/components.md` | Canonical component names and states | UI Spec Designer — consult before introducing any component, add new ones |
| `conventions/micro-copy.md` | Voice, tone, CTA patterns, error message patterns | UX Journey Designer and UI Spec Designer |
| `conventions/bdd-conventions.md` | Gherkin writing standards and step patterns | Specs Writer |
| `conventions/journey-patterns.md` | Recurring trigger, friction, and outcome patterns | UX Journey Designer |

**Rule**: Before introducing a new component, actor, copy pattern, or BDD step pattern, check the relevant convention file first. If it exists, use it. If it doesn't, add it to the convention file so future features stay consistent.

## Feature Scope & Granularity

### When to split vs. combine

- **One feature = one coherent user goal.** If an actor can accomplish the goal without touching another feature, it's correctly scoped.
- **Split when screens exceed ~8-10 per feature.** A UI spec with 15+ screens is too large to review. Break it into sub-features (e.g. `1.0.1a-registration`, `1.0.1b-email-verification`).
- **Split when actors diverge completely.** If the customer experience and the admin experience share zero screens, they are separate features.
- **Combine when splitting creates orphan screens.** If splitting would leave a screen that belongs to both features, keep them together or create a shared pattern in `product-context.md`.

### Shared screens

When two features share a screen (e.g. a dashboard that surfaces data from multiple features):
1. The feature that OWNS the screen's primary purpose owns the UI spec for that screen
2. Other features reference it: `"See Screen 3 in ui-specs/[owner-feature].md"`
3. Record the dependency in `product-context.md` under Cross-Feature Dependencies

### One brainstorm → multiple features

If a brainstorm produces multiple distinct features:
1. The Specs Writer should produce separate feature specs, each with its own filename
2. Record the relationship in `product-context.md` under Cross-Feature Dependencies
3. Each feature proceeds through the pipeline independently

## File Naming Convention

All files across `features/`, `specs/`, `journeys/`, and `ui-specs/` must share the exact same filename.

```
features/1.0.1-customer-registration-and-auth.md   ← source
specs/1.0.1-customer-registration-and-auth.md
journeys/1.0.1-customer-registration-and-auth.md
ui-specs/1.0.1-customer-registration-and-auth.md
```

Never create a downstream file with a different name than its feature file.
