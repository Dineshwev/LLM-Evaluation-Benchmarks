# Citation Verification Rubric

**Version 1.0** — Independent Portfolio Evaluation Framework  
*Not an official industry standard; designed for structured citation assessment in AI-generated content.*

---

## 1. Evaluation Unit

Before conducting any evaluation, clearly define the three core elements being assessed:

### **Claim**
A statement or assertion made by the AI system that requires empirical or factual support. Claims can be:
- Factual assertions (e.g., "The Great Wall of China is over 13,000 miles long")
- Causal statements (e.g., "COVID-19 vaccines reduce hospitalization rates")
- Definitional claims (e.g., "Machine learning is a subset of artificial intelligence")
- Quantitative statements (e.g., "70% of Americans use social media")

**Identifying Claims:**
- Extract sentences or phrases that make factual or empirical assertions
- Identify the core proposition that would require evidence to support
- Note compound claims that contain multiple independent assertions

### **Citation**
The reference provided by the AI system to support a claim. Citations should ideally include:
- Source type (academic paper, book, website, report, etc.)
- Author or organizational source
- Title or URL
- Publication year or date
- Page number, section, or specific reference point (when available)

**Citation Quality Notes:**
- Complete citations enable verification
- Incomplete citations (missing author, date, or URL) limit evaluability
- Generic references (e.g., "studies show") without specific source are incomplete

### **Evidence Passage**
The specific text, data, or statement from the cited source that is claimed to support the assertion. When evaluating, extract:
- Direct quotations from the source
- Relevant data points, statistics, or figures
- Contextual information surrounding the claim support
- The scope and qualification of the evidence (e.g., "in some cases," "meta-analysis shows")

**Documentation Standard:**
Record evidence passages verbatim or with clear indication of paraphrasing. Include surrounding context to assess whether the evidence is being taken out of context.

---

## 2. Core Evaluation Questions

Answer these questions sequentially when evaluating each claim-citation pair:

### **Question 1: Does the cited source address the claim?**
Determine whether the source discusses the topic or subject matter of the claim, even if not perfectly aligned.

- **Yes → Proceed to Question 2**
- **No → Verdict: Unsupported or Citation Missing**

### **Question 2: Does the evidence actually support the full claim?**
Assess whether the cited passage provides direct, explicit support for the entire claim.

- **Yes, fully supports → Proceed to scoring**
- **Partially → Proceed to Question 3**
- **No → Proceed to Question 4**

### **Question 3: Is only part of the claim supported?**
When a claim contains multiple components, determine whether the source supports all of them.

- **Yes, partial support identified → Likely verdict: Partially Supported**
- **No, unrelated parts unsupported → Proceed to Question 4**

### **Question 4: Does the source contradict the claim?**
Check whether the source directly refutes, contradicts, or presents conflicting information.

- **Yes, clear contradiction → Verdict: Contradicted**
- **No → Proceed to Question 5**

### **Question 5: Is the citation relevant but insufficient?**
Assess whether the source is topically appropriate but lacks specificity, detail, or completeness.

- **Yes, relevant but vague → Verdict: Insufficient Evidence**
- **No → Proceed to Question 6**

### **Question 6: Is a citation missing?**
Verify that a citation was provided. If no source is cited:

- **No citation provided → Verdict: Citation Missing**
- **Citation provided → Return to earlier analysis**

---

## 3. Verdict Categories

### **Fully Supported**

**Definition:**  
The cited source provides explicit, direct evidence that supports the entire claim. The evidence is clear, unambiguous, and logically entails or directly states the claim.

**When to Use:**
- The source explicitly confirms the claim with specific evidence
- All components of a multi-part claim are supported
- The evidence is recent, relevant, and of sufficient quality
- No qualifying language in the source undermines the support

**Example:**  
- **Claim:** "The Earth's atmosphere is composed of approximately 78% nitrogen."
- **Citation:** NASA Atmospheric Composition Reference
- **Evidence:** "Nitrogen (N₂) comprises 78.08% of the Earth's atmosphere..."
- **Verdict:** Fully Supported ✓

---

### **Partially Supported**

**Definition:**  
The cited source provides support for only some components of the claim. Some aspects are verified; others lack direct source support or require additional evidence.

**When to Use:**
- A multi-component claim has one or more parts unsupported
- The source confirms a weaker version of the claim than stated
- Qualifying language in the source (e.g., "may," "could," "in some cases") limits the strength of support
- The evidence addresses related but not identical claims

**Example:**  
- **Claim:** "Artificial intelligence is transforming healthcare and transportation sectors equally."
- **Citation:** McKinsey AI Impact Report 2023
- **Evidence:** "Healthcare AI applications have achieved 40% adoption rates, while autonomous vehicle deployment remains limited to 2% of transportation sectors."
- **Verdict:** Partially Supported (healthcare claim supported; transportation claim contradicted or unsupported) ⚠

---

### **Unsupported**

**Definition:**  
The cited source does not provide meaningful evidence supporting the claim. The source may be tangentially related or address a different topic entirely.

**When to Use:**
- The source discusses a related but distinct topic
- The cited passage doesn't address the core claim
- The connection between citation and claim requires external knowledge or inference not present in the source
- No evidence in the source substantiates the specific claim

**Example:**  
- **Claim:** "Python is the most popular programming language for machine learning."
- **Citation:** "A Brief History of Programming Languages"
- **Evidence:** The source mentions Python's creation in 1991 but contains no data on machine learning adoption or popularity comparisons.
- **Verdict:** Unsupported ✗

---

### **Contradicted**

**Definition:**  
The cited source directly refutes, contradicts, or presents conflicting information that undermines or refutes the claim.

**When to Use:**
- The source explicitly states opposite information
- The evidence presents data that directly contradicts the claim
- The source provides a counter-argument to the claim
- The contradiction is explicit, not merely implied

**Example:**  
- **Claim:** "Annual inflation in 2022 remained below 5% in the United States."
- **Citation:** U.S. Bureau of Labor Statistics 2022 Report
- **Evidence:** "The annual inflation rate for 2022 reached 8.0%, the highest level in 40 years."
- **Verdict:** Contradicted ✗

---

### **Citation Missing**

**Definition:**  
A claim is presented without any citation, or the citation provided is so incomplete that the source cannot be identified or retrieved.

**When to Use:**
- No source reference is provided for the claim
- The citation is vague or generic ("studies show," "some experts believe") without specific source identification
- The citation is malformed or missing critical identifying information (author, date, title, URL)
- The cited source cannot be located or verified due to incomplete information

**Example:**  
- **Claim:** "Most people prefer video content to text-based learning."
- **Citation:** (None provided, or only "Studies show...")
- **Verdict:** Citation Missing ⊘

---

### **Insufficient Evidence**

**Definition:**  
A citation is provided and is relevant to the claim, but the evidence is too vague, underdeveloped, outdated, or lacks necessary detail to adequately support the claim.

**When to Use:**
- The source is appropriate but makes only a passing reference to the claim
- The evidence provided is too general or lacks specificity
- The citation is outdated or from a low-credibility source
- Necessary context, qualifications, or caveats in the source are not captured by the claim
- The source is credible but makes no empirical or quantitative claim (e.g., "we believe this is important")

**Example:**  
- **Claim:** "Remote work increases productivity by 35%."
- **Citation:** "A Study on Remote Work Outcomes" (published 2015, single small sample)
- **Evidence:** "Remote work showed positive productivity effects in our survey of 50 employees."
- **Verdict:** Insufficient Evidence (dated source, small sample, no specific metric or percentage) ≈

---

## 4. Evaluation Dimensions

When assigning a verdict, assess each claim-citation pair across five dimensions. These dimensions provide structured reasoning for the verdict.

### **Dimension 1: Entailment**
Does the evidence logically support or entail the claim?

| Rating | Meaning | Explanation |
|--------|---------|-------------|
| **2** | Strong entailment | The claim is directly stated or necessarily follows from the evidence |
| **1** | Partial entailment | The claim is supported but with qualifications, caveats, or limited scope |
| **0** | No entailment | The evidence does not logically support the claim |

### **Dimension 2: Completeness**
Does the evidence address all components of the claim?

| Rating | Meaning | Explanation |
|--------|---------|-------------|
| **2** | Complete | All parts of a multi-component claim are addressed |
| **1** | Partial | Some but not all components are supported |
| **0** | Incomplete | Major components lack support |

### **Dimension 3: Relevance**
Is the cited source topically and contextually appropriate for the claim?

| Rating | Meaning | Explanation |
|--------|---------|-------------|
| **2** | Highly relevant | Source is directly focused on the claim's topic |
| **1** | Somewhat relevant | Source addresses related but not identical topic |
| **0** | Not relevant | Source is tangential or unrelated |

### **Dimension 4: Evidence Quality**
Is the evidence from a credible, reliable, and appropriately recent source?

| Rating | Meaning | Explanation |
|--------|---------|-------------|
| **2** | High quality | Primary source, peer-reviewed, recent, authoritative |
| **1** | Moderate quality | Secondary source, reasonable credibility, adequate recency |
| **0** | Low quality | Unreliable source, outdated, lacks credibility, anecdotal |

### **Dimension 5: Citation Placement**
Is the citation appropriately positioned and correctly attributed?

| Rating | Meaning | Explanation |
|--------|---------|-------------|
| **2** | Properly cited | Clear, complete citation with specific reference point |
| **1** | Partially cited | Citation provided but lacks some details (page, date, etc.) |
| **0** | Not cited | No citation or non-retrievable source |

---

## 5. Scoring Method

### **Scoring Framework**

Each dimension is rated on a scale of 0–2:
- **2 points** = Criterion fully met
- **1 point** = Criterion partially met
- **0 points** = Criterion not met

### **Composite Score**

Sum scores across all five dimensions to generate a composite score out of 10.

**Interpretation:**

| Score Range | Interpretation | Verdict Alignment |
|-------------|-----------------|-------------------|
| **9–10** | Excellent support | Fully Supported |
| **7–8** | Good support with minor gaps | Fully Supported or Partially Supported |
| **5–6** | Moderate support with notable gaps | Partially Supported or Insufficient Evidence |
| **3–4** | Weak or questionable support | Unsupported or Insufficient Evidence |
| **1–2** | Minimal or no support | Unsupported, Contradicted, or Citation Missing |
| **0** | No support; contradicted or cited | Citation Missing, Contradicted, or Unsupported |

### **Using Scores in Verdict Assignment**

Composite scores serve as **supporting evidence** for verdict assignment but should not be purely mechanical:

1. **Calculate the composite score** across all dimensions
2. **Consult core evaluation questions** to confirm verdict alignment
3. **Apply decision rules** (Section 6) when borderline cases arise
4. **Document reasoning** linking scores to the assigned verdict

**Example:**
- Entailment: 2 (strong)
- Completeness: 1 (partial)
- Relevance: 2 (high)
- Evidence Quality: 2 (high)
- Citation Placement: 2 (proper)
- **Composite: 9/10**
- **Verdict:** Fully Supported or Partially Supported (depending on which component is unsupported)

---

## 6. Decision Rules

Use these rules to resolve ambiguous cases and choose between similar verdicts.

### **Rule 1: Fully Supported vs. Partially Supported**

**Choose Fully Supported when:**
- All key claims or claim components are directly addressed in the source
- Evidence is explicit and unqualified (not hedged with "may," "could," or "suggests")
- No significant components lack support

**Choose Partially Supported when:**
- One or more components of a multi-part claim are unsupported or contradicted
- Evidence supports a narrower or weaker version of the claim than stated
- Source uses qualifying language that limits the scope of support
- Additional evidence would be needed to fully support all aspects

**Borderline Rule:** When a minor component is unsupported but the major claim is strongly supported, Fully Supported is appropriate. When core components lack support, use Partially Supported.

---

### **Rule 2: Unsupported vs. Insufficient Evidence**

**Choose Unsupported when:**
- The cited source does not address the claim's topic
- No relevant evidence exists in the provided source
- The connection requires external knowledge or inference
- The source is tangentially related at best

**Choose Insufficient Evidence when:**
- The source is topically relevant and addresses the claim
- Evidence exists but is too vague, limited in scope, or lacks necessary detail
- The source is credible but makes only a passing or underdeveloped reference
- The source is outdated but would have been sufficient if current
- A qualitative claim lacks quantitative support (or vice versa)

**Borderline Rule:** If you can locate even a relevant passage in the source, lean toward Insufficient Evidence. If the source has no bearing on the claim, use Unsupported.

---

### **Rule 3: Unsupported vs. Contradicted**

**Choose Unsupported when:**
- The source doesn't address the claim
- The source is unrelated to the claim
- The evidence simply fails to support (but doesn't refute)

**Choose Contradicted when:**
- The source explicitly states opposite information
- Evidence directly conflicts with the claim
- The source provides a counter-argument or refutation
- Quantitative evidence contradicts the claim's assertion

**Borderline Rule:** Only use Contradicted if the source explicitly presents opposing information. If the source merely fails to confirm the claim without refuting it, use Unsupported.

---

### **Rule 4: Missing Citation vs. Citation Missing Verdict**

**Assign Citation Missing verdict when:**
- No source is cited for the claim
- The citation is so incomplete that it cannot be retrieved (no author, date, or URL)
- Generic language ("research suggests," "studies show") is used without specific source identification

**Document for Unsupported when:**
- The evaluator attempts but cannot retrieve the cited source (document the retrieval attempt)
- This may be treated as Unsupported if the citation cannot be verified, or Citation Missing if the citation was never provided

---

## 7. Evaluator Notes

### **Standards for Rigorous Evaluation**

Follow these principles to maintain consistency and avoid bias in your assessments.

#### **A. Avoid Unwarranted Assumptions**

**Principle:** Judge the claim-citation pair based solely on explicit evidence from the source.

**Practices:**
- Do not assume the source supports a claim based on its title or general topic alone
- Do not infer support from related but unstated information in the source
- Do not assume the AI system's intended meaning if the claim is ambiguous
- Do not extend evidence beyond what the source explicitly states (e.g., "the source mentions X, so probably also means Y")

**Bad Example:**  
- Claim: "Social media negatively impacts mental health."
- Citation: "A Review of Adolescent Social Media Use"
- Verdict: Fully Supported (assumed based on title alone, without reading the content)

**Good Example:**  
- Read the actual content; confirm that the review explicitly discusses negative mental health impacts
- Note any qualifications, counterarguments, or limited evidence
- Assign verdict based on evidence found, not title

---

#### **B. Rely on the Provided Source Only**

**Principle:** When evaluating a citation, assess whether the source actually provided to you supports the claim. Do not supplement with outside knowledge.

**Practices:**
- Evaluate based only on the source text provided
- Do not assume personal knowledge about the topic
- If you have conflicting outside knowledge, document this as a note but base the verdict on the provided source
- Do not assume a source is correct or credible based on your prior beliefs about it
- Do not use your expertise to "fill in gaps" that the source doesn't explicitly cover

**Bad Example:**  
- Claim: "Quantum entanglement allows instantaneous communication."
- Citation: A source that discusses quantum entanglement but doesn't mention communication
- Verdict: Fully Supported (based on personal physics knowledge that you added, not the source)

**Good Example:**  
- Evaluate the provided source strictly
- Verdict: Unsupported or Insufficient Evidence (the source doesn't make the communication claim)
- Note: Personal knowledge suggests this claim is incorrect, but the verdict is based on whether the source supports it

---

#### **C. Separate Fact from Inference**

**Principle:** Distinguish between explicit claims in the source and inferences you might draw.

**Practices:**
- Mark inferences with "inferred from" or "implied by" language
- Require explicit evidence for direct verdicts, not inference
- When the source requires interpretation, note the ambiguity
- Do not treat a probable inference as equivalent to explicit evidence

**Bad Example:**  
- Claim: "Climate change will cause mass migration."
- Citation: A source stating "rising sea levels threaten coastal regions"
- Verdict: Fully Supported (inferred that climate change will cause mass migration)

**Good Example:**  
- The source does not explicitly connect sea level rise to migration
- Verdict: Partially Supported or Unsupported (depending on how directly connected they are)
- Note: "The source supports threat to coastal regions; migration connection is implied, not stated"

---

#### **D. Document Ambiguity**

**Principle:** When evaluation is difficult or ambiguous, record the ambiguity explicitly.

**Practices:**
- Note when the source is unclear or contradictory
- Record when the claim itself is ambiguous or multi-faceted
- Document when context is missing that would clarify the relationship
- Identify when the verdict is on a borderline between categories
- When reasonable evaluators might disagree, state this clearly

**Example Ambiguity Notes:**
- "The source uses 'may indicate' language, creating ambiguity about strength of support"
- "The claim contains two distinct propositions; Proposition A is supported, Proposition B is not"
- "The evidence is statistical but the claim is universal; borderline between Partially Supported and Unsupported"
- "The citation is to a 2015 source; data is potentially outdated but relevant"

---

#### **E. Record Contextual Information**

**Practices:**
- Note the date of the source and whether recency is relevant to the claim
- Identify the source type (peer-reviewed, news, blog, corporate report, etc.)
- Record whether the evidence is primary (original research) or secondary (review/summary)
- Note any disclosed limitations, caveats, or qualifications in the source
- Document the scope of evidence (e.g., "U.S. only," "specific demographic," "meta-analysis of 45 studies")

---

#### **F. Avoid These Common Evaluation Errors**

| Error | Description | How to Avoid |
|-------|-------------|-------------|
| **Title Bias** | Assuming a source supports a claim based on its title alone | Read the actual content; verify explicit support |
| **Semantic Similarity Trap** | Treating topical relevance as evidence support | Distinguish between "addresses the topic" vs. "supports the claim" |
| **Belief Bias** | Rating citations as stronger when they align with your views | Maintain neutrality; use explicit evidence criteria |
| **Recency Illusion** | Overweighting recent sources or underweighting older ones inappropriately | Assess recency relative to the claim's nature |
| **Overconfidence** | Assigning verdicts without reviewing source material carefully | Document all verdicts with specific evidence quotes |
| **Context Collapse** | Taking evidence out of context and losing important qualifications | Include surrounding sentences; note caveats and qualifications |

---

## 8. Evaluation Template

Use this template for consistent documentation:

```markdown
## Claim-Citation Evaluation

**Claim ID:** [Assign unique identifier]  
**Claim Text:** [Exact claim from AI response]  
**Cited Source:** [Author, Title, Year, URL or reference]  

### Evidence Passage
[Direct quote from source]

*Context:* [Surrounding sentences for context]

### Dimensional Scoring
- Entailment: [0/1/2] — [Brief explanation]
- Completeness: [0/1/2] — [Brief explanation]
- Relevance: [0/1/2] — [Brief explanation]
- Evidence Quality: [0/1/2] — [Brief explanation]
- Citation Placement: [0/1/2] — [Brief explanation]

**Composite Score:** [X/10]

### Verdict
**Verdict:** [Fully Supported | Partially Supported | Unsupported | Contradicted | Citation Missing | Insufficient Evidence]

**Reasoning:** [2–3 sentences explaining the verdict and how dimensions support it]

### Evaluator Notes
[Any ambiguities, caveats, missing context, or borderline considerations]

**Confidence Level:** [High | Moderate | Low]
```

---

## Summary

This rubric provides a structured, evidence-based framework for evaluating whether AI-generated citations actually support the claims they purport to validate. The combination of clear evaluation questions, verdict categories with examples, dimensional scoring, and decision rules enables consistent, transparent, and defensible citation assessment suitable for AI quality assurance, RAG evaluation, and portfolio demonstration purposes.

**Remember:** This is a practical portfolio framework, not an official industry standard. Adapt it to your specific evaluation context while maintaining the core principles of evidence-based reasoning and transparent documentation.
