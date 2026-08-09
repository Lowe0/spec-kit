## Problem statement:
Everyone using spec driven development says “just use opus”.  It’s expensive and overkill.

## Proposal:
A spec driven development setup that’s light enough for daily driving in sonnet.

## Principles:
Light
- Keep agents and prompts small
- Don’t scale up or down; this is for goldilocks problems, not massive projects or changing the color of a label
Contract-driven
- All handoffs should be in the form of defined contracts in and out
Composable
- Break repeated, shared actions into smaller prompts
- Use contracts as duck typing - if two prompts accept the same contract, and return the same contract, then they’re interchangeable
- Use prompts to do things, use agents to chain together prompts
Verifiable
- Record evidence of entry and exit gates in human-readable format
