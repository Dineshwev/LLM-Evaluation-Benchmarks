# Unified Portfolio Evaluation Methodology

## 1. Unified Evaluation Philosophy

The core philosophy underlying this portfolio is that **LLM evaluation must move from subjective impressions to deterministic, criteria-based measurement.** As models become increasingly fluent, superficial evaluations ("this looks like a good answer") become dangerously misleading. Fluency can mask hallucinations, constraint violations, and critical reasoning failures.

To address this, all evaluation frameworks developed in this portfolio adhere to three foundational principles:
1. **Dimension Independence:** Quality is not monolithic. Responses are scored across highly specific dimensions (e.g., Factuality, Tone, Entailment) so that a failure in one area cannot be masked by success in another.
2. **Evidence-Based Scoring:** No score is assigned without direct, quoted evidence from the AI response. 
3. **Structured Failure Gating:** Composite scores are useful for ranking, but dangerous for safety. Each methodology employs an "Override" or "Gate" (e.g., the Critical Failure Override or Vulnerability Override) to cap final verdicts when a response fails a safety-critical dimension, regardless of its overall score.

---

## 2. The Three Evaluation Pillars

The portfolio is structured around three distinct evaluation disciplines, each designed to test a different aspect of AI interaction:

| Pillar | Focus | Core Question | Approach |
|---|---|---|---|
| **Citation Verification** | Grounding & Trust | *Does the cited source actually support the claim being made?* | Evaluates strict logical entailment, checking for scope expansion, missing qualifiers, and citation placement. |
| **LLM Response Evaluation** | Quality & Usability | *Is the response accurate, helpful, and compliant with user instructions?* | Evaluates standard cooperative prompts across 7 dimensions (Accuracy, Relevance, Completeness, Instruction Following, Reasoning, Hallucination, Clarity). |
| **Adversarial Testing** | Resilience & Calibration | *How does the model behave when the prompt is actively trying to break it?* | Evaluates defensive resilience across 4 targeted dimensions (Trap Detection, Constraint Adherence Under Load, Factuality/Calibration, Recovery/Tone). |

---

## 3. Why Different Tasks Require Different Rubrics

A common pitfall in AI evaluation is attempting to use a single, generalized rubric ("Accuracy, Fluency, Helpfulness") for all outputs. This portfolio demonstrates why different tasks require bespoke frameworks:

### Accuracy vs. Entailment
In the **Citation Verification** portfolio, we found that a claim can be *factually accurate* in the real world but *unsupported* by the provided citation. A general "Accuracy" rubric would rate the response as successful, entirely missing the grounding failure (hallucinated citations). Therefore, Citation Verification requires an "Entailment" metric, not an "Accuracy" metric.

### Helpfulness vs. Defensiveness
In the **LLM Response Evaluation** portfolio, a model is rewarded for answering the prompt completely and adapting to the user's instructions (Helpfulness). 
However, in the **Adversarial Testing** portfolio, this exact same trait becomes a critical vulnerability. When given a false premise or a leading question, a "helpful" model will often agree with the user, resulting in Sycophancy or False Certainty. Adversarial testing requires a rubric that explicitly rewards *Defensiveness*—the ability to politely refuse, correct the user, and calibrate uncertainty.

---

## 4. Meta-Evaluation: Testing the Frameworks

This portfolio does not merely evaluate LLMs; it evaluates the **evaluation frameworks themselves**. 

Instead of applying a framework to a random sample of responses and accepting the results, the methodology involves designing *targeted stress tests* to find the breaking points of the rubric. 

**Key Methodological Discovery:**
During the *LLM Response Evaluation* arc, we designed Case 006 (Completeness Failure) and Case 007 (Clarity Failure) to test the boundaries of the v1 methodology. We discovered an "Override Gap" where a model could score 0 in a dimension (e.g., providing an entirely unreadable response) yet still mathematically achieve a "Good" final verdict. This empirical discovery drove the development of **Scoring Methodology v2**, proving that robust evaluation requires continuous meta-evaluation and framework iteration.
