# PM Agentic Workflow

A structured pipeline of AI agent definitions that transform product ideas into implementation-ready artifacts — stage by stage, with no ambiguity left for developers to resolve.

---

## What This Is

This repo defines a **product management pipeline powered by AI agents**. Each agent has a precise role, a defined input, and a defined output. Together they form an assembly line: raw product thinking goes in one end, fully-specced UI and backend contracts come out the other.

The agents don't write code — they write the specifications, user journeys, and screen blueprints that eliminate the gap between "we decided to build X" and "a developer can start building X today."

---

## The Pipeline

```
Product decisions / requirements
           ↓
  ┌─────────────────┐
  │  Specs Writer   │  →  features/[name].md   (Feature Spec)
  │                 │  →  specs/[name].md       (BDD Spec)
  └────────┬────────┘
           ↓
  ┌─────────────────────┐
  │  UX Journey         │  →  journeys/[name].md  (User Journey)
  │  Designer           │
  └────────┬────────────┘
           ↓
  ┌─────────────────────┐
  │  UI Spec            │  →  ui-specs/[name].md  (UI Spec)
  │  Designer           │
  └─────────────────────┘
```

### Stage 1 — Specs Writer
Turns product decisions and requirements into two documents:
- **Feature Spec** (`features/`) — what the feature does, why it exists, all actors, flows, business rules, and data contracts
- **BDD Spec** (`specs/`) — Gherkin scenarios covering every behavior, edge case, and error path

Feature Spec always comes first. BDD scenarios are only written once the Feature Spec is confirmed.

### Stage 2 — UX Journey Designer
Reads the Feature Spec and produces a **User Journey** (`journeys/`) — a step-by-step narrative of every actor's experience: goals, emotional states, friction points, design decisions, micro-copy, and error flows. Includes a BDD Coverage Check to ensure every scenario has a journey moment.

### Stage 3 — UI Spec Designer
Reads the User Journey and produces a **UI Spec** (`ui-specs/`) — a screen-by-screen specification with layout intent, component inventory, component states, exact micro-copy, and screen transitions. Written precisely enough that a UI designer can open it and build in Figma without asking a single question.

---

## Directory Structure

```
pm-agentic-workflow/
├── agents/                  ← Agent definitions
│   ├── idea-brainstormer.md
│   ├── specs-writer.md
│   ├── ux-journey-designer.md
│   └── ui-spec-designer.md
│
├── brainstorms/             ← Independent: Product Briefs (not part of pipeline)
├── features/                ← Stage 1 output: Feature Specs
├── specs/                   ← Stage 1 output: BDD Specs
├── journeys/                ← Stage 2 output: User Journey narratives
├── ui-specs/                ← Stage 3 output: UI Specifications
└── designs/                 ← Pencil.dev design files (.pen)
```

---

## File Naming Convention

Every output file shares the exact same filename across all four directories:

```
features/1.0.1-customer-registration.md
specs/1.0.1-customer-registration.md
journeys/1.0.1-customer-registration.md
ui-specs/1.0.1-customer-registration.md
```

This makes tracing any screen or behavior back to its origin spec a single lookup.

---

## Idea Brainstormer — Independent Tool

The **Idea Brainstormer** (`agents/idea-brainstormer.md`) sits outside the pipeline. It is a conversational agent — you chat with it to explore or stress-test a product idea, and it produces a structured **Product Brief** saved in `brainstorms/`.

- `brainstorms/` is a free-form workspace. Multiple briefs can live there at any time, at any stage of maturity.
- Files are not auto-cascaded and are not covered by the pre-commit hook.
- When you're happy with a brief and ready to build, you hand it to the Specs Writer manually to kick off the pipeline.

The agent works in two modes — detected automatically from how you open the conversation:
- **Blank slate** — you have a raw idea, it helps you shape it
- **Existing context** — you bring something formed, it pokes holes and finds gaps

It acts as a critical co-founder: challenges assumptions, holds the line on vague answers, and won't let you skip past a weak problem definition.

---

## Consistency Enforcement

Two layers ensure downstream files never silently drift from their feature source:

### 1. CLAUDE.md Rule (AI-initiated edits)
Whenever a `features/*.md` file is modified by an AI agent, it automatically checks for and updates all corresponding downstream files in the same operation. Changes are never considered done until all downstream files are in sync.

### 2. Git Pre-commit Hook (manual edits)
When you commit changes that include `features/*.md`, the hook detects which downstream files exist but are not staged, and blocks the commit with a warning:

```
┌─────────────────────────────────────────────────────────────┐
│  ⚠️  PIPELINE SYNC WARNING                                   │
└─────────────────────────────────────────────────────────────┘

  You are committing changes to features/*.md but the following
  downstream files are NOT staged and may be out of sync:

  specs/1.0.1-customer-registration.md
  journeys/1.0.1-customer-registration.md
```

To bypass intentionally: `git commit --no-verify`

---

## How to Use

**Before the pipeline** (optional but recommended):
- Start a conversation with the Idea Brainstormer. It stress-tests your idea and saves a Product Brief to `brainstorms/`. When you're satisfied with the brief, hand it to the Specs Writer to kick off the pipeline.

**The pipeline:**
1. **Spec the feature** — give the Specs Writer your requirements (or a brainstorm brief). It produces the Feature Spec first, BDD spec second.
2. **Run the journey** — give the UX Journey Designer the Feature Spec. It maps every actor flow into a human narrative.
3. **Spec the UI** — give the UI Spec Designer the journey. It produces a screen-by-screen spec ready for Figma.
4. **Commit** — the pre-commit hook ensures you don't drift.
