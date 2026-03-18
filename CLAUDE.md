## Spec Cascade Rule

Whenever a `features/*.md` file is modified (by you or the user), immediately and automatically:

1. Check if corresponding files exist in `specs/`, `journeys/`, and `ui-specs/` with the same filename
2. For each that exists, read it and identify what changed in the feature file
3. Cascade the relevant changes into each downstream file — do not wait to be asked
4. Only stop and ask if a change in the feature is ambiguous enough that you cannot confidently cascade it

**Never consider a feature file edit "done" until all existing downstream files are in sync.**

## Pipeline Stage Order

The pipeline runs in strict order: `features/` → `specs/` → `journeys/` → `ui-specs/`

- Never skip a stage. If asked to produce a file at stage N but the stage N-1 file doesn't exist yet, create the missing upstream file first.
- Example: asked to write a UI spec but no journey file exists → write the journey first, then the UI spec.

`brainstorms/` is independent — it is not part of the pipeline. Files there are free-form working documents. The user decides when one is ready and hands it to the Specs Writer manually. Never auto-cascade from or into `brainstorms/`.

## File Naming Convention

All files across `features/`, `specs/`, `journeys/`, and `ui-specs/` must share the exact same filename.

```
features/1.0.1-customer-registration-and-auth.md   ← source
specs/1.0.1-customer-registration-and-auth.md
journeys/1.0.1-customer-registration-and-auth.md
ui-specs/1.0.1-customer-registration-and-auth.md
```

Never create a downstream file with a different name than its feature file.
