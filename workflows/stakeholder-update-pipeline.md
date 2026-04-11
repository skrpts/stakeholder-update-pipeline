---
type: workflow
id: stakeholder-update-pipeline
title: Stakeholder Update Pipeline
description: "Multi-stage pipeline that transforms raw product data into executive summaries, board decks, and tailored stakeholder communications"
tags: [Production, Tested, Communication, Metrics]
connections:
  - target: data-summarisation
    type: uses
  - target: narrative-framing
    type: uses
  - target: audience-adaptation
    type: uses
  - target: stakeholder-analysis
    type: uses
  - target: executive-summary
    type: uses
  - target: llm-service
    type: runs_on
  - target: stakeholder-comms-framework
    type: references
  - target: company-okrs
    type: references
  - target: stakeholder-management-guide
    type: references
  - target: exec-summary-template
    type: references
  - target: board-deck-outline-template
    type: references
  - target: risk-assessment
    type: uses
  - target: language-polish
    type: uses
  - target: consistency-check
    type: uses
metadata:
  estimated_duration: "20-30 minutes"
  avg_tokens: 15000
  trigger: manual
execution:
  - skill: "data-summarisation"
  - skill: "narrative-framing"
    input_from: "data-summarisation"
  - skill: "audience-adaptation"
    input_from: "narrative-framing"
  - skill: "stakeholder-analysis"
    input_from: "audience-adaptation"
  - skill: "executive-summary"
    input_from: "stakeholder-analysis"
  - skill: "risk-assessment"
    input_from: "executive-summary"
  - skill: "language-polish"
    input_from: "executive-summary"
  - skill: "consistency-check"
    input_from: "executive-summary"
---

## Stakeholder Update Pipeline

This workflow transforms raw product data — metrics, milestone updates, roadmap status, risk registers — into polished stakeholder communications tailored to different audiences. It produces executive summaries, board deck content, metric narratives, and stakeholder emails from a single data input.

### Prerequisites

Before running this pipeline, gather:

- Current product metrics (adoption, revenue, engagement, performance)
- Milestone status (on track, at risk, delayed, completed)
- Roadmap progress update
- Key decisions made or pending
- Risk register or known issues
- Wins and achievements worth highlighting

### Pipeline Stages

#### Stage 1: Data Intake and Metric Narration

**Nodes:** `metrics-dashboard-narrator`, `risk-highlight-prompt`
**Skill:** `data-summarisation`

Run these two prompts in parallel on the raw input data:

##### 1a: Metrics Narration
- Transform raw metrics into a written narrative that explains what the numbers mean, not just what they are
- Identify trends: improving, declining, or stable
- Flag metrics that have crossed thresholds (targets met, SLAs breached, growth inflection points)
- Contextualise against historical performance and targets

##### 1b: Risk Identification
- Scan the input data for risks, blockers, and issues
- Categorise risks by severity (critical, high, medium, low) and likelihood
- Frame each risk with: what it is, why it matters, what is being done about it, and what decision (if any) is needed from stakeholders
- Distinguish between risks that need stakeholder action and those that are informational only

**Error handling:** If metrics data is incomplete or outdated, flag the gaps explicitly rather than working around them. An executive summary built on stale data is worse than no summary at all.

#### Stage 2: Executive Summary Generation

**Node:** `executive-summary-writer`
**Skills:** `data-summarisation`, `narrative-framing`
**References:** `exec-summary-template`

- Synthesise the metrics narrative and risk highlights into a one-page executive summary
- Lead with the headline: the single most important thing the reader needs to know
- Structure: headline, key metrics (3-5 max), progress update, risks and mitigations, decisions needed
- Optimise for a reader who has 2 minutes and will not scroll past the first page

#### Stage 3: Audience-Specific Outputs

Run these two prompts in parallel, both consuming the executive summary as input:

##### 3a: Board Deck Generation

**Node:** `board-deck-generator`
**Skill:** `audience-adaptation`
**References:** `board-deck-outline-template`

- Transform the executive summary into board-level presentation content
- Frame product updates in terms of business outcomes, market position, and strategic alignment
- Include: strategic narrative, key metrics with trend indicators, competitive positioning, resource allocation summary, asks of the board
- Tone: confident, data-backed, forward-looking. Boards want to see that the team has a plan, not just results.

##### 3b: Stakeholder Email Composition

**Node:** `stakeholder-email-composer`
**Skill:** `audience-adaptation`

- Generate stakeholder update emails tailored to different audiences:
  - **Executive leadership:** strategic summary, key decisions needed, resource asks
  - **Cross-functional partners:** progress on shared initiatives, dependencies, collaboration needs
  - **Team leads:** detailed operational update, blockers, team recognition
- Each email variant should be self-contained — recipients should not need to read the full executive summary
- Tone adapts per audience: executives get crisp, decision-oriented language; team leads get operational detail; partners get collaborative framing

#### Stage 4: Quality Review

Before finalising:

- Verify consistency across all outputs — the same metric should not be described as "strong growth" in the exec summary and "moderate improvement" in the board deck
- Check that risk framing is consistent — a risk flagged as critical in one output should not be downplayed in another
- Ensure no sensitive information appears in outputs intended for broader audiences
- Verify that every "decision needed" item includes enough context for the decision-maker to act

### Output

The pipeline produces:

1. **Executive summary** — one-page stakeholder-ready summary
2. **Board deck content** — slide-by-slide content for board presentation (8-12 slides)
3. **Metrics narrative** — detailed written narrative of dashboard data
4. **Risk briefing** — categorised risk register with mitigations and asks
5. **Stakeholder emails** — 2-3 audience-tailored email drafts

### Error Handling

- **Incomplete data:** Surface gaps explicitly in the output; do not fabricate or interpolate missing metrics
- **Contradictory data:** Flag contradictions and present both data points rather than silently choosing one
- **Sensitive information:** If financial or personnel data is included in the input, flag it for review before including in broader-audience outputs

## Inputs

| Name | Required | Description | Example |
|------|----------|-------------|---------|
| `{{input.product_metrics}}` | Yes | Current product metrics — adoption, revenue, engagement, performance data | "MAU: 45,000 (up 12%). Revenue: $2.1M ARR (up 8%). Trial-to-paid: 28% (down from 34%). Uptime: 99.97%." |
| `{{input.milestone_status}}` | Yes | Milestone status — what is on track, at risk, delayed, or completed | "Auth rewrite: completed. API v2: at risk (1 week behind). Mobile launch: on track for April 15. Dashboard redesign: delayed to Q3." |
| `{{input.reporting_period}}` | No | The reporting period this update covers | "Q1 2026" or "March 2026" or "Sprint 14" |
| `{{input.key_decisions}}` | No | Key decisions made or pending that stakeholders should know about | "Decided to defer Salesforce integration to Q3. Pending: board approval for headcount increase." |
| `{{input.known_risks}}` | No | Risk register or known issues requiring stakeholder attention | "Enterprise pipeline at risk — 2 of 3 target accounts paused procurement. Support ticket volume up 25%." |

## Outputs

| Name | Description |
|------|-------------|
| Workflow output | Final output generated by this workflow |

## Setup

Before running this workflow:

1. No external services required — paste your content directly and provide any supporting context as inputs or source nodes.
2. Review the included documents, assets, or source nodes and customise them to match your team, brand, or domain conventions where needed.
3. No specific AI provider or API key is required beyond your configured skrptiq LLM provider.

## Provider Notes

- The longer synthesis stages benefit from a model with strong reasoning and a generous context window.
- Extraction, classification, and formatting steps generally run well on smaller or faster models.
- Because there are no vendor-specific integrations here, provider choice is mostly a trade-off between speed, quality, and cost.

## Example Input

To test this workflow immediately after import:

```
Product Metrics: "MAU: 45,000 (up 12% from 40,200). Revenue: $2.1M ARR (up 8%).
Trial-to-paid conversion: 28% (down from 34%). Platform uptime: 99.97%."

Milestone Status: "Auth rewrite: completed on schedule. API v2: at risk, 1 week behind.
Mobile launch: on track for April 15."

Key Decisions: "Decided to defer Salesforce integration to Q3 due to resource constraints."

Known Risks: "Enterprise pipeline at risk — 2 of 3 target accounts paused procurement."
```

