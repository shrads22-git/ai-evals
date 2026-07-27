## Extra Practice - Formal Eval Threshold

### Feature

**Citation-Backed Competitor Pricing Comparison**

This feature answers questions about competitor pricing using approved source evidence.

### Metric

**Pricing Groundedness Pass Rate**

```text
Pricing Groundedness Pass Rate =
Number of cases that pass all grounding requirements
÷
Total number of evaluated cases
× 100
```

A case passes only when:

* Every price, currency, billing period, plan and seat requirement matches the approved evidence
* Every pricing claim includes the required citation
* The model correctly abstains when evidence is missing, stale or conflicting
* The response does not introduce unsupported discounts, fees or pricing details

### Threshold

**Pricing Groundedness Pass Rate = 100%**

All 20 dataset cases must pass:

```text
20 passing cases ÷ 20 total cases = 100%
```

Supporting requirements:

* Citation Coverage = 100%
* Unsupported Pricing Claims = 0
* Correct Abstention Rate = 100% for applicable cases

### Method

1. Run all 20 cases against the model candidate in Staging.
2. Use deterministic checks to compare structured pricing details with the approved evidence.
3. Use a calibrated LLM-as-a-Judge to evaluate grounding, citation support and correct abstention.
4. Treat a case as failed if either the deterministic evaluator or groundedness judge detects an unsupported pricing claim.
5. Require Cohen’s κ ≥ 0.6 between the LLM judge and human reviewers before using the judge for release decisions.

### Dataset

**Ascend IQ Pricing Golden Set v1**

File:

```text
04-eval-gates/datasets/ascend-iq-pricing-golden-v1.csv
```

The versioned dataset contains 20 cases covering current pricing, stale pricing, missing and conflicting evidence, currencies, billing periods, seat minimums, discounts, regional pricing, competitor comparisons and correct abstention.

### Gate Severity

* **Severity:** Hard Gate — Blocker
* **Pipeline placement:** Staging Build
* **Failure action:** Block production deployment if any case fails

### Formal PRD Requirement

> The Ascend IQ Citation-Backed Competitor Pricing Comparison feature must achieve a 100% Pricing Groundedness Pass Rate on the Ascend IQ Pricing Golden Set v1. All 20 cases must pass, citation coverage must equal 100%, and unsupported pricing claims must equal zero. The threshold is measured using deterministic pricing validation and a calibrated LLM-as-a-Judge. This is a Hard Gate in Staging, and any failure blocks production deployment.