# Citation Verification Case Study 006: AI Coding Assistant Privacy Claims

## Evaluation Metadata

**Case Study ID:** case_006_ai_coding_assistant_privacy  
**Evaluation Date:** 2026-09-02  
**Evaluation Framework:** Citation Verification Rubric v1.0 & Methodology v1.0  
**Response Type:** AI-Generated Comparative Privacy Response with Citations  
**Subject Domain:** AI Coding Assistant Data Handling, Model Training, Data Retention  
**Evaluator Notes:** This response compares GitHub Copilot and Cursor on privacy, data retention, and model training. The response includes intentional citation failures across multiple categories: overgeneralization, direct contradiction of source, citation missing, partially supported claims, unsupported comparative conclusions, and product-surface confusion. This case tests the framework's ability to detect when claims exceed, contradict, or lack support from cited documentation.

---

## Original Query

"Compare the privacy and data handling practices of GitHub Copilot and Cursor for software developers. Are developers' private code and prompts used for AI model training, how long is data retained, and which tool provides stronger privacy protection for enterprise teams?"

---

## AI-Generated Response

## GitHub Copilot vs Cursor: Privacy and Data Handling

GitHub Copilot and Cursor both offer privacy protections for developers and enterprise organizations, but their approaches to data retention and model training are different.

### GitHub Copilot

**Model training:** GitHub Copilot never uses private code, prompts, or generated suggestions for AI model training, regardless of whether the user has an Individual, Business, or Enterprise subscription.

Citation: https://github.com/features/copilot

**Data retention:** GitHub Copilot permanently stores all developer prompts and generated code suggestions so users can access their complete interaction history.

Citation: https://github.com/features/copilot

**Enterprise privacy:** GitHub Copilot Business and Enterprise customer data is not used to train GitHub's AI models.

Citation: https://github.com/features/copilot

**Memory:** Copilot Memory permanently retains repository facts and developer preferences unless the user manually deletes them.

Citation: https://docs.github.com/en/copilot/concepts/agents/copilot-memory

### Cursor

**Privacy Mode:** When Privacy Mode is enabled, Cursor does not use customer code for training, and its AI model providers do not store or train on customer data.

Citation: https://cursor.com/data-use

**Default enterprise protection:** Privacy Mode is enabled by default for Cursor Enterprise teams.

Citation: https://prod.cursor.com/docs/enterprise/privacy-and-data-governance

**Universal Zero Data Retention:** Every model available in Cursor operates under Zero Data Retention, so no model provider ever retains prompts or responses.

Citation: https://prod.cursor.com/docs/enterprise/privacy-and-data-governance

**Cloud Agents:** Cursor Cloud Agents never store copies of customer repositories because Privacy Mode prevents all cloud storage of source code.

### Comparison

| Area | GitHub Copilot | Cursor |
|---|---|---|
| Private code used for training | Never for any user | Not used when Privacy Mode is enabled |
| Enterprise data used for training | No | No |
| Prompt retention | Permanently retained | Zero retention |
| Model-provider retention | Never retained | Never retained |
| Privacy controls | Limited | Privacy Mode |
| Cloud code storage | Not stored | Never stored |

## Conclusion

Cursor clearly provides stronger privacy protection than GitHub Copilot because it guarantees Zero Data Retention across every model and never stores source code in the cloud. GitHub Copilot, by contrast, permanently retains developer prompts and may use private code from individual users for model training.

For highly regulated enterprise environments, organizations should therefore choose Cursor because it provides complete Zero Data Retention and stronger protection for proprietary source code.

---

## Claim-by-Claim Evaluation

---

## Claim 1

**Claim:**  GitHub Copilot never uses private code, prompts, or generated suggestions for AI model training, regardless of whether the user has an Individual, Business, or Enterprise subscription.

**Citation:**  https://github.com/features/copilot

**Evidence Passage (from GitHub Copilot docs):**  For Business and Enterprise: "Your business data is not used to train GitHub Copilot models." For Individual users: "Your code snippets, prompts, code completions, and generated code may be used to train GitHub Copilot models, subject to your settings or unless you opt out."

**Context:**  The cited GitHub documentation explicitly distinguishes between subscription tiers. Business and Enterprise customer data is excluded from training. Individual users' code MAY be used for training unless they opt out. The claim's universal statement contradicts this documented distinction.

**Rubric Scoring:**

| Dimension | Score | Justification |
|---|---:|---|
| Entailment | 0/2 | The source directly contradicts the universal claim. Individual users' data may be used; Enterprise data is not. |
| Completeness | 0/2 | The claim ignores the documented distinction between subscription tiers. |
| Relevance | 2/2 | The source is directly about training use policies. |
| Evidence Quality | 2/2 | The source is official GitHub documentation. |
| Citation Placement | 2/2 | Citation is placed appropriately. |

**Composite Score:** 6/10

**Verdict:** **Unsupported**

**Rationale:**  The claim states an absolute rule that directly contradicts GitHub's documented policy. The response is false as stated.

**Ambiguities & Limitations:**  The response conflates subscription tiers that have materially different privacy policies. This is a significant factual error.

**Confidence Level:** High

---

## Claim 2

**Claim:**  GitHub Copilot permanently stores all developer prompts and generated code suggestions so users can access their complete interaction history.

**Citation:**  https://github.com/features/copilot

**Evidence Passage (from GitHub Copilot docs):**  For Business and Enterprise: "IDE prompts and suggestions are not retained." For Individual users: "Copilot may retain your code snippets and prompts for up to 28 days."

**Context:**  The cited documentation directly contradicts the claim. For Business/Enterprise, IDE prompts and suggestions are NOT retained. For Individual users, retention is up to 28 days, not permanent. The blanket claim is inaccurate.

**Rubric Scoring:**

| Dimension | Score | Justification |
|---|---:|---|
| Entailment | 0/2 | The source states the opposite: Business/Enterprise don't retain IDE prompts; Individual users have up to 28 days. |
| Completeness | 1/2 | The claim misses the subscription-tier distinction and the 28-day limit. |
| Relevance | 2/2 | The source is about data retention policy. |
| Evidence Quality | 2/2 | Official GitHub documentation. |
| Citation Placement | 2/2 | Citation is appropriately placed. |

**Composite Score:** 6/10

**Verdict:** **Unsupported**

**Rationale:**  The claim is contradicted by official documentation. GitHub does not permanently store IDE prompts for Business/Enterprise customers. For Individual users, retention is limited to 28 days. The universal claim is false.

**Ambiguities & Limitations:**  The response conflates different subscription tiers and misrepresents retention duration. This is a significant factual error.

**Confidence Level:** High

---

## Claim 3

**Claim:**  GitHub Copilot Business and Enterprise customer data is not used to train GitHub's AI models.

**Citation:**  https://github.com/features/copilot

**Evidence Passage (from GitHub Copilot docs):**  "Your business data is not used to train GitHub Copilot models."

**Context:**  GitHub's official documentation explicitly states that Business and Enterprise customer data is not used for training. The claim is a direct and accurate reflection of this policy.

**Rubric Scoring:**

| Dimension | Score | Justification |
|---|---:|---|
| Entailment | 2/2 | The source directly supports the claim. Business data is not used for training. |
| Completeness | 2/2 | The claim captures the complete promise for this subscription tier. |
| Relevance | 2/2 | The source is directly about training use. |
| Evidence Quality | 2/2 | Official GitHub documentation is authoritative. |
| Citation Placement | 2/2 | Citation is appropriately placed. |

**Composite Score:** 10/10

**Verdict:** **Fully Supported**

**Rationale:**  GitHub explicitly states that Business and Enterprise customer data is not used for training. The claim is accurate and directly supported.

**Ambiguities & Limitations:**  None. The policy is clear for these subscription tiers.

**Confidence Level:** High

---

## Claim 4

**Claim:**  Copilot Memory permanently retains repository facts and developer preferences unless the user manually deletes them.

**Citation:**  https://docs.github.com/en/copilot/concepts/agents/copilot-memory

**Evidence Passage (from GitHub Copilot docs):**  "To prevent stale information from lingering, any stored fact or preference that goes unused is automatically deleted after 28 days. The 28-day timer may reset whenever Copilot successfully validates and uses an entry."

**Context:**  The cited documentation directly contradicts the claim. Copilot Memory does not permanently retain information. Unused facts and preferences are automatically deleted after 28 days.

**Rubric Scoring:**

| Dimension | Score | Justification |
|---|---:|---|
| Entailment | 0/2 | The source states that unused information is automatically deleted after 28 days, contradicting the claim of permanent retention. |
| Completeness | 0/2 | The claim misses the automatic 28-day deletion policy entirely. |
| Relevance | 2/2 | The citation is to an official GitHub documentation page about Copilot Memory. |
| Evidence Quality | 2/2 | Official GitHub documentation. |
| Citation Placement | 2/2 | Citation is well-placed for this feature-specific claim. |

**Composite Score:** 6/10

**Verdict:** **Unsupported**

**Rationale:**  The claim is factually contradicted by the official documentation. Unused Memory information is automatically deleted after 28 days; it is not permanently retained until manual deletion.

**Ambiguities & Limitations:**  The claim fails to mention the automatic expiration of stale information.

**Confidence Level:** High

---

## Claim 5

**Claim:**  When Privacy Mode is enabled, Cursor does not use customer code for training, and its AI model providers do not store or train on customer data.

**Citation:**  https://cursor.com/data-use

**Evidence Passage (from Cursor docs):**  "With Privacy Mode enabled, customer code is not used for Cursor training, and model providers do not store or train on the data under our ZDR agreements. Exceptions include abuse investigations and non-ZDR models requiring special provider approval."

**Context:**  Cursor's documentation supports the core claim: Privacy Mode prevents training use and model providers do not store data under ZDR agreements. However, the documentation also lists exceptions. The response omits these important exceptions, making the claim too absolute.

**Rubric Scoring:**

| Dimension | Score | Justification |
|---|---:|---|
| Entailment | 1/2 | The source supports the main idea but documents exceptions that the claim does not mention. |
| Completeness | 1/2 | The claim omits abuse investigation exceptions and non-ZDR model exceptions. |
| Relevance | 2/2 | The source is directly about Privacy Mode and data handling. |
| Evidence Quality | 2/2 | Official Cursor documentation. |
| Citation Placement | 2/2 | Citation is appropriately placed. |

**Composite Score:** 8/10

**Verdict:** **Partially Supported**

**Rationale:**  The core principle is correct: Privacy Mode excludes code from training and prevents provider storage under ZDR. However, the claim is too absolute because it omits documented exceptions. This is an overgeneralization of the actual policy.

**Ambiguities & Limitations:**  The claim should specify that exceptions exist for legal/safety investigations and non-ZDR models.

**Confidence Level:** High

---

## Claim 6

**Claim:**  Privacy Mode is enabled by default for Cursor Enterprise teams.

**Citation:**  https://prod.cursor.com/docs/enterprise/privacy-and-data-governance

**Evidence Passage (from Cursor Enterprise docs):**  "Privacy Mode is enabled by default for all Cursor Enterprise teams, ensuring all prompts and code are excluded from training."

**Context:**  Cursor's official enterprise documentation explicitly confirms that Privacy Mode is the default configuration for Enterprise teams. The claim is accurate and directly supported.

**Rubric Scoring:**

| Dimension | Score | Justification |
|---|---:|---|
| Entailment | 2/2 | The source directly states Privacy Mode is enabled by default for Enterprise. |
| Completeness | 2/2 | The claim accurately captures the enterprise default configuration. |
| Relevance | 2/2 | The source is about enterprise privacy configuration. |
| Evidence Quality | 2/2 | Official Cursor Enterprise documentation. |
| Citation Placement | 2/2 | Citation is well-placed for enterprise claims. |

**Composite Score:** 10/10

**Verdict:** **Fully Supported**

**Rationale:**  Cursor's official documentation explicitly confirms that Privacy Mode is enabled by default for Enterprise teams. The claim is accurate.

**Ambiguities & Limitations:**  None. The policy is clearly stated.

**Confidence Level:** High

---

## Claim 7

**Claim:**  Every model available in Cursor operates under Zero Data Retention, so no model provider ever retains prompts or responses.

**Citation:**  https://prod.cursor.com/docs/enterprise/privacy-and-data-governance

**Evidence Passage (from Cursor docs):**  "Most models available in Cursor operate under Zero Data Retention agreements. Some models require provider-side retention for compliance or performance reasons and are not covered by ZDR unless expressly authorized by Cursor. Customers can view ZDR eligibility for each model in the settings."

**Context:**  The cited documentation directly contradicts the claim's universal statement. Cursor does NOT guarantee that every model operates under ZDR. Some models fall outside ZDR agreements and require provider-side retention. The claim's absolute language is not supported.

**Rubric Scoring:**

| Dimension | Score | Justification |
|---|---:|---|
| Entailment | 0/2 | The source says some models require provider-side retention; the claim says no provider ever retains. |
| Completeness | 0/2 | The claim states a universal rule that the source denies. |
| Relevance | 2/2 | The source is about model retention and ZDR eligibility. |
| Evidence Quality | 2/2 | Official Cursor documentation. |
| Citation Placement | 2/2 | Citation is appropriately placed. |

**Composite Score:** 6/10

**Verdict:** **Unsupported**

**Rationale:**  The source explicitly states that some models are not ZDR-eligible and require provider-side retention. The claim's universal statement is contradicted by the documentation.

**Ambiguities & Limitations:**  The claim uses absolute qualifiers ("every," "no…ever") that the source does not support. This is a significant factual error.

**Confidence Level:** High

---

## Claim 8

**Claim:**  Cursor Cloud Agents never store copies of customer repositories because Privacy Mode prevents all cloud storage of source code.

**Citation:**  None provided.

**Evidence Passage (from Cursor Cloud Agents docs):**  "Cursor Cloud Agents store encrypted copies of customer code during task execution for operational and debugging purposes. These copies are deleted after the task completes."

**Context:**  This claim is stated without any citation. Furthermore, the claim is factually contradicted by Cursor's official documentation, which explicitly states that Cloud Agents DO store encrypted copies of customer code. The response is both uncited and inaccurate.

**Rubric Scoring:**

| Dimension | Score | Justification |
|---|---:|---|
| Entailment | 0/2 | No source provided. Documentation contradicts the claim: agents do store copies. |
| Completeness | 0/2 | The claim is incomplete and misleading without mentioning temporary encrypted storage. |
| Relevance | 0/2 | No source provided at all. Claim fails basic citation requirement. |
| Evidence Quality | 0/2 | Citation is missing. |
| Citation Placement | 0/2 | No citation provided. |

**Composite Score:** 0/10

**Verdict:** **Citation Missing**

**Rationale:**  The claim is uncited and factually contradicted by Cursor's official documentation, which confirms that Cloud Agents do store encrypted copies of code. This is a fundamental failure on both citation and accuracy dimensions.

**Ambiguities & Limitations:**  The response provides no source to support the claim. The claim is provably false.

**Confidence Level:** High

---

## Claim 9

**Claim:**  Cursor clearly provides stronger privacy protection than GitHub Copilot because it guarantees Zero Data Retention across every model and never stores source code in the cloud.

**Citation:**  Implied from previous claims, but no direct citation for this comparative conclusion.

**Evidence Passages:**  This claim relies on Claim 7 (universal ZDR) and Claim 8 (Cloud Agent storage), both of which have been found to be unsupported or factually incorrect. Claim 2 (permanent retention for Copilot) is also contradicted by GitHub documentation.

**Context:**  This is a comparative conclusion based on earlier claims, some of which are demonstrably false. The reasoning chain itself is materially flawed: if Claim 7 is false (some models DO require provider-side retention), and Claim 8 is false (Cloud Agents DO store copies), then the comparative premise collapses. The conclusion cannot be supported because its factual foundation is unsound.

**Rubric Scoring:**

| Dimension | Score | Justification |
|---|---:|---|
| Entailment | 0/2 | The conclusion depends on false or unsupported claims (Claims 2, 7, 8). |
| Completeness | 1/2 | The comparison omits important nuance about subscription tiers and conditional policies. |
| Relevance | 2/2 | The comparison is relevant to the user query. |
| Evidence Quality | 0/2 | The underlying evidence (Claims 2, 7, 8) is false or unsupported. |
| Citation Placement | 1/2 | No direct citation for the conclusion itself; relies on invalid prior claims. |

**Composite Score:** 5/10

**Verdict:** **Partially Supported**

**Rationale:**  While it is true that Cursor offers stronger privacy options for Enterprise (Privacy Mode by default), the comparative conclusion is undermined by the falsity of its supporting claims. The response cannot validly claim Cursor has "universal" or "complete" ZDR protection when some models are excluded. This is an example of a conclusion that may contain true elements but whose reasoning is fundamentally flawed.

**Ambiguities & Limitations:**  The response conflates different subscription tiers and product features, and makes claims ("every model," "never stores") that are contradicted by the cited documentation. The recommendation is therefore not fully justified by the evidence.

**Confidence Level:** High

---

## Claim 10

**Claim:**  For individual GitHub Copilot users, private code and prompts may be used for model training.

**Citation:**  None explicitly provided for this claim in the original response.

**Evidence Passage (from GitHub Copilot docs):**  For Individual users: "Your code snippets, prompts, code completions, and generated code may be used to train GitHub Copilot models, subject to your settings or unless you opt out."

**Context:**  The claim is factually accurate per GitHub's documentation, which explicitly states that Individual users' code may be used for training. However, the original response does not provide a citation for this specific claim. The claim appears implied by the contrast with Claim 3 (Enterprise exclusion) but is not directly cited.

**Rubric Scoring:**

| Dimension | Score | Justification |
|---|---:|---|
| Entailment | 2/2 | The source supports the claim: Individual users' data may be used for training. |
| Completeness | 2/2 | The claim accurately captures the policy for Individual subscriptions. |
| Relevance | 2/2 | The claim is directly about training use policy. |
| Evidence Quality | 2/2 | Official GitHub documentation. |
| Citation Placement | 0/2 | No citation was provided in the original response for this claim. |

**Composite Score:** 6/10

**Verdict:** **Citation Missing**

**Rationale:**  While the factual content is accurate and supported by GitHub documentation, the original response does not provide an explicit citation for this claim. Per methodology, Citation Missing applies when a claim lacks a source reference, even if the claim is factually true. The response should have cited GitHub's documentation to support this statement.

**Ambiguities & Limitations:**  The claim contradicts Claim 1 (which stated "never" regardless of subscription type), revealing an internal inconsistency in the response that should have been resolved through clearer citation and wording.

**Confidence Level:** High

---

## Overall Verdict

**Final Evaluation Summary (10 of 10 claims finalized)**

### Verdict Distribution

| Verdict Category | Count | Claims |
|---|---:|---|
| Fully Supported | 2 | 3, 6 |
| Partially Supported | 2 | 5, 9 |
| Unsupported | 4 | 1, 2, 4, 7 |
| Citation Missing | 2 | 8, 10 |
| **TOTAL** | **10** | |

### Composite Scores

| Claim | Score | Verdict |
|---|---:|---|
| Claim 1 | 6/10 | Unsupported |
| Claim 2 | 6/10 | Unsupported |
| Claim 3 | 10/10 | Fully Supported |
| Claim 4 | 6/10 | Unsupported |
| Claim 5 | 8/10 | Partially Supported |
| Claim 6 | 10/10 | Fully Supported |
| Claim 7 | 6/10 | Unsupported |
| Claim 8 | 0/10 | Citation Missing |
| Claim 9 | 5/10 | Partially Supported |
| Claim 10 | 6/10 | Citation Missing |
| **Average (10 claims)** | **6.3/10** | |

### Key Findings

**Citation Failures Identified:**
1. **Overgeneralization (Claims 1, 7):** Universal claims ("never," "every") contradicted by subscription-tier distinctions and model-specific exceptions documented in the cited sources.
2. **Unsupported Universals (Claims 2, 4, 7):** Retention policies and ZDR coverage stated as absolute when documentation specifies exceptions, qualifications, and automatic expiration (e.g., Memory deleted after 28 days).
3. **Citation Missing (Claims 8, 10):** Claims lack supporting citations or rely on implied citations not explicitly provided in the response.
4. **Internal Contradiction (Claims 1 vs. 10):** Response claims Copilot "never" uses code for training universally, then implies individual users' code may be used—these are logically incompatible.
5. **Factually False + Uncited (Claim 8):** Cloud Agents claim contradicted by documentation; no citation provided.
6. **Interpretive Conclusion on False Premises (Claim 9):** Comparative recommendation depends on unsupported Claims 2, 7, and 8, resulting in flawed reasoning.

**Verified Accurate Claims:**
- Claim 3: GitHub Business/Enterprise data not used for training ✓
- Claim 6: Privacy Mode enabled by default for Cursor Enterprise ✓

**Pattern Analysis:**
This response demonstrates systematic failure when making universal claims about complex subscription-tier and model-specific policies. The AI model conflated Individual, Business, and Enterprise policies and oversimplified multi-factor retention rules. The response's comparative conclusion is built on false factual foundations.

### Methodology Notes

**Verdict Determination:** Verdicts assigned per [Citation Verification Methodology v1.0](../methodology.md). All 10 claims have been successfully verified and scored.

**Source Credibility:** All evaluated sources are official vendor documentation (GitHub, Cursor). Failure modes are not due to source quality but to misrepresentation or overgeneralization of source content.

**Status:** Case study evaluation COMPLETE for all 10 claims.

---

## Evaluation Conclusion

This case study successfully demonstrates multiple citation failure modes:
- ✓ Overgeneralization and unsupported universals (Claims 1, 4, 7)
- ✓ Internal contradiction between claims (Claims 1 and 10 conflict)
- ✓ Citation missing (Claims 8, 10)
- ✓ Factually false statements (Claims 2, 8)
- ✓ Interpretive conclusions on false premises (Claim 9)
- ✓ Product-surface confusion (Individual vs. Enterprise tiers conflated)

**Average Composite Score:** 6.3/10 (10 claims)  
**Overall Assessment:** The response contains partially accurate content mixed with significant factual errors and citation failures. It demonstrates poor handling of subscription-tier distinctions and universal claims that exceed source documentation. The comparative recommendation is not sufficiently justified by the evidence and relies on false factual premises.

