# LLM Response Evaluation Case Study 002: Instruction Following

## Evaluation Metadata

- **Case Study ID:** case_002_instruction_following
- **Evaluation Date:** 2026-09-02
- **Evaluation Framework:** LLM Response Evaluation Rubric v1.0 & Scoring Methodology v1.0
- **Response Type:** Professional Documentation Draft
- **Subject Domain:** Software Product Communication / Technical Writing
- **Primary Evaluation Focus:** Instruction Following
- **Evaluator Notes:** This case tests the framework's ability to penalize a response that is factually accurate, clearly written, and highly relevant, but systematically fails multiple explicit user constraints. The response reads like a competent, professional answer to the general topic — but it is not compliant with the user's actual task. It demonstrates that factual correctness and good writing are insufficient if explicit constraints are ignored. Critically, this case also reveals that the Critical Failure Override is not triggered by a zero in Instruction Following, surfacing an important structural nuance in the scoring methodology.

---

## Original User Query

> "I need you to write a release notes entry for our software product, **DataSync Pro v4.2**, released on **March 14, 2026**.
>
> **Follow these rules precisely:**
>
> 1. **Format:** Write in plain prose only. Do **not** use bullet points, numbered lists, or headers.
> 2. **Length:** The entire response must be **120 words or fewer**.
> 3. **Must include:** Reference all three of the following new features by their exact names: **Smart Conflict Resolution**, **Offline Mode**, and **Live Dashboard**.
> 4. **Must NOT include:** Do not mention the legacy feature **DataSync Bridge** or the old version name **DataSync Classic** anywhere in the response.
> 5. **Audience:** Write for **non-technical end users**. Avoid engineering jargon.
> 6. **Call to action:** End with exactly one sentence encouraging users to update.
> 7. **Voice:** Write in **second person** ("you" / "your").
> 8. **Opening:** Begin the entry with the version number and release date.

---

## AI-Generated Response

### DataSync Pro v4.2 — Release Notes (March 14, 2026)

We are excited to announce the release of **DataSync Pro v4.2**, which brings several significant improvements over DataSync Classic based on customer feedback collected throughout Q1 2026.

**Key Improvements in This Release:**

- **Smart Conflict Resolution:** Our improved conflict-resolution engine now leverages a deterministic merge algorithm to handle concurrent write operations, eliminating data collisions in multi-node environments.
- **Offline Mode:** The new offline capability utilizes a local delta-sync buffer, allowing the application to queue transactional changes and synchronize them asynchronously upon network restoration.
- **Live Dashboard:** Real-time telemetry feeds are now surfaced through a WebSocket-backed Live Dashboard, providing sub-second latency metrics for your team's operational visibility.
- **Legacy Migration:** Users migrating from DataSync Bridge will find an automated schema translation utility now bundled in the installer.

We strongly recommend upgrading to v4.2 as soon as possible to take advantage of these improvements.

---

## Instruction Inventory

| Instruction ID | Exact or Faithful Instruction | Instruction Type | Required Behavior |
|---|---|---|---|
| I1 | "Write in plain prose only. Do not use bullet points, numbered lists, or headers." | Format | Response must be entirely in paragraph form. No bullets, lists, or markdown headers. |
| I2 | "The entire response must be 120 words or fewer." | Length | Total word count of the response must not exceed 120. |
| I3 | "Reference all three of the following new features by their exact names: Smart Conflict Resolution, Offline Mode, and Live Dashboard." | Inclusion Requirement | All three feature names must appear verbatim in the response. |
| I4 | "Do not mention the legacy feature DataSync Bridge or the old version name DataSync Classic anywhere in the response." | Exclusion Requirement | Neither "DataSync Bridge" nor "DataSync Classic" must appear anywhere in the response. |
| I5 | "Write for non-technical end users. Avoid engineering jargon." | Audience / Tone | Vocabulary and explanations must be accessible to a non-technical reader. No engineering terminology. |
| I6 | "End with exactly one sentence encouraging users to update." | Inclusion Requirement / Structure | The final sentence must be a direct call to action for users to upgrade. |
| I7 | "Write in second person ("you" / "your")." | Voice | All prose must use second-person voice ("you", "your"). First person ("we", "our") is not compliant. |
| I8 | "Begin the entry with the version number and release date." | Structure / Ordering | The very first content must state "DataSync Pro v4.2" and "March 14, 2026." |

---

## Reference Evaluation Standard

A fully compliant response to this query would:

1. Open immediately with the version number and date in plain prose (no header formatting).
2. Consist entirely of connected prose paragraphs — no bullets, numbered lists, or bold section headers.
3. Come in at 120 words or fewer when counted.
4. Name all three features (**Smart Conflict Resolution**, **Offline Mode**, **Live Dashboard**) at least once each, verbatim.
5. Contain no reference to **DataSync Bridge** or **DataSync Classic**.
6. Use vocabulary a general consumer could understand without engineering knowledge — no terms like "deterministic merge algorithm," "delta-sync buffer," "WebSocket," or "asynchronous."
7. Use "you" and "your" consistently throughout.
8. End with a single sentence calling on the user to update.

---

## Dimension-by-Dimension Evaluation

### 1. Factual Accuracy
- **Score:** 2/2
- **Evidence:** The release is correctly identified as DataSync Pro v4.2, dated March 14, 2026. The three named features (Smart Conflict Resolution, Offline Mode, Live Dashboard) are mentioned. The general descriptions of what each feature does are plausible and not internally contradictory.
- **Justification:** All verifiable factual elements within the response are accurate relative to the prompt's grounding information. No factual claims are invented or distorted.
- **Failure Mode:** None.

---

### 2. Relevance
- **Score:** 2/2
- **Evidence:** The entire response is about DataSync Pro v4.2 and its new capabilities, directly aligned with the user's prompt.
- **Justification:** The response stays entirely on topic. There is no topic drift or tangential content unrelated to the product release.
- **Failure Mode:** None.

---

### 3. Completeness
- **Score:** 1/2
- **Evidence:** The response includes the product name, date, and all three feature names. However, the closing sentence — *"We strongly recommend upgrading to v4.2 as soon as possible..."* — is written in first person ("We"), which makes it a partially compliant call to action. More significantly, the explicit instruction was to end with the call to action, but the last structural element of the response is the recommendation sentence after a bulleted list, not a distinct concluding prose paragraph.
- **Justification:** The call-to-action sentence is present but does not fully satisfy its requirement because of the voice violation (first person). The main structural content of all three features is addressed. The score of 1 reflects a response that is largely complete but misses the precise construction of the required closing element.
- **Failure Mode:** Answering only part of a multi-part question (inclusion requirement partially met).
- **Note:** The completeness penalty is specifically for the omission of a required element. The format and voice issues driving this incompleteness are also penalized independently under Instruction Following (I6, I7). Per methodology, double-penalizing the same root failure across unrelated dimensions is avoided; here, Completeness captures the *missing element outcome*, while Instruction Following captures the *rule violation causes*.

---

### 4. Instruction Following
- **Score:** 0/2
- **Evidence:**
  - **I1 Violated:** Response opens with a `### DataSync Pro v4.2 — Release Notes (March 14, 2026)` markdown header, then uses `**Key Improvements in This Release:**` as a bold section label, and presents content as a four-item bullet list.
  - **I4 Violated:** *"...improvements over DataSync Classic based on customer feedback..."* and *"Users migrating from DataSync Bridge..."* — both forbidden terms appear explicitly.
  - **I5 Violated:** *"deterministic merge algorithm"*, *"delta-sync buffer"*, *"transactional changes"*, *"asynchronously"*, *"WebSocket-backed"*, *"sub-second latency"* — multiple engineering-specific terms used.
  - **I7 Violated:** Response uses *"We are excited to announce"* and *"We strongly recommend"* — consistent first-person voice, not second person.
- **Justification:** The response fundamentally ignores the core format requirement (I1: prose only), violates an explicit exclusion rule by naming both banned terms (I4), uses engineering jargon throughout contrary to the non-technical audience directive (I5), and consistently adopts first-person voice instead of the required second person (I7). Four of eight instructions are violated, including the most structurally significant ones. Per the rubric, a score of 0 is appropriate when the model "fundamentally ignores the core format, style, or negative constraints."
- **Failure Mode:** Ignoring the requested output format; violating explicit negative constraints; using the wrong tone/audience level; adopting incorrect voice.

---

### 5. Reasoning Quality
- **Score:** 2/2
- **Evidence:** The response presents features in a logical sequence from the most complex (conflict resolution) to accessibility features (offline mode) to visibility tools (dashboard), followed by a migration note and a recommendation.
- **Justification:** While this task does not require multi-step logical deduction, the response presents its content in a coherent, organized sequence. There are no non-sequiturs or contradictions in the structure of the explanation.
- **Failure Mode:** None.

---

### 6. Hallucination / Unsupported Claims
- **Score:** 2/2
- **Evidence:** The response does not fabricate feature capabilities, invent URLs, or make unsupported assertions beyond what was grounded in the prompt.
- **Justification:** All mentioned features were specified in the user's prompt. Descriptions of what each feature does (e.g., handling "concurrent write operations," queuing "changes upon network restoration") are plausible engineering descriptions with no fabricated specifics that can be identified as invented.
- **Failure Mode:** None.

---

### 7. Clarity and Communication
- **Score:** 2/2
- **Evidence:** The response is well-structured, uses consistent formatting, and communicates each feature's value clearly on its own terms.
- **Justification:** Setting aside the instruction-following failures, the text itself is professionally written, grammatically correct, and easy to read. The bullet-point structure is clear and scannable. This dimension scores on the *quality of communication*, not the *appropriateness of format to the user's constraints* — the latter is captured by Instruction Following.
- **Failure Mode:** None. Note: The technically-worded descriptions count as a communication style choice here; their failure to meet the *audience* requirement is addressed under I5 in Instruction Following, not here.

---

## Instruction Compliance Matrix

| Instruction ID | Required Behavior | Actual Response Behavior | Result |
|---|---|---|---|
| I1 | Plain prose only; no bullets, lists, or headers | Opens with a markdown header (`###`); uses a bold section label; delivers all features as a 4-item bullet list | **Not Followed** |
| I2 | 120 words or fewer | Response contains approximately 167 words | **Not Followed** |
| I3 | Name all three features: Smart Conflict Resolution, Offline Mode, Live Dashboard | All three feature names appear verbatim in the response | **Followed** |
| I4 | Do not mention DataSync Bridge or DataSync Classic | Both "DataSync Classic" and "DataSync Bridge" appear explicitly | **Not Followed** |
| I5 | Non-technical audience; avoid engineering jargon | Uses "deterministic merge algorithm," "delta-sync buffer," "WebSocket-backed," "sub-second latency," "asynchronously" | **Not Followed** |
| I6 | End with one sentence encouraging users to update | A recommendation sentence is present at the end, though written in first person ("We strongly recommend...") | **Partially Followed** |
| I7 | Second person ("you" / "your") throughout | Uses first person ("We are excited," "We strongly recommend," "Our improved") throughout | **Not Followed** |
| I8 | Begin with the version number and release date | Version and date appear in the opening header (though as a header, not prose) | **Partially Followed** |

**Summary:** 1 Followed, 2 Partially Followed, 5 Not Followed.

---

## Critical Failure Check

- **Triggered:** No
- **Reason:** The Critical Failure Override applies only when a response scores **0 in Factual Accuracy (Dimension 1)** or **0 in Hallucination / Unsupported Claims (Dimension 6)**. This response scores:
  - Factual Accuracy: **2** — Override condition not met.
  - Hallucination: **2** — Override condition not met.
- **Impact:** The Critical Failure Override does **not** engage. Despite scoring 0 in Instruction Following, the raw composite score determines the final verdict without a cap adjustment.

---

## Composite Score

| Dimension | Score | Max |
|---|---|---|
| 1. Factual Accuracy | 2 | 2 |
| 2. Relevance | 2 | 2 |
| 3. Completeness | 1 | 2 |
| 4. Instruction Following | 0 | 2 |
| 5. Reasoning Quality | 2 | 2 |
| 6. Hallucination / Unsupported Claims | 2 | 2 |
| 7. Clarity and Communication | 2 | 2 |
| **Total** | **11** | **14** |

**Raw Score:** 11 / 14  
**Raw Verdict Category:** Good (10–12 range)  
**Critical Failure Override:** Not Triggered  
**Final Verdict: Good**

---

## Detailed Failure Analysis

### Failure 1: Format Violation (I1)
- **Instruction violated:** I1 — "Write in plain prose only. Do not use bullet points, numbered lists, or headers."
- **How the response violated it:** The response opens with a markdown H3 header, introduces a bold section label, and delivers all feature content as a four-item bulleted list. The response contains no prose paragraphs.
- **Violation type:** Complete — the instruction was comprehensively ignored; the entire content structure contradicts it.
- **Why it matters:** This is a professional documentation task. A changelog formatted as bullet points cannot be used in a prose-only output field. The user's downstream use case (e.g., inserting into a CMS or email body with specific layout requirements) is broken by this failure.

---

### Failure 2: Word Count Exceeded (I2)
- **Instruction violated:** I2 — "The entire response must be 120 words or fewer."
- **How the response violated it:** The response contains approximately 167 words, exceeding the 120-word limit by approximately 47 words (≈39% over).
- **Violation type:** Complete — the response substantially exceeds the stated limit.
- **Why it matters:** Word count constraints often exist because the text must fit a specific content slot (e.g., an email preview, a UI panel, or a character-limited field). Exceeding the limit makes the output unusable for its intended deployment context without significant editing.

---

### Failure 3: Explicit Exclusion Violation (I4)
- **Instruction violated:** I4 — "Do not mention the legacy feature DataSync Bridge or the old version name DataSync Classic anywhere in the response."
- **How the response violated it:** The response contains: *"improvements over DataSync Classic"* and *"Users migrating from DataSync Bridge."* Both forbidden terms appear.
- **Violation type:** Complete — both excluded terms are explicitly present.
- **Why it matters:** This is the most professionally damaging failure. Naming a deprecated product in a release notes entry can confuse customers, undermine the product positioning strategy, and require the team to discard the output entirely. Exclusion constraints of this kind exist precisely because incorrect mentions cause reputational or operational harm.

---

### Failure 4: Audience / Tone Violation (I5)
- **Instruction violated:** I5 — "Write for non-technical end users. Avoid engineering jargon."
- **How the response violated it:** The response uses: *"deterministic merge algorithm," "delta-sync buffer," "transactional changes," "asynchronously," "WebSocket-backed," "sub-second latency metrics," "operational visibility."*
- **Violation type:** Complete — the text is written in technical engineering language throughout.
- **Why it matters:** A non-technical user reading this changelog would not understand what the product has changed or why it matters to them. The user's core requirement — communicating to an end-user audience — is entirely unmet.

---

### Failure 5: Voice Violation (I7) — Partial
- **Instruction violated:** I7 — "Write in second person ('you' / 'your')."
- **How the response violated it:** The response consistently uses first person: *"We are excited to announce," "Our improved conflict-resolution engine," "We strongly recommend."*
- **Violation type:** Complete — no second-person voice is used anywhere in the response.
- **Why it matters:** Voice requirements exist for brand consistency. A product using "you"-centered messaging that receives "we"-centered content must rewrite the draft before use.

---

## Overall Verdict

This response demonstrates a critical distinction: **answering the topic** is not the same as **answering the user's requested task**.

The AI correctly knows what DataSync Pro v4.2 is, correctly names all three features, and produces a professionally structured and grammatically clean piece of writing. On the general question of "write something about this software release," the response would pass. A casual reader would likely consider it satisfactory.

However, the user did not ask for "something about this software release." The user asked for a highly constrained professional documentation artifact: prose-only, 120 words maximum, second-person voice, non-technical language, with two terms explicitly banned. The AI delivered a bulleted, 167-word, first-person, technically-worded document that names both banned terms.

Despite scoring 0 in Instruction Following, the composite score lands at 11/14, placing the final verdict at **Good** — because the Critical Failure Override does not activate for instruction-following failures. This reveals an important structural characteristic of the methodology: the override protects against factual and hallucination disasters, but systematic instruction-following failure can co-exist with a high overall score.

---

## Evaluation Conclusion

**Methodological Lesson:** A response that follows zero of five critical constraints can still receive a "Good" verdict if its factual accuracy, relevance, hallucination, and clarity dimensions score highly. This demonstrates that the Critical Failure Override has a narrow scope by design — it targets factual reliability, not task compliance. 

Evaluators and methodology designers should be aware of this gap: for tasks where instruction-following is the primary success criterion (e.g., constrained professional writing, code generation with specific rules, or structured output formatting), a supplementary task-compliance check or a weighted scoring mechanism may be needed to prevent high-scoring but operationally unusable responses from achieving misleadingly positive verdicts.
