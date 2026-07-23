# M3 · Lab 2 · Eval Spec – Ascend IQ P0

## Part 1 · The 5-Part Eval Spec

### 1. Target Risk

**Failure Mode**

Hallucinated competitive insights that are not supported by retrieved evidence.

**Risk Type**

Output

**Trust Metric**

UX Trust

---

### 2. Evaluator

**Type**

Hybrid (Code + LLM-as-Judge)

**Detection Logic**

- The **Code Evaluator** parses every declarative factual statement comparing Ascend IQ with a competitor.
- Each competitive claim must reference at least one citation ID returned by the retrieval system.
- The **LLM-as-Judge** (using a different model family than the generation model) verifies that each cited source actually supports the claim.
- The evaluation fails if any competitive claim lacks a valid citation or contradicts the cited evidence.

---

### 3. Threshold

**Metrics**

- **Citation Coverage**

  ```
  Citation Coverage =
  (# factual competitive claims with at least one valid supporting citation)
  ÷
  (Total factual competitive claims)
  × 100%
  ```

- **Required Threshold:** **100%**
- **Unsupported Factual Claims:** **0**
- **LLM-as-Judge Agreement:** Cohen's κ ≥ **0.6**

**Strategy**

Safety First (Maximize True Positive Rate)

---

### 4. Business Stakes

Unsupported competitive insights:

- Reduce executive trust.
- Increase the risk of incorrect strategic decisions.
- Damage product credibility.
- Negatively impact enterprise renewals and customer confidence.

---

### 5. Owner

**Primary Owner**

- AI Product Manager (Ascend IQ)

**Reviewers**

- Engineering Lead
- QA / AI Evaluation Lead

---

# Part 2 · Three Audience Messages

## A. Engineering (Jira Ticket)

### Definition

A **competitive claim** is a factual statement about a competitor or a factual comparison between Ascend IQ and a competitor.

### Acceptance Criteria

**IF** the response contains one or more competitive claims,

**THEN** every competitive claim must:

- Reference at least one retrieved citation.
- Be fully supported by the cited evidence.

**IF** any competitive claim:

- lacks a supporting citation, **OR**
- contradicts the cited evidence,

**THEN**

- Suppress the unsupported statement.
- Replace it with:

> Unable to verify this insight from available sources.

### Release Criteria

- Citation Coverage = **100%**
- Unsupported Competitive Claims = **0**

---

## B. UX / Design

When a competitive insight cannot be verified:

Replace only the unsupported statement with:

> We couldn't verify this competitive insight using our available sources. You can review the supporting evidence below or refresh the search to retrieve newer information.

### Actions

- View Sources
- Refresh Search
- Continue Conversation

### UX Requirements

- Never display raw evaluator failures, stack traces, or internal validation messages.
- Preserve conversation context.
- Allow users to continue asking follow-up questions without restarting the conversation.

---

## C. Leadership (Bi-Weekly Update)

Implemented a citation-backed evaluation gate that prevents unsupported competitive intelligence from reaching enterprise customers.

### Release Requirements

- 100% Citation Coverage
- Zero Unsupported Competitive Claims

### Business Impact

This evaluation gate:

- Protects customer trust.
- Reduces reputational risk.
- Improves confidence in strategic decision-making.
- Helps safeguard enterprise renewals by ensuring all competitive insights are evidence-backed.

---

## Self-Review Checklist

- [x] P0 failure mode is clearly defined.
- [x] Risk type is classified as **Output**.
- [x] Thresholds are measurable and objective.
- [x] Detection logic combines deterministic rules with semantic validation.
- [x] Engineering requirements are written as binary acceptance criteria.
- [x] UX defines a graceful fallback without exposing internal errors.
- [x] Leadership update emphasizes business value rather than implementation details.
- [x] Ownership and accountability are clearly assigned.

---

_Save this as `03-eval-suites/lab-2-eval-spec.md` in your repository._

_Generated for the AI Evals Certification · Module 3 Lab 2_
