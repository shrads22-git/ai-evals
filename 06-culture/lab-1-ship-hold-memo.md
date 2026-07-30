# Ship/Hold Memo · Ascend IQ

> **Decision:** 🛑 HOLD

**To:** CPO · cc Engineering Lead, QA / AI Evaluation Lead  
**From:** Shraddha Jadhav · AI Evals Cohort · July 30, 2026

## The Answer

I recommend we HOLD the full launch of Ascend IQ because the current evaluation evidence includes an enterprise-pricing hallucination that violates our zero-tolerance hard gate and creates unacceptable customer-trust risk. Audit found a fabricated enterprise price,  M4 hard gate requires Pricing Hallucination Rate = 0%. We cannot honestly recommend SHIP while that blocker remains.

## The Arguments

### 1. Customer trust is at risk because pricing hallucinations remain unresolved.

Our Module 2 audit identified an unsupported enterprise-pricing claim, along with other factual hallucinations. Because enterprise customers may use Ascend IQ for strategic decisions, presenting invented pricing as fact could undermine product credibility and customer confidence. This directly violates the zero-tolerance pricing-hallucination gate established in Module 4.

### 2. Release readiness has not been demonstrated against the required grounding gates.

Module 3 defines clear release requirements of 100% citation coverage and zero unsupported competitive claims. However, the current artifacts do not contain a completed candidate evaluation proving that Ascend IQ meets those thresholds. Shipping without that evidence would mean approving the launch based on defined controls rather than demonstrated results.

### 3. Post-launch degradation could go undetected because drift monitoring is not yet implemented.

The Module 5 Coverage Matrix identifies drift monitoring as the most critical coverage gap. Competitor information, sources, and market conditions change continuously, so undetected drift could systematically degrade classification quality and influence sales or strategy decisions. The planned weekly drift suite and versioned 500-item gold dataset should be implemented before broader rollout.

## Evidence · Trust Metrics

```
- Pricing groundedness: 1 verified unsupported pricing failure (Gate: 20/20 cases pass, 100% groundedness, 0 unsupported pricing claims) ✗ FAIL · Source: M4 Gate Map, Row 01 + Formal Eval Threshold
- Citation coverage: Candidate result not yet documented (Gate: 100%) ✗ NOT DEMONSTRATED · Source: M3 Eval Spec
- Judge calibration: Cohen’s κ = -0.29 (Gate: κ ≥ 0.60) ✗ FAIL · Source: M3 Judge Calibration, 12 traces
- Judge-human raw agreement: 50%, with 6 disagreements across 12 traces · Source: M3 Judge Calibration
- Response latency: 4.2 seconds in the verified latency failure (Gate: ≤ 2.0 seconds) ✗ FAIL · Source: M4 Gate Map, Row 03
- Drift-monitoring coverage: Not implemented (Required mitigation: weekly drift suite using a versioned dataset of at least 500 signals) ✗ COVERAGE GAP · Source: M5 Coverage Matrix
```

## Business Risk

HOLD path: The launch is delayed while the team reruns all 20 pricing golden-set cases, improves judge calibration from κ = -0.29 to at least 0.60, and establishes the planned 500-signal drift dataset. This creates short-term schedule and competitive-window risk but prevents deployment before the hard gates are satisfied.

## Next Step · Decision Needed

Approve the launch hold by EOD Friday, July 31, 2026. Engineering and the AI Evaluation Lead must rerun the 20-case pricing golden set, demonstrate 100% pricing groundedness and citation coverage, achieve judge calibration of κ ≥ 0.60, and present the results for a new ship/hold review before production deployment.

## Reflection

Defining “good enough” forced me to distinguish between having an evaluation framework and having evidence that the product actually passes it. The team had created measurable gates, but the capstone showed that a documented threshold alone does not create launch confidence the model candidate must pass the gate, and the evaluator enforcing it must also be calibrated and trustworthy.
