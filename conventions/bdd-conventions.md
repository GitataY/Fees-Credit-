# BDD Conventions

Standards for writing Gherkin scenarios across all features. The Specs Writer must consult this file and follow these patterns.

---

## What BDD Scenarios Are (and Are Not)

These scenarios are **acceptance criteria written in Gherkin format**. They define expected behavior from the user's perspective. They are NOT:

- Executable test code (developers translate these into tests)
- Implementation specifications (they don't reference tables, APIs, or code)
- A substitute for the Feature Spec (they complement it)

---

## Scenario Naming

```gherkin
# Good — describes the behavior and outcome
Scenario: New customer registers with valid email and password

# Bad — describes implementation
Scenario: POST /api/register returns 201

# Bad — too vague
Scenario: Registration works
```

---

## Step Patterns

### Given (preconditions)
- Describe the world state, not setup code
- `Given a customer with email "user@example.com" does not exist`
- NOT: `Given the database is empty`

### When (actions)
- Describe what the actor does, not what the system does
- `When the customer submits the registration form`
- NOT: `When a POST request is sent to /register`

### Then (outcomes)
- Describe observable results from the actor's perspective
- `Then the customer sees a confirmation message`
- `Then the customer receives a verification email`
- NOT: `Then the database contains a new user row`

---

## Tagging Convention

```gherkin
@phase1 @feature-name @happy-path    # Normal flow
@phase1 @feature-name @edge-case     # Boundary condition
@phase1 @feature-name @error-path    # Failure scenario
```

---

## Scenario Organization Order

1. Happy path scenarios first
2. Edge cases second
3. Error paths last

Within each group, order from most common to least common.

---

## Established Patterns (add as features are built)

| Pattern | Example | Used in |
|---------|---------|---------|
| _Example: Auth precondition_ | _Given the customer is signed in_ | _Multiple features_ |
