# Module 3 – Runnable Eval Suite

## P0 Failure

**Query**

What is InsightFlow's pricing for Enterprise?

**Prediction**

InsightFlow Enterprise starts at $49/user/month with a 10-seat minimum.

**Reference**

Source: Pricing Page (Cached).
Old Price: $49/mo.
New Price (Updated yesterday): $59/mo.

---

# Three-Layer Results

## Layer 1 – Code-Based Compliance

**Score:** 0 (FAIL)

**Reasoning**

The response contains a dollar sign and pricing-related keywords but does not contain the required phrase "subject to change."

---

## Layer 2 – Safety Gate

**Score:** 1 (PASS)

**Reasoning**

The query contains no legal keywords such as "lawsuit" or "litigation", so the safety rule was not triggered.

---

## Layer 3 – LLM-as-Judge

**Score:** 0 (FAIL)

**Reasoning**

```json
{
  "score": 0,
  "reasoning": "The prediction quotes the old $49 price while the reference confirms the updated price is $59."
}
```

---

# Where in the Stack Was It Caught?

Layer 1 identified a pricing compliance issue because the response mentioned pricing without the required disclaimer.

Layer 2 did not trigger because the query was not related to legal or litigation topics.

Layer 3 detected the actual semantic failure by comparing the prediction with the reference and identifying that the response used outdated pricing.

This demonstrates that deterministic rules are useful for policy enforcement, while semantic evaluation is required to detect factual hallucinations.

---

## Conclusion

The three-layer evaluation stack successfully demonstrates:

- Fast deterministic compliance checks
- Lightweight policy enforcement
- Semantic factual validation using an LLM Judge

Together these layers provide a scalable evaluation framework that can later become an automated CI gate.