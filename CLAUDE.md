## Spec Cascade Rule

Whenever a `features/*.md` file is modified (by you or the user), immediately and automatically:

1. Check if corresponding files exist in `specs/`, `journeys/`, and `ui-specs/` with the same filename
2. For each that exists, read it and identify what changed in the feature file
3. Cascade the relevant changes into each downstream file — do not wait to be asked
4. Only stop and ask if a change in the feature is ambiguous enough that you cannot confidently cascade it

**Never consider a feature file edit "done" until all existing downstream files are in sync.**

## Pipeline Stage Order

The pipeline runs in strict order: `brainstorms/` → `features/` + `specs/` → `journeys/` → `ui-specs/`

**Stage entry requirements:**
| Stage | Agent | Required input |
|-------|-------|---------------|
| Stage 1 | Specs Writer | A `brainstorms/[name].md` brief |
| Stage 2 | UX Journey Designer | `features/[name].md` |
| Stage 3 | UI Spec Designer | `journeys/[name].md` |

**If a required input does not exist, stop and redirect — do not proceed, do not auto-create.**
Tell the user exactly which file is missing and which agent produces it.

Example: user asks the UX Journey Designer to work on a feature but no `features/[name].md` exists → respond: "I need a Feature Spec before I can design the journey. Please run the Specs Writer on your brainstorm brief first to produce `features/[name].md`."

`brainstorms/` files are not auto-cascaded and are not covered by the Spec Cascade Rule. The user controls when a brief moves to Stage 1.

## File Naming Convention

All files across `features/`, `specs/`, `journeys/`, and `ui-specs/` must share the exact same filename.

```
features/1.0.1-customer-registration-and-auth.md   ← source
specs/1.0.1-customer-registration-and-auth.md
journeys/1.0.1-customer-registration-and-auth.md
ui-specs/1.0.1-customer-registration-and-auth.md
```

Never create a downstream file with a different name than its feature file.
