# Lab, Judge Calibration (Atlas grounding rubric)

**Cohen's κ:** -0.29 (Poor / none), FAILS the κ ≥ 0.60 gate

- Traces labeled: 12/12
- Raw agreement p₀: 50%
- Chance agreement pₑ: 61%
- Disagreements: 6

### Confusion matrix (judge × you)

| | You: PASS | You: FAIL |
| --- | :---: | :---: |
| **Judge: PASS** | 6 | 4 |
| **Judge: FAIL** | 2 | 0 |

## Diagnosis

The judge is too lenient toward fluent but ungrounded answers and too strict toward correct abstentions.

The judge incorrectly passed responses that introduced unsupported information not present in the retrieved source, such as an auto-renewal clause (T-02), SLA penalty figures (T-03), a nonexistent invoice line item (T-07), and a fabricated 12% volume discount (T-09). These responses were well-written and confident, but they violated the grounding requirement.
The judge incorrectly failed responses that honestly stated the retrieved records did not contain the requested information (T-06 and T-10). Under the rubric, acknowledging missing evidence is the correct, grounded behavior and should be considered a PASS.

Overall, the judge appears to reward fluency and completeness over factual grounding while penalizing appropriate uncertainty, causing it to diverge from human judgment.

## Rubric revision

PASS only if every factual claim is supported by retrieved evidence.

If any unsupported claim appears, FAIL regardless of writing quality.

If the information is missing from the retrieved documents, an explicit statement that the answer cannot be determined counts as PASS.

Example1
Question
Who owns the account?

Answer
I couldn't find that information in the retrieved documents.

PASS

Example2

Question
Volume discount?

Answer
12% after 500 units.

Retrieved source contains nothing.

FAIL