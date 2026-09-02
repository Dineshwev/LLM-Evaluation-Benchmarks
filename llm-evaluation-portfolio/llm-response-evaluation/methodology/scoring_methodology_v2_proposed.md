# LLM Response Evaluation Scoring Methodology (v2 — Proposed)

## Status: Proposed Revision — Not Yet Adopted

This document proposes a structured revision to [Scoring Methodology v1.0](./scoring_methodology_v1.md). It should be read in conjunction with the [Cross-Case Synthesis (Cases 001–008)](../evaluations/cross_case_synthesis_001_008.md), which provides the empirical basis for the proposed changes.

All v1.0 mechanisms are preserved. This document specifies additions and amendments only.

---

## 1. Motivation

Scoring Methodology v1.0 defines a Critical Failure Override that caps the final verdict at Marginal whenever a response scores 0 in Factual Accuracy (D1) or Hallucination / Unsupported Claims (D6). This mechanism was validated in Cases 001 and 004, where it correctly prevented misleadingly high verdicts for responses containing fabricated facts and invented sources.

However, the eight-case stress-test portfolio identified a systematic gap: five dimensions — Relevance (D2), Completeness (D3), Instruction Following (D4), Reasoning Quality (D5), and Clarity & Communication (D7) — can each score 0 while the final verdict remains Good.

The following outcomes were demonstrated within the designed case set:

| Case | D = 0 | What Occurred | Final Verdict Under v1.0 |
|---|---|---|---|
| 002 | Instruction Following | AI violated 5 of 8 explicit user constraints | Good |
| 003 | Reasoning Quality | AI reached wrong conclusion through inconsistent metric application | Good |
| 005 | Relevance | AI answered the wrong question within the correct subject area | Good |
| 006 | Completeness | AI omitted the entire actionable deliverable the user requested | Good |
| 007 | Clarity | AI presented all correct content in an unreadable 430-word wall of text | Good |

In each of these cases, the response would be practically useless or actively misleading for the user's actual purpose — yet the scoring methodology classified them as Good. This is the gap that v2 addresses.

---

## 2. Core Proposed Change: Extended Override Gate

### Amendment to Section 4 — Decision Rules (Critical Failure Override)

**v1.0 rule (unchanged):**
> If a response scores a 0 in Factual Accuracy OR a 0 in Hallucination, the overall verdict is automatically capped at Marginal, regardless of the composite score.

**v2.0 addition:**
> This cap is **extended to all seven dimensions**. If a response scores 0 in **any** rubric dimension, the overall verdict is automatically capped at **Marginal**, regardless of the composite score.

**Rationale:** A score of 0 in any dimension represents a complete failure in that dimension — not a weakness or a partial gap, but a total absence of the quality being measured. A response that is completely irrelevant, completely incomplete, ignores all user instructions, reasons entirely invalidly, or cannot be understood has failed at a fundamental level, regardless of how well it performs in other dimensions. Applying the cap uniformly reflects the principle that **any categorical failure in a required quality dimension disqualifies a response from a Good or Excellent rating.**

### The v2 Override Table (Full)

| Dimension | v1.0 Triggers Override? | v2.0 Triggers Override? |
|---|---|---|
| D1 — Factual Accuracy | Yes | Yes |
| D2 — Relevance | No | **Yes** |
| D3 — Completeness | No | **Yes** |
| D4 — Instruction Following | No | **Yes** |
| D5 — Reasoning Quality | No | **Yes** |
| D6 — Hallucination | Yes | Yes |
| D7 — Clarity & Communication | No | **Yes** |

---

## 3. Rationale for Each Extended Dimension

### D2 — Relevance
A response that scores 0 in Relevance "misses the core intent of the prompt, answering a different question or providing overwhelmingly off-topic information." A user who receives such a response gains no progress toward their actual task. Regardless of how accurate or well-written the content is, it is useless for the user's purpose.

### D3 — Completeness
A response that scores 0 in Completeness "leaves critical parts of the prompt completely unanswered, rendering the output practically useless for the user's overall goal." By the rubric's own definition, a D3=0 response is *practically useless*. A response whose own rubric definition contains the phrase "practically useless" should not receive a Good verdict.

### D4 — Instruction Following
A response that scores 0 in Instruction Following "fundamentally ignores the core format, style, or negative constraints requested by the user." Explicit user constraints define what the user actually needs from the response. Completely ignoring them — particularly negative constraints such as "do not include X" — represents a failure to perform the requested task, independent of the quality of the content produced.

### D5 — Reasoning Quality
A response that scores 0 in Reasoning Quality "relies on flawed logic, contradictory statements, or invalid deductive steps" such that "the conclusion does not follow from the premises." A recommendation that does not logically follow from its own evidence is not a reliable recommendation. A reasoning-invalid response could lead users to incorrect decisions. Good responses should not contain conclusions that are logically disconnected from the evidence presented.

### D7 — Clarity & Communication
A response that scores 0 in Clarity is "highly disorganized...making it difficult for the user to extract the necessary information." Information that cannot be extracted is functionally absent. The distinction between Case 006 (D3=0, information missing) and Case 007 (D7=0, information present but inaccessible) matters for diagnosis, but the practical outcome — information the user cannot use — is similar in severity.

---

## 4. Unchanged Elements from v1.0

All other provisions of Scoring Methodology v1.0 remain unchanged:

- Individual dimension scoring (0, 1, 2 integers only)
- Composite score calculation (sum of 7 dimensions, max 14)
- Performance verdict categories (Excellent 13–14, Good 10–12, Marginal 6–9, Poor 0–5)
- Decision rules for partially correct responses
- Distinction between Factual Errors and Hallucinations
- Distinction between Incomplete and Irrelevant
- No hidden chain-of-thought evaluation
- Confidence level documentation (High / Moderate / Low)
- Ambiguity and limitation handling requirements
- Reproducibility requirements (quote evidence, explicit dimension mapping, integer constraints)

---

## 5. Impact Simulation: Cases 001–008 Under v2.0

The following table shows how the v2 extended override would have changed final verdicts for the designed case set:

| Case | Primary D = 0 | v1.0 Override? | v1.0 Verdict | v2.0 Override? | v2.0 Verdict | Changed? |
|---|---|---|---|---|---|---|
| 001 | D1 | Yes | Marginal | Yes | Marginal | No |
| 002 | D4 | No | Good | **Yes** | **Marginal** | **Yes** |
| 003 | D5 | No | Good | **Yes** | **Marginal** | **Yes** |
| 004 | D6 | Yes | Marginal | Yes | Marginal | No |
| 005 | D2 | No | Good | **Yes** | **Marginal** | **Yes** |
| 006 | D3 | No | Good | **Yes** | **Marginal** | **Yes** |
| 007 | D7 | No | Good | **Yes** | **Marginal** | **Yes** |
| 008 | None (mixed 1s) | No | Marginal | No | Marginal | No |

**v2.0 verdict distribution for this portfolio:**

| Verdict | v1.0 | v2.0 |
|---|---|---|
| Good | 5 cases | 0 cases |
| Marginal | 3 cases | 8 cases |

**Interpretation:** Under the proposed v2 rules, all eight intentionally stress-tested cases receive a Marginal verdict. This demonstrates that v2 closes the specific override gaps exposed by the portfolio, but it does not by itself establish that the revised methodology is validated for general real-world LLM evaluation. In practice, a normally-functioning strong response would score at least 1 in every dimension, producing a composite in the Good or Excellent band without triggering the extended override, but further empirical validation on undesigned datasets is required.

---

## 6. Addressing the Two-Path Marginal Problem

Scoring Methodology v1.0 identified that the Marginal verdict can be reached through two structurally different paths: a Critical Failure Override (Path A) or natural score accumulation below 10 (Path B). Under v2.0, a third path is added:

| Path | Mechanism | Example Case |
|---|---|---|
| A — Override (reliability) | D1=0 or D6=0 triggers cap; raw score may be Good | Cases 001, 004 |
| B — Score accumulation | Raw composite ≤ 9; no zeros | Case 008 |
| C — Override (usability) [NEW] | Any D = 0 triggers cap; raw score may be Good | Cases 002, 003, 005, 006, 007 |

To support verdict interpretation, evaluation reports under v2.0 should explicitly document which path produced the Marginal verdict. The Critical Failure Check section of each case study should be updated to specify:
- **Override Not Triggered** (Path B — score accumulation, if composite ≤ 9)
- **Reliability Override Triggered** (Path A — D1 or D6 = 0)
- **Usability Override Triggered** (Path C — D2, D3, D4, D5, or D7 = 0)

---

## 7. Limitations and Trade-offs of the v2 Proposal

### Trade-off 1: Strictness
The extended override is more demanding. A response that follows 7 of 8 explicit user instructions (scoring D4 = 1) will not trigger the override. A response that follows 0 of 8 (D4 = 0) will. The threshold remains the same (zero), but it now applies to five more dimensions.

### Trade-off 2: Equal weighting across dimensions
The extended override treats a D2=0 (completely irrelevant) and a D7=0 (completely unreadable) as equally disqualifying. In some task contexts, this may not reflect actual relative importance. A future v3 could introduce task-type-conditional override rules (e.g., for strict formatting tasks, D4 is as critical as D1).

### Trade-off 3: Not yet validated on real LLM responses
The v2 proposal is motivated by a designed case set in which every case was intentionally constructed to contain at least one failure. The extended override has not been tested against a set of real, undesigned LLM outputs — where the distribution of scores across dimensions may look very different. Validation on real outputs is recommended before adopting v2 as a production standard.

### Trade-off 4: Unchanged composite score
The v2 override extends the cap to more trigger conditions but does not revise the composite score or its underlying calculation. A response with D3=0 and everything else at 2 would score 12/14 under both v1 and v2 — the only difference is that v2 caps the verdict label at Marginal. This preserves score transparency while correcting the verdict label. Some evaluators may prefer a revised weighting scheme instead of a cap; this is documented as a potential v3 direction.

---

## 8. Summary of Proposed Changes

**Version:** v2.0 (Proposed)  
**Basis for revision:** Eight-case designed stress-test portfolio (Cases 001–008)  
**Status:** Proposed for review; not yet adopted as the evaluation standard

| Element | v1.0 | v2.0 (Proposed) |
|---|---|---|
| Composite scoring (0-14) | Unchanged | Unchanged |
| Verdict bands (Excellent/Good/Marginal/Poor) | Unchanged | Unchanged |
| Override trigger dimensions | D1, D6 | D1, D2, D3, D4, D5, D6, D7 |
| Override effect | Cap at Marginal | Cap at Marginal |
| Override path labeling | Not specified | Reliability / Usability / Accumulation paths documented |
| Number of cases in designed set | N/A | 8 |

The motivation, evidence basis, and trade-offs for this revision are fully documented in the Cross-Case Synthesis. The v1.0 document remains the current operative standard until this revision is formally adopted.
