Previous attempts to solve this problem have been unsuccessful for these reasons:

### Silent Failures
Using the GitHub spec-kit with Auto model selection, agents will skip over sections that are explicitly defined in the prompts or rules.
When challenged on these failures, the suggestion is to add one-off checks to prompts.  These silent failures then continue to happen, even with the new rule in place.
Agents will apologize for the miss, but continue to make the same errors.

### Conflicting Rules
As new one-off checks are added, they can conflict with checks in other prompts, or even within the same prompt.

### Prompt Reviews Spiral
Using even the largest models, asking the agent to review the prompts will find new issues:
- Fixing those issues introduces new contradictions
- Which need new fixes
- Which cause new contradictions
- Which are then found on re-review
- Which spiral into an infinite loop of fixes and contradictions

### False Positives
Eventually, agent reviews will identify nonexistent issues, exacerbating the churn documented above.

## Scope Drift
When a blocking issue came up during implementation, agents were inventing contrived solutions to preserve the existing plan instead of treating the change as separate work.
A plan is either completed as written, or the work in progress is discarded and restarted with a new plan. Natural follow-ups must remain separate follow-up work.
