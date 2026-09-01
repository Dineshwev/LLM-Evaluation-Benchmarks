# LLM Response Evaluation Case Study 005: Relevance / Topic Drift

## Evaluation Metadata

- **Case Study ID:** case_005_relevance_topic_drift
- **Evaluation Date:** 2026-09-02
- **Evaluation Framework:** LLM Response Evaluation Rubric v1.0 & Scoring Methodology v1.0
- **Response Type:** Technical Troubleshooting / Implementation Guidance
- **Subject Domain:** Software Development / API Integration (Python / OpenAI API)
- **Primary Evaluation Focus:** Relevance
- **Evaluator Notes:** This case tests the framework's ability to detect a response that is factually accurate, clearly written, well-organized, and free of hallucinations — but fails to answer the user's actual question. The user asked for specific implementation strategies to handle a production API error. The AI delivered a conceptual educational primer on how rate limiting works as a technology, mentioning the user's actual request in only a single vague sentence at the end. This case exposes an important structural characteristic of the scoring methodology: a Relevance score of 0 does not trigger the Critical Failure Override, allowing a largely off-topic response to receive a raw score of 11/14 and a final verdict of Good. This is the third consecutive case to achieve a 0 in a non-override dimension and still pass to a Good final verdict (alongside Cases 002 and 003), completing the portfolio's demonstration that the Critical Failure Override has a narrow and specific scope.

---

## Original User Query

> "I'm getting a `429 Too Many Requests` error from the OpenAI API in my Python application. What are the **specific strategies I should implement** to handle this error gracefully **in production**? I need concrete approaches, not just a general explanation."

---

## AI-Generated Response

### Understanding HTTP 429 and API Rate Limiting

API rate limiting is a fundamental mechanism used by web services to control how frequently clients can make requests within a given time window. Understanding how rate limiting works is essential context for any developer working with third-party APIs.

---

#### What Is Rate Limiting?

Rate limiting is a server-side control that caps the number of requests an API client can make within a defined period. When a client exceeds this limit, the server responds with an HTTP `429 Too Many Requests` status code, indicating that the client should slow down before retrying.

---

#### Why APIs Implement Rate Limits

APIs implement rate limits for several important reasons:
- **Infrastructure protection:** Prevents any single client from overwhelming shared server resources.
- **Fair resource allocation:** Ensures equitable access across all users of a shared API service.
- **Cost management:** Controls operational costs by limiting excessive or abusive usage.
- **Security:** Mitigates brute-force attacks and denial-of-service attempts that exploit high-frequency calls.

---

#### Common Rate-Limiting Algorithms

API providers use different technical approaches to enforce rate limits:

**Token Bucket Algorithm:** Each client is assigned a conceptual "bucket" of tokens that replenishes at a fixed rate. Each API request consumes one or more tokens. When the bucket is empty, further requests are rejected until tokens refill. This approach tolerates short bursts of activity.

**Leaky Bucket Algorithm:** Requests are added to a queue and processed at a fixed, consistent rate, smoothing out traffic spikes. Requests that arrive faster than the queue can process them are dropped.

**Sliding Window Counter:** Tracks the number of requests made within a rolling time window rather than a fixed interval, providing more even enforcement across time boundaries.

---

#### OpenAI's Rate Limiting Structure

OpenAI implements rate limits across several dimensions simultaneously:
- **Requests Per Minute (RPM):** The number of API calls permitted per minute.
- **Tokens Per Minute (TPM):** The combined input and output token volume processed per minute.
- **Requests Per Day (RPD):** A daily ceiling on total API calls.

Rate limits vary significantly by model and by API usage tier. The free tier carries the most restrictive limits, while pay-as-you-go and enterprise tiers receive progressively higher allowances. Developers should review the OpenAI rate limits documentation for their specific model and account tier.

---

#### HTTP Status Code Context

The `429 Too Many Requests` status code is defined in RFC 6585 and is the standardized response for rate limit violations across the web. Servers may include a `Retry-After` response header indicating how many seconds the client should wait before resubmitting. Some APIs also expose supplementary headers such as `X-RateLimit-Limit` and `X-RateLimit-Remaining` to communicate current usage relative to the client's allowance.

---

#### General Considerations

If you are consistently encountering `429` errors in your application, it is worth reviewing your current request volume against the published limits for your API tier. You may also wish to consider implementing retry logic and consulting your provider's documentation if your workload genuinely requires higher sustained throughput than your current tier allows.

---

## Reference Evaluation Standard

### What the User Actually Asked For

The user explicitly requested:
1. **Specific strategies** — not conceptual background.
2. **Implementation guidance** — how to actually build the handling.
3. **Production-grade approaches** — reliable, robust, deployable code patterns.
4. The user pre-empted the most common failure mode by explicitly adding: *"I need concrete approaches, not just a general explanation."*

### What a Compliant Response Would Have Provided

A relevant response would have addressed one or more of the following concrete strategies:
- **Exponential backoff with jitter:** Retry logic that progressively increases wait times after each failure, with a random jitter component to prevent retry storms.
- **Respecting the `Retry-After` header:** Reading the server-provided delay value from the `429` response headers before retrying.
- **Request queuing / rate-limiting client-side:** Implementing a local token bucket or request queue to proactively throttle outbound requests before hitting the server limit.
- **Circuit breaker pattern:** Temporarily halting requests when a threshold of consecutive failures is reached, then testing recovery.
- **Batching and chunking:** Combining multiple small requests into fewer larger requests to reduce RPM.
- **Tier upgrade or model switching:** Selecting a lower-cost model with higher rate limits for lower-priority tasks.
- **Python-specific libraries:** Using `tenacity`, `backoff`, or `openai`'s native retry helpers.

None of these strategies appear in the AI response beyond a single vague sentence ("consider implementing retry logic").

---

## Dimension-by-Dimension Evaluation

### 1. Factual Accuracy
- **Score:** 2/2
- **Evidence:** The token bucket, leaky bucket, and sliding window algorithm descriptions are accurate. OpenAI's rate limit dimensions (RPM, TPM, RPD) are correctly named. The `Retry-After` header attribution to RFC 6585 is accurate. The tiered rate limit structure is correctly described.
- **Justification:** All factual claims in the response are objectively correct and verifiable. The response fails on relevance, not accuracy — the information is true, it is simply not the information the user needed.
- **Failure Mode:** None.

---

### 2. Relevance
- **Score:** 0/2
- **Evidence:** The user stated explicitly: *"I need concrete approaches, not just a general explanation."* The AI's response consists of: five conceptual sections on what rate limiting is, why it exists, and how three rate-limiting algorithms work; one section on OpenAI's rate limit structure in general terms; and one concluding paragraph containing the single sentence: *"You may also wish to consider implementing retry logic and consulting your provider's documentation."*
- **Justification:** The user's core intent — "what specific strategies should I implement in my production Python application?" — is not addressed by the response. The response answers a fundamentally different question: "What is rate limiting and how does it work conceptually?" The one-sentence mention of retry logic at the end does not constitute addressing the prompt; it is a vague gesture toward the topic that provides no actionable information. Per the rubric definition, a score of 0 applies when "the response misses the core intent of the prompt, answering a different question." The user pre-empted this failure mode in the query itself, explicitly requesting concrete approaches and not general explanations — making this violation unambiguous.
- **Failure Mode:** Topic drift — the model pivots from the requested troubleshooting and implementation task to a conceptual educational overview of the broader subject area.

---

### 3. Completeness
- **Score:** 1/2
- **Evidence:** The response technically contains a gesture toward the user's actual question: *"You may also wish to consider implementing retry logic and consulting your provider's documentation."*
- **Justification:** The user asked a multi-component question: (1) what strategies exist, and (2) how to implement them in production. The response leaves the implementation question comprehensively unanswered. However, the single mention of "retry logic" prevents a score of 0 — the response does not leave the topic entirely unanswered; it leaves it essentially unanswered, which maps to a score of 1. The critical practical information (how to implement retry logic, what patterns to use, what Python libraries to apply) is absent.
- **Note on Completeness vs. Relevance:** Completeness measures whether all parts of the query are covered; Relevance measures whether the response is appropriately focused on what was asked. This response is irrelevant because it addresses the wrong topic, and incomplete because it does not cover the requested topic. Both dimensions are penalized, but for different underlying reasons as defined by the rubric.
- **Failure Mode:** Answering only the most tangential aspect of a multi-part question.

---

### 4. Instruction Following
- **Score:** 2/2
- **Evidence:** The user specified no explicit format, length, tone, or output structure constraints beyond requesting concrete approaches. The response is structured with clear headers and readable prose.
- **Justification:** No formatting, length, or exclusion constraints were specified in the query beyond the substance of the answer. The response's format is internally consistent and professional. The instruction-following failure, if any, is absorbed under Relevance: the user said "not just a general explanation," but this is a substantive content constraint that Relevance captures, not a formatting constraint for Instruction Following.
- **Failure Mode:** None.

---

### 5. Reasoning Quality
- **Score:** 2/2
- **Evidence:** The response proceeds logically: from the definition of rate limiting → to why it exists → to how it is implemented algorithmically → to OpenAI's specific structure → to HTTP standard context → to general guidance. Each section builds coherently on the prior.
- **Justification:** Evaluated on the observable reasoning presented in the final output: the conceptual explanation is internally coherent, the progression from abstract to specific is logically sound, and there are no non-sequiturs or contradictions. The response applies its (misdirected) knowledge accurately. The fact that this reasoning addresses the wrong topic is captured under Relevance, not Reasoning Quality.
- **Failure Mode:** None.

---

### 6. Hallucination / Unsupported Claims
- **Score:** 2/2
- **Evidence:** The response attributes HTTP 429 to RFC 6585 (correct), describes standard rate-limiting algorithms accurately, and correctly identifies OpenAI's RPM/TPM/RPD rate limit dimensions without fabricating benchmark data, fake URLs, or non-existent features.
- **Justification:** All claims are verifiable and accurate. No external studies, fictional products, or invented statistics are introduced. The response's entire failure is in what it chose to discuss, not in whether what it said about that topic is fabricated.
- **Failure Mode:** None.

---

### 7. Clarity and Communication
- **Score:** 2/2
- **Evidence:** The response uses clear section headers, consistent bullet formatting for the "why APIs implement rate limits" list, and clean prose throughout.
- **Justification:** Setting aside its complete misdirection, the response is professionally structured and easy to read. A developer wanting to learn about rate limiting conceptually would find it highly useful. This dimension scores on the quality of the communication itself, not the appropriateness of the topic.
- **Failure Mode:** None.

---

## Critical Failure Check

- **Triggered:** **No**
- **Reason:** The Critical Failure Override applies only when a response scores **0 in Factual Accuracy (Dimension 1)** or **0 in Hallucination / Unsupported Claims (Dimension 6)**. This response scores:
  - Factual Accuracy: **2** — Override condition not met.
  - Hallucination: **2** — Override condition not met.
- **Impact:** The Critical Failure Override does **not** engage. A score of 0 in Relevance does not activate the override. The raw composite score determines the final verdict without adjustment.
- **Methodological note:** This is the third case (alongside Cases 002 and 003) to score 0 in a non-override dimension without triggering the cap. Cases 001 and 004 triggered the override via D1=0 and D6=0 respectively. The pattern across five cases fully maps the override's scope: it activates for factual reliability failures only.

---

## Composite Score

| Dimension | Score | Max |
|---|---|---|
| 1. Factual Accuracy | 2 | 2 |
| 2. Relevance | 0 | 2 |
| 3. Completeness | 1 | 2 |
| 4. Instruction Following | 2 | 2 |
| 5. Reasoning Quality | 2 | 2 |
| 6. Hallucination / Unsupported Claims | 2 | 2 |
| 7. Clarity and Communication | 2 | 2 |
| **Total** | **11** | **14** |

**Raw Score:** 11 / 14  
**Raw Verdict Category:** Good (10–12 range)  
**Critical Failure Override:** Not Triggered  
**Final Verdict: Good**

---

## Detailed Relevance Failure Analysis

### The Core Drift

The user's query contains a precise, actionable task: implement production-grade error handling for a specific HTTP error in a specific programming context. The prompt even anticipates the most common failure mode and explicitly disallows it: *"I need concrete approaches, not just a general explanation."*

The AI responded with a general explanation.

### What the Response Covers vs. What Was Asked

| Topic | Asked? | Covered? |
|---|---|---|
| What rate limiting is | No | Yes — extensively |
| Why APIs implement rate limiting | No | Yes — extensively |
| Token bucket / leaky bucket algorithms | No | Yes — in detail |
| OpenAI's rate limit tiers and dimensions | Implicitly useful | Yes |
| RFC reference for HTTP 429 | No | Yes |
| Retry-After header behavior | Partially yes | One sentence — no implementation |
| Exponential backoff with jitter | Yes | No |
| Client-side request queuing | Yes | No |
| Circuit breaker pattern | Yes | No |
| Python implementation libraries (tenacity, backoff) | Yes | No |
| Reading response headers in Python | Yes | No |
| Production error handling patterns | Yes | No |

The response provides deep coverage of five topics the user did not ask about, and zero coverage of the six most important topics the user did ask about.

### Why This Pattern Occurs

This is a realistic failure mode caused by the AI anchoring on the surface subject ("rate limiting") rather than the user's actual task ("handle this error in production"). The model generates high-quality content about the topic area while missing the user's intent about *what to do* with that topic.

---

## Overall Verdict

This case demonstrates a subtle but practically significant failure: **knowing about something is not the same as answering a question about it**. The AI clearly has substantial knowledge of API rate limiting — its conceptual explanation is accurate, well-organized, and clearly communicated. But the user did not ask to be educated about rate limiting. They asked how to fix a production problem.

The composite score reaches 11/14, placing the final verdict at **Good** — identical to Cases 002 and 003, which suffered from instruction-following and reasoning failures respectively. The Critical Failure Override does not engage. A developer receiving this response has been handed a technically correct primer on a topic they already understood (they are experiencing the error, not confused about what it is), with no actionable guidance on their actual problem.

The portfolio now demonstrates a consistent pattern: **five of the seven rubric dimensions can fail at their maximum severity (score = 0) without triggering the Critical Failure Override**, which is narrowly scoped to Dimensions 1 and 6.

---

## Evaluation Conclusion

**Methodological Lesson:** Relevance is the dimension that tests whether the model understood *the user's task*, not just *the user's topic*. A model can produce a fully accurate, well-written response within the correct subject area while completely failing to address the user's actual task intent — and still receive a "Good" final verdict because Relevance = 0 does not trigger the Critical Failure Override. Evaluators and system designers who rely solely on overall scores without inspecting individual dimension scores will miss this failure entirely. Relevance must be evaluated as an independent primary criterion, not inferred from the quality of the content the model did produce.
