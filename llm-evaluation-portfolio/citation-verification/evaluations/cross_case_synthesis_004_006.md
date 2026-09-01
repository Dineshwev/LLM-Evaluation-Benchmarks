# Cross-Case Synthesis: Citation Verification Cases 004–006

## 1. Portfolio Overview

The three case studies collectively evaluate AI-generated responses across regulatory compliance, API data-retention policy, and AI coding-assistant privacy.

| Case Study | Domain | Claims | Avg. Composite Score |
|---|---|---|---|
| Case 004 | EU AI Act risk framework | 11 | 9.2/10 |
| Case 005 | API data retention and privacy | 10 | 8.2/10 |
| Case 006 | AI coding assistant privacy | 10 | 6.3/10 |
| **Portfolio Total** | **Cross-domain citation evaluation** | **31** | **7.9/10 weighted average** |

### Final Portfolio-Level Verdict Distribution

| Verdict | Count | Percentage |
|---|---|---|
| Fully Supported | 13 | 41.9% |
| Partially Supported | 8 | 25.8% |
| Unsupported | 7 | 22.6% |
| Citation Missing | 3 | 9.7% |
| **Total** | **31** | **100%** |

The overall portfolio shows that citation quality is generally strong, but across the portfolio, 18 of 31 claims (58.1%) were not fully supported, indicating that citation presence frequently did not translate into complete claim-level support.

## 2. Most Common Citation-Failure Patterns

### Failure Pattern 1: Overgeneralization

The most frequent problem across Cases 005 and 006 was the expansion of a limited source statement into a broad or universal claim.

**Example**

A source may state:
> A feature applies to eligible customers.

The AI response transforms this into:
> The feature applies to all customers.

This occurred particularly with:
- Zero Data Retention eligibility
- model coverage
- subscription-specific privacy policies
- endpoint-specific data retention
- enterprise versus individual product tiers

**Methodological lesson**

A citation can be factually relevant while still failing to support the scope of the claim.
The evaluator must therefore test:
> Does the source support the claim exactly as broadly as it is written?

### Failure Pattern 2: Unsupported Universal Language

Absolute terms created several of the weakest claims in the portfolio.

Common examples included language such as:
- all
- every
- never
- always
- permanently
- under any circumstances
- without exception

These words significantly raise the burden of evidence.

**Examples from the cases**
- OpenAI allegedly retaining all API data indefinitely.
- ZDR applying to all endpoints or features.
- Anthropic ZDR covering all models.
- GitHub Copilot never using data across every subscription tier.
- Cursor providing ZDR across every model.

**Methodological insight**

A useful evaluation rule is:
> The broader the claim, the stronger and more explicit the evidence must be.

### Failure Pattern 3: Source–Claim Scope Mismatch

Several claims were related to the cited source but exceeded its actual scope.

For example, a source could discuss:
> abuse-monitoring logs,

while the response claimed:
> permanent retention of all customer data.

Or a source could discuss:
> a specific enterprise subscription,

while the response generalized the policy to:
> all users and all subscription tiers.

This pattern is particularly important because the citation may appear legitimate at first glance.

**Key insight**

Topical relevance is not the same as entailment.
A source can receive:
- high relevance,
- high evidence quality,
- correct citation placement,

while the overall claim still fails because the source does not actually entail it.

### Failure Pattern 4: Product-Surface Confusion

Case 006 particularly demonstrated confusion between different product layers.

Examples included:
- Individual vs Business vs Enterprise subscriptions
- Copilot core functionality vs Copilot Memory
- IDE privacy settings vs Cloud Agents
- model-provider retention vs platform retention

A policy applying to one product surface was incorrectly generalized to another.

**Methodological lesson**

Before scoring a claim, the evaluator should identify:
- Which product?
- Which feature?
- Which subscription tier?
- Which user category?
- Which model or endpoint?
- Which type of stored data?

If these dimensions are mixed together, a claim can easily become misleading.

### Failure Pattern 5: Citation Missing

Three claims across the portfolio lacked sufficient direct citation support.

This included cases where:
- a new factual claim appeared in the conclusion,
- an earlier citation was assumed to support a later statement,
- an inference was presented without directly identifying supporting evidence.

**Important distinction**

An uncited claim should not automatically be considered false.
Instead:
> Citation Missing means the response failed to provide sufficient evidence for verification.

This distinction preserves the difference between:
- **Unsupported** → cited evidence does not support or contradicts the claim.
- **Citation Missing** → no adequate citation is provided for verification.

## 3. Strong Examples vs Weak Examples

### Strong Example: Direct Policy Match

The strongest claims in the portfolio generally had three characteristics:

1. **Explicit source wording:** The source directly addressed the same factual question.
2. **Accurate scope:** The AI response preserved qualifiers such as:
   - eligible customers,
   - by default,
   - unless explicitly opted in,
   - subject to exceptions.
3. **No unnecessary expansion:** The response did not transform a limited policy into a universal statement.

**Example pattern**
- **Source:** Data is not used for training unless the customer explicitly opts in.
- **Good AI claim:** Data is not used for training by default unless the customer explicitly opts in.

This is a strong claim because the important condition is preserved.

### Weak Example: Universal Expansion

- **Source:** Some eligible customers may receive Zero Data Retention.
- **Weak AI claim:** All customers receive Zero Data Retention.

The citation may still be relevant, official, and correctly placed, but the claim fails on entailment and scope.

### Weak Example: Contradiction of Source

Case 006 Claim 4 provides a particularly clear failure pattern.

The claim stated that Copilot Memory permanently retains stored information unless manually deleted.
The evidence instead stated that unused information is automatically deleted after 28 days.

This is stronger than ordinary partial support because the source establishes a material contradiction.

**Methodological takeaway**
When a source directly contradicts a claim:
- Entailment should be very low.
- Completeness should reflect the omitted contradictory condition.
- The final verdict should generally be Unsupported.

## 4. Portfolio-Level Quality Pattern

The cases show a clear decline in overall support:

| Case | Average Score | General Pattern |
|---|---|---|
| Case 004 | 9.2/10 | Mostly well-supported |
| Case 005 | 8.2/10 | Moderate overgeneralization |
| Case 006 | 6.3/10 | Multiple systematic citation failures |

This creates a useful progression across the portfolio.

- **Case 004:** Demonstrates a relatively strong citation-based response with a smaller number of nuanced failures.
- **Case 005:** Introduces stronger examples of overgeneralization, absolute claims, retention-policy confusion, and unsupported comparative conclusions.
- **Case 006:** Tests more complex failure modes involving product-tier confusion, internal contradiction, feature-specific scope mismatch, missing citations, and unsupported comparative recommendations.

## 5. Final Methodology Insights

### Insight 1: Citation presence does not equal citation support
The central finding across all three cases is:
A response can contain official citations and still make unsupported claims.
Evaluation must examine the relationship between the specific claim and the specific evidence.

### Insight 2: Entailment should be evaluated independently from source quality
A source can be official, authoritative, highly relevant, and still fail to support the claim being made. This is exactly why a multi-dimensional rubric is more useful than simply checking whether a citation exists.

### Insight 3: Qualifiers are evidence-bearing information
Words such as *eligible, may, by default, unless, subject to exceptions, for Business and Enterprise, certain endpoints* are not minor details. Removing them can fundamentally change the meaning of a policy.

**Evaluation principle:**
If removing a qualifier makes a claim materially broader, the qualifier must be treated as part of the evidence.

### Insight 4: Conclusions require independent scrutiny
Comparative conclusions often introduce new claims (e.g., "Provider A provides stronger privacy protection than Provider B"). Even if every underlying factual statement is cited, the comparative judgment may still require clear evaluation criteria, accurate underlying evidence, and acknowledgment of limitations. Therefore, synthesis claims should not automatically inherit the support level of earlier factual claims.

### Insight 5: Internal consistency matters
Case 006 demonstrated that an AI response can contain claims that conflict with each other. A strong citation-verification methodology should therefore examine claim-to-source consistency and claim-to-claim consistency. A response can fail even when individual citations appear superficially plausible if its own claims are logically incompatible.

## 6. Final Portfolio Conclusion

Across 31 evaluated claims, the portfolio demonstrates that the most significant citation failures do not usually come from completely unrelated sources. Instead, they commonly arise when AI-generated responses:
- broaden a limited source statement,
- remove important qualifiers,
- convert conditional policies into universal guarantees,
- confuse subscription tiers or product features,
- present comparative judgments as factual conclusions,
- rely on implied rather than explicit citations,
- or contradict information contained elsewhere in the same response.

The strongest responses preserved the exact scope and conditions of the cited evidence. The weakest responses used authoritative sources but silently expanded their meaning.

**Core methodological conclusion**
Citation verification is not primarily a test of whether a source exists. It is a test of whether the source actually supports the claim, with the same scope, conditions, and level of certainty expressed in the response.

### Final portfolio snapshot
- **Cases evaluated:** 3
- **Total claims:** 31
- **Fully Supported:** 13
- **Partially Supported:** 8
- **Unsupported:** 7
- **Citation Missing:** 3
- **Weighted average composite score:** 7.9/10

**Overall portfolio finding:** The framework successfully distinguishes between citation presence, source relevance, source quality, and genuine claim-level support. The most persistent failure mode is scope expansion—turning conditional, limited, or product-specific documentation into broader universal claims.
