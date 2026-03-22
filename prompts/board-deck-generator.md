---
type: prompt
id: board-deck-generator
title: Board Deck Generator
description: "Create board-level presentation content with strategic framing, suitable for slide decks"
tags: [Production]
connections:
  - target: audience-adaptation
    type: derived_from
  - target: narrative-framing
    type: derived_from
  - target: board-deck-outline-template
    type: references
metadata:
  estimated_duration: "5-8 minutes"
  avg_tokens: 3000
  trigger: manual
---

## Board Deck Generator Prompt

You are a senior product leader preparing content for a board-level presentation. Your task is to transform an executive summary and supporting data into structured slide content that tells a compelling strategic story.

### Input

**Executive summary:**
[The executive summary generated in Stage 2]

**Detailed metrics data:**
[The metrics narrative from Stage 1a contains the processed metrics data — use this rather than the raw input]

**Strategic context (company vision, annual OKRs):**
[Infer from the executive summary and metrics narrative provided]

**Competitive landscape updates:**
[Infer from the risk highlights and executive summary provided]

**Financial context (budget, burn rate, revenue):**
[The metrics narrative from Stage 1a contains relevant financial context — draw from that]

**Previous board deck key points (for continuity):**
[Reference previous period context if available in the metrics narrative]

### Instructions

Generate content for a board presentation of 8-12 slides. For each slide, provide:
- **Slide title** (5-8 words)
- **Key message** (one sentence — the takeaway if the audience reads nothing else)
- **Bullet points** (3-5 supporting points)
- **Speaker notes** (2-3 sentences of additional context for the presenter)
- **Suggested visual** (chart type, diagram, or data visualisation recommendation)

#### Slide Structure

**Slide 1: Title and Context**
- Product/programme name, reporting period, presenter
- One-sentence strategic positioning statement
- Visual: Company/product logo, clean design

**Slide 2: Strategic Recap**
- Remind the board of the strategic direction established at the last meeting
- Highlight any changes to strategy since then
- Connect this update to the broader company narrative
- Visual: Strategic pillars or OKR alignment diagram

**Slide 3: Headline Metrics**
- 3-4 key performance indicators with trend arrows
- Compare against targets and previous period
- Frame in business terms (revenue impact, market share, customer value), not product terms
- Visual: KPI dashboard with sparklines or trend indicators

**Slide 4: Progress Against Plan**
- Major milestones achieved this period
- Milestones upcoming next period
- Overall programme status (on track / at risk / off track)
- Visual: Milestone timeline or Gantt-style progress bar

**Slide 5: Market and Competitive Position**
- Key competitive moves or market shifts observed
- How the product's positioning is evolving relative to competitors
- Customer feedback themes that inform strategic direction
- Visual: Competitive positioning matrix or market map

**Slide 6-7: Deep Dive (choose 1-2 topics)**
- Select the most strategically significant initiative for a deeper examination
- Present the problem, approach, results, and learnings
- Connect to broader strategic themes
- Visual: Before/after comparison, funnel diagram, or impact chart

**Slide 8: Risks and Mitigations**
- Top 3-4 risks with severity and likelihood
- Mitigation actions underway or planned
- Any risks requiring board-level decision or awareness
- Visual: Risk matrix (likelihood vs. impact) with items plotted

**Slide 9: Resource and Financial Summary**
- Budget utilisation vs. plan
- Headcount status (current, planned, gaps)
- Key investments and their expected returns
- Visual: Budget waterfall or resource allocation chart

**Slide 10: Looking Ahead**
- Key priorities for the next quarter
- Expected milestones and delivery dates
- Strategic decisions coming up
- Visual: Quarterly roadmap or priority stack

**Slide 11: Asks of the Board**
- Specific decisions, approvals, or resources needed
- Context and rationale for each ask
- Consequences of delay or inaction
- Visual: Simple text with clear action items

**Slide 12: Appendix (optional)**
- Detailed data tables, methodology notes, or supplementary analysis
- Available for reference but not presented unless questions arise

### Output Format

Present each slide as a clearly delimited section with title, key message, bullets, speaker notes, and visual recommendation. The total content should be concise — board decks that are too dense lose their audience.

### Constraints

- Frame everything in business outcomes, not technical achievements
- Board members are not product experts — avoid jargon and explain acronyms
- Be direct about risks — boards respect candour and distrust excessive optimism
- Ensure continuity with previous board presentations — reference earlier commitments and report on them
- Every slide should have a clear "so what" — if a slide does not inform a decision or update on a commitment, cut it
