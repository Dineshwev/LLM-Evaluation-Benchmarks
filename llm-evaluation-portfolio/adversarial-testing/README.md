# Adversarial Testing Portfolio

This is the third pillar of the LLM Evaluation Portfolio. While standard evaluations test how well a model assists a cooperative user, this portfolio evaluates **model robustness against intentionally difficult, misleading, or adversarial prompts.**

## Project Structure

```
adversarial-testing/
│
├── README.md                           # This index file
├── methodology/
│   ├── adversarial_testing_rubric_v1.md
│   └── adversarial_scoring_methodology_v1.md
├── test-cases/                         # Planned cases
└── evaluations/                        # Future cross-case synthesis
```

## Core Philosophy

An LLM's true reliability is tested when the prompt itself is flawed, overloaded, or actively trying to induce a failure. A robust model must balance **helpfulness** (answering what it can) with **defensiveness** (refusing to adopt false premises, hallucinate, or violate core instructions).

## Planned Evaluation Vectors

We will evaluate the model across eight distinct adversarial categories:

1. **Prompt Injection / Instruction Conflict:** Testing whether secondary or hidden instructions can override primary system directives.
2. **Ambiguity and Underspecification:** Testing if the model asks for clarification or confidently guesses (and risks hallucinating) when given insufficient detail.
3. **False-Premise Traps:** Embedding an incorrect fact into the premise of the question to see if the model adopts it or corrects it.
4. **Constraint Overload:** Providing an excessive number of formatting, length, and content constraints to test cognitive load and instruction-dropping.
5. **Leading-Question Bias:** Phrasing questions to push the model toward a specific, potentially inaccurate or unsafe conclusion.
6. **Context Distraction:** Filling the prompt with highly detailed but completely irrelevant information to test attention mechanisms and relevance filtering.
7. **Conflicting Requirements:** Giving instructions that contradict each other (e.g., "be comprehensive" but "use under 50 words") to test conflict resolution.
8. **Confidence and Uncertainty Calibration:** Pressuring the model to provide a definitive answer on a topic where no definitive answer exists.

## Methodology Status

The initial evaluation framework (v1) was established and successfully held up under portfolio testing. Unlike the LLM Response Evaluation portfolio, the Vulnerability Override in this adversarial framework correctly captured catastrophic failures without needing a v2 revision.
- [Adversarial Testing Rubric v1](./methodology/adversarial_testing_rubric_v1.md)
- [Adversarial Scoring Methodology v1](./methodology/adversarial_scoring_methodology_v1.md)

## Completed Case Studies

1. [Case 001: Prompt Injection](./test-cases/case_001_prompt_injection.md)
2. [Case 002: Ambiguity and Underspecification](./test-cases/case_002_ambiguity_underspecification.md)
3. [Case 003: False-Premise Traps](./test-cases/case_003_false_premise_trap.md)
4. [Case 004: Constraint Overload](./test-cases/case_004_constraint_overload.md)
5. [Case 005: Leading-Question Bias](./test-cases/case_005_leading_question_bias.md)
6. [Case 006: Context Distraction](./test-cases/case_006_context_distraction.md)
7. [Case 007: Conflicting Requirements](./test-cases/case_007_conflicting_requirements.md)
8. [Case 008: Confidence and Uncertainty Calibration](./test-cases/case_008_confidence_calibration.md)

## Cross-Case Synthesis

A full review of the adversarial portfolio, including vector analysis (direct vs indirect attacks), failure patterns (sycophancy, selective compliance, false certainty), and portfolio statistics, is available in the synthesis document:
- [**Cross-Case Synthesis: Adversarial Testing Cases 001–008**](./evaluations/cross_case_synthesis_001_008.md)
