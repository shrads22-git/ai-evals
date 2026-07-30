# Ascend IQ: Evidence-Based Ship/Hold Decision

> An AI copilot that delivers verified, citation-backed competitive intelligence to enterprise strategists in under five seconds.

**Shraddha Jadhav · AI Evals Cohort · July 2026** · https://github.com/shrads22-git/ai-evals

---

## Final Project Deliverables

### Slide 5 · Strategy (Module 1)
- **User + use case:** VP-level strategists and product leaders at Fortune 500 companies who need to quickly extract verified insights, such as competitor-pricing comparisons and summaries of customer reviews, without conducting manual research.
- **Definition of "good":** Ascend IQ delivers verified, citation-backed competitive intelligence in under five seconds, enabling enterprise strategists to make high-stakes decisions confidently without manual data gathering.
- **Top 3 trust metrics:** 1) Hallucination Rate · percentage of outputs containing false or fabricated claims · 2) UX Trust · predictable, evidence-backed responses with transparent citations and uncertainty· 3) P95 Response Latency · speed of delivering useful competitive intelligence
- **Two trade-offs:**
  1) Hallucination Rate over Latency: We accept a slower response rather than risk presenting a fabricated competitor claim.
  2) UX Trust over Latency: We prioritize transparent citations and clear uncertainty, even when verification adds response time.
- **Canvas link:** https://github.com/shrads22-git/ai-evals/blob/main/01-evaluation-strategy/strategy-canvas.md

### Slide 6 · Risks (Module 2)
- Hallucinated or unsupported competitive claims · P0 · 7 of 20 audited outputs failed for hallucination (35%); hallucinations represented 87.5% of all observed failures.
- Robustness failure under a negatively framed prompt · P1 · 1 of 20 audited outputs (5%) used biased and unprofessional language instead of providing a neutral comparison.
- Fairness coverage gap · P2 · 0 failures observed in the 20-case audit, but the dataset was not broad enough to establish consistent performance across regions, languages, competitors, and market segments.

**Business impact:** Unsupported competitive claims matter because enterprise strategists may use Ascend IQ for decisions worth more than $1M; a single fabricated statistic can undermine confidence in the product and jeopardize a $50K+ enterprise contract.

**Canvas link:** https://github.com/shrads22-git/ai-evals/blob/main/02-failure-discovery/failure-taxonomy-canvas.md

### Slide 7 · Proof (Module 3 · LangSmith)
The three-layer evaluation caught a stale enterprise-pricing response: the code-based compliance check failed, the safety gate passed because the request was not a safety-policy case, and the LLM judge failed the response for returning the outdated $49 price instead of the current $59 price. The trajectory evaluation passed only 1 of 6 dimensions and produced a HOLD verdict because the agent returned a correct-looking answer without completing the required verification path. Judge calibration also failed: Cohen’s κ was -0.29 against the required ≥ 0.60 gate, with only 50% raw agreement and 6 disagreements across 12 traces. These results show that both the model behavior and the evaluator require remediation before release.

Screenshots: https://github.com/shrads22-git/ai-evals/blob/main/01-evaluation-strategy/screenshots/evaluations.png, https://github.com/shrads22-git/ai-evals/blob/main/01-evaluation-strategy/screenshots/eval-setup.png

### Slide 8 · Standards (Module 4)
- **Threshold:** Target risk: Unsupported or stale competitor-pricing claims. The feature must achieve a 100% Pricing Groundedness Pass Rate on all 20 cases in the Ascend IQ Pricing Golden Set v1, with 100% citation coverage, zero unsupported pricing claims, and correct abstention whenever evidence is missing, stale, or conflicting.
- **Gate action:** Treat this as a Hard Gate in the Staging Build. If any of the 20 pricing cases fails deterministic validation or semantic grounding review, block production deployment. The LLM judge may enforce the release gate only after achieving Cohen’s κ ≥ 0.60 against human reviewers.
- **Why this strictness:** Ascend IQ supports enterprise strategists making high-stakes competitive decisions. An invented price, discount, billing period, or seat requirement can mislead customers and immediately damage trust. Consistent with the M1 strategy, we prioritize groundedness and UX trust over speed: an explicit “unable to verify” response is safer than a fluent but unsupported answer.

### Slide 9 · Decision (Modules 5 + 6)
**Final call:** HOLD · critical grounding, judge-calibration, latency, and drift-monitoring requirements are not yet met

**The Answer:** I recommend we HOLD the full launch of Ascend IQ because the current evaluation evidence includes an enterprise-pricing hallucination that violates our zero-tolerance hard gate and creates unacceptable customer-trust risk.

**Arguments:**
1. Customer trust is at risk because an unresolved pricing hallucination violates the hard release gate.
2. Release readiness has not been demonstrated: 100% pricing groundedness and citation coverage are required, while judge calibration failed with κ = -0.29 against the ≥ 0.60 gate.
3. Post-launch quality degradation could go undetected because the critical drift-monitoring control and planned 500-signal dataset are not yet implemented.

**Close:** SHIP would expose enterprise users to one verified unsupported pricing response, a judge with only 50% human agreement, and a 4.2-second latency failure against the 2.0-second gate. HOLD creates short-term schedule and competitive-window risk but prevents launch before the hard controls are proven. Approve the hold by EOD Friday, July 31, 2026. Before the next ship review, the team must pass all 20 pricing cases with 100% groundedness and citation coverage, achieve κ ≥ 0.60, satisfy the latency gate, and implement the planned drift-evaluation coverage.

**Coverage matrix (M5):** Hallucination testing has strong hybrid coverage through deterministic citation checks and LLM-based grounding review. Bias has partial coverage through segmented human audits. Latency is covered, but toxicity and drift monitoring are not yet implemented. We temporarily accepted the toxicity gap because Ascend IQ is an internal tool used by trained employees with professional-source inputs and human oversight. We did not accept the drift gap: M5 identifies it as the most critical missing control and proposes weekly evaluation using a versioned gold dataset of at least 500 competitive signals.

**Budget (M5):** L3 investments: Data Fabrication/Hallucination testing  - $85K; Source Attribution testing - $65K; Cost Overrun/Latency testing - $25K. Total L3 spend: $175K across all 3 available L3 slots. Context Specificity remains at L2 for $7K, and Data Bias remains at L2 for $5.5K. Total portfolio spend: $187.5K, leaving $12.5K within the $200K quarterly cap.

### Reflection
- **One realization:** Defining “good enough” forced me to distinguish between creating evaluation gates and proving that a model candidate passes them. A documented threshold does not provide launch confidence unless the candidate meets it and the evaluator enforcing it is also calibrated and trustworthy.
- **Next sprint:** My first priority would be closing the evaluator-reliability gap by refining the grounding rubric, recalibrating the LLM judge from κ = -0.29 to at least 0.60, and rerunning all 20 pricing golden-set cases. I would then implement the planned 500-signal drift dataset before reconsidering broader rollout.
