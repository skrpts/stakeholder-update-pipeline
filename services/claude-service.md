---
type: service
id: claude-service
title: Claude Service
description: "How this skrpt uses Claude for stakeholder communications, narrative framing, and report generation"
tags: [Production, Tested]
connections:
  - target: stakeholder-update-pipeline
    type: runs_on
metadata:
  provider: "anthropic"
  model: "claude-sonnet"
  estimated_tokens_per_run: 15000
---

## Claude Service — Stakeholder Update Pipeline

This skrpt uses Anthropic Claude as its primary AI service for transforming raw product data into polished stakeholder communications.

### Usage Pattern

Claude is invoked at each stage of the pipeline:

1. **Metrics narration** — interpreting raw dashboard data and producing written narrative
2. **Risk identification** — scanning data for risks and framing them for executive consumption
3. **Executive summary generation** — synthesising metrics and risks into a one-page summary
4. **Board deck generation** — transforming summaries into strategic presentation content
5. **Email composition** — adapting content for multiple stakeholder audiences

### Model Requirements

- **Writing quality:** All outputs are stakeholder-facing communications that require professional, polished prose
- **Audience awareness:** The model must adapt tone, vocabulary, and detail level across different audience segments within a single run
- **Consistency:** Metric values, risk assessments, and narrative framing must remain consistent across multiple outputs generated from the same input data
- **Structured output:** Board deck content requires reliable slide-by-slide structure; emails require proper formatting

### Token Budget

- Typical full pipeline run: 12,000-18,000 tokens
- Metrics narration: 2,000-2,500 tokens
- Risk highlights: 2,000-2,500 tokens
- Executive summary: 2,000-3,000 tokens
- Board deck: 3,000-4,000 tokens
- Stakeholder emails: 2,500-3,500 tokens

### Configuration

- Temperature: 0.4 (moderate — allows natural-sounding prose while maintaining accuracy)
- System prompt should emphasise professional communication, factual accuracy, and audience awareness
- For board deck generation, include examples of good slide structure in the context
