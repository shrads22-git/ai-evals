# Module 4 · Launch Strategy · Section 4.0 Release Criteria

_Generated from the M4 Launch Strategy Builder. Drop this into your PRD as Section 4.0._

## 4.0 Release Criteria

The following thresholds must be met by Model Candidate v1.x before approval for production deploy. Eval Specs from Module 3 define the measurement methodology.

| Severity | Metric | Threshold | Dataset | Method |
|---|---|---|---|---|
| 🔴 Hard (Blocker) | Pricing Hallucination Rate | 0% | `Ascend_IQ_Logs` | 03-eval-suites/lab-2-eval-spec.md |
| 🟡 Soft (Review) | Exceeded Max Threshold | <=2.0 seconds | `Ascend_IQ_Logs` | _[Example Spec]_ |
| 🔵 Advisory (Monitor) | Slang Detected | >=95% | `Ascend_IQ_Logs` | _[Example Spec]_ |

## 4.1 CI Gate Policy

These thresholds run in a GitHub Actions gate on every pull request, replaying deterministic fixtures from the regression golden set (≥ 30 cases). PM owns the policy; Engineering owns the YAML.

> Block the merge if Pricing Hallucination Rate is greater than 0% or citation coverage falls below 100% on the pricing golden set. 

If  P95 response latency exceeds 2.0 seconds, we recommend a Staged Rollout because it limits the slower experience to a controlled user group while Engineering collects production performance data and resolves the bottleneck.

Warn, but do not block, if P95 latency exceeds 2.0 seconds or Brand-Voice Compliance falls below 95%; latency failures require performance investigation, while tone failures are tracked for future prompt and rubric improvements and improve dataset.

## 4.2 Mitigation Plan · Soft Gate

**Selected Lever:** Staged Rollout

> If our Soft Gate fails (P95 response latency exceeds 2.0 seconds across the representative performance fixture set or 2 consecutive runs.), we recommend **Staged Rollout** because It limits the slower experience to a controlled group of users while Engineering profiles bottlenecks and collects production latency data, reducing customer-experience risk before expanding to full availability.

---

_Lab artifact for Module 4, AI Evals Certification, Product School. Becomes the Eval Gates slide of the Final Project deck._
