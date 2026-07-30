# AI Evals Portfolio

This repository contains my projects and hands-on exercises completed as part of an AI Evaluation course. The goal is to learn how to design, build, evaluate, and operationalize evaluation frameworks for Large Language Models (LLMs) and AI agents.

## Objectives

Through these projects I am learning how to:

- Define evaluation strategies for AI applications
- Build high-quality evaluation datasets using LangSmith
- Create automated evaluation harnesses
- Design evaluation metrics and success criteria
- Audit model failures and categorize trust risks
- Operationalize AI evaluations in development workflows
- Improve model quality using systematic evaluation

## Repository Structure

```
Module 1: 01-evaluation-strategy/
├── strategy-canvas.md
├── starter-email-dataset.md
├── sample-email.md
├── eval-harness-proof.md
├── operationalize-good.md
└── screenshots/

Module 2: 02-failure-discovery/
├── audit-log.md
├── failure-taxonomy-canvas.md
└── latency-log.md

Module 3: 03-eval-suites/
├── lab-1a-eval-suite.md
├── lab-1b-trajectory.md
├── lab-2-eval-spec.md
└── lab-judge-calibration.md

Module 4: 04-eval-gates/
├── datasets/
│   └── ascend-iq-pricing-golden-v1.csv
├── lab-1-gate-map.md
├── lab-2-launch-strategy.md
└── lab-3-extra-practice-formal-eval-threshold.md

Module 5: 05-scale/
├── lab-1-coverage-matrix.md
└── lab-2-budget-crisis.md

Module 6: 06-culture/
├── lab-1-ship-hold-memo.md
└── lab-2-final-pitch.html
```
---

## Projects

### Module 1 – Evaluation Strategy

This project includes:

- Product evaluation strategy
- Success metrics based on Latency, Hallucination, UX Trust, Robustness, and Fairness
- Trade-off analysis
- Starter evaluation dataset
- Evaluation harness using LangSmith
- Documentation and supporting screenshots

---

### Module 2 – Failure Discovery

This project focuses on auditing model outputs to identify quality issues and build a structured failure taxonomy.

It includes:

- Manual audit of 20 LLM evaluation results
- Comparison of LLM-as-Judge scores with human review
- Failure categorization using Trust Metrics
- Hallucination, Robustness, and Fairness analysis
- Latency analysis using a defined SLA (≤ 3.5 seconds)
- Failure Taxonomy Canvas documenting the highest-risk failure categories

---

### Module 3 – Evaluation Design & Calibration

This module focuses on designing production-ready evaluation systems and improving evaluator reliability.

It includes:

#### Runnable Evaluation Suite

- Created runnable evaluation scenarios for grounded and ungrounded responses
- Compared predictions against reference answers
- Identified failure locations across the evaluation pipeline
- Practiced structured PASS / FAIL evaluation using LLM-as-a-Judge

#### Evaluation Specification

Designed an evaluation specification for **Ascend IQ**, including:

- P0 Risk identification
- Citation Coverage metric
- Evaluation methodology
- Acceptance thresholds
- Engineering requirements
- UX behavior
- Leadership communication

#### Judge Calibration

Evaluated 12 Atlas traces by comparing human judgments with an LLM judge.

Topics covered:

- Human-in-the-loop evaluation
- PASS / FAIL rubric design
- Cohen's κ agreement
- Judge disagreement analysis
- Rubric refinement
- Calibration examples

**Key takeaway**

> A judge should reward grounded answers, penalize unsupported claims, and correctly handle situations where the retrieved evidence is insufficient.

---

### Module 4 - Ship Safely with Eval Gates

This module focuses on translating evaluation risks into enforceable CI/CD gates and measurable PRD release criteria.

It includes:

#### Eval Gate Mapping

* Classified verified failures as Hard, Soft, or Advisory gates
* Connected each failure to revenue, legal, brand, or customer-experience risk
* Selected the appropriate pipeline placement: PR, Staging, or Release
* Excluded correct safety behavior from gating to prevent false failures and alert fatigue

#### Launch Strategy and Release Criteria

Defined measurable launch requirements for Ascend IQ:

| Gate     | Risk                        | Metric                      | Threshold     | Enforcement                           |
| -------- | --------------------------- | --------------------------- | ------------- | ------------------------------------- |
| Hard     | Stale pricing hallucination | Pricing Hallucination Rate  | = 0%          | Blocks release                        |
| Soft     | Response latency            | P95 Response Latency        | ≤ 2.0 seconds | Requires mitigation before proceeding |
| Advisory | Off-brand tone              | Brand-Voice Compliance Rate | ≥ 95%         | Warns without blocking                |

The CI policy distinguishes between absolute blockers, conditional approvals, and monitoring signals:

* Pricing hallucinations block the build with no exception
* Latency failures require an approved Staged Rollout mitigation
* Tone failures generate warnings for future prompt and rubric improvements

#### Mitigation Planning

Selected a **Staged Rollout** for latency failures. If P95 latency exceeds 2.0 seconds in two consecutive performance tests, availability is limited to a controlled user group while Engineering investigates performance bottlenecks.

**Key takeaway**

> Eval gates convert evaluation results into enforceable launch decisions: Hard Gates block unacceptable risk, Soft Gates require mitigation, and Advisory Gates provide monitoring signals without stopping delivery.

---

### Module 5 – Scaling Evaluation Coverage

This module focuses on scaling evaluation across multiple trust risks while making explicit coverage and budget trade-offs.

It includes:

#### Coverage Matrix

- Mapped coverage across hallucination, bias, latency, toxicity, and drift monitoring
- Defined evaluation methods and ground truth for covered risks
- Accepted the temporary toxicity-coverage gap for an internal product with trained users and human oversight
- Identified missing drift monitoring as the most critical coverage gap
- Proposed a weekly drift-evaluation suite using a versioned gold dataset of at least 500 competitive signals

#### Evaluation Budget Allocation

Allocated a `$200,000` quarterly evaluation budget across five failure categories:

| Evaluation | Level | Cost |
| --- | :---: | ---: |
| Data Fabrication / Hallucination | L3 | $85,000 |
| Source Attribution Failure | L3 | $65,000 |
| Cost Overruns / Latency | L3 | $25,000 |
| Context Specificity | L2 | $7,000 |
| Data Bias | L2 | $5,500 |

- Total L3 investment: `$175,000`
- Total portfolio investment: `$187,500`
- Remaining budget: `$12,500`

**Key takeaway**

> Scaling evaluation requires prioritizing the highest-impact risks, accepting lower-cost coverage where defensible, and making critical monitoring gaps visible rather than claiming complete coverage.

### Module 6 – Ship/Hold Decision and Final Pitch

This capstone combines the strategy, failure analysis, evaluation results, release gates, coverage decisions, and budget allocation from Modules 1–5 into an executive launch recommendation for Ascend IQ.

#### Ship/Hold Memo

Applied the Pyramid Principle to create an executive-ready decision memo that:

- Leads with a clear **HOLD** recommendation
- Organizes the reasoning around customer trust, release readiness, and operational control
- Compares evaluation results against explicit release gates
- Distinguishes between defined evaluation controls and demonstrated passing evidence
- Ends with a specific remediation plan and decision deadline

The launch was held because:

- A verified unsupported enterprise-pricing response violated the zero-tolerance pricing gate
- Pricing groundedness and citation coverage were not demonstrated across the complete golden set
- Judge calibration achieved Cohen’s κ = `-0.29`, below the required `≥ 0.60`
- The trajectory evaluation passed only `1 of 6` dimensions
- A verified latency case took `4.2 seconds` against the `≤ 2.0-second` gate
- Drift monitoring had not yet been implemented

#### Final Executive Pitch

Created a shareable HTML presentation that communicates:

- The Ascend IQ user promise and evaluation strategy
- The primary failure taxonomy and business impact
- Evaluation-suite and judge-calibration results
- Hard, Soft, and Advisory release gates
- Portfolio-level coverage and budget decisions
- The final evidence-based HOLD recommendation
- Required remediation before the next ship review

- [Read the Ship/Hold Memo](06-culture/lab-1-ship-hold-memo.md)
- [Open the Final Pitch Deck](06-culture/lab-2-final-pitch.html)

**Key takeaway**

> A release threshold is not evidence that a product is ready. The model candidate must pass the gate, and the evaluator enforcing that gate must also be reliable and calibrated.
---

## Skills Practiced

- AI Evaluation using LangSmith (Playground, Datasets, Experiments, Evaluations, LLM-as-a-Judge, and Tracing)
- Evaluation Strategy Design
- Evaluation Specification Design
- Judge Calibration
- Failure Analysis
- Human-in-the-Loop Evaluation
- Prompt Engineering
- Dataset Creation
- LLM Testing
- AI Agent Development
- Tool Calling
- Trajectory Evaluation
- Trust Metrics
- Latency Analysis
- Quality Metrics
- Eval Gate Design
- Risk-Based Release Criteria
- CI/CD Quality Gates
- Pipeline Gate Placement
- PRD Metric and Threshold Definition
- Mitigation and Staged Rollout Planning
- Git & GitHub
- Markdown Documentation
- LangChain
- LangGraph
- Evaluation Coverage Strategy
- Evaluation Portfolio Prioritization
- Evaluation Budget Allocation
- Drift Monitoring Design
- Executive Ship/Hold Decision-Making
- Pyramid Principle Communication
- Evidence-Based Launch Recommendations
- Executive AI Evaluation Storytelling

> **Note:** Current evaluations use OpenAI as both the model provider and the LLM-as-Judge. Future work will explore independent judge models, multi-model evaluation, and production-style agent evaluation to reduce evaluator bias.

---

## Tools

- OpenAI
- LangSmith
- LangChain
- LangGraph
- GitHub
- Visual Studio Code

---

## Status

## Status

- ✅ Module 1 – Evaluation Strategy
- ✅ Module 2 – Failure Discovery
- ✅ Module 3 – Evaluation Design & Judge Calibration
- ✅ Module 4 – Ship Safely with Eval Gates
- ✅ Module 5 – Scale Evaluation Coverage
- ✅ Module 6 – Ship/Hold Memo and Final Pitch

The six-module capstone demonstrates an end-to-end AI evaluation lifecycle: strategy, failure discovery, evaluation design, release gating, portfolio scaling, and evidence-based launch decision-making.
