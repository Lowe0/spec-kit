## Response

The strongest idea across these documents is that the kit should move responsibility out of prompt prose and into explicit, inspectable boundaries. The failures described in `what-went-wrong.md` are not primarily failures of wording. They are failures of enforcement: an agent can acknowledge a rule, skip it, and still produce something that appears acceptable. Adding more instructions increases the surface area for contradiction without changing that incentive.

Contracts therefore need to be more than documentation. They should define the smallest useful input and output shape, make invalid states visible, and give the next agent enough information to reject an incomplete handoff. JSON is a good canonical representation for this because it makes structure unambiguous and supports validation and rendering. Human-readable Markdown should remain a view of the contract or its evidence, not the source of truth.

The distinction between a contract and evidence is important. A contract describes what must be true at a boundary; evidence shows why we believe it is true. Evidence should be tied to observable facts—such as a test result, a file or symbol, a diff, or an explicit unresolved issue—rather than merely an agent’s assertion that it followed a process. Otherwise, “only outputs matter” risks replacing one form of compliance theater with another.

The proposed lightness is not just a matter of shorter prompts. It is a matter of reducing the amount of state each agent must hold in context and reducing the number of decisions that are left implicit. Small composable prompts with narrow contracts can help medium models, but composition also has a cost: every handoff can lose context, introduce translation errors, or add ceremony. A useful component should earn that cost by making a boundary independently verifiable or reusable. Agents should coordinate prompts, while contracts should carry the durable state between them.

The “pairs” idea is compelling where one agent’s success criterion is naturally different from another’s—for example, producing a failing test and then demonstrating that the implementation makes it pass. It should not become a universal requirement that doubles every step. The practical test is whether the separation creates an independent opportunity to detect a shortcut. If both sides can be satisfied by repeating the same unverified claim, the pair adds little.

The same principle applies to Inspect and Adapt. Lightweight issue capture during the main flow is valuable; an unconstrained prompt-review loop is exactly the spiral the history warns about. Adaptation should operate on concrete observations, have a bounded scope, and distinguish a real defect from a possible concern or a stylistic preference. The kit should make uncertainty explicit instead of forcing every observation into a rule.

Several principles reinforce one another:

- Well-formedness is the bootstrap layer. Before optimizing development behavior, every operation needs a valid input, a valid output, and a clear failure path.
- Verifiability is the trust layer. Entry and exit gates should be checkable from artifacts or execution results, not from obedience to prose.
- Composability is the reuse layer. Shared contracts should allow interchangeable implementations without requiring agents to know each other’s prompts.
- Measurement is the learning layer. Prompt size, handoff count, failure rate, and review churn are useful observations, but none should become a success target by itself.

There is also a useful scope boundary in the problem statement. This kit is for recurring, medium-sized changes where the cost of heavyweight planning exceeds its value. It should be deliberately opinionated about its supported workflow and deliberately honest when a task falls outside it. “At least as good as existing spec-kit for the work I actually do” is a better bar than feature parity, and it gives the project permission to leave unsuitable use cases alone.

My current view is that the kit’s defining feature should be a small set of machine-checkable contracts and evidence-bearing transitions, with prompts treated as replaceable implementations. If a behavior matters, the system should make violating it observable at a boundary. If it cannot do that, the behavior is guidance or preference—not a guarantee—and should be described accordingly.
