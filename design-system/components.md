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
| _Example: TextInput_ | _Input_ | _Single-line text entry_ | _default, focused, filled, error, disabled_ |
| _Example: PasswordInput_ | _Input_ | _Masked text entry with show/hide toggle_ | _default, focused, filled, error, disabled_ |

### Buttons

| Component Name | Type | Purpose | Minimum States |
|---------------|------|---------|----------------|
| _Example: PrimaryButton_ | _Button_ | _Main call to action_ | _default, hover, loading, disabled, success_ |
| _Example: SecondaryButton_ | _Button_ | _Alternative or cancel action_ | _default, hover, disabled_ |

### Feedback

| Component Name | Type | Purpose | Minimum States |
|---------------|------|---------|----------------|
| _Example: AlertBanner_ | _Feedback_ | _Page-level success/error/warning message_ | _success, error, warning, info_ |

### Layout

| Component Name | Type | Purpose | Notes |
|---------------|------|---------|-------|
| _Example: FormCard_ | _Container_ | _Groups related form fields_ | _Centered on page, max-width constrained_ |

### Navigation

| Component Name | Type | Purpose | Notes |
|---------------|------|---------|-------|

### Data Display

| Component Name | Type | Purpose | Minimum States |
|---------------|------|---------|----------------|

---

## Naming Conventions

- **PascalCase** for all component names (`TextInput`, not `text-input` or `textInput`)
- **Semantic names** that describe function, not implementation (`PrimaryButton`, not `BlueButton`)
- **No framework prefixes** (`TextInput`, not `MuiTextField` or `v-input`)
- **Specificity when needed** (`PasswordInput` not just `Input` — be precise enough that the name alone tells you what it is)
