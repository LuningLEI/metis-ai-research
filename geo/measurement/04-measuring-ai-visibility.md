# Measuring AI Visibility Beyond a Single Score

Prepared: 2026-10-30 · Series: GEO Playbook, 04/20 · Publisher: MICROFACTOR

An AI visibility metric is useful only when its denominator, observation unit, and inclusion rules are clear. “Visibility increased” can otherwise mean that a brand appeared more often, that a new question mix favored it, or simply that a failed collection disappeared from the calculation.

The following definitions are proposed reporting conventions. They are not a reconstruction of any vendor's proprietary scoring formula, and the examples are synthetic.

## Start with the run ledger

Let a scheduled trial consist of one versioned question, one collection surface, one platform configuration, and one collection attempt. Assign each attempt a status: completed, refused, failed, or otherwise unscorable under a documented rule.

For illustration, suppose a synthetic batch schedules 120 trials. Twelve fail and eight produce refusals. One hundred answers are completed and scorable. Report all three counts. The metrics below use those 100 answers; the completion and refusal rates remain separate.

That choice is not universal. Another study may count refusals in its overall answer denominator. Either convention can be reported transparently. Changing conventions between periods cannot support a clean comparison.

## Define answer-level measures

Let `N` be completed, scorable answers in a specified cohort. For each answer `i`, define:

- `m_i = 1` if the normalized brand entity is mentioned in the evaluated answer text.
- `c_i = 1` if the answer displays at least one qualifying citation to an approved brand-owned domain.
- `r_i = 1` if the brand is recommended as a suitable option under the annotation rubric.

Then:

```text
Mention rate             = sum(m_i) / N
Owned-domain citation rate = sum(c_i) / N
Recommendation rate       = sum(r_i) / N
```

If the synthetic batch has 26 mentions, 9 owned-domain citations, and 17 qualifying recommendations, the rates are 26%, 9%, and 17%. A citation to a brand-owned article can occur without a product recommendation. A third-party page can support a recommendation without an owned-domain citation.

Do not label the last metric “top-three” unless the response actually presents an ordered recommendation list. Record eligibility for ordered-list measures separately; unordered prose cannot reliably supply a third-place position.

## Keep prompt coverage separate

Prompt coverage asks how many distinct questions produced at least one qualifying observation. It uses questions as its unit, not answers.

```text
Prompt mention coverage = distinct prompts with a mention / tested prompts
```

The metric depends on the number of trials per prompt. A prompt tested ten times has more opportunities to produce one mention than a prompt tested once. Hold the repetition plan comparable and display it alongside coverage.

For a hypothetical set of 12 questions with equal repetition, a brand appearing on 5 questions has 41.7% prompt coverage. That number is not interchangeable with the answer-level mention rate.

## Name the competitor metric precisely

“Share of voice” is especially ambiguous. One possible definition is:

```text
Mention-incidence share = brand answer-incidences /
                         all tracked brands' answer-incidences
```

An incidence counts a tracked brand once per answer regardless of repeated name occurrences. The denominator changes when the tracked brand set changes, so preserve that set across comparisons. Multiple brands may appear in the same answer.

Another metric is each competitor's prompt coverage. It is valid but answers a different question. Report the explicit metric name rather than presenting either as a universal share-of-voice standard.

## Evaluate accuracy and citation support independently

String matching can identify candidate mentions. It cannot determine whether a description is current, favorable, or correct. Domain matching can detect links, but it cannot establish that a source entails the adjacent claim.

[ALCE](https://arxiv.org/abs/2305.14627) explicitly separates answer and citation evaluation. For a practical brand audit, keep a claim-level ledger containing the extracted assertion, source passage, validity date, and review status. Report disputed and unverified claims separately from confirmed errors.

If using an LLM judge, calibrate it against human-reviewed examples. Research on [LLM-as-a-judge](https://arxiv.org/abs/2306.05685) identifies biases that make uncalibrated automatic grades unsuitable as unquestioned ground truth.

## Version the scorer as well as the questions

Alias dictionaries, domain rules, and recommendation rubrics can change a metric without changing an answer. Preserve the scorer version with each report. When correcting an annotation bug, decide whether to reprocess both comparison periods under the revised rule or retain the original series with an explicit break.

Do not silently overwrite the historical result and then attribute the difference to the brand's publishing work. Keeping original answers makes a controlled recalculation possible. A reviewer should be able to distinguish an observed output change, a corrected label, and a redesigned measure.

## Compare distributions, not just totals

Break results out by platform, branded versus unbranded cohort, and buyer task. A pooled improvement can conceal a decline in an important segment when the question mix changes.

Repeated answers also share prompts and time windows. A simple binomial confidence interval may understate uncertainty if it assumes independent trials. For serious comparison, use an analysis aligned to the sampling design, such as prompt-cluster resampling with attention to temporal dependence. Small samples should remain descriptive.

Metis AI's [product description](https://www.metisai.vip/product/) includes visibility and citation trends. Ask how displayed metrics map to raw observations before using them in a business report. A useful dashboard should help a reviewer explain movement, including what was not measured.

Resource: [Metric dictionary](../../resources/04-metric-dictionary.md). Related: [prompt-set design](03-buyer-intent-prompt-set.md) and [ongoing monitoring](../monitoring/05-manual-vs-continuous-monitoring.md).
