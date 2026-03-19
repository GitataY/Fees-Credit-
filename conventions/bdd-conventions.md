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

---

## Full Example: Customer Registration

A reference example of a complete, well-formed BDD spec. Use it to calibrate scenario quality, naming, step language, and coverage depth.

```gherkin
# Feature: Customer Registration
# Phase: 1
# Spec: specs/1.0.1-customer-registration.md

Feature: Customer Registration
  As a new customer
  I want to create an account with my email and password
  So that I can access the platform and invite my team

  Background:
    Given the registration page is open
    And no account exists for "user@example.com"

  # ---- Happy Path ----

  @phase1 @registration @happy-path
  Scenario: New customer registers with valid credentials
    Given the customer enters email "user@example.com"
    And the customer enters a password that meets the requirements
    When the customer submits the registration form
    Then the customer sees a "Check your email" confirmation screen
    And the customer receives a verification email at "user@example.com"
    And the account is created in an unverified state

  @phase1 @registration @happy-path
  Scenario: Customer verifies their email address
    Given the customer has a valid verification link from their email
    When the customer opens the verification link
    Then the customer's account is activated
    And the customer is taken to the onboarding screen

  # ---- Edge Cases ----

  @phase1 @registration @edge-case
  Scenario: Customer submits form with leading and trailing whitespace in email
    Given the customer enters email "  user@example.com  "
    And the customer enters a valid password
    When the customer submits the registration form
    Then the account is created for "user@example.com"
    And the customer sees the "Check your email" confirmation screen

  @phase1 @registration @edge-case
  Scenario: Customer opens an expired verification link
    Given the customer has a verification link that is more than 24 hours old
    When the customer opens the verification link
    Then the customer sees an "This link has expired" message
    And the customer is offered the option to resend a new verification email

  @phase1 @registration @edge-case
  Scenario: Customer opens a verification link that has already been used
    Given the customer has already verified their account
    When the customer opens the same verification link again
    Then the customer is taken directly to the sign-in screen
    And no error is shown

  # ---- Error Paths ----

  @phase1 @registration @error-path
  Scenario: Customer attempts to register with an already-registered email
    Given an account already exists for "existing@example.com"
    And the customer enters email "existing@example.com"
    And the customer enters a valid password
    When the customer submits the registration form
    Then the customer sees the message "An account with this email already exists. Try signing in instead."
    And no new account is created

  @phase1 @registration @error-path
  Scenario: Customer submits form with an invalid email format
    Given the customer enters "notanemail" in the email field
    And the customer enters a valid password
    When the customer submits the registration form
    Then the customer sees the message "Please enter a valid email address"
    And the form is not submitted

  @phase1 @registration @error-path
  Scenario: Customer submits form with a password that is too short
    Given the customer enters a valid email address
    And the customer enters a password with fewer than 8 characters
    When the customer submits the registration form
    Then the customer sees the message "Password must be at least 8 characters"
    And the form is not submitted

  @phase1 @registration @error-path
  Scenario: Verification email fails to send
    Given the email delivery service is unavailable
    And the customer submits valid registration details
    When the customer submits the registration form
    Then the account is created in an unverified state
    And the customer sees the message "We couldn't send your verification email. You can request a new one from the sign-in screen."
```

### What makes this example correct

- **Feature header** states the actor, action, and business value — not a system description
- **Background** captures shared preconditions once — not repeated in every scenario
- **Happy path first**, then edge cases, then error paths
- **Scenario names** describe the outcome, not the mechanics ("registers with valid credentials", not "registration POST succeeds")
- **Given** describes world state ("no account exists for..."), not test setup ("database is seeded with...")
- **When** describes what the actor does ("submits the registration form"), not the system ("POST /api/register is called")
- **Then** describes what the actor observes ("sees a confirmation screen", "receives a verification email") — not internal state ("a row is inserted into users")
- **Error messages are exact** — copy the real string, never "an error is shown"
- **Edge cases are real** — whitespace trimming, expired links, already-used links — not invented scenarios
- **Every scenario is independently readable** — no implicit state carried between scenarios
