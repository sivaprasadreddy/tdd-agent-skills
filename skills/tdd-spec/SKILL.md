---
name: tdd-spec
description: Clarify feature intent, resolve business-rule ambiguities, and produce reviewable behavioral requirements and acceptance criteria before implementation.
disable-model-invocation: true
---

# Behavior Specification

## Purpose
Establish what the software must do before an agent chooses how to implement it.

## Workflow
1. Read the available request, issue, specification, and relevant project context.
2. Separate explicit requirements from assumptions and inferred details.
3. Identify ambiguities, conflicting rules, missing failure behavior, boundary conditions, and relevant security or data-integrity concerns.
4. Ask the human only the questions whose answers materially affect expected behavior. Group related questions; do not ask about implementation details unless they affect behavior.
5. Suggest relevant edge cases and negative scenarios. Clearly label suggestions that need a business decision.
6. Produce a concise behavior specification with:
   - Goal and scope
   - Actors and preconditions
   - Main success paths
   - Validation and failure behavior
   - Business rules and invariants
   - Boundary and edge cases
   - Acceptance criteria stated as observable outcomes
   - Explicit assumptions and out-of-scope items
7. Save the specification as `{feature-title}-spec.md` in the feature's agreed documentation location. Use a short, filesystem-safe feature title (lowercase kebab-case); do not overwrite an existing specification without checking with the human. Present the file for human review. Do not treat unresolved assumptions as approved requirements.

## Rules
- The human owns business intent and final decisions about expected behavior.
- Do not silently invent business rules or convert technical preferences into business requirements.
- Prefer observable behavior over prescribing classes, methods, frameworks, or internal design.
- Reuse existing project conventions and documented decisions; call out conflicts rather than silently overriding them.
- Keep requirements testable, specific, and concise.
- Do not begin feature implementation until the behavior and material ambiguities are approved.

## Handoff
Provide the approved `{feature-title}-spec.md` and its acceptance criteria to `tdd-tests` and, when useful, the implementation-planning workflow.
