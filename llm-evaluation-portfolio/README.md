# LLM Evaluation Portfolio

## About This Portfolio

This portfolio demonstrates structured, reproducible evaluation of AI-generated content across three applied domains. It is an independent project designed to showcase practical competencies in AI output quality assessment, citation verification, and evaluation methodology design.

The work is organized into four portfolio areas. Each area contains case studies, methodology documentation, and evaluation results produced through systematic, criterion-based assessment.

---

## Portfolio Areas

| Area | Description | Status |
|---|---|---|
| [Citation Verification](./citation-verification/) | Structured evaluation of whether AI-generated citations actually support the claims they purport to validate | Active — Cases 001–006 complete |
| [LLM Response Evaluation](./llm-response-evaluation/) | Quality assessment of AI-generated responses across multiple dimensions | Active — Cases 001–008 complete + Synthesis |
| [Adversarial Testing](./adversarial-testing/) | Evaluation of AI system behavior under adversarial prompting conditions | Active — Cases 001–008 complete + Synthesis |
| [Methodology](./methodology/) | Core evaluation frameworks, rubrics, and decision procedures used across this portfolio | Active |

---

## Citation Verification Sub-Portfolio

The citation verification project is the most developed area of this portfolio. It evaluates whether AI-generated responses accurately represent the sources they cite, using a multi-dimensional scoring rubric and structured verdict categories.

### Completed Cases

| Case | Domain | Claims | Avg. Score | Key Failure Modes |
|---|---|---|---|---|
| [Case 001](./citation-verification/test-cases/case_001_supabase_planetscale_neon.md) | Database pricing and features | — | — | — |
| [Case 002](./citation-verification/test-cases/case_002_hnsw_vs_ivf.md) | Vector search algorithms | — | — | — |
| [Case 003](./citation-verification/test-cases/case_003_eu_ai_act.md) | EU AI Act overview | — | — | — |
| [Case 004](./citation-verification/test-cases/case_004_eu_ai_act_risk_framework.md) | EU AI Act risk framework | 11 | **9.2/10** | Wording gaps, citation mismatch, 1 missing citation |
| [Case 005](./citation-verification/test-cases/case_005_api_security_citation_failures.md) | API data retention & privacy | 10 | **8.2/10** | Overgeneralization, unsupported universals, scope mismatch |
| [Case 006](./citation-verification/test-cases/case_006_ai_coding_assistant_privacy.md) | AI coding assistant privacy | 10 | **6.3/10** | Product-surface confusion, internal contradiction, factual errors |

### Portfolio Summary (Cases 004–006)

| Metric | Value |
|---|---|
| Total claims evaluated | 31 |
| Weighted average composite score | **7.9 / 10** |
| Claims fully supported | 13 (41.9%) |
| Claims not fully supported | 18 (58.1%) |

#### Verdict Distribution

| Verdict | Count | % |
|---|---|---|
| Fully Supported | 13 | 41.9% |
| Partially Supported | 8 | 25.8% |
| Unsupported | 7 | 22.6% |
| Citation Missing | 3 | 9.7% |

#### Cross-Case Synthesis

A full synthesis of Cases 004–006 is available in:
[`evaluations/cross_case_synthesis_004_006.md`](./citation-verification/evaluations/cross_case_synthesis_004_006.md)

It covers:
- Portfolio-level verdict distribution and score calculation
- Five common citation-failure patterns with concrete examples
- Strong vs weak claim examples
- Portfolio-level quality progression
- Five methodology insights drawn from the full evaluation

---

## Core Methodology

All evaluations in this portfolio apply a five-dimension scoring rubric:

| Dimension | What It Measures |
|---|---|
| **Entailment** | Does the source logically support the claim as written? |
| **Completeness** | Does the claim preserve all important qualifiers in the source? |
| **Relevance** | Is the source topically appropriate for the claim? |
| **Evidence Quality** | Is the source credible, authoritative, and current? |
| **Citation Placement** | Is the citation positioned appropriately relative to the claim? |

Each dimension is scored 0–2, giving a composite score of 0–10 per claim.

### Verdict Categories

| Verdict | Meaning |
|---|---|
| **Fully Supported** | Source directly and completely supports the claim |
| **Partially Supported** | Source supports some but not all components of the claim |
| **Unsupported** | Source does not support, or directly contradicts, the claim |
| **Citation Missing** | No verifiable citation is provided for the claim |

Full rubric and methodology documentation:
- [`citation-verification/rubric.md`](./citation-verification/rubric.md)
- [`citation-verification/methodology.md`](./citation-verification/methodology.md)

---

## Key Portfolio Finding

> Citation verification is not primarily a test of whether a source exists. It is a test of whether the source actually supports the claim, with the same scope, conditions, and level of certainty expressed in the response.

The most persistent failure mode across all cases is **scope expansion** — turning conditional, limited, or product-specific documentation into broader universal claims by silently removing qualifiers such as *eligible, may, by default, for Business and Enterprise, subject to exceptions*.

---

## Skills Demonstrated

- Structured citation verification and claim-to-source alignment analysis
- Multi-dimensional rubric design and consistent application
- AI output quality assessment across technical domains
- Evidence-based verdict assignment with documented rationale
- Cross-case synthesis and portfolio-level pattern analysis
- Reproducible evaluation methodology development
