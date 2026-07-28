# Lab 1, Ascend Analytics Coverage Matrix

**Product:** Competitor Signal Tracker (Internal)

## Coverage row

| Product | Hallucination | Bias | Latency | Toxicity | Drift Monitoring |
| --- | :---: | :---: | :---: | :---: | :---: |
| Competitor Signal Tracker (Internal) | ✅ | ⚠️ | ✅ | ❌ | ❌ |

## Method + Ground Truth (two ✅/⚠️ cells)

### Hallucination Rate
- **Method:** Hybrid evaluation combining deterministic citation-coverage checks with an LLM-as-a-Judge that compares each competitive claim against the retrieved source evidence.
- **Ground truth:** Pass = 100% of factual competitive claims include at least one valid citation, every claim is supported by the cited evidence, and the unsupported-claim rate is 0%.

### Bias (Fairness)
- **Method:** Monthly human review of a layered sample covering major competitors, company sizes, geographic regions, source types, and positive, neutral, and negative competitive signals.
- **Ground truth:** Pass = no competitor or market segment shows an unexplained difference greater than 10% in classification error or negative-signal rate after controlling for the underlying source evidence.

## Strategic acceptance

**Accepted gap:** Toxicity (UX Trust)

We are willing to accept this gap temporarily because the product is internal, its primary users are trained Sales and Strategy employees, and its inputs come mainly from professional public sources. The expected impact is lower than unsupported claims or model drift, so current resources should be directed toward grounding and robustness. Human review and access controls provide interim safeguards.

## Critical mitigation

**Critical gap:** Drift Monitoring (Robustness)

**Why critical:** We have flagged drift monitoring as the most critical gap because competitor language, news sources, market conditions, and signal patterns change continuously. Undetected degradation could systematically misclassify competitive movements and influence sales positioning, strategic planning, and investment decisions at scale.

**Mitigation plan:** To close this gap, we will create a drift-evaluation suite using a versioned gold dataset of at least 500 competitive signals, segmented by competitor, industry, geography, source type, signal category, and sentiment. Each item will have a human-verified classification and score. The suite will run weekly and after every model, prompt, or data-pipeline change. It will also evaluate a rolling sample of production signals each month. An absolute classification-accuracy drop greater than 5 percentage points, or a greater than 10% error increase for any monitored segment, will trigger investigation and block further rollout until reviewed.
