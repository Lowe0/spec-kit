---
mode: agent
description: Create or update a living feature specification.
---

<!-- Artifact scope: Copilot-specific -->

# Specify

Create or update a living feature specification from the provided project request and context.

## Input

- Project request
- Relevant project context, if available
- Existing feature specification, if one exists

## Instructions

- Define the feature and its intended behavior, not a single implementation change.
- Preserve valid existing behavior when updating a feature spec.
- Make ambiguity and assumptions explicit.
- Do not create an implementation plan, change delta, task list, or code.

## Output

Return:

1. The proposed living feature specification.
2. Any unresolved questions that prevent the specification from being considered complete.
3. Any assumptions made while drafting or updating it.

If the input is invalid or insufficient, return the questions needed to continue and do not invent requirements.
