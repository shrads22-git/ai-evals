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
Module 1 : 01-evaluation-strategy/
├── strategy-canvas.md
├── starter-email-dataset.md
├── sample-email.md *(self learning)*
├── eval-harness-proof.md
├── operationalize-good.md *(self learning)*
└── screenshots/

Module 2 : 02-failure-discovery/
├── audit-log.md
├── failure-taxonomy-canvas.md
└── latency-log.md

Module 3 : 03-eval-suites/
├── lab-1a-eval-suite.md
├── lab-1b-trajectory.md
├── lab-2-eval-spec.md
└── lab-judge-calibration.md/

Agents *(work in progress)*
├── calculator_agent.py
├── research_agent.py *(coming soon)*
└── trajectory-evaluation *(coming soon)*
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

### AI Agent Development *(Self Learning)*

Beyond the course, I am exploring modern AI agent architectures using **LangChain**, **LangGraph**, and **LangSmith**.

Current work includes:

#### Calculator Agent

Built a simple AI agent capable of:

- Selecting the appropriate tool based on the user's request
- Executing arithmetic through a deterministic calculator tool
- Producing observable execution traces in LangSmith

This project introduced key agent concepts including:

- Tool Calling
- Function Calling
- Agent Planning
- Execution Traces
- LangSmith Observability

The resulting execution trajectory follows:

```
User Question
      ↓
LLM decides to use Calculator
      ↓
Calculator Tool executes
      ↓
LLM generates final response
```

This serves as the foundation for understanding **trajectory evaluation**, where the quality of an AI system is measured not only by its final answer but also by the sequence of decisions it makes while solving a task.

Future work will extend this agent with multiple tools, allowing evaluation of:

- Tool Selection
- Tool Usage
- Planning
- Grounding
- Recovery
- Efficiency

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
- LangChain
- LangGraph
- Trust Metrics
- Latency Analysis
- Quality Metrics
- Git & GitHub
- Markdown Documentation

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

- ✅ Module 1 – Evaluation Strategy
- ✅ Module 2 – Failure Discovery
- ✅ Module 3 – Evaluation Design & Judge Calibration

More projects will be added as I continue building production-style AI evaluation systems.
