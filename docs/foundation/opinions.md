This document contains general thoughts on how I'd like the kit to work.
It is the `opinion` part of `opinionated framework`.

## Use JSON, not Markdown, for contracts:
- Json is trivial to render as MD; the inverse is not true
- Once contracts mature, they can be reworked as plain text
- Establish structure instead of inferring it using pattern-matching, or worse, exact-matching

## Start with well-formedness as a bootstrap:
- Assert that every prompt takes an input, even if it’s just text
- Assert that every prompt has an output, even if it’s just text
- Given a valid input, a prompt should be able to proceed without breaking any defined rules
- Given an invalid input, a prompt should fail back to the agent that called it

## Use contracts, don’t defer to prompts:
- A prompt should contain everything needed to fulfill its responsibilities
- Do not say “refer to <specific prompt>” to get contract details
- Document the contract separately, and have both the producing and consuming prompt refer to it
- Contracts should prioritize agent-to-agent communication

## Only outputs matter - so the things that matter need to be outputs
- If a particular process needs to be followed, then evidence of the process needs to be an output of the prompt

## Some things need pairs
- A single agent can take shortcuts to get to an accepted output
- But an agent is unlikely to take shortcuts on behalf of another agent
- Separate multi-step processes among agents to break the incentive to skip over steps
- Example: Test Driven Development
  - Make one agent red, have it write the failing test
  - Make one agent green, have it verify the failing test and code until it passes
  - Have each agent reject the other’s input if the process wasn’t followed
  - Make refactor its own agent as well

### Follow Up or Restart
- Changes to a spec or prompt are follow-up work, not changes to work in progress
- Always consider whether the spec can be finished as-is and a new spec created, even if some work will be wasted
- If the spec cannot be completed as written, discard work in progress and restart the workflow
- Try to keep stories small enough that discarding work to keep the spec clean is not prohibitively expensive

## Inspect and Adapt
- Prompts should document inconsistencies while they’re being used
- Documentation should be light - make a note and return to the main flow of the prompt
- A final prompt should aggregate the issues and produce recommendations after the spec story is done
- Prefer to continue on and adapt the prompts at the end, rather than trying to fix prompts mid-cycle
- Not every cycle should find an inconsistency; ideally, most won't
- Not every inconsistency needs to be automated away; deferring to the human can avoid bloating the prompts
- Inspect and adapt should be batchable; with the information captured and committed, it can be aggregated for review

## Measure, don’t Target
- “When a measure becomes a target, it ceases to be a useful measure”
- Monitor the length, depth, and complexity of prompts before vs after changes
- Don’t target specific metrics - consider every change’s value vs cost

## Justify Its Existence
- https://xkcd.com/927/
- For this to be useful, it needs to do something better than existing spec-kit
- It also needs to at least do the things I do, as well as spec-kit
- It can do some things worse than spec-kit, as long as they’re not things that I normally do
- It can do some things worse than spec-kit, as long as they’re not things that I normally do
