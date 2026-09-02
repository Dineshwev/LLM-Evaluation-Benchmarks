# Validation, Limitations, and Future Work

---

## 1. Purpose and Scope

This document provides a rigorous statement of what the LLM Evaluation Portfolio has demonstrated, what it has not demonstrated, and what future work would be required to extend the portfolio's findings to broader claims.

The portfolio is composed of three evaluation pillars—Citation Verification (6 cases), LLM Response Evaluation (8 cases), and Adversarial Testing (8 cases)—and a Methodology section documenting the evaluation frameworks developed across them. Together, the portfolio contains 22 deliberate evaluation case studies, three complete evaluation rubrics, three scoring methodologies, one proposed methodology revision, and three cross-case syntheses.

**The portfolio is a demonstration of evaluation framework design and stress-testing methodology.** It is not a benchmark study claiming to represent the statistical distribution of LLM performance across a population of models, domains, or naturally occurring prompts. No claim in this portfolio should be read as an estimate of how frequently real-world language models exhibit any of the failure modes documented here.

---

## 2. What the Portfolio Demonstrates

The following conclusions are directly supported by the completed work. Each is bounded precisely to the evidence available.

**Citation verification can distinguish factual truth from citation entailment and completeness.** The Citation Verification framework demonstrates, across six designed cases, that the verdict categories—Fully Supported, Partially Supported, Unsupported, Contradicted, Citation Missing, Insufficient Evidence—correctly differentiate these distinct failure modes. A claim can be factually accurate while still receiving an Unsupported verdict if the cited source does not entail it, and vice versa. This distinction was applied consistently across evaluated claim-citation pairs.

**Multi-dimensional response evaluation can expose serious failures hidden by high composite scores.** The LLM Response Evaluation portfolio demonstrates that a response scoring 12/14 on a seven-dimension rubric can simultaneously contain a categorical failure—such as providing an unreadable wall of text (Case 007), answering the wrong question (Case 005), or omitting the entire deliverable the user requested (Case 006)—while still receiving a Good final verdict under Scoring Methodology v1.0. This is demonstrated within the designed case set; it shows that the structural gap exists, not that it occurs at a particular frequency in real deployments.

**Adversarial evaluation requires different criteria from ordinary response-quality evaluation.** The Adversarial Testing framework demonstrates that the traits measured by cooperative quality rubrics—helpfulness, compliance, tone—become exploitable vulnerabilities under adversarial conditions. Across the eight adversarial cases, the model with the highest Recovery & Tone score (1.5/2.0 average) also produced the most dangerous failures, confirming that polished presentation does not indicate adversarial robustness.

**Deliberately designed edge cases can be used to stress-test the evaluation methodology itself.** Both the LLM Response Evaluation and Adversarial Testing portfolios demonstrate that rubric behavior under controlled failure conditions can be systematically evaluated. By designing cases to produce specific dimension scores, it is possible to observe whether the methodology's override mechanisms engage when they should, whether composite scores correctly reflect verdict-relevant information, and whether verdict labels accurately communicate the quality of the underlying response.

**Override mechanisms can be evaluated by observing whether intentionally constructed catastrophic failures are appropriately reflected in final verdicts.** In the LLM Response Evaluation portfolio, the Critical Failure Override correctly engaged for Cases 001 and 004, and correctly did not engage for Cases 008. In the Adversarial Testing portfolio, the Vulnerability Override correctly engaged for Cases 003, 007, and 008. In both portfolios, the observation that an override does not produce false positives or false negatives within the designed case set is meaningful evidence about that override's behavior—but only within those cases.

---

## 3. Limitation: Intentionally Constructed Test Cases

Every case study in this portfolio was deliberately designed with a specific evaluation objective. In the LLM Response Evaluation portfolio, seven of the eight cases were each designed to produce exactly one dimension at zero and the remaining six near maximum. In the Adversarial Testing portfolio, each case targeted a specific adversarial vector. In the Citation Verification portfolio, cases were selected to include a range of citation quality and failure types.

### Advantages of the designed approach

**Clear ground truth.** Because each case was constructed with a known intended score profile, it is straightforward to verify whether the rubric correctly identifies the intended failure. There is no ambiguity about what the correct verdict should be.

**Controlled failure conditions.** Designing cases that isolate one dimension per case allows the rubric's behavior under each specific failure mode to be observed cleanly, without confounding from simultaneous failures in other dimensions.

**Strong methodology stress testing.** As documented in the cross-case syntheses, the designed cases were capable of exposing structural gaps in the methodology (the override gap in LLM Response Evaluation v1) as well as confirming framework adequacy (the Adversarial Testing v1 finding).

### Limitations of the designed approach

**Not random samples.** The cases do not constitute a random sample from any population of real AI interactions. They were selected because they were useful for a specific evaluation purpose, not because they are representative of what AI systems typically produce.

**Not representative estimates of production LLM behavior.** The fact that a specific failure mode was successfully designed into a case study does not indicate how frequently that failure mode occurs in deployed AI systems. Case 004 demonstrates that an LLM response can contain fabricated citations. It does not indicate what proportion of deployed LLM responses contain fabricated citations.

**Failure frequencies cannot be inferred.** The portfolio contains exactly one case where D1 (Factual Accuracy) scored zero (Case 001, LLM Response Evaluation), one case where D6 (Hallucination) scored zero (Case 004), and so on. These frequencies were determined by the portfolio design, not by observation. No frequency estimate for any failure mode is derivable from this data.

**Models may behave differently on naturally occurring prompts.** Prompts designed to produce specific failure modes are inherently unusual. Real user prompts have different distributions of complexity, ambiguity, constraint density, and adversarial content. The portfolio cannot make claims about model behavior under natural-language conditions.

---

## 4. Limitation: Lack of Independent Real-World Validation

None of the three evaluation frameworks in this portfolio has been validated against a sufficiently large independent dataset of naturally occurring, non-designed model outputs.

The LLM Response Evaluation Scoring Methodology v2 (Proposed) explicitly acknowledges this limitation:

> "The v2 proposal is motivated by a designed case set in which every case was intentionally constructed to contain at least one failure. The extended override has not been tested against a set of real, undesigned LLM outputs — where the distribution of scores across dimensions may look very different. Validation on real outputs is recommended before adopting v2 as a production standard."

This limitation applies equally to all three frameworks and to v1 as well as v2. The frameworks have been shown to behave correctly under controlled conditions. They have not been shown to behave correctly at scale, across models, or across domains that were not part of the portfolio case selection.

### What independent validation should test

Future validation studies should address the following conditions not present in the current portfolio:

- **Multiple models.** The portfolio evaluates a single AI system per case. Validation should confirm that the rubrics produce consistent, interpretable results when applied to outputs from multiple different language models.
- **Multiple domains.** The portfolio covers database administration, space exploration, business analysis, API security, product research, and other domains chosen for illustrative purposes. Validation should test whether rubric behavior is stable across domains not represented in the current case set.
- **Multiple prompt types.** The portfolio includes cooperative, underspecified, adversarial, and overloaded prompts by design. Validation should sample prompt types in proportions that reflect real-world usage.
- **Naturally occurring outputs.** Validation requires responses that were generated by real models in response to real user prompts—not responses constructed to meet a design specification.
- **Different difficulty levels.** Prompts of varying complexity, ambiguity, and domain depth are needed to test whether rubric verdicts scale appropriately across the full quality range.
- **Independent evaluators.** Validation cases should be scored by evaluators who had no involvement in the rubric's development, to test whether the rubric's decision rules are sufficiently explicit for consistent application.

---

## 5. Limitation: Evaluator Subjectivity and Inter-Rater Reliability

All evaluations in this portfolio were conducted by a single evaluator. No inter-rater reliability data exists for any of the three frameworks.

Explicit rubric definitions and evidence-quotation requirements improve scoring consistency, but they do not eliminate the evaluator's role in making judgment calls. Several dimensions are particularly susceptible to evaluator subjectivity:

- **Relevance (LLM Response Evaluation D2):** Determining whether a response "misses the core intent of the prompt" requires a judgment about what that intent was. The rubric's definitions constrain this judgment, but boundary cases remain.
- **Completeness (LLM Response Evaluation D3):** Determining whether a response "leaves critical parts of the prompt completely unanswered" requires a judgment about which parts are critical, which depends on implied user goals not always stated in the prompt.
- **Reasoning Quality (LLM Response Evaluation D5):** Evaluating whether an argument contains "minor logical leaps" (score: 1) versus "flawed logic" (score: 0) is a judgment that may vary between evaluators with different analytical backgrounds.
- **Clarity & Communication (LLM Response Evaluation D7):** Readability is partly subjective. A format that one evaluator considers "well-structured" may strike another as unnecessarily complex.
- **Factuality & Calibration (Adversarial Testing D3):** Determining whether a response is "overconfident" (score: 1) versus projecting "false certainty" constitutes a hallucination (score: 0) requires a judgment about where overconfidence ends and fabrication begins.

No inter-rater reliability statistics are reported in this portfolio because no multi-rater evaluation was conducted.

### Recommended future work

- **Multiple independent raters.** Future evaluation studies should require at least two independent raters per case, with a protocol for resolving disagreement.
- **Agreement measurement.** Inter-rater agreement should be quantified using an appropriate statistic (e.g., Cohen's kappa or Krippendorff's alpha) reported alongside the evaluation results.
- **Adjudication procedures.** A defined process for reaching a final verdict when raters disagree should be documented in the methodology before multi-rater evaluation begins.
- **Calibration exercises.** Before independent rating begins, raters should score a set of calibration examples with known intended verdicts to align their interpretation of the rubric criteria.
- **Published annotation guidelines.** Supplementary annotation guidelines resolving the most commonly contested boundary cases should be developed and published alongside the rubric.

---

## 6. Limitation: Equal Weighting and Aggregation

All three frameworks use equal-weight composite scoring: each dimension contributes 0, 1, or 2 points regardless of its relative importance in a given deployment context.

### What equal weighting provides

Equal weighting ensures that composite scores are transparent and interpretable without knowledge of a weighting scheme. A score of 10/14 in the LLM Response Evaluation framework means the response averaged 1.43/2.0 across seven equally weighted dimensions. This is mathematically unambiguous.

Equal weighting is also the most defensible default in the absence of empirical evidence about the relative harm of different failure modes. Assigning a higher weight to, say, Factual Accuracy than to Clarity would require empirical justification—evidence that factual errors cause more harm than unclear responses across a representative sample of use cases. No such data exists in the portfolio.

### What equal weighting does not provide

Equal weighting does not reflect actual deployment priorities. In practice:
- For a medical information system, Factual Accuracy and Hallucination may be far more important than Clarity.
- For a code generation system, Instruction Following may be more important than Relevance.
- For an executive summary tool, Clarity and Completeness may matter more than Reasoning Quality detail.

The LLM Response Evaluation portfolio makes this limitation concrete: Cases 006 and 007 each scored 12/14 with one dimension at zero, receiving a Good verdict. Under equal weighting, the zero was arithmetically absorbed by six perfect scores. Whether equal weighting accurately reflected the relative importance of Completeness and Clarity in those specific cases is a question that cannot be answered from the portfolio data alone.

### Future directions

- **Empirically derived weights.** A weighting scheme could be derived from user studies quantifying the impact of different failure modes on task completion, user satisfaction, or downstream decision quality.
- **Risk-weighted scoring.** High-stakes deployment contexts (medical, legal, financial) may warrant overrides or weight multipliers for specific dimensions without changing the underlying rubric.
- **Domain-specific decision gates.** Rather than a universal extended override, a future methodology version could define task-type-conditional gates—specifying which dimensions trigger overrides for which deployment contexts.
- **Multi-level verdict systems.** Verdicts could be separated into a quality verdict (based on composite score) and a safety verdict (based on dimension-specific thresholds), preserving the information in both while preventing them from masking each other.

---

## 7. Limitation: Override Mechanisms

### The LLM Response Evaluation override history

Scoring Methodology v1.0 defined a Critical Failure Override covering D1 (Factual Accuracy) and D6 (Hallucination). The eight-case stress-test portfolio demonstrated that this override was insufficient: five additional dimensions could each score zero while the response received a Good verdict.

This finding led to Scoring Methodology v2 (Proposed), which extends the override to all seven dimensions. v2 remains a proposal. The evidence supporting it comes entirely from the designed stress-test portfolio. v2 has not been applied to real-world, non-designed outputs, and it has not been tested against a representative sample that would reveal whether the extended override produces false positives—cases where the extended override caps a genuinely useful response at Marginal because a single minor criterion was scored at zero.

### The Adversarial Testing override outcome

The Adversarial Scoring Methodology v1.0 defined a Vulnerability Override covering D1 (Trap Detection & Resistance) and D3 (Factuality & Calibration). The eight-case adversarial portfolio found no structural gap: the override engaged in 3 of 8 cases, and in each case the override correctly identified a catastrophic failure. No case produced a misleadingly positive verdict due to insufficient override coverage.

### The critical distinction

The fact that the Adversarial Testing v1 framework performed well on the designed adversarial cases does not mean it is universally superior to the LLM Response Evaluation v1 or v2 frameworks. The adversarial rubric uses a 4-dimension structure designed specifically for adversarial resilience measurement. It was not designed for—and cannot be used for—general cooperative response quality evaluation. Its override design is appropriate for its task domain; the question of whether a different set of adversarial cases would expose a gap in the Adversarial Testing v1 override remains open.

The key distinction that applies to all override mechanisms in this portfolio is:

> **"Performed as intended on designed cases"** is not equivalent to **"validated for general use."**

The designed cases confirm that the override behaves correctly when presented with the specific failure modes the cases were built to produce. They do not confirm how the override would behave across a broader distribution of inputs.

---

## 8. Limitation: Ground Truth and Temporal Stability

Several evaluation domains in this portfolio depend on external facts, technical specifications, or policy documents that may change over time.

The Citation Verification cases evaluate claims about specific software products, regulatory frameworks, and technical standards. The LLM Response Evaluation cases involve claims about database behavior (e.g., transaction isolation levels), AI product features, and software engineering practices. The Adversarial Testing cases involve technical claims about database architecture (e.g., PostgreSQL foreign key indexing) that are subject to version-specific behavior.

All evaluations were conducted at a specific point in time. A claim that is correctly scored as Factually Accurate or Fully Supported today may become Factually Inaccurate or Partially Supported if the underlying technical reality changes—for example, if a database engine introduces a new feature that alters the accuracy of a claim about its behavior.

The Citation Verification README explicitly identifies this as a limitation: "Evaluations capture source content at a specific point in time; sources may evolve or be updated after evaluation."

### Future needs

- **Versioned source snapshots.** Cases that depend on external documents, product documentation, or regulatory texts should reference and archive a specific version of the source, not merely a URL.
- **Evaluation dates.** All case studies should record the date of evaluation to enable future determination of whether the factual ground truth has changed.
- **Source provenance tracking.** For technical claims, the specific version of the software, standard, or policy being evaluated should be recorded.
- **Periodic re-validation.** Cases evaluating rapidly changing domains (product features, regulatory requirements, security best practices) should be identified for periodic re-review.
- **Handling conflicting authoritative sources.** In some domains, multiple authoritative sources may make contradictory claims. The methodology should define how to handle such cases, and future cases should include at least one example of this pattern.

---

## 9. Future Work Roadmap

The following phased roadmap describes the work required to extend this portfolio from framework demonstration to validated evaluation methodology.

### Phase 1 — Independent Validation

Apply the existing rubrics to a new set of naturally occurring, non-designed model outputs. The validation set should be collected from real user interactions (with appropriate consent and privacy handling) or from publicly available LLM output datasets. No modification to the rubrics should occur during Phase 1; the goal is to observe how the rubrics behave on inputs they were not designed for.

**Success criteria:** The rubrics can be applied to at least 50 non-designed cases per framework, with verdicts that are coherent, internally consistent, and explainable by reference to the rubric definitions.

### Phase 2 — Multi-Rater Evaluation

Recruit at least two independent evaluators per case for a subset of the Phase 1 outputs. Evaluators should have no prior involvement in rubric development.

**Success criteria:** Each evaluated case receives independent dimension scores and verdicts from two or more raters with no coordination between them.

### Phase 3 — Reliability Analysis

Measure inter-rater agreement for each dimension using an appropriate statistic. Identify dimensions with persistently low agreement as candidates for rubric clarification.

**Success criteria:** Agreement statistics are computed and published for each dimension. Dimensions falling below a defined agreement threshold are flagged for rubric review. Any rubric revisions motivated by reliability findings are documented and versioned.

### Phase 4 — Framework Refinement

Revise rubric definitions only when the Phase 2–3 evidence supports revision. Each revision should be documented with the specific evidence motivating it, the specific change made, and the version number of the revised document.

**Success criteria:** Revised rubric versions are published with complete change logs, and the impact of revisions on previously scored cases is documented.

### Phase 5 — Cross-Model Benchmarking

Apply the validated rubrics to outputs from multiple different language models under identical prompt conditions. This phase will produce comparative data on rubric-defined quality dimensions across models, domains, and prompt types.

**Success criteria:** At least two models are evaluated on at least 20 identical prompts per framework, with all results published and reproducible.

### Phase 6 — Longitudinal Evaluation

Repeat a fixed set of evaluation cases across different versions of the same model to observe how rubric-defined quality dimensions change across model iterations. This phase supports tracking whether models are improving, regressing, or redistributing their failure modes across dimensions over time.

**Success criteria:** A fixed test set of at least 30 cases is evaluated on at least two versions of a model, with longitudinal findings documented.

### Phase 7 — Public Reproducibility Package

Publish a structured dataset containing prompts, responses, dimension-level scores, verdicts, and evaluator justifications from Phases 1–6 in a format that allows independent researchers to replicate, extend, or audit the evaluations. The package should include evaluation templates, annotated scoring instructions, and a description of inter-rater resolution procedures.

**Success criteria:** An independent researcher can reproduce the evaluation process and arrive at equivalent verdicts using only the published package and its accompanying documentation.

---

## 10. Proposed Validation Principles

The following principles should guide all future methodology changes and validation activities. They are informed by the experience of building and stress-testing the three frameworks in this portfolio.

**No rubric revision based on a single anecdote unless it exposes a deterministic logical contradiction.** A single case in which an evaluator is uncertain how to score a dimension does not indicate that the rubric is flawed. Revision is warranted when multiple independent cases reveal the same ambiguity, or when a case exposes a deterministic contradiction in the rubric's stated rules.

**Separate stress-test evidence from prevalence evidence.** Evidence from designed stress-test cases demonstrates what happens to the methodology under specific controlled conditions. It does not demonstrate how frequently those conditions occur in the wild. These two types of evidence must be cited separately and must not be conflated in any claim about the framework's real-world performance.

**Document every scoring change.** Revisions to rubric definitions, scoring scales, verdict bands, or override mechanisms must be versioned and documented with the evidence that motivated the change. The relationship between v1.0 and the proposed v2.0 of the LLM Response Evaluation Scoring Methodology is the model for this practice.

**Preserve backward compatibility through versioning.** When a rubric is revised, the prior version remains the reference for all previously published evaluations. Cases evaluated under v1 should not be retroactively re-scored under v2 without explicit documentation of the re-scoring and its rationale.

**Report negative findings.** The Adversarial Testing portfolio found that its v1 methodology required no revision after eight cases. This negative finding—no structural gap detected—is as important as the positive finding in LLM Response Evaluation. Both should be reported and neither should be suppressed in favor of a more dramatic narrative.

**Distinguish framework validity from model performance.** The evaluation frameworks are tools for measuring model behavior. A finding that a framework correctly identifies a failure mode is a claim about the framework. A finding that models frequently exhibit a failure mode requires a representative sample of model outputs. These are different claims and must be stated separately.

**Avoid claiming generalizability beyond the evaluated dataset.** Any claim about LLM quality, safety, or reliability that derives from this portfolio should be explicitly scoped to the cases evaluated. Claims that would require broader evidence—about model behavior in general, about failure rates in production, about which dimensions matter most—must be accompanied by the data required to support them.

---

## 11. Conclusion

The LLM Evaluation Portfolio demonstrates a structured approach to designing, stress-testing, and refining evaluation frameworks for AI-generated content. Its three pillars—Citation Verification, LLM Response Evaluation, and Adversarial Testing—represent distinct evaluation disciplines with distinct rubrics, distinct scoring systems, and distinct override mechanisms, each calibrated to the specific failure modes relevant to its evaluation task.

The portfolio's strongest contribution is methodological. It demonstrates that rubric design is itself a testable hypothesis: structured, controlled stress-testing can reveal gaps in override coverage, expose failure modes that composite scores conceal, and determine when a framework revision is warranted versus when the evidence supports that the framework is adequate as designed. The finding that LLM Response Evaluation v1 required a proposed revision while Adversarial Testing v1 did not—and that this difference emerged from the same stress-testing practice applied to both—illustrates that meta-evaluation produces genuine findings rather than guaranteed validation.

The portfolio does not claim to establish how frequently any failure mode occurs in real-world AI deployments, how any specific model performs across a representative prompt distribution, or that any of the three frameworks is validated for production use without further empirical testing.

Future work should focus on applying the existing rubrics to independent, naturally occurring datasets; measuring inter-rater reliability; refining rubric definitions where reliability evidence identifies ambiguity; and developing the longitudinal and cross-model benchmarking capacity needed to support claims about real-world model quality. Until that work is complete, the portfolio should be read as what it is: a principled demonstration of how to build, test, and responsibly document LLM evaluation frameworks.

---

## Consistency Audit

*Performed after drafting to verify that no synthetic-case results are presented as real-world prevalence, proposed methodologies are correctly labeled, and all portfolio-specific facts are verified against source files.*

| Check | Verification | Source |
|---|---|---|
| Cases 002, 003, 005, 006, 007: zero-score dimensions and verdicts | Verified (12/14 Good in all five) | `cross_case_synthesis_001_008.md` (LLM RE) §3 and §4 |
| Cases 001 and 004: override engagement | Verified (both correctly capped at Marginal) | `cross_case_synthesis_001_008.md` (LLM RE) §4 |
| Case 008 score: 9/14 Marginal via accumulation | Verified | `cross_case_synthesis_001_008.md` (LLM RE) §1 |
| Adversarial v1 override: engaged in 3 of 8 cases | Verified (Cases 003, 007, 008) | `cross_case_synthesis_001_008.md` (Adversarial) §5 |
| Adversarial average scores by dimension | Verified (D1: 1.125, D2: 1.375, D3: 1.125, D4: 1.500) | `cross_case_synthesis_001_008.md` (Adversarial) §2 |
| Adversarial: no v2 proposed | Verified | `cross_case_synthesis_001_008.md` (Adversarial) §5 |
| v2 status: proposed, not validated | Verified (explicit language quoted) | `scoring_methodology_v2_proposed.md` §5 and §8 |
| Citation Verification: 6 verdict categories | Verified | `citation-verification/rubric.md` §3 |
| Citation Verification: inherent limitations | Verified (10 limitations documented) | `citation-verification/README.md` §Limitations |
| LLM RE: 7 dimensions | Verified | `llm_response_evaluation_rubric_v1.md` |
| LLM RE: override covers D1 and D6 only (v1) | Verified | `scoring_methodology_v1.md` §4 |
| Case 007: 430-word wall of text description | Verified | `cross_case_synthesis_001_008.md` (LLM RE) §4 |
| No inter-rater reliability statistics claimed | Confirmed — no such data exists in repository | N/A |
| No failure frequency estimates from designed cases | Confirmed — all frequency claims removed | N/A |
