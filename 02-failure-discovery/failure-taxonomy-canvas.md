# Failure Taxonomy Canvas

## Product
Ascend IQ

## Top 3 Failure Categories

| Rank | Trust Metric | Frequency | User Impact | Example | Mitigation |
|------|--------------|----------:|------------|---------|------------|
| 1 | Hallucination | 7 | High | Invented Enterprise pricing | Strengthen retrieval grounding, require citation-backed responses, improve prompts |
| 2 | Robustness | 1 | Medium | Biased response to negative prompt | Improve system prompts and add adversarial test cases |
| 3 | Fairness | 0 | Low | No failures observed | Continue monitoring with diverse evaluation datasets |

## Key Findings

- Hallucination was the dominant failure mode (87.5% of all failures).
- No human overrides were required.
- The LLM-as-Judge agreed with human review on all evaluations.
- No fairness issues were identified in the current evaluation dataset.

## Recommendations

1. Prioritize reducing hallucinations through retrieval-augmented generation (RAG) and citation verification.
2. Expand robustness testing with adversarial and ambiguous prompts.
3. Continue monitoring fairness using a more diverse evaluation dataset.
4. Track latency alongside quality metrics to ensure performance improvements do not reduce answer quality.
