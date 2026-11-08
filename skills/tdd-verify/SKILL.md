---
name: tdd-verify
description: Challenge an implementation against approved requirements and test evidence, looking for gaps that a self-validating implementation workflow can miss.
disable-model-invocation: true
---

# Independent Verification

## Purpose
Determine whether the implementation satisfies the approved behavior—not merely whether the agent's tests pass.

## Workflow
1. Read the approved behavior specification and acceptance criteria independently of the implementation summary.
2. Inspect the actual code changes and test suite. Do not rely solely on the implementing agent's claims.
3. Trace each acceptance criterion to relevant tests and implementation evidence. Mark each as verified, partially verified, unverified, or failed.
4. Look for:
   - Missing or weak scenarios, especially negative paths and boundary conditions
   - Tests that duplicate implementation assumptions or assert only internal details
   - Incorrect expected values, incomplete assertions, and tests that can pass when behavior is wrong
   - Data-integrity, transaction, rollback, concurrency, retry, and duplicate-request defects where relevant
   - Authorization, validation, privacy, and error-handling gaps where relevant
   - Regressions and unintended scope changes
5. Run relevant tests and quality checks when possible. Record exact checks run and their outcomes.
6. Where useful, propose adversarial cases, mutation-testing checks, or independent manual checks to assess whether the tests would catch plausible defects.
7. Produce a concise verification report with criterion-level evidence, findings by severity, unverified areas, and a recommendation: accept, request changes, or seek a human decision.
8. If verification succeeds—all acceptance criteria are verified, relevant tests and quality checks pass, and no blocking findings or unverified areas remain—set `Status` to `COMPLETED` in the approved `{feature-title}-spec.md` metadata, preserving its other metadata and content. Otherwise, leave the status unchanged. This status records successful verification; the human retains final acceptance authority.

## Rules
- Treat the approved behavior specification—not the implementation or its tests—as the source of expected behavior.
- Passing tests are evidence, not proof. A green build alone is not an acceptance decision.
- Do not silently alter requirements or tests during verification.
- Distinguish confirmed defects from risks, missing evidence, and subjective suggestions.
- Do not report a check as passed if it was not executed.
- Escalate ambiguous or conflicting expected behavior to the human.
- The human retains final acceptance authority.

## Handoff
Return the verification report to the human. If changes are required, provide actionable findings to `tdd-implement`, preserving the approved requirements and test expectations.
