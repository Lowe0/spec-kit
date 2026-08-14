This document contains general thoughts on how I'd like the kit to work.
It is the `opinion` part of `opinionated framework`.

## Copilot-Friendly, Not Copilot-Only
- Terms like `agent`, `prompt`, and `instructions` are borrowed from GitHub Copilot
- The kit should avoid architecture that makes it only work with Copilot
- Copilot is the current build target, but each artifact should document whether it is common, Copilot-specific, or not yet classified
- While no specific non-Copilot hosts are in scope right now, that could change in the future
  - If that happens, the `artifacts` folder should be split into common and host-specific versions
  - The existing classifications should provide the starting point for that separation
  - Releases of the kit should then combine the common and one-host-specific version, similar to how programs build for multiple operating systems and binary architectures in a single release

## Bring Your Own Memory Bank
- This kit will provide a basic memory bank, but it is intended to be replaced by the user.
- Building the ideal memory bank is not a goal of this kit.
- In future versions, creating a memory bank could itself be spun off as an agent, looking at how other kits are structured and proposing the best mix for the developer.

## Bring Your Own Agents, Too
- This kit will provide agents and prompts that are more well-defined than the memory bank
- However, it's still not meant to be a turnkey system
- The agents and prompts should be enough to get through an exploratory project
- Users should expect to make limited changes to the agents as they start their main project
- Once the main project is established, users can make larger changes or fully replace agents with new ones that adhere to the same contracts

## Spec-Anchored
- Use a spec to define a feature, not a change
- The `specify` prompt should create or update an evolving spec
- A separate artifact is needed for traceability
  - Part of a per-change plan file?
  - A per-change delta spec?

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
- Contracts sit between agents, so naming them after a specific agent is an anti-pattern

## Only outputs matter, so the things that matter need to be outputs
- If a particular process needs to be followed, then evidence of the process needs to be an output of the prompt

## Some things need pairs
- A single agent can take shortcuts to get to an accepted output
- But an agent is unlikely to take shortcuts on behalf of another agent
- Separate multistep processes among agents to break the incentive to skip over steps
- Example: Test-Driven Development
  - Make one agent red, have it write the failing test
  - Make one agent green, have it verify the failing test and code until it passes
  - Have each agent reject the other’s input if the process wasn’t followed
  - Make refactor its own agent as well

## Follow Up or Restart
- Prefer to finish a change as planned, rather than altering the plan mid-change
- If the change can be implemented as planned, then finish and follow up with a new plan
- If the change cannot be implemented as planned, discard work in progress and restart the workflow
- Try to keep stories small enough that discarding work to keep the spec clean is not prohibitively expensive

## Inspect and Adapt
- Prompts should document inconsistencies while they’re being used
- Do not break out of the workflow, just document the issue and continue
- A final prompt should aggregate the issues and produce recommendations after the spec story is done
- Prefer to continue on and adapt the prompts at the end, rather than trying to fix prompts mid-cycle
- Not every cycle should find an inconsistency; ideally, most won't
- Not every inconsistency needs to be automated away; deferring to the human can avoid bloating the prompts
- Inspect and adapt should be batchable; with the information captured and committed, it can be aggregated for review

## Measure, don’t Target
- “When a measure becomes a target, it ceases to be a useful measure”
- Monitor the length, depth, and complexity of prompts before vs after changes
- Don’t target specific metrics; consider every change’s value vs cost

## Justify Its Existence
- https://xkcd.com/927/
- For this to be useful, it needs to do something better than existing spec-kit
- It also needs to at least do the things I do, as well as spec-kit
- It can do some things worse than spec-kit, as long as they’re not things that I normally do
- It can do some things worse than spec-kit, as long as they’re not things that I normally do
