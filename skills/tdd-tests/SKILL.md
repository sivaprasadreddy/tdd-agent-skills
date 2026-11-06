---
name: tdd-tests
description: Derive reviewable, implementation-independent test scenarios from approved requirements and acceptance criteria.
disable-model-invocation: true
---

# Test Design

## Purpose
Turn approved expected behavior into a test strategy that can detect incorrect implementations, not merely confirm the code's assumptions.

## Workflow
1. Read the approved behavior specification and acceptance criteria. If they are missing or ambiguous, request clarification through `tdd-spec`.
2. Derive scenarios for:
   - Successful behavior
   - Validation and rejection paths
   - Boundaries and edge cases
   - State changes and invariants
   - Failure atomicity and rollback where relevant
   - Authorization, security, and data isolation where relevant
   - Concurrency, retries, and duplicate requests where relevant
   - Compatibility and regression behavior where relevant
3. For each scenario, state setup/preconditions, action, and observable expected result.
4. Map scenarios to appropriate test levels: unit, integration, contract, end-to-end, or manual exploratory checks. Prefer testing behavior at the lowest level that provides meaningful confidence; use real infrastructure for important integration boundaries when practical.
5. Identify gaps in observability or testability and propose the smallest useful test seam. Avoid introducing abstractions solely to make tests easy.
6. Present the scenario set, test-level choices, and uncovered risks for human review before treating them as the verification baseline.
7. After approval, implement the tests or hand off a clear test plan for implementation.

## Rules
- Derive expected results from approved requirements, never from the current implementation.
- Do not assume that a scenario is correct merely because it is easy to test.
- Include negative assertions: rejected operations must leave state unchanged where the requirements demand it.
- Assert externally meaningful outcomes and important invariants; avoid brittle assertions about private implementation details.
- Do not over-mock. Mock external boundaries when useful, but test persistence, transactions, framework wiring, and integration behavior with realistic dependencies when those are material to correctness.
- Do not silently resolve conflicting requirements. Ask the human.
- Keep tests independent, deterministic, and repeatable.
- Do not claim that passing tests proves correctness; document important untested risks.

## Handoff
Provide the approved test scenarios, test-level strategy, and test suite to `tdd-implement` and `tdd-verify`.
