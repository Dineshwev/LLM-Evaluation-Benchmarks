# Methodology

This directory contains the portfolio-level methodology and meta-evaluation documentation that connects the three evaluation pillars of this portfolio:

- [Citation Verification](../citation-verification/)
- [LLM Response Evaluation](../llm-response-evaluation/)
- [Adversarial Testing](../adversarial-testing/)

Where the individual portfolio pillars focus on *what* was evaluated and *what* was found, these documents focus on *how* evaluation frameworks are designed, compared, stress-tested, limited, and refined. This is the methodological record of the portfolio as a research practice, not just a collection of results.

---

## 1. Purpose

A single universal quality score is often insufficient for evaluating LLM behavior. Different evaluation targets require different definitions of success and failure, different failure-severity hierarchies, and different override mechanisms.

This portfolio addresses three distinct evaluation targets:

- **Grounding and citation support.** Does the cited source actually entail the specific claim made? Factual accuracy in the real world is irrelevant if the cited source does not support the specific claim at the specific scope and confidence level expressed.
- **Overall response quality.** Does the response accurately, completely, relevantly, and clearly address the user's cooperative prompt? Quality here is multi-dimensional; no single property (fluency, accuracy, length) summarizes it reliably.
- **Defensive resilience under adversarial conditions.** Does the model maintain factual accuracy and calibration when the prompt is designed to induce failure through false premises, excessive constraints, context distraction, or uncertainty pressure? The traits that make a model helpful in cooperative contexts—agreeableness, confidence, fluency—can become exploitable vulnerabilities under adversarial conditions.

Because these evaluation targets are distinct, the portfolio maintains three separate rubrics, each calibrated to its task domain.

---

## 2. Methodology Documents

The following documents constitute the active methodology record for this portfolio. All were created as part of the structured methodology phase that followed completion of the three evaluation pillars.

| Document | Purpose | Key Contribution |
|---|---|---|
| [portfolio_evaluation_methodology.md](./portfolio_evaluation_methodology.md) | Establishes the unified evaluation philosophy underlying all three pillars | Explains why dimension independence, evidence-based scoring, and critical overrides are foundational to the portfolio; includes comparison of the three frameworks |
| [framework_comparison.md](./framework_comparison.md) | Compares the three evaluation frameworks side by side | Side-by-side table of dimensions, scoring scales, verdict categories, and override mechanisms; explains why one universal rubric would fail all three tasks simultaneously; documents cross-framework design patterns and key differences |
| [scoring_design_principles.md](./scoring_design_principles.md) | Documents the design reasoning behind the scoring systems | Explains how to design dimensions from failure modes; demonstrates arithmetically why composite scores can hide catastrophic failures; defines when overrides are appropriate; addresses double-penalization, equal weighting, and rubric revision criteria |
| [validation_limitations_and_future_work.md](./validation_limitations_and_future_work.md) | Provides a rigorous limitations and future-work statement for the entire portfolio | Distinguishes demonstrated findings from proposed changes and from claims requiring independent validation; documents seven-phase validation roadmap and ten proposed validation principles |

---

## 3. Portfolio Methodology Architecture

The following diagram shows how the portfolio's methodology components relate to each other:

```
Evaluation Framework Design
(Rubrics, scoring scales, verdict categories, override mechanisms)
        ↓
Task-Specific Rubrics
(Citation Verification: 5 dimensions / LLM Response: 7 dimensions / Adversarial: 4 dimensions)
        ↓
Stress-Test Cases
(Designed to isolate specific failure modes and probe override behavior)
        ↓
Cross-Case Analysis
(Synthesis documents identify patterns, override gaps, and verdict distribution)
        ↓
Methodology Evaluation
(Framework behavior under designed cases used as evidence about the framework itself)
        ↓
Framework Refinement
(LLM Response Evaluation v2 proposed based on override-gap evidence;
 Adversarial v1 found adequate — no revision warranted)
        ↓
Independent Future Validation
(Required before any framework is adopted as a production standard)
```

The key feature of this architecture is that **stress-test cases serve two roles simultaneously**: they evaluate model responses, and they evaluate the framework's capacity to correctly classify those responses. This dual purpose is what enables meta-evaluation.

---

## 4. Core Methodological Principles

The following principles are shared across all three evaluation frameworks. Full explanations and evidence are in [scoring_design_principles.md](./scoring_design_principles.md).

**Task-specific evaluation.** Different evaluation targets require different rubrics. A citation's adequacy is measured by entailment, not by whether the claim it supports happens to be true. A response's quality is measured across multiple independent dimensions. Adversarial resilience requires measuring what the model *refuses* to do, not just what it does.

**Explicit dimension separation.** Each rubric decomposes its evaluation target into independent dimensions and scores them separately before aggregation. This prevents strong performance in one area from masking complete failure in another.

**Evidence-based scoring.** Every score of 1 or 0 must be justified with a direct quotation from the evaluated text. Scores cannot be assigned on the basis of general impressions.

**Transparent failure definitions.** Each score level is defined primarily by the failure mode it detects, not just by the positive standard it falls short of. This makes the boundary between score levels falsifiable.

**Composite scores with caution.** Composite scores are useful for ranking responses but insufficient alone for detecting categorical failures. A score of 12/14 with one dimension at zero looks the same as a score of 12/14 with no zeros. Only dimension-level inspection reveals the difference.

**Critical or vulnerability overrides.** Each framework that uses composite scoring implements an override mechanism to prevent high aggregate scores from yielding misleadingly positive verdicts when a specific critical dimension fails completely.

**Reproducibility.** All evaluations require quoted evidence, explicit dimension scores, integer scales, and documented decision rules so that independent evaluators can reach the same verdict from the same input.

**Stress testing the methodology itself.** Deliberately designed edge cases are used to observe framework behavior under controlled failure conditions. This treats the rubric as a hypothesis to be tested, not an assumed truth.

**Versioning and refinement.** When stress-testing reveals a structural gap, a proposed revision is documented with the evidence that motivated it, the specific change, and explicit acknowledgment of what the revision does and does not establish.

**Clear distinction between designed-case evidence and real-world validation.** Evidence from designed stress-test cases demonstrates how the framework behaves under controlled conditions. It does not establish failure rates in real-world AI deployments or validate the framework for production use without independent testing.

---

## 5. Key Portfolio-Level Findings

The following findings are supported by the completed portfolio case studies. Each is carefully scoped to the evidence available.

**High composite scores can conceal severe dimension-level failures.** Within the LLM Response Evaluation designed case set, five cases each scored 11 or 12 out of 14 while containing a categorical failure—one dimension at zero—that rendered the response practically useless for the user's stated goal. This was demonstrated within the designed cases; it shows that the structural gap exists, not that it occurs at any particular frequency in real deployments.

**Different evaluation targets require different failure definitions.** A response that is factually accurate may still fail citation entailment. A response that is accurate and relevant may still be unusable due to an instruction constraint it violated. A helpful, accurate response may fail adversarially because its agreeableness enabled sycophancy. These failures are orthogonal and cannot be detected by a single rubric.

**Override mechanisms can address some aggregation failures but must themselves be stress-tested.** The LLM Response Evaluation v1 Critical Failure Override correctly engaged for Cases 001 and 004 and did not produce false positives. However, the stress-test portfolio revealed a gap: five dimensions could each score zero without triggering it. The Adversarial Testing v1 Vulnerability Override, by contrast, was found to engage correctly in all cases where it was designed to apply, with no gap detected.

**Deliberately designed cases can reveal deterministic weaknesses in an evaluation framework.** The practice of designing cases to isolate specific failure modes produced a concrete, reproducible finding: LLM Response Evaluation v1 would rate a response as Good regardless of whether Relevance, Completeness, Instruction Following, Reasoning Quality, or Clarity scored zero. This is a deterministic property of the methodology, not a probabilistic estimate.

**The proposed LLM Response Evaluation v2 methodology addresses a specific gap exposed by the designed cases but remains unvalidated on independent real-world datasets.** The v2 proposal extends the Critical Failure Override from 2 to all 7 dimensions. Under the proposed v2 rules, all eight intentionally stress-tested cases receive a Marginal verdict. This demonstrates that v2 closes the specific gap, but it does not establish that v2 is validated for general use. Further empirical validation on undesigned datasets is required.

---

## 6. Relationship to the Three Evaluation Pillars

| Pillar | Primary Question | Methodological Focus |
|---|---|---|
| [Citation Verification](../citation-verification/) | Does the cited source genuinely support this specific claim at the scope and confidence expressed? | Claim-level entailment; 5 dimensions; 6 qualitative verdict categories; no composite-to-verdict band; decision-rule gates |
| [LLM Response Evaluation](../llm-response-evaluation/) | Is this response accurate, relevant, complete, instruction-compliant, logically sound, hallucination-free, and readable? | Response-level quality; 7 dimensions; 0–14 composite; 4 score-band verdicts; Critical Failure Override on D1 and D6 (v1) |
| [Adversarial Testing](../adversarial-testing/) | Does the model maintain factual calibration and detect adversarial manipulation when the prompt is designed to induce failure? | Interaction-level resilience; 4 dimensions; 0–8 composite; 4 robustness-band verdicts; Vulnerability Override on D1 and D3 |

---

## 7. Limitations

The methodology documents in this directory rest on a foundation of intentionally constructed evaluation cases. Several limitations follow from this:

- **Cases were designed stress tests, not random samples.** Failure-mode frequencies observed in the portfolio cannot be generalized to real-world AI deployments.
- **The portfolio is not a statistically representative benchmark.** No claim about LLM quality in general should be derived from this portfolio without independent replication.
- **Inter-rater reliability has not been established.** All evaluations in this portfolio were conducted by a single evaluator. No inter-rater agreement data exists.
- **Some ground truth is time-sensitive.** Cases evaluating technical specifications, product documentation, or regulatory text may become inaccurate as those sources evolve.
- **Proposed methodology changes require independent validation.** The LLM Response Evaluation v2 proposal has been tested only on the eight-case designed set that motivated it. It has not been validated on real-world outputs.

Full treatment of these limitations is in [validation_limitations_and_future_work.md](./validation_limitations_and_future_work.md).

---

## 8. Future Work

The [validation_limitations_and_future_work.md](./validation_limitations_and_future_work.md) document defines a seven-phase roadmap:

1. **Independent validation** — Apply existing rubrics to naturally occurring, non-designed model outputs.
2. **Multi-rater evaluation** — Score a validation set with multiple independent evaluators.
3. **Reliability measurement** — Quantify inter-rater agreement per dimension; flag dimensions with persistent ambiguity.
4. **Empirical framework refinement** — Revise rubric definitions only where reliability evidence supports revision.
5. **Cross-model benchmarking** — Evaluate multiple language models under identical conditions.
6. **Longitudinal testing** — Repeat evaluation across model versions to track quality changes over time.
7. **Public reproducibility package** — Publish structured datasets, scoring templates, and annotated guidelines for independent replication.

---

## 9. Navigation

**Portfolio root:**
- [Top-level Portfolio README](../README.md)

**Evaluation pillars:**
- [Citation Verification](../citation-verification/README.md)
- [LLM Response Evaluation](../llm-response-evaluation/README.md)
- [Adversarial Testing](../adversarial-testing/README.md)

**Methodology documents (this directory):**
- [portfolio_evaluation_methodology.md](./portfolio_evaluation_methodology.md) — Unified philosophy and framework comparison overview
- [framework_comparison.md](./framework_comparison.md) — Detailed side-by-side comparison of all three frameworks
- [scoring_design_principles.md](./scoring_design_principles.md) — Design reasoning for dimensions, composites, overrides, and rubric revision
- [validation_limitations_and_future_work.md](./validation_limitations_and_future_work.md) — Limitations, roadmap, and validation principles

---

## Consistency Audit

*Performed after drafting to verify all filenames, descriptions, and portfolio-specific facts.*

| Check | Result |
|---|---|
| `portfolio_evaluation_methodology.md` exists | ✅ Verified (4,436 bytes) |
| `framework_comparison.md` exists | ✅ Verified (24,363 bytes) |
| `scoring_design_principles.md` exists | ✅ Verified (21,790 bytes) |
| `validation_limitations_and_future_work.md` exists | ✅ Verified (30,170 bytes) |
| Citation Verification: 5 dimensions, 6 verdict categories | ✅ Verified against `rubric.md` §3–4 |
| LLM Response Evaluation: 7 dimensions, 0–14 scale, 4 verdict bands | ✅ Verified against `scoring_methodology_v1.md` §2–3 |
| LLM Response Evaluation v1 override: D1 and D6 only | ✅ Verified against `scoring_methodology_v1.md` §4 |
| Adversarial Testing: 4 dimensions, 0–8 scale, 4 verdict bands | ✅ Verified against `adversarial_scoring_methodology_v1.md` §1–2 |
| Adversarial Testing override: D1 and D3 | ✅ Verified against `adversarial_scoring_methodology_v1.md` §3 |
| LLM RE v2 described as proposed, not validated | ✅ Confirmed — uses the word "proposed" throughout |
| Five Good-with-zero-dimension cases: scores stated as 11 or 12 of 14 | ✅ Verified against `cross_case_synthesis_001_008.md` (LLM RE) §1 |
| No failure-frequency claims from designed cases | ✅ Confirmed — all findings scoped to "within the designed case set" |
| Navigation paths use relative links matching actual filenames | ✅ Verified |
| Top-level README and all pillar READMEs exist | ✅ Verified |
