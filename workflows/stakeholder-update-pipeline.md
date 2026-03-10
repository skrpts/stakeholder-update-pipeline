---
type: workflow
id: stakeholder-update-pipeline
title: Stakeholder Update Pipeline
description: "Multi-stage pipeline that transforms raw product data into executive summaries, board decks, and tailored stakeholder communications"
tags: [Production, Tested]
connections:
  - target: data-summarisation
    type: uses
  - target: narrative-framing
    type: uses
  - target: audience-adaptation
    type: uses
  - target: executive-summary-writer
    type: uses
  - target: board-deck-generator
    type: uses
  - target: metrics-dashboard-narrator
    type: uses
  - target: stakeholder-email-composer
    type: uses
  - target: risk-highlight-prompt
    type: uses
  - target: claude-service
    type: runs_on
  - target: stakeholder-comms-framework
    type: references
  - target: stakeholder-management-guide
    type: references
  - target: exec-summary-template
    type: references
  - target: board-deck-outline-template
    type: references
metadata:
  estimated_duration: "20-30 minutes"
  avg_tokens: 15000
  trigger: manual
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
