---
mode: agent
description: Create or update a living feature specification.
---

<!-- Artifact scope: Copilot-specific -->

# Specify

Create or update a living feature specification from the provided project request and context.

Use the input and output contract in `artifacts/contracts/specifier.contract.json`.

## Input

The input is a freeform project request plus any relevant context or existing
feature specification. The calling operation determines whether this creates or
updates the feature spec; this contract does not distinguish those cases.

## Instructions

- Define the feature and its intended behavior, not a single implementation change.
- Preserve valid existing behavior when updating a feature spec.
- Make ambiguity and assumptions explicit.
- Do not create an implementation plan, change delta, task list, or code.

## Output

Return the contract’s successful output, including the proposed living feature
specification and its repo-relative `spec.md` path. If the input is insufficient,
return the contract’s `needs_input` output with the questions needed to continue.

If the input is invalid or insufficient, return the questions needed to continue and do not invent requirements.
