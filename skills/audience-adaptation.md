---
type: skill
id: audience-adaptation
title: Audience Adaptation
description: "Adapting content tone, depth, and focus for different stakeholder groups while maintaining message consistency"
tags: [Production, Tested, writing:communication, communication:stakeholder, communication:narrative]
connections:
  - target: llm-service
    type: runs_on
metadata:
  estimated_duration: "3-5 minutes"
  avg_tokens: 2000
  trigger: manual
---

## Audience Adaptation

This skill enables the tailoring of product communications for different stakeholder audiences. The same underlying information needs to be presented differently depending on the reader's role, interests, technical literacy, and decision-making authority.

### Core Capabilities

#### Audience Profiles

##### Board of Directors / Investors

- **Primary interest:** Strategic direction, market position, financial performance, risk exposure
- **Detail level:** High-level only. No feature-level detail unless it is strategically significant.
- **Time budget:** 2-3 minutes of reading, 15-30 minutes of discussion
- **Tone:** Confident, forward-looking, data-backed. Boards want assurance that the team has a plan and is executing against it.
- **What they need to decide:** Resource allocation, strategic pivots, major investments, risk acceptance
- **What to avoid:** Technical jargon, feature lists, sprint-level details, internal process issues

##### Executive Leadership (C-suite, VPs)

- **Primary interest:** Goal attainment, cross-functional alignment, resource needs, blockers requiring escalation
- **Detail level:** Moderate. Key initiatives with status, headline metrics, top risks.
- **Time budget:** 5-10 minutes of reading
- **Tone:** Direct, action-oriented. Executives want to know what is on track, what is not, and what they need to do.
- **What they need to decide:** Priority trade-offs, resource reallocation, escalation of blockers
- **What to avoid:** Exhaustive detail on individual tasks, implementation specifics, status updates on low-priority items

##### Cross-Functional Partners (other product teams, engineering leads, design)

- **Primary interest:** Dependencies, shared milestones, collaboration needs, interface contracts
- **Detail level:** Moderate to high. Enough detail on shared work to identify misalignments early.
- **Time budget:** 5-10 minutes of reading
- **Tone:** Collaborative, transparent. Partners need honest status updates to plan their own work.
- **What they need to decide:** Dependency timelines, shared resource allocation, API contracts
- **What to avoid:** One-sided framing that makes the reporting team look good at the expense of accuracy

##### Team and Team Leads

- **Primary interest:** Execution status, blockers, recognition, upcoming priorities
- **Detail level:** High. Specific tasks, individuals, technical decisions.
- **Time budget:** 10-15 minutes of reading
- **Tone:** Operational, inclusive, recognition-focused. Teams want to know their work matters and that leadership sees it.
- **What they need to decide:** Tactical execution choices, technical approach, sprint commitments
- **What to avoid:** Overly formal language, corporate-speak, omitting team recognition

#### Adaptation Mechanics

When adapting a single update for multiple audiences:

1. **Start with the full picture** — compile all available data, achievements, risks, and decisions
2. **Filter by relevance** — each audience gets only the information relevant to their role and decision authority
3. **Adjust depth** — board gets headlines, executives get summaries, partners get operational detail, teams get full context
4. **Shift framing** — the same achievement might be framed as "market expansion" for the board, "target exceeded" for leadership, "great engineering work" for the team
5. **Calibrate tone** — formal and strategic for board; direct and action-oriented for executives; collaborative for partners; appreciative and operational for teams

### Constraints

- Never change the substance of the message between audiences — only the framing and depth
- Ensure metric values are identical across all audience versions
- If bad news is included for one audience, it must be included (appropriately framed) for all relevant audiences
- Never include information in a broader audience that has not been shared with the directly affected team first
