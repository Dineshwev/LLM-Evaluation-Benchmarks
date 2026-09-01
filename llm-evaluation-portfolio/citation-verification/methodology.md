# Citation Verification Methodology

**Version 1.0** — Independent Portfolio Evaluation Framework

---

## Overview

This methodology document describes the systematic process for evaluating whether citations provided in AI-generated responses actually support the claims they purport to validate. The evaluation focuses on **claim-to-source alignment** rather than universal truth, as detailed in Section 11.

This document provides step-by-step procedures, decision-making principles, and handling rules for common evaluation scenarios.

---

## Scope of Evaluation

### **Critical Distinction: Source Support vs. Universal Truth**

This evaluation assesses **whether the cited source supports the claim**, not whether the claim is universally true according to external knowledge or consensus.

**Important Principle:**
- **We evaluate:** Does the cited source provide evidence that supports the claim as stated?
- **We do NOT evaluate:** Is the claim actually true according to my knowledge, current science, or expert consensus?

**Implications:**

1. **Never supplement with outside knowledge.** Base verdicts solely on the provided source.

2. **Evaluate the source, not reality.** If a source makes an unsupported or incorrect claim, and that source is cited, the verdict reflects whether the source supports the AI's claim—not whether the claim is factually correct.

3. **If you know a source is wrong:** Document this in evaluator notes, but do not allow it to override the verdict. Example:
   - Claim: "The Earth is flat."
   - Citation: "FlatEarthSociety.org"
   - Evidence: "Our research shows the Earth is a flat plane..."
   - Verdict: Fully Supported (the source supports the claim, even though the claim is false)
   - Evaluator Note: "Source is not credible; claim is factually incorrect"

4. **If a source is missing or incomplete:** This affects the verdict (Citation Missing, Unsupported, or Insufficient Evidence), not the claim's truth.

---

## 10-Step Evaluation Process

### **Step 1: Select an AI-Generated Answer**

**Objective:** Identify the AI response to be evaluated.

**Procedure:**
1. Obtain a complete AI-generated response to a query or prompt
2. Confirm the response contains:
   - Multiple factual claims or assertions
   - Citations or source references
   - A combination of supported and potentially unsupported statements

**Documentation:**
- Record the query or prompt that generated the response
- Record the complete AI response verbatim
- Note the date/time of the interaction (if applicable)
- Record the AI system name and version (if known)

**Quality Check:**
- Ensure the response is substantial enough to yield meaningful evaluation
- Avoid single-sentence responses without multiple claims
- Prefer responses where citation claims are explicit and retrievable

**Example Source:**
```
Q: How does machine learning differ from traditional programming?

AI Response: Machine learning is a subset of artificial intelligence that enables 
systems to learn from data without being explicitly programmed (Smith, 2019). Unlike 
traditional programming, which relies on hard-coded rules, machine learning systems 
adjust their behavior based on patterns in training data. According to research from 
Stanford AI Index (2023), over 70% of enterprises have adopted some form of machine 
learning technology. This represents a fundamental shift in how software is developed 
and deployed.
```

---

### **Step 2: Split the Answer into Atomic Verifiable Claims**

**Objective:** Decompose the response into individual, discrete claims that can be independently verified.

**Procedure:**

1. **Identify claim boundaries:** Read through the response and mark sentences or sentence fragments that make distinct assertions
2. **Separate compound claims:** Split sentences containing multiple independent claims
3. **Isolate factual assertions:** Focus on claims that make empirical, factual, or causal statements
4. **Number each claim:** Assign a unique identifier to each atomic claim for tracking

**Claim Atomicity Rules:**

| Rule | Example | Result |
|------|---------|--------|
| **One subject + one predicate** | "ML adjusts behavior based on patterns" | 1 claim |
| **Multiple subjects or predicates** | "ML and AI are used in healthcare and finance" | Split into 2–4 claims |
| **Compound subjects with single assertion** | "Both X and Y are true" | Can be 1 claim if assertion is identical |
| **Conditional or hedged statements** | "ML may improve productivity in some cases" | 1 claim (includes hedging as part of claim) |
| **Quantitative + context** | "70% of enterprises adopted ML" | 1 claim (number + population + assertion) |

**Multi-Claim Sentence Handling:** See Section 8.

**Example Claim Segmentation:**

Original response (from Step 1 example):
```
Machine learning is a subset of artificial intelligence that enables systems to 
learn from data without being explicitly programmed (Smith, 2019). Unlike 
traditional programming, which relies on hard-coded rules, machine learning systems 
adjust their behavior based on patterns in training data. According to research from 
Stanford AI Index (2023), over 70% of enterprises have adopted some form of machine 
learning technology. This represents a fundamental shift in how software is developed 
and deployed.
```

Segmented claims:
1. **Claim 1:** Machine learning is a subset of artificial intelligence
2. **Claim 2:** ML enables systems to learn from data without being explicitly programmed
3. **Claim 3:** Traditional programming relies on hard-coded rules
4. **Claim 4:** ML systems adjust behavior based on patterns in training data
5. **Claim 5:** Over 70% of enterprises have adopted machine learning technology (per Stanford AI Index 2023)
6. **Claim 6:** ML adoption represents a fundamental shift in software development

---

### **Step 3: Identify the Citation Associated with Each Claim**

**Objective:** Extract and record the source cited for each claim.

**Procedure:**

1. **Scan for citation markers:** Look for explicit citations near each claim:
   - Parenthetical citations: (Author, Year)
   - Footnotes or endnotes: [1], [Ref. 2]
   - Inline references: "According to [Source]..."
   - URL or direct links
   - Generic references: "research shows," "studies indicate"

2. **Match citations to claims:** Determine which claim each citation is intended to support
   - If a citation immediately follows a claim, it supports that claim
   - If a citation appears at the end of a paragraph, it may support multiple claims in that paragraph
   - If a citation is distant from a claim, note the ambiguity

3. **Record citation completeness:**
   - Complete: Author, title, year, and/or URL
   - Partial: Missing author, date, or URL
   - Absent: No citation provided

**Citation Recording Template:**

```
Claim 1: Machine learning is a subset of artificial intelligence
Citation: (Smith, 2019)
Citation Completeness: Partial (author and year provided; missing title or URL)
Citation Proximity: Immediate (citation directly follows claim)
Citation Clarity: Clear association
```

**Handling Ambiguous Citations:** See Section 9.

**Example Citation Association:**

From Step 1 response:
- **Claim 1:** ML is a subset of AI → Citation: **(Smith, 2019)**
- **Claim 2:** ML enables learning without explicit programming → Citation: **(Smith, 2019)** (same citation)
- **Claim 3:** Traditional programming uses hard-coded rules → Citation: **None provided**
- **Claim 4:** ML adjusts behavior based on patterns → Citation: **None provided**
- **Claim 5:** 70% enterprise adoption → Citation: **Stanford AI Index (2023)**
- **Claim 6:** Fundamental shift in software development → Citation: **None provided**

---

### **Step 4: Retrieve or Inspect the Cited Source**

**Objective:** Obtain access to the actual source material to verify claims.

**Procedure:**

1. **Locate the source:**
   - If a URL is provided, access the webpage or document
   - If author/year provided, search for the publication
   - If a generic reference is given, document that source retrieval is not possible

2. **Verify source authenticity:**
   - Confirm the source exists and is accessible
   - Check for obvious signs of fabrication or misattribution
   - Note source type (peer-reviewed, news, blog, corporate report, etc.)

3. **Collect source metadata:**
   - Author(s)
   - Publication date
   - Source type and authority
   - URL or DOI (if applicable)
   - Publisher or organization

4. **Document retrieval status:**
   - Retrieved successfully
   - Partially accessible (abstract only, paywalled content)
   - Not found or inaccessible
   - Too vague to retrieve

**Source Retrieval Documentation:**

```
Citation: (Smith, 2019)
Retrieval Status: Successfully retrieved
Source Full Information: 
  - Title: "Machine Learning Fundamentals"
  - Author: John Smith, Jane Doe
  - Publication: Journal of AI Research, Vol. 45, No. 3
  - Year: 2019
  - DOI: 10.1234/jair.2019
  - Access: Publicly available online
  
Citation: Stanford AI Index (2023)
Retrieval Status: Partially accessible
Source Full Information:
  - Title: "AI Index Report 2023"
  - Author: Stanford Human-Centered Artificial Intelligence
  - Publication: Annual Report
  - Year: 2023
  - URL: https://aiindex.stanford.edu/report/
  - Access: Executive summary available; full report requires registration
```

**Handling Unavailable Sources:**

The verdict depends on the retrievability of the citation itself:

- **Citation cannot be identified or located** (e.g., generic "studies show" with no specific source) → **Citation Missing**
  - The AI provided no verifiable citation reference
  - Evaluator cannot determine whether a source exists

- **Citation is identifiable and source is found, but does not support the claim** → **Unsupported**
  - The citation is specific enough to locate (e.g., Author, Year)
  - The source has been accessed and reviewed
  - The source does not contain evidence for the claim

- **Citation is identifiable but source cannot be accessed** (paywalled, archived, no longer available) → **Note the retrieval limitation**
  - Document the retrieval attempt and the access barrier
  - Provide a verdict based on other available evidence:
    - If citation metadata (title, abstract, etc.) can be reviewed but full text cannot be accessed: Assign **Insufficient Evidence** if preliminary information suggests relevance, or **Unsupported** if preliminary information suggests non-relevance
    - If no information about the source can be obtained: Assign **Citation Missing** (cannot verify citation)
  - Record in evaluator notes that source access was limited

- **Citation references a source found but evidence passage cannot be located within the source** → **Unsupported**
  - The source exists and is accessible
  - Evaluator has searched the source and found no relevant passage
  - Verdict reflects that no evidence was found, not that the source is inaccessible

---

### **Step 5: Locate the Relevant Evidence Passage**

**Objective:** Find the specific text, data, or statement in the source that addresses the claim.

**Procedure:**

1. **Search within the source:**
   - Use Ctrl+F or equivalent to search for key terms from the claim
   - Read sections likely to address the claim topic
   - Note the page number, section, or URL location

2. **Identify the evidence passage:**
   - Extract the exact text that supports or contradicts the claim
   - Include surrounding context (1–2 sentences before and after)
   - Record whether evidence is a direct quote, paraphrase, or data point

3. **Assess evidence relevance:**
   - Confirm the passage addresses the claim's core assertion
   - Note if the passage is tangential or tangentially related
   - Identify any qualifications or caveats in the source

4. **Document the evidence:**

```
Claim 1: Machine learning is a subset of artificial intelligence

Source: Smith (2019), "Machine Learning Fundamentals"
Evidence Location: Page 3, Section 1.1

Evidence Passage (Direct Quote):
"Machine learning represents a specialized domain within the broader field of 
artificial intelligence, focusing on systems that improve through experience and 
data exposure rather than explicit instruction."

Context:
[Preceding sentence] "AI encompasses multiple approaches to creating intelligent systems."
[Following sentence] "This distinction is important for understanding the scope and 
limitations of each approach."

Evidence Assessment: 
- Directly addresses the claim
- Confirms ML is part of AI
- Uses slightly different language but same concept
```

**If No Evidence Passage Found:**
- Note the absence explicitly
- Mark as: Evidence not located
- Prepare for verdict: **Unsupported** or **Insufficient Evidence**

---

### **Step 6: Compare the Evidence Against the Exact Claim**

**Objective:** Assess how well the evidence passage aligns with the specific claim.

**Procedure:**

1. **State the claim precisely:**
   - Record the exact claim text
   - Note any qualifications (e.g., "may," "tends to," "studies suggest")
   - Identify the core assertion

2. **State the evidence precisely:**
   - Record the exact evidence text
   - Note any qualifications in the source
   - Identify what the evidence asserts

3. **Perform explicit comparison:**
   - Does the evidence directly state the claim? (Yes/No)
   - Does the evidence logically entail the claim? (Yes/No)
   - Does the evidence address all components of the claim? (Yes/No/Partially)
   - Does the evidence contradict the claim? (Yes/No)
   - Is the evidence relevant but insufficient? (Yes/No)

4. **Document alignment:**

```
CLAIM: "Machine learning is a subset of artificial intelligence"

EVIDENCE: "Machine learning represents a specialized domain within the broader 
field of artificial intelligence"

COMPARISON ANALYSIS:

| Dimension | Assessment |
|-----------|-----------|
| **Direct Statement** | Not identical wording; equivalent concept |
| **Logical Entailment** | Evidence entails the claim |
| **Component Coverage** | Claim has 2 components (ML, subset of AI); evidence covers both |
| **Contradiction** | No contradiction; evidence supports claim |
| **Relevance** | Highly relevant; directly addresses relationship between ML and AI |
| **Sufficiency** | Evidence is sufficient for the claim |

CONCLUSION: Evidence aligns with claim.
```

**Comparison Rules:**

- **Exact match not required:** Paraphrasing and equivalent wording are acceptable
- **Must address core assertion:** Tangential evidence doesn't suffice
- **Qualifications matter:** If evidence is hedged ("may," "tends to"), note this
- **Multi-part claims:** All parts must be addressed (or note partial support)

---

### **Step 7: Apply the Evaluation Rubric**

**Objective:** Systematically assess the claim-citation pair using the structured rubric.

**Procedure:**

1. **Answer the core evaluation questions:**
   - Does the cited source address the claim?
   - Does the evidence actually support the full claim?
   - Is only part of the claim supported?
   - Does the source contradict the claim?
   - Is the citation relevant but insufficient?
   - Is a citation missing?

2. **Score each evaluation dimension:**

   | Dimension | Rating | Justification |
   |-----------|--------|---------------|
   | **Entailment** | 2/1/0 | Does evidence logically support the claim? |
   | **Completeness** | 2/1/0 | Are all claim components addressed? |
   | **Relevance** | 2/1/0 | Is the source topically appropriate? |
   | **Evidence Quality** | 2/1/0 | Is the source credible and current? |
   | **Citation Placement & Traceability** | 2/1/0 | Is the citation positioned and traceable; can the source be retrieved? |

3. **Calculate composite score:**
   - Sum all dimension scores (range: 0–10)
   - Note the score as supporting evidence, not deterministic

**Example Rubric Application:**

```
Claim 1: Machine learning is a subset of artificial intelligence
Citation: Smith (2019)

DIMENSION SCORING:

Entailment: 2/2
  Evidence directly states ML is within AI; strong logical connection

Completeness: 2/2
  Both components of claim (ML, subset, AI) are addressed

Relevance: 2/2
  Source is focused on ML-AI relationship

Evidence Quality: 2/2
  Peer-reviewed academic source, 2019 publication, reputable journal

Citation Placement & Traceability: 2/2
  Citation is positioned immediately after the claim; complete (author, year); source is readily retrievable

COMPOSITE SCORE: 10/10

Verdict Alignment: Score suggests "Fully Supported"
```

---

### **Step 8: Assign a Verdict**

**Objective:** Select the appropriate verdict category based on evidence analysis.

**Procedure:**

1. **Review composite score:** Use as supporting evidence
2. **Apply decision rules:** Consult the rubric's decision rules for borderline cases
3. **Consider special circumstances:**
   - Source recency (is the source outdated?)
   - Source credibility (is the source from an authoritative source?)
   - Claim hedging (does the claim include qualifications?)
   - Context (is important context missing?)

4. **Select verdict from six categories:**
   - **Fully Supported** — Evidence directly supports the entire claim
   - **Partially Supported** — Evidence supports part of the claim
   - **Unsupported** — Source doesn't address the claim
   - **Contradicted** — Source contradicts the claim
   - **Citation Missing** — No citation provided or citation is non-retrievable
   - **Insufficient Evidence** — Source is relevant but too vague or limited

5. **Document the verdict:**

```
VERDICT: Fully Supported ✓

Rationale:
The source explicitly states that machine learning is a specialized domain within 
artificial intelligence. The evidence directly addresses the claim with clear, 
unambiguous language. All components of the claim are covered, and no qualifications 
or caveats in the source limit the support.

Confidence: High
```

**Verdict Selection Logic:**
- If score 9–10 and no contradictions → **Fully Supported**
- If score 7–8 or partial coverage → **Partially Supported**
- If score 5–6 and ambiguous → **Partially Supported** or **Insufficient Evidence**
- If source is relevant but incomplete → **Insufficient Evidence**
- If source is unrelated → **Unsupported**
- If source contradicts → **Contradicted**
- If no source provided or unretrievable → **Citation Missing**

---

### **Step 9: Document the Rationale**

**Objective:** Create a clear, transparent record of the evaluation reasoning.

**Procedure:**

1. **Write a brief summary (2–4 sentences):**
   - Restate the claim
   - Note the source
   - Summarize the evidence
   - State the verdict and key reason

2. **Record supporting evidence:**
   - Direct quotes from the source
   - Key data points or statistics
   - Relevant context

3. **Note decision points:**
   - Which evaluation questions were decisive?
   - Were any dimension scores particularly influential?
   - Did any special circumstances affect the verdict?

4. **Use standard documentation format:**

```
---

## Evaluation: Claim 1

**Claim:** Machine learning is a subset of artificial intelligence

**Citation:** Smith (2019), "Machine Learning Fundamentals"

**Evidence Passage:**
"Machine learning represents a specialized domain within the broader field of 
artificial intelligence, focusing on systems that improve through experience..."

**Verdict:** Fully Supported ✓

**Rationale:**
Smith (2019) explicitly positions machine learning as a domain within artificial 
intelligence. The source directly confirms the claim with clear, unambiguous language. 
The definition provided addresses all aspects of the claim (ML exists, AI is broader, 
ML is a subset). No hedging or qualifications limit the support.

**Composite Score:** 10/10
- Entailment (2/2): Direct, unambiguous
- Completeness (2/2): All components addressed
- Relevance (2/2): Directly focused
- Evidence Quality (2/2): Peer-reviewed academic source
- Citation Placement (2/2): Complete, retrievable citation

---
```

---

### **Step 10: Record Ambiguity and Limitations**

**Objective:** Document any evaluation challenges, uncertainties, or contextual factors.

**Procedure:**

1. **Identify sources of ambiguity:**
   - Unclear claim wording (does the claim have multiple interpretations?)
   - Vague citation (could the citation refer to multiple sources?)
   - Context-dependent meaning (does meaning depend on external information?)
   - Source ambiguity (does the source address the claim but use different terminology?)

2. **Assess confidence level:**
   - **High:** Clear evidence, unambiguous verdict
   - **Moderate:** Some ambiguity but verdict is reasonably supported
   - **Low:** Significant ambiguity; multiple verdicts could be justified

3. **Record limitations:**
   - Source retrieval issues (partial access, paywalled)
   - Currency issues (source is outdated)
   - Evaluator knowledge gaps (unfamiliar with technical terminology)
   - Missing context (important background information unavailable)

4. **Document findings:**

```
**Ambiguities & Limitations:**

1. Source Ambiguity
   - The term "subset" is used in different ways in ML literature; Smith (2019) uses 
     it similarly to the AI response, so no misinterpretation detected.

2. Confidence Level: High
   - The claim is straightforward; the evidence is explicit; no competing 
     interpretations reasonably apply.

3. Limitations
   - The claim is basic definitional; it does not assess the depth or nuance of the 
     ML-AI relationship.
   - The source is academic but from 2019; terminology may have evolved slightly, 
     though the basic relationship remains valid.

4. Evaluator Notes
   - No alternative interpretations of this claim identified
   - Citation is complete and source is retrieved without difficulty
   - No external knowledge was required for this evaluation

**Re-evaluator Reproducibility: High**
Another evaluator following this methodology should reach the same verdict.
```

---

## Source Selection Principles

### **Principles for Selecting AI Responses to Evaluate**

1. **Diverse Query Types:**
   - Factual questions (e.g., "What is X?")
   - How-to or procedural questions (e.g., "How does X work?")
   - Comparative questions (e.g., "How does X differ from Y?")
   - Current event or recent development questions

2. **Variety of Domains:**
   - Technology and AI (software, algorithms, applications)
   - Science and research (biological, physical, social)
   - Current events and news
   - History and definitions

3. **Citation Density:**
   - Prefer responses with multiple claims (3+) and citations
   - Avoid single-claim responses or uncited claims
   - Seek responses that mix cited and uncited claims for variety

4. **Claim Diversity:**
   - Include definitional claims
   - Include quantitative claims (statistics, percentages)
   - Include causal claims ("X causes Y")
   - Include mixed-evidence responses (some claims well-supported, others weak)

5. **Source Retrievability:**
   - Prioritize responses with retrievable citations (published works, accessible URLs)
   - Note responses with non-retrievable or vague citations for evaluation
   - Avoid responses citing exclusively private or classified sources

---

## Claim Segmentation Principles

### **How to Break Responses Into Atomic Claims**

1. **One subject, one predicate per claim:**
   - "AI and ML are both subsets of computer science" → Split into 2 claims
   - "ML improves through data exposure" → 1 claim

2. **Compound assertions:**
   - "X is true and Y is true" → Can be 1 claim if both are asserted about the same subject
   - "X is true because Y is true" → 1 claim (causal)
   - "X is true; also, Z is true" → 2 claims if independent

3. **Quantitative specificity:**
   - "70% of enterprises use ML" → 1 claim (specific number + population + assertion)
   - "Most companies use ML" → 1 claim (less specific but same concept)

4. **Hedged or qualified claims:**
   - "ML tends to improve with more data" → 1 claim (includes hedging as part of assertion)
   - Include qualifications ("may," "could," "suggests") as part of the claim

5. **Avoid over-segmentation:**
   - "Machine learning systems learn from data" → 1 claim (even though multiple concepts)
   - Don't split into subject + verb + object separately
   - Keep closely related concepts together

---

## Evidence Comparison Rules

### **Standards for Comparing Evidence to Claims**

1. **Exact wording not required:**
   - Paraphrase counts if meaning is preserved
   - Synonymous language is acceptable
   - Different terminology is acceptable if semantics align

2. **Evidence must address core assertion:**
   - Tangential coverage insufficient
   - Related but distinct topics insufficient
   - Must directly support the specific claim

3. **Qualifications in evidence matter:**
   - If source says "may improve," claim cannot be "improves"
   - If source says "in some cases," generalized claim not fully supported
   - Hedging in source limits strength of support

4. **Completeness for multi-part claims:**
   - All components must be addressed for "Fully Supported"
   - Missing components → "Partially Supported"
   - Contradicted components → "Partially Supported" or "Contradicted"

5. **Evidence-to-claim direction:**
   - Evidence must support the direction of the claim
   - If claim is positive, evidence cannot be negative
   - If claim is specific, evidence can be general (broad supports specific)
   - If claim is general, evidence cannot be only specific (specific doesn't always support general)

---

## Handling Multi-Claim Sentences

### **When a Single Sentence Contains Multiple Claims**

**Scenario 1: Compound Subject, Single Predicate**

```
"Both machine learning and deep learning are subsets of artificial intelligence."

Segmentation:
- Claim A: Machine learning is a subset of AI
- Claim B: Deep learning is a subset of AI

Citation Association: Both claims share the same citation if one is provided.
```

**Scenario 2: Single Subject, Multiple Predicates**

```
"Machine learning enables systems to learn from data and adjust behavior without explicit programming."

Segmentation:
- Claim A: ML enables learning from data
- Claim B: ML enables behavior adjustment without explicit programming

Interpretation: These may be evaluated separately or as one claim depending on 
whether they require separate evidence or are aspects of the same concept.
```

**Scenario 3: Multiple Independent Assertions**

```
"Artificial intelligence has transformed healthcare (Smith, 2020), and neural networks 
are the primary mechanism (Johnson, 2021)."

Segmentation:
- Claim A: AI has transformed healthcare → Citation: Smith (2020)
- Claim B: Neural networks are primary mechanism → Citation: Johnson (2021)

Each claim evaluated independently with its specific citation.
```

**Decision Rule:**
- Split sentences into separate claims only if each component requires independent verification
- Keep related concepts together if they're aspects of a single assertion
- When in doubt, err toward more segmentation (more granular evaluation)

---

## Handling Partial Source Support

### **When a Citation Supports Only Part of a Claim**

**Scenario: Multi-Component Claim**

```
Claim: "Machine learning has revolutionized healthcare diagnostics and treatment planning."

Citation: Medical AI Research Review (2023)

Evidence found:
- Strong evidence for ML improving diagnostics
- No evidence for impact on treatment planning

Verdict: Partially Supported
Reasoning: Source supports diagnostics component but not treatment planning component.
```

**Scenario: Quantitative Claim with Different Metric**

```
Claim: "70% of hospitals have adopted AI-based diagnostic systems."

Citation: Healthcare Tech Survey 2023

Evidence: "63% of hospitals reported using some form of automated diagnostic support."

Verdict: Partially Supported
Reasoning: Source supports concept but with different percentage; exact statistic not verified.
```

**Scenario: Claim Stronger Than Source Evidence**

```
Claim: "Machine learning definitely improves student learning outcomes."

Citation: Educational Research Study 2022

Evidence: "Several studies suggest ML-based personalized learning may have positive effects 
in some contexts."

Verdict: Partially Supported
Reasoning: Source uses hedged language ("suggest," "may"); claim is too definitive.
```

**Decision Rules for Partial Support:**
1. Identify which components are supported
2. Identify which components lack support
3. Consider whether unsupported components are essential to the core claim
4. Assign "Partially Supported" if even one essential component lacks evidence
5. Use evaluator notes to clarify which parts are/aren't covered

---

## Handling Outdated Sources

### **When Citations Are From Older Sources**

**Recency Assessment:**

| Claim Type | Acceptable Age | Consideration |
|-----------|-----------------|---------------|
| **Definitional** (e.g., "ML is a subset of AI") | Indefinite | Definitions rarely change |
| **Historical fact** | Indefinite | Historical facts are stable |
| **Technology capability** | 2–5 years | Rapid advancement; recency matters |
| **Statistical/empirical** | <2 years | Data changes; old stats are unreliable |
| **Best practices** | 1–3 years | Practices evolve |
| **Current events** | <6 months | Current events change rapidly |

**Handling Outdated Sources:**

1. **For definitional or historical claims:**
   - Older sources acceptable
   - Verdict assignment unaffected by age
   - Note age in evaluator notes but don't downgrade verdict

2. **For technical or quantitative claims:**
   - Note if source is older than typical currency period
   - Consider whether the field has evolved significantly
   - Reduce "Evidence Quality" score if outdated
   - Assignment verdict may shift to "Insufficient Evidence" if recency is critical
   - Document recency concern

3. **For current events or recent developments:**
   - Strongly downgrade "Evidence Quality" score
   - Mark as "Insufficient Evidence" if source predates the development
   - Consider "Contradicted" if landscape has changed significantly

**Example:**

```
Claim: "Deep learning has recently become the dominant approach in natural language processing."

Citation: Deep Learning Review, 2015

Assessment:
- Source is 9 years old; claims about "recent" developments are problematic
- The landscape has changed substantially since 2015
- While the claim may be true, a 2015 source cannot establish "recent" developments

Verdict: Insufficient Evidence
Reasoning: Source is outdated for claims about recent developments. Current evidence 
(2023+) would be needed to verify current status.

Evidence Quality Score: 0/2 (outdated for this application)
```

---

## Reproducibility Considerations

### **Ensuring Others Can Replicate Your Evaluation**

1. **Document Everything:**
   - Record the exact claim text (verbatim)
   - Record the exact evidence text (verbatim)
   - Include page numbers or section identifiers
   - Note URLs or access methods for sources

2. **Minimize Subjective Interpretation:**
   - Explain why you segmented claims a particular way
   - Justify verdict choices with explicit criteria
   - Flag ambiguities and note how they were resolved
   - Separate factual assessment from subjective judgment

3. **Source Citation Standards:**
   - Provide enough information for another evaluator to retrieve the source
   - Use standard citation format (Author, Year)
   - Include URLs with access dates
   - Note if source requires authentication or subscription

4. **Use Consistent Methodology:**
   - Apply the rubric uniformly across all cases
   - Use the same scoring scale consistently
   - Follow the same decision rules for similar situations
   - Use the same evaluation template format

5. **Evaluator Transparency:**
   - Note any special knowledge or expertise you bring
   - Disclose conflicts of interest or biases
   - Note if you evaluated the same claim multiple times and got different verdicts
   - Record your confidence level honestly

6. **Version Control:**
   - Date all evaluations
   - Note methodology version used
   - Track revisions to verdicts with reasons
   - Maintain consistent record format

**Reproducibility Checklist:**

```
☐ Claim text recorded verbatim
☐ Citation fully documented with retrieval information
☐ Evidence passage recorded verbatim with context
☐ Source access method documented
☐ Evaluation dimensions scored with justification
☐ Composite score calculated
☐ Verdict assigned with explicit reasoning
☐ Decision rules consulted (if applicable)
☐ Ambiguities identified and resolved
☐ Evaluator confidence level recorded
☐ Special circumstances noted
☐ Evaluation template used consistently
☐ All supporting evidence and notes included

Reproducibility Assessment: High / Moderate / Low
(Can another evaluator reach the same verdict using your documentation?)
```

---

## Special Cases & Decision Matrices

### **When Verdict Selection Is Ambiguous**

**Decision Matrix 1: Fully Supported vs. Partially Supported**

| Factor | Fully Supported | Partially Supported |
|--------|-----------------|-------------------|
| **All claim components addressed?** | Yes | No |
| **Evidence uses hedging language?** | No / Minimal | Yes |
| **Scope/qualifier in source?** | Not limiting | Limiting |
| **Minor gaps present?** | No | Yes |
| **Verdict** | ✓ | ⚠ |

**Decision Matrix 2: Unsupported vs. Insufficient Evidence**

| Factor | Unsupported | Insufficient Evidence |
|--------|-------------|---------------------|
| **Is source topically relevant?** | No | Yes |
| **Can you find related passage?** | No | Yes, but vague |
| **Needs different source?** | Yes | Would strengthen but not required |
| **Source is authoritative?** | N/A (unrelated) | Yes, but incomplete |
| **Verdict** | ✗ | ≈ |

**Decision Matrix 3: Unsupported vs. Contradicted**

| Factor | Unsupported | Contradicted |
|--------|-------------|-------------|
| **Source addresses claim topic?** | No | Yes |
| **Source directly opposes claim?** | N/A | Yes |
| **Evidence is negative (opposite)?** | No evidence | Explicit opposition |
| **Verdict** | ✗ | ✗✗ |

---

## Evaluation Documentation Template

Use this template for consistent, reproducible evaluation:

```markdown
# Evaluation Summary

**Evaluation Date:** [Date]
**Evaluator:** [Name]
**Case ID:** [ID]
**Methodology Version:** 1.0

---

## Source Material

**Original Query/Prompt:**
[Record the query that generated the AI response]

**AI System:**
[Name and version of AI system, if known]

**AI Response:**
[Full response text]

---

## Claim-by-Claim Evaluation

### Claim [ID]: [Claim Text]

**Citation:** [Full citation with retrieval info]

**Evidence Passage:**
> [Direct quote]

**Context:**
[Surrounding text for context]

---

**Rubric Scoring:**

| Dimension | Score | Justification |
|-----------|-------|---------------|
| Entailment | 0–2 | |
| Completeness | 0–2 | |
| Relevance | 0–2 | |
| Evidence Quality | 0–2 | |
| Citation Placement | 0–2 | |

**Composite Score:** [X]/10

**Verdict:** [Fully Supported | Partially Supported | Unsupported | Contradicted | Citation Missing | Insufficient Evidence]

**Rationale:**
[2–4 sentence explanation]

**Ambiguities & Limitations:**
[Any evaluation challenges]

**Confidence Level:** High / Moderate / Low

---

[Repeat for each claim]

## Summary

**Total Claims Evaluated:** [N]
**Fully Supported:** [N] ([X%])
**Partially Supported:** [N] ([X%])
**Unsupported:** [N] ([X%])
**Contradicted:** [N] ([X%])
**Citation Missing:** [N] ([X%])
**Insufficient Evidence:** [N] ([X%])

**Overall Assessment:**
[Summary of citation quality, patterns observed, notable findings]

**Reproducibility Confidence:**
[High / Moderate / Low] — Another evaluator should reach [similar/identical] verdicts

---
```

---

## Summary

This methodology provides a structured, transparent, and reproducible framework for evaluating whether AI-generated citations support the claims they purport to validate. By following these 10 steps, applying the specified principles, and using consistent documentation standards, evaluators can generate reliable assessments suitable for portfolio demonstration, RAG evaluation, and AI quality assurance contexts.

The key principle throughout is evaluating **source-to-claim alignment**, not universal truth. This distinction allows systematic assessment of citation quality regardless of external knowledge or consensus about claim validity.
