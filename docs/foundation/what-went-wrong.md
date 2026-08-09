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

## Amendment Bias
When a blocking issue came up during implementation, agents were inventing contrived solutions to avoid amending already-completed specifications.
The amendment process was meant to handle revisions to the current spec only, not to past work.
Changes that seemed like natural follow-ups were being avoided, citing the amendment process.