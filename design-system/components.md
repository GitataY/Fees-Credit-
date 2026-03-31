# Component Vocabulary

The canonical list of component names used across all UI specs. The UI Spec Designer must consult this file before introducing new components, and must update it when a new component is introduced.

This file is the design system's source of truth for naming. All UI specs must use these exact names.

---

## How to Use This File

- **Before writing a UI spec**: Read this file. If a component you need already exists, use its name exactly.
- **When introducing a new component**: Add it here with its type, purpose, and minimum states. Then use it in the UI spec.
- **Never duplicate**: If `TextInput` exists, don't introduce `TextField` or `InputText`.

---

## Components

### Inputs

| Component Name | Type | Purpose | Minimum States |
|---------------|------|---------|----------------|
| TextInput | Input | Single-line text entry | default, focused, filled, error, disabled |
| NumberInput | Input | Numeric value entry | default, focused, filled, error, disabled |
| DateInput | Input | Date picker / date entry | default, focused, filled, error, disabled |
| SelectInput | Input | Dropdown single-select | default, focused, selected, error, disabled |
| TextareaInput | Input | Multi-line text entry | default, focused, filled, error, disabled |
| RadioGroup | Input | Single-choice selection from a set of labeled options | default, selected, disabled |

### Buttons

| Component Name | Type | Purpose | Minimum States |
|---------------|------|---------|----------------|
| PrimaryButton | Button | Main call to action | default, hover, loading, disabled, success |
| SecondaryButton | Button | Alternative or cancel action | default, hover, disabled |
| DestructiveButton | Button | Irreversible or high-risk actions | default, hover, loading, disabled |
| GhostButton | Button | Low-emphasis action; often used for menus or secondary navigation | default, hover, disabled |
| IconButton | Button | Compact action represented by an icon (e.g., remove row) | default, hover, disabled |

### Feedback

| Component Name | Type | Purpose | Minimum States |
|---------------|------|---------|----------------|
| AlertBanner | Feedback | Page-level contextual message | success, error, warning, info |
| ToastNotification | Feedback | Transient confirmation after an action (auto-dismisses) | success, error |
| InlineValidationMessage | Feedback | Field-level error shown below an input | hidden, visible |
| InlineBackdateNotice | Feedback | Contextual notice when a date entry differs from today (e.g. backdated payment) | hidden, visible |
| ConfirmationDialog | Feedback / Overlay | Modal confirmation for destructive or irreversible actions | open, confirming, closed |
| StatusBadge | Feedback / Display | Inline indicator of a record's current status | per-status values (see ui-specs for value sets) |

### Layout

| Component Name | Type | Purpose | Notes |
|---------------|------|---------|-------|
| FormCard | Container | Groups related form fields | Centered on page, max-width constrained |
| PageHeader | Layout | Screen title, optional subtitle, breadcrumb | Sits at top of content area inside the Finance shell |
| SectionHeader | Layout | Within-page section title and divider | Used to separate logical groups of content on a single screen |
| EmptyState | Layout | Empty list or section with message and optional action | Follows pattern: [What would be here] + [How to get started] |
| CommitmentCard | Container / Callout | Elevated card used to surface an important statement the user must read before acting | left border accent; full-size text — never small print |

### Navigation

| Component Name | Type | Purpose | Notes |
|---------------|------|---------|-------|
| BreadcrumbNav | Navigation | Path indicator within the Finance module hierarchy | Muted secondary text; not a primary navigation element |
| TabBar | Navigation | Horizontal tab strip for multi-section views | Also used as SegmentedControl for binary/ternary toggles |

### Data Display

| Component Name | Type | Purpose | Minimum States |
|---------------|------|---------|----------------|
| DataTable | Data Display | Tabular data with column headers; supports filtering and row actions | loading, populated, filtered-empty, empty |
| MetricCard | Data Display | Single KPI tile — large value + label | loading, populated, zero, alert |
| InstalmentScheduleRow | Data Display | Single row in a payment plan schedule — instalment number, due date, amount, status | default, first (may have rounding), missed (warning color) |
| PaymentHistoryRow | Data Display | Single row in a payment history list — date, amount, method, reference | default |
| PlanSummaryCard | Data Display | Compact card summarising a plan's total, instalment count, and template name | loading, populated |
| SelectableCard | Input / Data Display | Tappable card used to select from a set of options (e.g. template selection) | default, selected, loading |
| FeatureDescriptionBlock | Content Block | Explains a feature's purpose — headline + body. Used on settings screens before opt-in. | default |
| OfferBanner | Content Block / AlertBanner variant | In-app banner surfacing a credit offer on the fee screen. Uses school name as trust signal. | hidden, visible, dismissed |
| OfferHeadlineBlock | Content Block | Leads with credit amount and student name — dominant visual element on the offer screen. | loading, populated |
| HowItWorksBlock | Content Block | Explains offer mechanics (credited to school, repaid through regular payments) before consent. | default |
| RepaymentScheduleBlock | Data Display | Shows estimated per-period repayment amount and KES total repayment. | loading, populated |
| WaterfallExpectationCallout | CommitmentCard variant | Sets waterfall split expectation at acceptance — part of each future payment will be split. Soft/informational variant of CommitmentCard. | visible, hidden |
| DataSharingDisclosureBlock | Content Block | Consent Step 1 — states data sharing and CRB reporting commitments explicitly. Full-size, not small print. | default |
| CRBFramingBlock | Content Block | Reframes CRB reporting as consequence of behaviour (positive if repaid; negative only if missed). Companion to DataSharingDisclosureBlock. | default |
| ProcessingStatusBlock | Content Block | Bridges ACCEPTED → DISBURSED gap post-acceptance. Changes state based on disbursement webhook. | processing, disbursed, failed |
| DisbursementTimelineBlock | Data Display | Shows when and how much was credited to the school's paybill for one arrangement. | loading, credited, pending, failed |
| WaterfallAllocationList | Data List | Chronological list of fee payments and their waterfall split per arrangement. | loading, populated, empty, completed |
| ArrangementMetadataPanel | Content Block | Technical metadata for one credit arrangement — consent channel, date, tier, ID. | default |
| DisbursedMetricHero | Data Display (hero) | Visually dominant metric card for the primary value metric on the Credit Dashboard. Larger type and distinct card treatment vs. standard MetricCard. | loading, populated, zero |
| RiskClarificationCallout | CommitmentCard variant | Answers "does the school owe money?" before the admin reads the commitment. Single sentence, info tone. | default |
| ReadOnlyNotice | Content Block | Persistent label clarifying that a dashboard is view-only and no actions are available. | default |
| EscalationRouteBlock | Content Block | Persistent Zeraki Finance support contact shown on credit dashboard and arrangement detail. Load-bearing in error states. | default, highlighted |

---

## Naming Conventions

- **PascalCase** for all component names (`TextInput`, not `text-input` or `textInput`)
- **Semantic names** that describe function, not implementation (`PrimaryButton`, not `BlueButton`)
- **No framework prefixes** (`TextInput`, not `MuiTextField` or `v-input`)
- **Specificity when needed** (`PasswordInput` not just `Input` — be precise enough that the name alone tells you what it is)
