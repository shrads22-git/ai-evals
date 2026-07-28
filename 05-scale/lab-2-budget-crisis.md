# Lab 2, Ascend IQ Budget Crisis

**Quarterly budget cap:** $200,000
**Total Level 3 spend:** $175,000 (3 of max 3 slots used)

## Portfolio decision grid

| Failure | Trust metric | Risk | Level | Cost |
| --- | --- | :---: | :---: | ---: |
| Data Fabrication | Hallucination Rate | P0 | L3 | $85,000 |
| Context Specificity | UX Trust | P1 | L2 | $7,000 |
| Source Attribution Failure | Robustness | P1 | L3 | $65,000 |
| Data Bias | Fairness | P2 | L2 | $5,500 |
| Cost Overruns | Latency | P3 | L3 | $25,000 |

## Fallback methods (non-Level 3 items)

### L2 · Context Specificity (UX Trust · P1)
- **Method:** Run a weekly LLM-as-a-Judge audit of 100 segmented  production outputs. Sample across request types, clients, competitors, and complexity levels. The judge will compare each response with the user's requested scope and score instruction adherence, relevance, and completeness. A human reviewer will examine every failed or borderline result.
- **Why this fallback is defensible:** Pass = at least 95% of sampled responses satisfy the requested scope, with no single request category falling below 90%. A breach triggers prompt remediation and an expanded audit.

### L2 · Data Bias (Fairness · P2)
- **Method:** Run a weekly audit of 100 outputs balanced across US, APAC, EMEA, company size, industry, source type, and signal sentiment. Compare source representation, omission rates, classification accuracy, and positive/negative signal distribution across geographic segments. A human analyst will investigate disparities greater than 10%.
- **Why this fallback is defensible:** Bias can distort strategic insights, but this internal product has trained analysts who can review findings before external use. Geographic bias also requires aggregate comparison across a representative sample rather than continuous evaluation of individual outputs. A structured weekly audit is therefore more useful and cost-effective than evaluating every response independently.

For Threshold: Pass = no region has an unexplained difference greater than 10% in source representation, omission rate, or classification error after controlling for available source evidence.
