---
name: tdd-implement
description: Implement approved behavior with automated tests as a feedback loop, choosing test-first or exploratory implementation according to task risk and uncertainty.
disable-model-invocation: true
---

# Test-Verified Implementation

## Purpose
Implement the approved behavior while using tests as a meaningful feedback mechanism, without turning TDD into a ritual.

## Inputs
- Approved behavior specification and acceptance criteria
- Approved test scenarios or tests, where available
- Existing project architecture, conventions, and quality gates

## Workflow
1. Inspect the relevant code, tests, architecture, and project instructions before changing anything.
2. Choose an approach based on the task:
   - **Test-first by default:** business rules, calculations, state transitions, transactions, and well-understood behavior. Add or confirm a failing test before implementation.
   - **Explore first when justified:** unfamiliar integrations, UI discovery, prototypes, and technical spikes. Explore only enough to learn; once expected behavior is agreed, add tests before considering the work complete.
   - **Regression-first:** for bug fixes, create a test that reproduces the reported defect before applying the fix whenever practical.
3. Implement the smallest coherent change that satisfies the approved behavior and project conventions.
4. Run focused tests, diagnose failures, and correct the implementation. Then run relevant broader tests and quality checks.
5. Review changes for unintended behavior, security concerns, data integrity, transaction boundaries, and unnecessary complexity.
6. Report what changed, tests executed and their results, deviations from the specification, and remaining risks.

## Rules
- Treat approved requirements and tests as constraints, not suggestions.
- Never change, delete, weaken, skip, or make a test less meaningful merely to obtain a green build. If a test conflicts with an approved requirement, stop and ask for clarification.
- Do not generate tests solely from the implementation and present them as independent evidence.
- Do not make unrelated refactors or expand scope without approval.
- Do not hardcode test-specific behavior or use shortcuts that bypass real application behavior.
- Do not claim tests passed unless they were actually executed; distinguish not-run, blocked, and failed checks.
- If implementation reveals a requirement gap, return to the human for a decision instead of inventing behavior.
- Keep the implementation understandable and aligned with the project's established level of abstraction.

## Handoff
Deliver the implementation, test results, changed-file summary, deviations, and known risks to `tdd-verify`.
