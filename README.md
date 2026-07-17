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
└── screenshots/
```

## Projects

### Module 1 – Evaluation Strategy

This project includes:

- Product evaluation strategy
- Success metrics based on Latency, Hallucination, UX Trust, Robustness, and Fairness
- Trade-off analysis
- Starter evaluation dataset
- Evaluation harness using LangSmith
- Documentation and supporting screenshots

### Module 2 – Failure Discovery

This project focuses on auditing model outputs to identify quality issues and build a structured failure taxonomy.

It includes:

- Manual audit of 20 LLM evaluation results
- Comparison of LLM-as-Judge scores with human review
- Failure categorization using Trust Metrics
- Hallucination, Robustness, and Fairness analysis
- Latency analysis using a defined SLA (≤ 3.5 seconds)
- Failure Taxonomy Canvas documenting the highest-risk failure categories

## Skills Practiced

- AI Evaluation using LangSmith (Playground, Datasets, Experiments, Evaluations, and LLM-as-a-Judge)
- Evaluation Strategy Design
- Failure Analysis
- Human-in-the-Loop Evaluation
- Prompt Engineering
- Dataset Creation
- LLM Testing
- Trust Metrics
- Latency Analysis
- Quality Metrics
- Git & GitHub
- Markdown Documentation

> **Note:** Current evaluations use OpenAI as both the model provider and the LLM-as-Judge. Future work will explore using independent judge models from different providers to reduce evaluation bias.

## Tools

- OpenAI
- LangSmith
- GitHub
- Visual Studio Code

## Status

- Module 1 – Evaluation Strategy Complete
- Module 2 – Failure Discovery Complete

More projects will be added as I progress through the course.
