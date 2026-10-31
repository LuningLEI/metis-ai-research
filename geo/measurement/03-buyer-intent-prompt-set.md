# How to Build a Buyer-Intent Prompt Set for GEO

Prepared: 2026-10-30 · Series: GEO Playbook, 03/20 · Publisher: MICROFACTOR

A GEO question set is a measurement instrument. It defines which buyer situations your visibility results describe. If the questions are arbitrary, an accurately computed score can still answer the wrong business question.

The starting point should be the decisions your customers make, including situations where your product is unsuitable. A useful set captures those decisions without placing the desired brand name into every question.

## Define the target population honestly

Most teams do not possess a representative sample of everything real buyers ask assistants. They have sales conversations, support tickets, on-site search terms, product requirements, and selected community discussions. Those sources can support a purposeful evaluation set. They rarely justify claiming a market-wide visibility estimate.

Historical Reddit discussions, for example, can reveal attribution confusion or doubts about monitoring tools. They do not establish current query volume, verified buyer identity, or the prevalence of a particular problem.

Describe the set as a curated collection of relevant buying situations unless stronger sampling evidence exists. Record where each question originated and whether its wording was edited. Remove private details before adding customer-derived language to shared files.

## Build a task matrix before writing prompts

Use several dimensions, but avoid blindly enumerating every combination:

| Dimension | Example values for a fictional workplace application |
|---|---|
| Buyer role | Operations manager, IT reviewer, team administrator |
| Task | Schedule shifts, approve changes, export records |
| Constraint | Small team, intermittent connectivity, limited setup time |
| Decision stage | Discover options, compare approaches, verify a requirement |
| Market and language | Explicitly chosen target region and language |
| Brand condition | Unbranded discovery or named-brand verification |

The matrix exposes holes. A question set consisting entirely of broad discovery prompts may miss the constraints that determine whether a buyer can actually adopt a product.

Choose coverage intentionally. For a small baseline, include the most consequential situations first and explain what remains outside scope. More prompts do not automatically create better representativeness.

## Separate discovery from recognition

An unbranded question such as “Which scheduling tools support rotating shifts for a small operations team?” tests category discovery. A question such as “Does Example Scheduler support rotating shifts?” supplies the entity and tests a different capability.

Putting both in one denominator obscures that difference. Maintain separate cohorts with identifiers, intent labels, and inclusion rules. Track their results side by side rather than interpreting their average as one probability of being found.

Also include a few scope checks: questions for requirements your product does not support. These can reveal whether an answer inaccurately recommends the product outside its actual capabilities. High visibility is not inherently good when the recommendation is wrong.

## Version the instrument

At minimum, preserve these fields:

```text
prompt_id, prompt_version, cohort, buyer_task, constraints,
language, target_market, source_type, question_text, inclusion_reason
```

Keep wording stable in the baseline. If a product change makes a question obsolete, retire its version with a reason. Introduce the replacement explicitly instead of rewriting history. Keep exploratory prompts in a separate file or cohort.

Test conditions belong in the run record rather than being silently assumed: collection surface, search setting when observable, platform identifier, session context, and time. A question about a target market does not prove that the request was physically executed from that market.

## Plan repetitions around the inference

Repeated runs help describe variability within a scenario. New scenarios expand coverage. These are different uses of budget.

The [Anthropic evaluation guide](https://www.anthropic.com/research/demystifying-evals-for-ai-agents) distinguishes a task from repeated trials. Applied here, that distinction prevents a team from describing repeated versions of a single buyer question as broad market coverage.

Start with a modest, inspectable collection. Repeat selected questions across collection windows, then inspect whether observed differences are concentrated in one platform or task. If reporting intervals later, account for shared prompts and collection windows rather than treating every output as independent.

## Keep priority weights separate from observed demand

Some buying situations matter more commercially than others. You can assign weights for internal prioritization, but label their basis: sales-team judgment, documented opportunity mix, or another specified source. A subjective priority weight is not a measured query-frequency estimate.

If presenting a weighted aggregate, preserve the unweighted result and cohort breakdown. Freeze weights for a comparison period, or recompute both periods using the same declared weights. Otherwise, a change in business priorities can appear as an improvement in answer behavior even when the underlying outputs remain unchanged.

## Protect a holdout from editorial feedback

If every page is rewritten against the exact evaluation prompts, improvement may reflect adaptation to a narrow test. Reserve a small set of related questions that content authors do not use as drafting instructions. Compare performance there as a check on transfer.

This borrows the logic of evaluation separation rather than claiming a web publishing program is equivalent to model training. The practical concern is the same: optimization can overfit the instrument.

Metis AI can be assessed against this design using its [documented monitoring offering](https://www.metisai.vip/product/). Confirm which question configuration and record-keeping functions are available in the actual product. The supplied CSV is an editorial measurement template, not a claimed platform import format.

Resource: [Buyer-intent prompt CSV](../../resources/03-prompt-set.csv). Related: [metric definitions](04-measuring-ai-visibility.md) and [monitoring cadence](../monitoring/05-manual-vs-continuous-monitoring.md).
