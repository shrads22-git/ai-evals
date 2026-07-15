# Operationalize "Good"

## 1. Verified Insights

**Qualitative Goal:** Deliver verified, citation-backed competitive intelligence.

**Pass if:**
- Every factual claim is supported by at least one citation from the provided source documents.
- No unsupported or fabricated information is included.

**Fail if:**
- Any factual claim lacks a supporting citation.
- The response contains hallucinated or contradictory information.

**Quantitative Metric:**
- **Hallucination Rate** = (Responses containing unsupported factual claims ÷ Total responses) × 100%
- **Target:** ≤ 1%

---

## 2. Instant Answers

**Qualitative Goal:** Deliver answers quickly enough to eliminate the need for manual research.

**Pass if:**
- The response is returned within **5 seconds** at the P95 latency.

**Fail if:**
- The P95 response time exceeds **5 seconds**.

**Quantitative Metric:**
- **P95 Response Latency**
- **Target:** ≤ 5 seconds

---

## 3. Confident Strategic Decisions

**Qualitative Goal:** Enable users to confidently trust the AI's recommendations.

**Pass if:**
- Every recommendation is supported by citations.
- The response clearly communicates uncertainty when evidence is incomplete or conflicting.
- No unsupported recommendations are presented as facts.

**Fail if:**
- Recommendations lack supporting evidence.
- Uncertainty is omitted when evidence is insufficient.
- The response presents speculative information as certain.

**Quantitative Metric:**
- **UX Trust Score** = (Responses meeting all trust criteria ÷ Total responses) × 100%
- **Target:** ≥ 95%