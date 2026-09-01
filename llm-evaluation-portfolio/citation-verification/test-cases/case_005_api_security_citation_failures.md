# Citation Verification Case Study 005: API Security and Data Retention Claims

## Evaluation Metadata

**Case Study ID:** case_005_api_security_citation_failures  
**Evaluation Date:** 2026-09-01  
**Evaluation Framework:** Citation Verification Rubric v1.0 & Methodology v1.0  
**Response Type:** AI-Generated Comparative Privacy Response with Citations  
**Subject Domain:** API Data Retention, Model Training, and Zero Data Retention (ZDR)  
**Evaluator Notes:** This response cites official documentation for OpenAI and Anthropic, but several claims overstate what the cited pages actually say. The main issues are broad generalizations, unsupported universals, and a mismatch between the specific wording of the source and the claim made by the AI. Evaluation therefore focuses on precise claim-to-source alignment rather than the general plausibility of the broader topic.

---

## Original Query

"Compare the data retention and privacy practices of OpenAI's API and Anthropic's Claude API. How long is customer data retained, is customer data used for model training, and are Zero Data Retention options available?"

---

## AI-Generated Response

OpenAI's API and Anthropic's Claude API both provide enterprise-focused data controls, but they differ significantly in retention policies and Zero Data Retention options.

## OpenAI API

- **Standard retention:** OpenAI retains all API customer prompts and responses indefinitely unless the customer manually deletes them.

  Citation: https://platform.openai.com/docs/models/default-usage-policies-by-endpoint

- **Model training:** Data submitted through the OpenAI API is not used to train OpenAI models by default unless the customer explicitly opts in.

  Citation: https://platform.openai.com/docs/models/default-usage-policies-by-endpoint

- **Zero Data Retention:** Eligible OpenAI API customers can apply for Zero Data Retention, which excludes customer content from abuse-monitoring logs.

  Citation: https://platform.openai.com/docs/models/default-usage-policies-by-endpoint

- **Universal coverage:** Once Zero Data Retention is enabled, no OpenAI API endpoint or feature can store customer data.

  Citation: https://platform.openai.com/docs/models/default-usage-policies-by-endpoint

## Anthropic Claude API

- **Standard retention:** Anthropic automatically deletes API inputs and outputs within 30 days, subject to certain exceptions.

  Citation: https://privacy.claude.com/en/articles/7996866-how-long-do-you-store-my-organization-s-data

- **Model training:** Anthropic never uses customer API data for model training under any circumstances.

  Citation: https://platform.claude.com/docs/en/manage-claude/api-and-data-retention

- **Zero Data Retention:** Anthropic offers Zero Data Retention arrangements under which eligible customer prompts and responses are not stored at rest after the API response is returned.

  Citation: https://platform.claude.com/docs/en/manage-claude/api-and-data-retention

- **Covered models:** All Anthropic models support Zero Data Retention without exception.

  Citation: https://platform.claude.com/docs/en/manage-claude/api-and-data-retention

## Comparison

| Area | OpenAI API | Anthropic Claude API |
|---|---|---|
| Standard retention | Indefinite by default | Up to 30 days |
| Used for model training | No, unless opt-in | Never under any circumstances |
| Zero Data Retention | Available to eligible customers | Available through special arrangements |
| ZDR coverage | All API endpoints and features | All models without exception |

## Conclusion

Both providers offer strong privacy protections for enterprise API customers. OpenAI provides Zero Data Retention controls for eligible customers, while Anthropic provides Zero Data Retention arrangements for qualifying organizations. However, OpenAI permanently retains API data by default, whereas Anthropic deletes all API data within 30 days.

For organizations with strict privacy requirements, Anthropic may therefore provide more comprehensive Zero Data Retention protection than OpenAI.

---

## Claim-by-Claim Evaluation

---

## Claim 1

**Claim:**  OpenAI retains all API customer prompts and responses indefinitely unless the customer manually deletes them.

**Citation:**  https://platform.openai.com/docs/models/default-usage-policies-by-endpoint

**Evidence Passage (from OpenAI docs):**  "Abuse monitoring logs may contain certain customer content... By default, abuse monitoring logs are generated for all API feature usage and retained for up to 30 days, unless longer retention is required by law..." and "As of March 1, 2023, data sent to the OpenAI API is not used to train or improve OpenAI models (unless you explicitly opt in to share data with us)."

**Context:**  The actual documentation describes a 30-day abuse-monitoring default, not indefinite retention for all API prompts and responses. It also distinguishes between abuse-monitoring logs, application state, and endpoint-specific retention rules. The claim appears to collapse several different retention categories into one blanket statement.

**Rubric Scoring:**

| Dimension | Score | Justification |
|---|---:|---|
| Entailment | 0/2 | The cited documentation does not support indefinite retention for all customer prompts and responses. It explicitly states a 30-day default for abuse-monitoring logs. |
| Completeness | 1/2 | The claim is too broad and general; the evidence explains a default retention model with important exceptions and category differences. |
| Relevance | 2/2 | The passage is about data retention and therefore relevant to the claim. |
| Evidence Quality | 2/2 | The source is an official OpenAI policy page and is relevant to the subject. |
| Citation Placement | 2/2 | The citation is placed appropriately, but the claim exceeds what the source actually says. |

**Composite Score:** 7/10

**Verdict:** **Unsupported**

**Rationale:**  The claim is not supported by the cited OpenAI policy language. The official docs describe default abuse-monitoring retention of 30 days, not indefinite retention for all prompts and responses. The statement is therefore an overgeneralization rather than a faithful reading of the source.

**Ambiguities & Limitations:**  The docs also allow for application state, endpoint-specific storage, and legal exceptions, so the broader claim is not precise even if some data may be retained longer under certain circumstances.

**Confidence Level:** High

---

## Claim 2

**Claim:**  Data submitted through the OpenAI API is not used to train OpenAI models by default unless the customer explicitly opts in.

**Citation:**  https://platform.openai.com/docs/models/default-usage-policies-by-endpoint

**Evidence Passage (from OpenAI docs):**  "As of March 1, 2023, data sent to the OpenAI API is not used to train or improve OpenAI models (unless you explicitly opt in to share data with us)."

**Context:**  This statement matches the official documentation almost exactly. The cited policy is not merely related; it directly states the default training policy.

**Rubric Scoring:**

| Dimension | Score | Justification |
|---|---:|---|
| Entailment | 2/2 | The claim matches the source wording closely and preserves the default-vs-opt-in distinction. |
| Completeness | 2/2 | The claim captures the default rule and the opt-in exception. |
| Relevance | 2/2 | The source directly addresses training use of API data. |
| Evidence Quality | 2/2 | Official documentation from OpenAI is high-quality source material for this issue. |
| Citation Placement | 2/2 | The citation is precise and directly anchors the claim to the policy. |

**Composite Score:** 10/10

**Verdict:** **Fully Supported**

**Rationale:**  The official documentation explicitly says API data is not used to train or improve models by default unless the customer opts in. The claim is a direct and accurate condensation of that rule.

**Ambiguities & Limitations:**  None material. The wording is accurate and consistent with the referenced policy.

**Confidence Level:** High

---

## Claim 3

**Claim:**  Eligible OpenAI API customers can apply for Zero Data Retention, which excludes customer content from abuse-monitoring logs.

**Citation:**  https://platform.openai.com/docs/models/default-usage-policies-by-endpoint

**Evidence Passage (from OpenAI docs):**  "Eligible customers may have their customer content excluded from these abuse monitoring logs... by getting approved for the Zero Data Retention or Modified Abuse Monitoring controls."

**Context:**  This claim is directly supported by the docs. The language describes ZDR as a controlled option for eligible customers and notes that it excludes customer content from abuse-monitoring logs.

**Rubric Scoring:**

| Dimension | Score | Justification |
|---|---:|---|
| Entailment | 2/2 | The source explicitly states that eligible customers can be approved for ZDR and that it excludes content from abuse-monitoring logs. |
| Completeness | 2/2 | The claim captures the essential rule without adding unsupported qualifiers. |
| Relevance | 2/2 | The source is specifically about data-retention controls and abuse monitoring. |
| Evidence Quality | 2/2 | Official documentation is appropriate and reliable for this policy question. |
| Citation Placement | 2/2 | The citation aligns closely with the claim. |

**Composite Score:** 10/10

**Verdict:** **Fully Supported**

**Rationale:**  The citation clearly supports the existence of OpenAI ZDR for eligible customers and confirms that it excludes customer content from abuse-monitoring logs.

**Ambiguities & Limitations:**  The docs also note limits and endpoint exceptions, so ZDR is not a blanket universal guarantee for every feature. But that nuance does not invalidate the claim as stated.

**Confidence Level:** High

---

## Claim 4

**Claim:**  Once Zero Data Retention is enabled, no OpenAI API endpoint or feature can store customer data.

**Citation:**  https://platform.openai.com/docs/models/default-usage-policies-by-endpoint

**Evidence Passage (from OpenAI docs):**  "Besides those specific behavior changes, the endpoints and capabilities listed as No for Zero Data Retention Eligible in the table below may still store application state, even if Zero Data Retention is enabled."

**Context:**  This is a direct contradiction of the AI claim. The doc explicitly states that some endpoints and capabilities may still store application state even with ZDR enabled, and that ZDR is limited to abuse-monitoring exclusions rather than total prohibition on all storage.

**Rubric Scoring:**

| Dimension | Score | Justification |
|---|---:|---|
| Entailment | 0/2 | The source explicitly says some ZDR-eligible endpoints or features may still store application state. |
| Completeness | 0/2 | The AI claim is a universal statement that the source explicitly rejects. |
| Relevance | 2/2 | The source is directly about ZDR and endpoint storage behavior. |
| Evidence Quality | 2/2 | The official docs are authoritative on the exact limitations of ZDR. |
| Citation Placement | 2/2 | The citation is relevant but fails to support the universal claim. |

**Composite Score:** 6/10

**Verdict:** **Unsupported**

**Rationale:**  The cited source specifically warns that ZDR does not universally prevent storage in all endpoints or features; some may still retain application state. The AI claim is therefore not supported and is contradicted by the source language.

**Ambiguities & Limitations:**  None material. The contradiction is explicit.

**Confidence Level:** High

---

## Claim 5

**Claim:**  Anthropic automatically deletes API inputs and outputs within 30 days, subject to certain exceptions.

**Citation:**  https://privacy.claude.com/en/articles/7996866-how-long-do-you-store-my-organization-s-data

**Evidence Passage (from Anthropic privacy docs):**  "For Anthropic API users, we automatically delete inputs and outputs on our backend within 30 days of receipt or generation, except: ... when you and we have agreed otherwise ... or if we need to retain them for longer to enforce our Usage Policy ..."

**Context:**  This matches the response closely. Anthropic's policy states a default 30-day deletion period, with named exceptions such as agreement-based retention, policy enforcement, and legal requirements.

**Rubric Scoring:**

| Dimension | Score | Justification |
|---|---:|---|
| Entailment | 2/2 | The source directly states the 30-day deletion timeframe and exception logic. |
| Completeness | 2/2 | The claim accurately captures the default rule and the existence of exceptions. |
| Relevance | 2/2 | The policy page is directly about retention for organization data. |
| Evidence Quality | 2/2 | The policy is official and directly relevant. |
| Citation Placement | 2/2 | The citation is well aligned with the claim. |

**Composite Score:** 10/10

**Verdict:** **Fully Supported**

**Rationale:**  The policy text states the default 30-day deletion rule and explicitly lists exceptions. The claim is accurate and precise.

**Ambiguities & Limitations:**  The statement says "subject to certain exceptions" which matches the policy, and those exceptions are clearly identified.

**Confidence Level:** High

---

## Claim 6

**Claim:**  Anthropic never uses customer API data for model training under any circumstances.

**Citation:**  https://platform.claude.com/docs/en/manage-claude/api-and-data-retention

**Evidence Passage (from Anthropic docs):**  "Retained data is never used for model training without your express permission."

**Context:**  The documentation supports a more careful claim: Anthropic does not use retained data for training without express permission. The AI response converts this into an absolute universal statement, which is stronger than the evidence.

**Rubric Scoring:**

| Dimension | Score | Justification |
|---|---:|---|
| Entailment | 1/2 | The source supports the idea that training requires express permission, but not the absolute wording "under any circumstances." |
| Completeness | 1/2 | The source says "without your express permission" rather than "never under any circumstances." |
| Relevance | 2/2 | The retention page is exactly about data usage and model training. |
| Evidence Quality | 2/2 | Official documentation, directly relevant. |
| Citation Placement | 2/2 | The citation matches the topic but not the absolute phrasing used in the claim. |

**Composite Score:** 8/10

**Verdict:** **Partially Supported**

**Rationale:**  The broad principle is correct: data is not used for training without express permission. But the claim states a universal rule that exceeds the source wording. The evidence supports a narrower statement, not the absolute statement made by the model.

**Ambiguities & Limitations:**  The official wording is permission-based, not absolute. This is a meaningful precision issue in the claim.

**Confidence Level:** High

---

## Claim 7

**Claim:**  Anthropic offers Zero Data Retention arrangements under which eligible customer prompts and responses are not stored at rest after the API response is returned.

**Citation:**  https://platform.claude.com/docs/en/manage-claude/api-and-data-retention

**Evidence Passage (from Anthropic docs):**  "Under a ZDR arrangement, Anthropic does not store customer prompts or responses at rest after the API response is returned."

**Context:**  This is a direct match to the docs. The claim is accurate and captures the essential ZDR promise without overreaching beyond the arrangement.

**Rubric Scoring:**

| Dimension | Score | Justification |
|---|---:|---|
| Entailment | 2/2 | The claim mirrors the source language closely. |
| Completeness | 2/2 | The claim captures the feature's core effect: no prompt/response storage at rest under ZDR. |
| Relevance | 2/2 | The source is dedicated to ZDR policy. |
| Evidence Quality | 2/2 | Official documentation is highly reliable. |
| Citation Placement | 2/2 | The cited page directly supports the claim. |

**Composite Score:** 10/10

**Verdict:** **Fully Supported**

**Rationale:**  The evidence directly states that under a ZDR arrangement, prompts and responses are not stored at rest after the API response is returned. This claim is substantially faithful to the source.

**Ambiguities & Limitations:**  The source also notes that ZDR has feature and model exceptions. The claim is valid for the described arrangement but not as a universal promise across all Anthropic features or models.

**Confidence Level:** High

---

## Claim 8

**Claim:**  All Anthropic models support Zero Data Retention without exception.

**Citation:**  https://platform.claude.com/docs/en/manage-claude/api-and-data-retention

**Evidence Passage (from Anthropic docs):**  "Claude Fable 5.1, Claude Mythos 5.1, Claude Fable 5, and Claude Mythos 5 are designated Covered Models ... and require 30-day data retention; ZDR is therefore not available for any of them unless expressly authorized by Anthropic."

**Context:**  This claim is directly contradicted by the official documentation. Anthropic explicitly states that several models are not available under ZDR and require 30-day retention.

**Rubric Scoring:**

| Dimension | Score | Justification |
|---|---:|---|
| Entailment | 0/2 | The source says ZDR is not available for Covered Models unless specially authorized. |
| Completeness | 0/2 | The claim states a universal "all models" rule that the source denies. |
| Relevance | 2/2 | The source is specifically about model retention and ZDR eligibility. |
| Evidence Quality | 2/2 | The doc is official and directly applicable. |
| Citation Placement | 2/2 | The citation is on point, but the claim is contradicted by the text. |

**Composite Score:** 6/10

**Verdict:** **Unsupported**

**Rationale:**  The source explicitly says some models are not ZDR-eligible and require 30-day retention. The claim that all Anthropic models support ZDR without exception is contradicted by the official policy.

**Ambiguities & Limitations:**  None. The contradiction is explicit in the source.

**Confidence Level:** High

---

## Claim 9

**Claim:**  OpenAI retains API data indefinitely by default, while Anthropic deletes all API data within 30 days.

**Citation:**  OpenAI docs + Anthropic privacy docs (cited in the response)

**Evidence Passage:**  OpenAI docs state abuse-monitoring logs are retained for up to 30 days by default, while Anthropic docs state that API inputs and outputs are automatically deleted within 30 days of receipt or generation, except for explicit exceptions.

**Context:**  The broad comparison is directionally correct in the sense that OpenAI and Anthropic both rely on a default 30-day retention window for their standard abuse-monitoring or API logs, but the AI response incorrectly states OpenAI retains all prompts and responses indefinitely by default. That overstatement makes the comparison inaccurate.

**Rubric Scoring:**

| Dimension | Score | Justification |
|---|---:|---|
| Entailment | 1/2 | The claim partially matches the Anthropic side but incorrectly overstates the OpenAI default. |
| Completeness | 1/2 | The OpenAI default is not indefinite for all customer content; the data model is more nuanced than the claim suggests. |
| Relevance | 2/2 | The comparison is directly relevant to the query. |
| Evidence Quality | 2/2 | Both source categories are official and relevant. |
| Citation Placement | 2/2 | The citations are in the right topic area even though the claim is imprecise. |

**Composite Score:** 8/10

**Verdict:** **Partially Supported**

**Rationale:**  The broad comparison is directionally close to the actual policy landscape, but the OpenAI half is overstated because the official docs do not say all prompts/responses are retained indefinitely. They say abuse-monitoring logs are retained by default for up to 30 days.

**Ambiguities & Limitations:**  The response blurs the distinction between retention logs, application state, and endpoint-specific behavior. This makes the comparison too absolute.

**Confidence Level:** High

---

## Claim 10

**Claim:**  Anthropic may therefore provide more comprehensive Zero Data Retention protection than OpenAI.

**Citation:**  OpenAI ZDR doc + Anthropic ZDR doc

**Evidence Passage:**  OpenAI docs: ZDR excludes customer content from abuse-monitoring logs, but some endpoints and capabilities may still retain application state. Anthropic docs: under ZDR, prompts and responses are not stored at rest after the API response is returned. 

**Context:**  This is a comparative conclusion, not a direct statement from either source page. The evidence supports a weaker conclusion: both providers offer some form of ZDR, but the exact scope differs by organization, feature, and model. The claim that Anthropic is inherently "more comprehensive" is not directly proven by the cited docs.

**Rubric Scoring:**

| Dimension | Score | Justification |
|---|---:|---|
| Entailment | 1/2 | There is some basis for claiming differences in ZDR scope, but the conclusion is stronger than what the docs support. |
| Completeness | 1/2 | The claim ignores the fact that OpenAI ZDR is also available to eligible customers and has feature-level limitations. |
| Relevance | 2/2 | The comparison is relevant to the user question. |
| Evidence Quality | 1/2 | The conclusion is derived from mixed operational details and is not directly stated in the sources. |
| Citation Placement | 2/2 | The citations are in the relevant section, but the conclusion is not directly supported by the source wording. |

**Composite Score:** 7/10

**Verdict:** **Partially Supported**

**Rationale:**  The claim is not obviously false, but it is not directly established by the provided evidence. The docs show both providers have ZDR options with specific limitations, but they do not clearly support a general conclusion that Anthropic is always more comprehensive in practice.

**Ambiguities & Limitations:**  ZDR scope varies by feature, organization, and model for both providers. The conclusion relies on an interpretation rather than a direct source statement.

**Confidence Level:** Moderate

---

## Overall Verdict

**Final assessment:** The response contains several materially important citation failures.

- It is correct on the general existence of OpenAI ZDR and Anthropic ZDR, and on the basic training-use rule for OpenAI and the basic 30-day retention rule for Anthropic.
- It is not correct when it converts those policies into universal or indefinite claims, especially around OpenAI's default retention and the claim that no OpenAI endpoint or feature can ever store customer data under ZDR.
- It also overstates Anthropic's training and ZDR model coverage by making absolute statements that are not directly supported by the cited policy documentation.

### Summary of verdicts

**Fully Supported: 4**

**Partially Supported: 3**

**Unsupported: 3**

**Citation Missing: 0**

### Average composite score

**Average score across 10 claims: 8.2/10**

**Interpretation:**  This is a mixed but weakly supported response. A few claims are well-grounded, but the response as a whole is weakened by overgeneralization, unsupported universals, and scope mismatches between the claim wording and the cited policy language.

---

## Evaluation Conclusion

This case is a useful illustration of a common citation failure pattern: the model includes official-looking references, but it does not always match the actual scope of the documentation. The strongest claims align with the policy language. The weak claims fail because they shift from a documented policy into a broader, more absolute version that the source does not say.

The core methodological lesson is that citation presence alone is not enough. In this case, the source itself limits the claim in several important ways, and the response silently expands those limits into broader statements about all data, all endpoints, and all models.