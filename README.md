# PM Agentic Workflow

A structured pipeline of AI agent definitions that transform product ideas into implementation-ready artifacts — stage by stage, with no ambiguity left for developers to resolve.

---

## What This Is

This repo defines a **product management pipeline powered by AI agents**. Each agent has a precise role, a defined input, and a defined output. Together they form an assembly line: raw product thinking goes in one end, fully-specced UI blueprints and technical plans come out the other.

The agents don't write code — they write the specifications, user journeys, screen blueprints, and technical specs that eliminate the gap between "we decided to build X" and "a developer can start building X today."

---

## The Pipeline

```
  ┌─────────────────────┐
  │  Idea Brainstormer   │  →  brainstorms/[name].md  (Product Brief)
  └────────┬─────────────┘
           │ required input ↓
  ┌─────────────────┐
  │  Specs Writer    │  →  features/[name].md   (Feature Spec)
  │                  │  →  specs/[name].md       (BDD Spec)
  └────────┬─────────┘
           │ required input ↓
  ┌─────────────────────┐
  │  UX Journey          │  →  journeys/[name].md  (User Journey)
  │  Designer            │
  └────────┬─────────────┘
           │ required input ↓
  ┌─────────────────────┐
  │  UI Spec             │  →  ui-specs/[name].md  (UI Spec)
  │  Designer            │
  └────────┬─────────────┘
           │ required input ↓
  ┌─────────────────────┐
  │  Technical Spec      │  →  tech-specs/[name].md  (Technical Spec)
  │  Writer              │
  └──────────────────────┘
```

Each agent checks its own preconditions and will **stop and redirect** if the required upstream file is missing — no skipping stages.

---

## Getting Started

### Prerequisites

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI installed
- This repo cloned locally

### How to Invoke Each Agent

Each agent is defined as a custom agent in `agents/`. You invoke them from Claude Code by name:

```bash
# Start a brainstorm session
claude "Use the Idea Brainstormer agent. I have an idea for a team onboarding tool."

# After brainstorm is ready — generate the feature spec
claude "Use the Specs Writer agent on brainstorms/team-onboarding-tool.md"

# After feature spec is confirmed — design the user journey
claude "Use the UX Journey Designer agent on features/1.0.1-team-onboarding.md"

# After journey is confirmed — produce the UI spec
claude "Use the UI Spec Designer agent on journeys/1.0.1-team-onboarding.md"

# After UI spec is confirmed — produce the technical spec
claude "Use the Technical Spec Writer agent on ui-specs/1.0.1-team-onboarding.md"
```

### The Review Gate

Every agent (except the Brainstormer) presents a **review summary** before its output is considered done:
- A self-assessment showing confidence levels per section
- Upstream feedback — issues discovered in the input files
- Coverage gaps — BDD scenarios or journey steps that aren't covered

**Review the output and confirm before moving to the next stage.** The agent will ask you explicitly.

---

## Pipeline Stages

### Stage 0 — Idea Brainstormer (Independent)

The Brainstormer sits outside the strict pipeline. It is a conversational agent — you talk through an idea or requirements, and it produces a structured **Product Brief** in `brainstorms/`. When you are satisfied, you hand it to the Specs Writer.

**Two modes — auto-detected:**
- **Devil's Advocate** — for new ideas you're still forming. Challenges hard, but respects a challenge budget (2-3 rounds per topic, then records the concern and moves on).
- **Expert Consultant** — for defined requirements. Asks deep questions, proposes improvements, flags risks.
- **Quick Update** — for minor revisions to existing briefs. Makes the change directly without re-entering challenge mode.

### Stage 1 — Specs Writer

Turns product decisions into two documents:
- **Feature Spec** (`features/`) — what, why, actors, flows, business rules, data contracts
- **BDD Spec** (`specs/`) — Gherkin scenarios covering every behavior, edge case, error path

Feature Spec always comes first. BDD scenarios are written once the Feature Spec is confirmed.

### Stage 2 — UX Journey Designer

Reads the Feature Spec and produces a **User Journey** (`journeys/`) — a step-by-step narrative of every actor's experience: Before (trigger & context), During (screen by screen with friction resolution), After (real-world outcome). Includes a BDD Coverage Check.

### Stage 3 — UI Spec Designer

Reads the User Journey and produces a **UI Spec** (`ui-specs/`) — screen-by-screen specification with layout intent, component inventory, component states, exact micro-copy, and transitions. Written precisely enough for a Figma designer to build without questions.

### Stage 4 — Technical Spec Writer

Reads the UI Spec + Feature Spec and produces a **Technical Spec** (`tech-specs/`) — API contracts, data model changes, integration points, security & performance considerations, and a phased implementation plan. Bridges the gap between "what to build" and "how to build it."

---

## Directory Structure

```
pm-agentic-workflow/
├── agents/                     ← Agent definitions (system prompts)
│   ├── idea-brainstormer.md
│   ├── specs-writer.md
│   ├── ux-journey-designer.md
│   ├── ui-spec-designer.md
│   └── technical-spec-writer.md
│
├── brainstorms/                ← Stage 0: Product Briefs (independent)
├── features/                   ← Stage 1: Feature Specs
├── specs/                      ← Stage 1: BDD Specs
├── journeys/                   ← Stage 2: User Journey narratives
├── ui-specs/                   ← Stage 3: UI Specifications
├── tech-specs/                 ← Stage 4: Technical Specifications
│
├── product-context.md          ← Cross-feature: shared patterns, actors, dependencies
├── design-system/
│   └── components.md           ← Cross-feature: canonical component vocabulary
├── conventions/
│   ├── micro-copy.md           ← Cross-feature: voice, tone, copy patterns
│   ├── bdd-conventions.md      ← Cross-feature: Gherkin writing standards
│   └── journey-patterns.md     ← Cross-feature: trigger, friction, outcome patterns
│
├── sync-reports/               ← Drift detection reports (auto-generated)
├── designs/                    ← Pencil.dev design files (.pen)
│
├── CLAUDE.md                   ← Pipeline rules and agent instructions
└── README.md
```

---

## Cross-Feature Consistency

### The Problem
Each feature goes through the pipeline independently, but real products need consistency — same component names, same copy patterns, same actors across features.

### The Solution
Shared context files that every agent reads and updates:

| File | What it ensures | Updated by |
|------|----------------|------------|
| `product-context.md` | Same actors, same navigation, same global rules | All agents |
| `design-system/components.md` | Same component names and states across all UI specs | UI Spec Designer |
| `conventions/micro-copy.md` | Same voice, tone, CTA patterns, error messages | UX Journey Designer, UI Spec Designer |
| `conventions/bdd-conventions.md` | Same Gherkin step style across all BDD specs | Specs Writer |
| `conventions/journey-patterns.md` | Same trigger and friction patterns across journeys | UX Journey Designer |

**Rule**: Before introducing anything new (component, actor, copy pattern), check the relevant file. If it exists, use it. If it doesn't, add it.

---

## Feedback Loops

### Forward: Drift Detection (replaces auto-cascade)

When a `features/*.md` file is modified, the system generates a **drift report** in `sync-reports/` listing which downstream files are affected and whether the change is mechanical or requires human judgment. You decide what to update.

### Backward: Upstream Feedback

Every agent (Specs Writer, UX Journey Designer, UI Spec Designer, Technical Spec Writer) includes an **Upstream Feedback** section in its output. When a downstream agent discovers a gap or inconsistency in the input file, it records the issue and proposed fix. You review and decide whether to update the upstream file.

### Git Pre-commit Hook

When committing changes to `features/*.md`, the hook checks whether downstream files exist but aren't staged. Blocks the commit with a warning. Bypass with `git commit --no-verify`.

---

## File Naming Convention

Every output file shares the exact same filename across all directories:

```
features/1.0.1-customer-registration.md
specs/1.0.1-customer-registration.md
journeys/1.0.1-customer-registration.md
ui-specs/1.0.1-customer-registration.md
tech-specs/1.0.1-customer-registration.md
```

This makes tracing any screen, behavior, or API endpoint back to its origin spec a single lookup.

---

## Feature Scope Guidelines

- **One feature = one coherent user goal.** If an actor can accomplish it without touching another feature, it's correctly scoped.
- **Split at ~8-10 screens.** UI specs with 15+ screens are too large to review.
- **Split when actors diverge completely.** If customer and admin share zero screens, they're separate features.
- **Shared screens**: The feature that owns the screen's primary purpose owns its spec. Others reference it.
- **One brainstorm → multiple features**: The Specs Writer produces separate feature specs. Dependencies are recorded in `product-context.md`.

See CLAUDE.md for the full scoping rules.
