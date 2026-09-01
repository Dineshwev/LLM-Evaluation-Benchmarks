# Citation Verification

## Overview

Citation Verification is an independent portfolio project that demonstrates a structured methodology for evaluating whether citations in AI-generated responses actually support the claims they purport to validate. This project implements systematic source-to-claim verification, focusing on **claim-to-source alignment**: Does the cited source provide evidence that supports the specific claim made?

This is a **portfolio demonstration project**, not an industry benchmark or production evaluation system. It showcases practical evaluation techniques for assessing citation quality and source-to-claim alignment in AI-generated content. While the methodology may be relevant to Retrieval-Augmented Generation (RAG) evaluation workflows, this project focuses specifically on structured claim verification rather than comprehensive RAG system evaluation.

---

## Objective

The primary objective of this project is to:

1. **Systematically assess claim-to-source alignment** in AI-generated responses
2. **Evaluate whether cited sources support claims** with structured verdict categories
3. **Document citation strengths and weaknesses** including missing citations, unsupported claims, and contradictory evidence
4. **Demonstrate reproducible evaluation methodology** suitable for citation verification and AI quality assurance workflows
5. **Record source quality as a separate dimension** while maintaining focus on whether sources actually support claims

---

## Core Evaluation Principle

This project evaluates **whether a cited source supports a claim**, not whether the claim is universally true according to external knowledge. This distinction is critical:

- **Primary Question:** Does the cited source provide evidence that supports the specific claim?
- **Secondary Considerations:** Source quality (credibility, recency, authority), citation completeness (retrievability, specificity), and source relevance (topical appropriateness) are recorded as separate evaluation dimensions.
- **Non-Goal:** Universal fact-checking or consensus-based truth assessment.

This approach allows systematic assessment of citation quality regardless of external knowledge about claim validity, enabling transparent, reproducible evaluation.

---

## What This Project Evaluates

### Primary Evaluation Focus: Claim-to-Source Alignment

The core evaluation question is whether a cited source supports a claim:

| Assessment | Description |
|-----------|-------------|
| **Claim-to-Source Alignment** | Whether the cited source explicitly addresses and supports the claim made |
| **Entailment** | Whether the claim logically follows from or is directly stated in the source material |
| **Partial Support** | When the source supports only some components of a multi-part claim |
| **Contradiction** | When the source contradicts or refutes the claim |
| **Claim Substantiation** | Whether adequate evidence exists in the source to verify the claim |

### Secondary Evaluation Dimensions

While maintaining focus on claim-to-source alignment, the project also records these dimensions:

| Dimension | Description |
|-----------|-------------|
| **Citation Completeness** | Whether material factual claims have appropriate, identifiable citations. This assesses whether the AI provided any citation reference that can be located and reviewed, not whether citations include exhaustive detail (e.g., page numbers are helpful but not universally required). |
| **Source Relevance** | Whether the cited source is topically or contextually appropriate for addressing the claim |
| **Evidence Quality** | The credibility, recency, and authority of the cited source (Note: A low-quality source may still support a claim; source quality is recorded separately from whether it provides support) |

### Citation vs. Source Quality Distinction

This project clarifies three related but distinct concepts:

- **Citation Correctness:** Is the citation attributed accurately? Does it refer to an actual source? (Yes/No)
- **Citation Completeness:** Can the citation be identified and retrieved? Does it reference a material factual claim requiring external evidence? (Yes/No/Partial)
- **Source Quality:** Is the source credible, authoritative, and sufficiently current? (Rating: High/Moderate/Low)

A source can be low-quality yet still support a claim. A source can be high-quality but insufficient or irrelevant. These are evaluated as separate dimensions.

---

## Evaluation Workflow

The evaluation process follows this structured workflow:

1. **Claim Extraction** → Identify and isolate individual claims in the AI response
2. **Citation Identification** → Extract and record the cited source(s) for each claim
3. **Source Retrieval** → Obtain and review the actual cited material
4. **Alignment Assessment** → Compare claim against source content
5. **Verdict Assignment** → Assign verdict based on evaluation criteria (see Verdict Categories)
6. **Evidence Documentation** → Record supporting evidence, discrepancies, and notes
7. **Analysis** → Aggregate findings and identify patterns

---

## Verdict Categories

Each claim-source pair is assigned one of six verdicts based on the alignment between the claim and the cited source:

### **Fully Supported**
The cited source explicitly supports the claim with clear, direct evidence. The claim is entailed by or directly stated in the source material. No significant qualifications or limitations in the source undermine the support.

### **Partially Supported**
The cited source supports only part of the claim. Some components or aspects are verified by the source; others lack adequate support or contradict the evidence.

### **Unsupported**
The claim is presented in the AI response, but the cited source does not provide meaningful evidence for it. The source may be tangentially related or address a different topic entirely. No connection between the source and the specific claim exists.

### **Contradicted**
The cited source explicitly contradicts, refutes, or presents conflicting information regarding the claim. The source evidence actually undermines or refutes the claim's validity.

### **Citation Missing**
A claim that requires external evidence is made, but no source is cited. Alternatively, the citation is so vague or incomplete (e.g., generic "studies show" without identifying the study) that the specific source cannot be identified or located.

**Distinction from Insufficient Evidence:** Citation Missing means no verifiable citation exists for the claim. If a citation does exist but is too vague or the source is too limited to properly evaluate, use Insufficient Evidence instead.

### **Insufficient Evidence**
A citation exists and is relevant to the claim, but the available evidence is too vague, underdeveloped, inaccessible, or context-limited to confidently determine whether it actually supports the claim. The source may be credible but makes only a passing reference, or the evidence lacks necessary specificity or detail.

**Distinction from Unsupported:** Insufficient Evidence means the source is on-topic and addressable, but the evidence within it is inadequate. Unsupported means the source doesn't address the claim at all.

---

## Repository Structure

```
citation-verification/
├── README.md                                      # Project documentation (this file)
├── methodology.md                                 # Step-by-step evaluation methodology (v1.0)
├── rubric.md                                      # Five-dimension scoring rubric (v1.0)
├── test-cases/                                    # Individual case studies
│   ├── case_001_supabase_planetscale_neon.md      # Database pricing & features
│   ├── case_002_hnsw_vs_ivf.md                    # Vector search algorithms
│   ├── case_003_eu_ai_act.md                      # EU AI Act overview
│   ├── case_004_eu_ai_act_risk_framework.md       # EU AI Act risk framework (9.2/10)
│   ├── case_005_api_security_citation_failures.md # API data retention & privacy (8.2/10)
│   └── case_006_ai_coding_assistant_privacy.md    # AI coding assistant privacy (6.3/10)
└── evaluations/                                   # Aggregate evaluation results
    └── cross_case_synthesis_004_006.md            # Cross-case synthesis: Cases 004–006
```

### Directory Details

- **test-cases/** → Contains individual citation verification case studies. Each case documents an AI-generated response, its claims, cited sources, and a full claim-by-claim evaluation with rubric scores and verdict assignments.
- **evaluations/** → Contains cross-case synthesis, pattern analysis, and aggregate portfolio findings drawn from completed case evaluations.

---

## Case Study Format

Each case study follows a standardized structure:

```markdown
# Case [ID]: [Brief Description]

## AI Response
[The complete AI-generated response being evaluated]

## Claims Identified
1. [Claim 1]
2. [Claim 2]
...

## Citations Provided
- Source A: [Citation details]
- Source B: [Citation details]

## Evaluation

### Claim 1
**Cited Source:** [Source identifier]
**Verdict:** [Fully Supported | Partially Supported | Unsupported | Contradicted | Citation Missing | Insufficient Evidence]
**Evidence:** [Direct quotes and analysis]
**Notes:** [Additional observations]

### Claim 2
[Evaluation details]
...

## Summary
[Overall assessment of citation quality and accuracy]
```

---

## Methodology

### Evaluation Process

1. **Claim Extraction** → Identify and isolate individual claims in the AI response
2. **Citation Identification** → Extract and record the cited source(s) for each claim
3. **Source Retrieval** → Obtain and review the actual cited material (if accessible)
4. **Evidence Location** → Find the specific passage in the source that may address the claim
5. **Alignment Assessment** → Compare the claim against the evidence passage to determine support
6. **Verdict Assignment** → Assign verdict based on alignment analysis (see Verdict Categories)
7. **Dimension Recording** → Document source quality, citation completeness, and relevance as secondary factors
8. **Documentation** → Record all findings with supporting evidence and reasoning
9. **Reproducibility** → Cases are structured to be evaluable independently by different reviewers

### Standards Applied

- **Source-to-Claim Focus** → Verdicts reflect whether the cited source supports the claim, independent of external truth
- **Evidence-Based Assessment** → Verdicts are grounded in specific textual evidence from the source
- **Semantic Precision** → Claims are evaluated for semantic alignment, not merely keyword overlap
- **Dimension Separation** → Source quality is recorded separately from claim support; a low-quality source may still support a claim
- **Contextual Interpretation** → Claims are evaluated within their original context and wording

---

## Limitations

This project has the following inherent limitations:

1. **Manual Evaluation** → Results reflect manual review and are subject to reviewer interpretation and judgment
2. **Limited Scale** → This portfolio project covers a limited number of cases and is not statistically representative of broader trends
3. **Source Access Dependency** → Evaluation depends on the ability to retrieve and access cited sources; some citations may be paywalled, archived, or unavailable
4. **Static Snapshots** → Evaluations capture source content at a specific point in time; sources may evolve or be updated after evaluation
5. **Not Production-Grade** → This project is designed for portfolio demonstration, not production deployment or automated processing
6. **Domain Scope** → Case selection may reflect limited domain coverage; findings may not generalize across all topics
7. **Subjectivity** → Some verdicts (e.g., "Partially Supported," "Insufficient Evidence") involve interpretive judgment despite structured evaluation criteria
8. **No Automation** → Lacks automated fact-checking, keyword extraction, or batch evaluation infrastructure
9. **Scope Clarity** → This project focuses on claim-to-source alignment; it does not perform comprehensive RAG evaluation, system-level assessment, or factual truth determination
10. **Methodology Adaptation** → Different evaluators may apply criteria slightly differently; this project demonstrates one consistent approach but is not a universal standard

---

## Skills Demonstrated

This project showcases the following professional competencies:

- **Citation Verification & Assessment** → Structured methodology for evaluating whether sources support claims
- **Claim-to-Source Alignment Analysis** → Systematic evaluation of semantic alignment between claims and evidence
- **AI Output Quality Assessment** → Practical techniques for evaluating citation quality and factual grounding in AI-generated content
- **Structured Evaluation Design** → Development of replicable, criterion-based evaluation frameworks with clear decision rules
- **Critical Analysis & Evidence Evaluation** → Detailed assessment of textual evidence, logical entailment, and substantiation
- **Documentation & Reproducibility** → Creation of transparent, detailed evaluation records suitable for independent review
- **Methodology Design** → Development of transparent, replicable evaluation processes with consistent standards and decision procedures
- **Relevance to RAG Workflows** → Techniques applicable to assessing whether retrieved documents are accurately cited in generated responses

---

## Use Cases & Applications

This project is relevant for professionals and teams working in:

- **Citation Quality Assessment** → Evaluating whether AI-generated responses cite sources accurately and appropriately
- **Fact-Checked Content Production** → Quality control for responses that require source substantiation
- **AI Output Evaluation** → Assessing citation practices and source grounding in large language model outputs
- **RAG System Evaluation** → Understanding whether retrieved documents are accurately referenced in generated responses (one component of comprehensive RAG evaluation)
- **Knowledge Base Verification** → Quality control for systems that integrate external sources
- **AI Training & Fine-Tuning** → Identifying patterns in citation quality for model improvement
- **Academic & Research Contexts** → Evaluating citation practices in AI-assisted research and writing

---

## License & Attribution

This is an independent portfolio project created for educational and professional demonstration purposes.

For questions or inquiries, please refer to the project repository.
