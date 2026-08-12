# Agent list

Agents are separated when they have different goals, inputs, outputs, or opportunities to verify another agent’s work. A workflow runner may invoke these agents in sequence; it does not need to be a domain-specific agent itself.

## Core workflow agents

| Agent | Verb | Responsibility | Key output |
| --- | --- | --- | --- |
| Specifier | `/specify` | Create or update the living feature spec. | Accepted feature spec, with unresolved questions made explicit. |
| Clarifier | Internal prompt invoked by `/specify` or `/change` | Resolve questions or ambiguities in a feature spec or change definition. | Decisions that can be incorporated into the relevant artifact. |
| Change designer | `/change` | Define one bounded change or delta against a living feature spec. | Accepted change artifact with traceability to the feature spec. |
| Planner | `/plan` | Turn the accepted change into an executable implementation plan. | Accepted plan with ordered work and verification points. |
| Red agent | `/implement` | Add a test or other executable check that demonstrates the missing behavior. | A failing test and evidence that it fails for the intended reason. |
| Green agent | `/implement` | Verify the Red agent’s failure, then implement the smallest change that makes it pass. | Passing tests and evidence that the intended failure is resolved. |
| Refactor agent | `/implement` | Improve the implementation while preserving the verified behavior. | Passing tests and evidence of the refactoring performed. |
| Acceptance agent | — | Independently verify that the implementation satisfies the change contract and contains the required evidence. | Accepted or rejected implementation handoff with reasons. |
| Sync agent | `/sync` | Reconcile the completed change with the living feature spec and finalize the change record. | Updated living spec and completed traceability artifact. |

## Supporting agents

| Agent | Verb | Responsibility | Key output |
| --- | --- | --- | --- |
| Inspect-and-adapt agent | — | Capture inconsistencies during a cycle and aggregate them for bounded review afterward. | Issues, recommendations, and a human decision where needed. |
| Commit agent | — | Verify the preceding handoff and create the configured commit. | Commit and handoff evidence. |

The Commit agent is optional because commit ownership is configurable. Inspect-and-Adapt may also be implemented as part of each workflow agent’s output plus a separate aggregation prompt; it does not need to interrupt the development flow.
