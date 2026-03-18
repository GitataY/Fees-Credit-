# Agent Pipeline

This document explains how the agents in this folder connect, what each one consumes, and what it produces. It is a reference note — not a spec, not an agent.

---

## The Full Pipeline

```
                        ┌─────────────────────────────┐
                        │       specs-writer.md       │
                        └─────────────┬───────────────┘
                                      │ produces
                          ┌───────────┴─────────────────────┐
                          ▼                                 ▼
               features/[name].md           specs/[name].md
               (Feature Spec)                   (BDD Spec)
                          │                                 │
                          └───────────┬─────────────────────┘
                                      ▼
                        ┌─────────────────────────────┐
                        │    ux-journey-designer      │
                        └─────────────┬───────────────┘
                                      │ produces
                                      ▼
                              journeys/[name].md
                              (User Journey)
                                      │
                                      ▼
                        ┌─────────────────────────────┐
                        │      ui-spec-designer       │
                        └─────────────┬───────────────┘
                                      │ produces
                                      ▼
                              ui-specs/[name].md
                              (UI Spec)
```

---

## Stage-by-Stage Reference

### Stage 1 — Specs Writer
**File**: `specs-writer.md`
**Input**: Product decisions, requirements, open questions
**Produces**:
- `features/[name].md` — Feature Spec (what, why, actors, flows, business rules, data contracts)
- `specs/[name].md` — BDD Spec (Gherkin scenarios for every behavior, written after Feature Spec is confirmed)

**Rule**: Feature Spec always comes first. BDD scenarios are only written once the Feature Spec is confirmed.

---

### Stage 2 — UX Journey Designer
**File**: `ux-journey-designer.md`
**Input**: `features/[name].md` (primary), `specs/[name].md` (validation)
**Produces**: `journeys/[name].md` — step-by-step user journey narrative (actor goals, emotional states, friction points, design decisions, micro-copy, error flows)

**Rule**: One journey file per feature. Includes a BDD Coverage Check table at the end — every BDD scenario must map to a named journey moment.

---

### Stage 3 — UI Spec Designer
**File**: `ui-spec-designer.md`
**Input**: `journeys/[name].md` (primary), `features/[name].md` (reference)
**Produces**: `ui-specs/[name].md` — screen-by-screen UI specification (layout intent, component inventory, component states, micro-copy, screen transitions)

**Rule**: One UI Spec per feature. Component names introduced here become the design system vocabulary — must be consistent across all specs.

---

## Directory Map

```
pm-agentic-workflow/
├── agents/                  ← Agent definitions (this folder)
│   ├── PIPELINE.md          ← You are here
│   ├── specs-writer.md
│   ├── ux-journey-designer.md
│   └── ui-spec-designer.md
│
├── features/                ← Stage 1 output: Feature Specs
├── specs/                   ← Stage 1 output: BDD Specs
├── journeys/                ← Stage 2 output: User Journey narratives
└── ui-specs/                ← Stage 3 output: UI Specifications
```

---

## File Naming Convention

All output files mirror the same filename across stages:

```
features/1.0.1-customer-registration-and-auth.md   ← Feature Spec
specs/1.0.1-customer-registration-and-auth.md       ← BDD Spec
journeys/1.0.1-customer-registration-and-auth.md    ← User Journey
ui-specs/1.0.1-customer-registration-and-auth.md    ← UI Spec
```

This makes tracing any screen or behavior back to its origin spec a single lookup.

---

## What Is NOT an Agent

The following files in this folder are not agents — they are reference documents:
- `PIPELINE.md` — this file

---

## Agents at a Glance

| Agent | Role | Primary Input | Primary Output |
|-------|------|--------------|----------------|
| Specs Writer | Feature + BDD specs | Product decisions | `features/`, `specs/` |
| UX Journey Designer | User journey narratives | `features/` | `journeys/` |
| UI Spec Designer | Screen + component specs | `journeys/` | `ui-specs/` |
