# LLM Response Evaluation Rubric (v1.0)

## Overview

This rubric is designed to systematically evaluate the overall quality of AI-generated responses. Unlike citation verification, which strictly measures source-to-claim alignment, this rubric assesses the substantive quality, accuracy, and utility of the response itself.

Evaluators must base their assessment strictly on **observable outputs and externally verifiable reasoning**. Hidden chains-of-thought or internal model processing steps are explicitly out of scope.

## Scoring Scale

Each dimension is scored on a **0 to 2 scale**:
- **2 (High Performance):** The response meets the highest standards for this dimension. Minor imperfections may exist but do not detract from the overall quality.
- **1 (Medium Performance):** The response shows partial success but contains noticeable flaws, omissions, or weaknesses that reduce its utility.
- **0 (Low Performance):** The response fails to meet basic standards for this dimension, demonstrating severe flaws, critical omissions, or fundamental misunderstandings.

---

## 1. Factual Accuracy
**Definition:** The degree to which the information presented in the response is objectively true, verifiable, and free of material errors.

- **2 (High):** All material facts, dates, names, and concepts are correct. Any minor inaccuracies are trivial and do not impact the core message.
- **1 (Medium):** The response contains some factual errors or relies on outdated information, but the core premise remains largely intact.
- **0 (Low):** The response contains critical factual errors that render the answer materially false or highly misleading.

**Common Failure Modes:**
- Confusing similar entities, dates, or technical terms.
- Providing deprecated or obsolete information (e.g., old API syntax).
- Presenting a highly debated topic as absolute consensus without nuance.

---

## 2. Relevance
**Definition:** The degree to which the response directly addresses the user's prompt without introducing off-topic, tangential, or unnecessary information.

- **2 (High):** The response is highly focused and directly answers the user's query. All context provided adds clear value.
- **1 (Medium):** The response addresses the prompt but includes significant tangential information or takes an indirect path to the answer.
- **0 (Low):** The response misses the core intent of the prompt, answering a different question or providing overwhelmingly off-topic information.

**Common Failure Modes:**
- "Topic drift," where the model pivots to a related but unrequested subject.
- Verbose preambles or conclusions that restate the prompt without adding value.

---

## 3. Completeness
**Definition:** The degree to which the response comprehensively covers all necessary aspects of the user's query.

- **2 (High):** All parts of the user's prompt are thoroughly addressed. The response anticipates logical follow-ups if appropriate.
- **1 (Medium):** The response addresses the main point but misses secondary constraints, sub-questions, or necessary context.
- **0 (Low):** The response leaves critical parts of the prompt completely unanswered, rendering the output practically useless for the user's overall goal.

**Common Failure Modes:**
- Answering only the first half of a multi-part question.
- Providing a conceptual explanation but failing to provide the requested code example.
- *Note:* Completeness is distinct from Relevance. A response can be highly relevant but incomplete, or highly complete but bloated with irrelevant tangents.

---

## 4. Instruction Following
**Definition:** The precision with which the response adheres to explicit negative or positive constraints provided in the prompt (e.g., format, length, tone, exclusion rules).

- **2 (High):** All explicit constraints (e.g., "output as a JSON array", "do not use libraries", "in under 50 words") are strictly followed.
- **1 (Medium):** The model follows most constraints but misses at least one specific directive (e.g., formats as JSON but includes a markdown preamble).
- **0 (Low):** The model fundamentally ignores the core format, style, or negative constraints requested by the user.

**Common Failure Modes:**
- Including explanatory text when instructed to return *only* code.
- Failing to adopt a requested persona or tone.
- Violating explicit negative constraints ("Do not mention X").

---

## 5. Reasoning Quality
**Definition:** The logical soundness, coherence, and step-by-step progression of arguments or solutions presented *in the final output*. 

- **2 (High):** The response presents a clear, logically sound progression from premise to conclusion. Mathematical, deductive, or causal steps are correct and easy to follow.
- **1 (Medium):** The reasoning has minor logical leaps, circular arguments, or convoluted explanations, though the final conclusion may still be correct.
- **0 (Low):** The response relies on flawed logic, contradictory statements, or invalid deductive steps. The conclusion does not follow from the premises.

**Common Failure Modes:**
- Non-sequiturs, where step B does not logically follow step A.
- Circular reasoning (assuming the conclusion as a premise).
- Reaching a correct final answer through flawed intermediate math or logic.

---

## 6. Hallucination / Unsupported Claims
**Definition:** The presence of fabricated information, fictitious sources, or claims stated with high confidence that have no basis in reality or provided context.

- **2 (High):** The response contains zero hallucinations. If the model does not know the answer, it explicitly states its limitations.
- **1 (Medium):** The response contains minor unsupported details, slightly hallucinated embellishments, or "hallucinates" minor syntax in code, but the core output is real.
- **0 (Low):** The response invents entire concepts, URLs, citations, software features, or historical events that do not exist. 

**Common Failure Modes:**
- "URL Hallucination": Generating plausible but broken web links.
- "Feature Hallucination": Claiming a software library has a function it does not possess.
- Presenting an unsupported assumption as a verified fact.

---

## 7. Clarity and Communication
**Definition:** The readability, structure, formatting, and overall communication effectiveness of the response.

- **2 (High):** The response uses clear formatting (bullet points, bolding, code blocks), proper grammar, and a professional tone. It is easy to skim and digest.
- **1 (Medium):** The response is understandable but suffers from poor formatting, overly dense paragraphs, or slightly awkward phrasing.
- **0 (Low):** The response is highly disorganized, grammatically flawed, or structurally confusing, making it difficult for the user to extract the necessary information.

**Common Failure Modes:**
- "Wall of text" without paragraph breaks or structural hierarchy.
- Inconsistent markdown formatting (e.g., broken code blocks).
- Overly academic or complex language when a simple explanation was requested.
