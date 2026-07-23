# Module 4 · Eval Gate Map · Ascend IQ Copilot

_Generated from the M4 Eval Gate Mapping Tool._

## Context

Eng flagged 5 verified failures in the Ascend IQ data log. (Row 14, refused legal query, was correctly Pass and is not mapped.) Each row below assigns a severity (Advisory · Soft · Hard) and a pipeline placement (Pull Request · Staging Build · Release Build).

## Gate Map

| Row | Failure Mode | Severity | Placement | Rationale |
|---|---|---|---|---|
| 01 | Hallucination · Stale Pricing | 🔴 Hard | Staging Build | Incorrect pricing can mislead prospects, damage customer trust, and create direct revenue risk. The staging groundedness suite must verify all pricing against current approved sources and block the build if any unsupported price is generated. |
| 17 | Tone · Slang Detected | 🟡 Soft | Staging Build | Off-brand slang can erode brand credibility and reduce the effectiveness of customer communications, but it does not carry the same risk as a factual hallucination. Evaluate tone with the staging judge suite and require review or an approved exception before release. |
| 05 | Hallucination · False Promise | 🔴 Hard | Staging Build | Falsely presenting a tentative speaker as confirmed can damage brand credibility and disappoint users, but the event data may change frequently. Run the full groundedness judge in staging and require review or updated source data before release. |
| 08 | Hallucination · Contradicts Specs | 🔴 Hard | Pull Request | An unsupported and disparaging competitor comparison creates legal, revenue, and trust risk and violates Ascend IQ’s core promise of citation-backed intelligence. Replay this fixture in PR CI and block any unsupported comparison or factual regression. |
| 03 | Latency · Exceeded Max Threshold | 🟡 Soft | Staging Build | A high latency can frustrate users and increase abandonment. But if the answer remains correct. Measure latency under realistic staging conditions and require investigation or an approved mitigation when the threshold is exceeded. |

## Sample Interactions (for reference)

**Row 01 · Hallucination · Stale Pricing**
- Input: What is InsightFlow's pricing for Enterprise?
- Output: InsightFlow Enterprise starts at $49/user/month with a 10-seat minimum.
- Eng reasoning: Hallucination, invented pricing numbers not in the source data.

**Row 17 · Tone · Slang Detected**
- Input: Draft a cold email about our new feature.
- Output: Hey! Check out this killer new feature, it's a total game changer for your stack!
- Eng reasoning: Tone, slang violates brand-voice guidelines.

**Row 05 · Hallucination · False Promise**
- Input: List the confirmed speakers for SaaStr.
- Output: Confirmed speakers include Jason Lemkin, Aaron Levie, and Sam Altman.
- Eng reasoning: Hallucination, Sam Altman is not on the confirmed speaker list.

**Row 08 · Hallucination · Contradicts Specs**
- Input: Compare our API rate limits to Competitor Z.
- Output: Our API is robust and developer-friendly. Competitor Z is known for strict throttling.
- Eng reasoning: Hallucination, fabricates a comparison and disparages a named competitor.

**Row 03 · Latency · Exceeded Max Threshold**
- Input: Summarize the top 3 complaints from DataViz's G2 reviews.
- Output: Users report issues with mobile load times, lack of dark mode, and steep learning curve.
- Eng reasoning: Latency, response time exceeded the max threshold (4.2s vs target 2.0s).

---

_Lab artifact for Module 4, AI Evals Certification, Product School._
