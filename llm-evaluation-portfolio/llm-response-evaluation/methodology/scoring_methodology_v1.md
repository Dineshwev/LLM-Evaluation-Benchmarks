# LLM Response Evaluation Scoring Methodology (v1.0)

## Overview
This document outlines the systematic process for applying the LLM Response Evaluation Rubric (v1.0). It establishes clear decision rules for calculating scores, defining final verdicts, and handling edge cases to ensure evaluations are reproducible and consistent across different evaluators.

## 1. Calculating Individual Dimension Scores
Each of the 7 core dimensions is scored on a discrete scale of **0, 1, or 2**.
- Fractional scores (e.g., 1.5) are **not permitted**. Evaluators must choose the integer that best describes the performance level.
- When an evaluator is torn between two scores, they should consult the "Common Failure Modes" in the rubric. If a response matches a listed failure mode for a "Low (0)" or "Medium (1)" rating, that lower score must be assigned.

## 2. Calculating the Composite Score
The overall composite score is the simple sum of the individual dimension scores. 
- Maximum possible score: **14** (7 dimensions × 2 points max)
- Minimum possible score: **0**

For reporting purposes, this score can be normalized to a 10-point scale: `(Composite Sum / 14) * 10`.

## 3. Performance Verdict Categories
Based on the un-normalized composite sum (0-14), the response is assigned an overall verdict:

| Verdict | Score Range | Definition |
|---|---|---|
| **Excellent** | 13 - 14 | The response is outstanding across almost all dimensions. It fully resolves the user's intent with high accuracy, clarity, and precision. |
| **Good** | 10 - 12 | The response is highly useful and largely correct, but suffers from minor flaws in completeness, clarity, or strict instruction following. |
| **Marginal** | 6 - 9 | The response provides some value but requires significant user correction. It may suffer from moderate factual errors, missing components, or poor reasoning. |
| **Poor** | 0 - 5 | The response is unusable. It contains severe factual errors, hallucinations, or completely fails to address the user's query. |

*Note: A critical failure override applies (see Decision Rules below).*

## 4. Decision Rules and Edge Cases

### Handling Partially Correct Responses
When a response gets some things right and some things wrong:
- Evaluate **Factual Accuracy** at 1 if the core premise holds, but drop to 0 if the error corrupts the primary answer.
- Evaluate **Completeness** at 1 if a sub-question is missed.

### Handling Factual Errors vs. Unsupported Assumptions (Hallucinations)
- **Factual Error (Dimension 1):** The model states something that can be proven objectively false (e.g., "The Earth has two moons").
- **Unsupported Assumption / Hallucination (Dimension 6):** The model invents an API endpoint, constructs a fake URL, or asserts a causal link without evidence. 
If a hallucination also functions as a factual error, penalize *both* dimensions.

### Distinguishing Incomplete from Irrelevant
- **Incomplete (Dimension 3 penalty):** The response stays on topic but stops short. It answers question A but ignores question B.
- **Irrelevant (Dimension 2 penalty):** The response introduces unrequested topics. It answers question A, then spends three paragraphs discussing an unrelated topic C.
A response can be highly relevant (stays perfectly on topic) but incomplete (misses half the constraints).

### Evaluating Reasoning Quality (No Hidden Chain-of-Thought)
Evaluators must assess **only the reasoning visible in the final generated text**. 
- Do not attempt to guess "what the model was thinking."
- Do not grade hidden `<think>` or chain-of-thought blocks if the system provides them natively in a hidden UI state. 
- Score based purely on whether the explicit logical steps presented to the user validly lead to the stated conclusion.

### Critical Failure Override
If a response scores a **0 in Factual Accuracy** OR a **0 in Hallucination**, the overall verdict is automatically capped at **Marginal**, regardless of the composite score. A beautifully formatted, perfectly relevant answer that is dangerously wrong cannot be classified as "Good."

## 5. Confidence Levels and Ambiguity

For every evaluation, the evaluator must record a Confidence Level:
- **High:** The prompt is unambiguous, the facts are easily verifiable, and the scoring aligns cleanly with the rubric.
- **Moderate:** The prompt contains some ambiguity, or the response sits exactly on the border between two score bands.
- **Low:** The user intent is highly subjective, or the domain is so obscure that factual verification is largely speculative.

**Ambiguity and Limitation Handling:**
All case studies must include a section for "Ambiguities & Limitations" where the evaluator documents why a specific score was difficult to assign. If the user prompt itself is contradictory (e.g., "Write a 500-word essay in two sentences"), the evaluator should document how this impacted the Instruction Following score.

## 6. Reproducibility Requirements
To ensure consistency across different evaluators:
1. **Quote the Evidence:** When justifying a score of 1 or 0, evaluators must explicitly quote the exact sentence or code block where the failure occurred.
2. **Explicit Dimension Mapping:** Evaluators cannot assign a generic verdict. They must output the score for all 7 dimensions independently.
3. **Strict Boundaries:** Evaluators must adhere to the 0, 1, 2 integer constraints.
