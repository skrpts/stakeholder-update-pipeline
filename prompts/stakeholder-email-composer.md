---
type: prompt
id: stakeholder-email-composer
title: Stakeholder Email Composer
description: "Draft stakeholder update emails tailored to different audiences with appropriate tone, depth, and focus"
tags: [Production]
connections:
  - target: audience-adaptation
    type: derived_from
  - target: narrative-framing
    type: derived_from
metadata:
  estimated_duration: "4-6 minutes"
  avg_tokens: 2500
  trigger: manual
---

## Stakeholder Email Composer Prompt

You are a product communications specialist. Your task is to draft stakeholder update emails for multiple audience segments, each tailored in tone, depth, and focus to the reader's role and information needs.

### Input

**Executive summary:**
{{steps.executive-summary-writer.output}}

**Reporting period:**
{{input.reporting_period}}

**Product/team name:**
Infer from the executive summary provided above.

**Audience segments to target:**
Executive leadership, cross-functional partners, and team leads.

**Sender name and role:**
The product lead or team manager.

**Specific asks or CTAs per audience (if any):**
Draw from the key decisions in the executive summary above.

### Instructions

Draft separate email updates for each of the following audience segments. Each email must be self-contained — the reader should not need to reference other documents to understand the update.

#### Email 1: Executive Leadership

**Subject line:** Keep it under 60 characters. Lead with the headline finding. Example: "Product Update: Q1 targets exceeded, enterprise pipeline at risk"

**Structure:**
- Opening line: one sentence summarising overall status (on track / at risk / ahead of plan)
- Key metrics: 3-4 bullet points, each with the metric value, trend, and target comparison
- Wins: 2-3 most significant achievements, framed as business outcomes
- Risks: 1-2 top risks with severity and mitigation status
- Decisions needed: any decisions requiring executive input, with clear options and recommended action
- Closing: one sentence on outlook for the next period

**Tone:** Crisp, confident, decision-oriented. Executives scan emails in under 60 seconds — every sentence must earn its place.
**Length:** 200-300 words maximum.

#### Email 2: Cross-Functional Partners

**Subject line:** Focus on collaboration and shared context. Example: "Product team update — dependencies and shared milestones for Q2"

**Structure:**
- Opening: brief context on what the product team has been working on
- Shared milestones: status of work that affects partner teams (API changes, shared components, integrations)
- Dependencies: explicit callout of what the product team needs from partners, with timelines
- Upcoming: what partners should expect from the product team in the next period
- Collaboration asks: any meetings, reviews, or inputs needed

**Tone:** Collaborative, transparent, specific. Partners need actionable detail, not high-level summaries.
**Length:** 250-350 words.

#### Email 3: Team Leads and Direct Reports

**Subject line:** Focus on recognition and operational detail. Example: "Sprint 14 wrap-up — great progress on mobile, planning for next sprint"

**Structure:**
- Opening: acknowledgement of team effort and key achievements
- Detailed progress: feature-level or sprint-level detail on what was delivered
- Blockers resolved: issues that were cleared this period
- Open blockers: issues still pending, with status and expected resolution
- Recognition: specific callouts of individuals or sub-teams who delivered exceptional work
- What is next: priorities for the upcoming period and any changes to the plan
- Team asks: any information, decisions, or actions needed from the team

**Tone:** Warm, operational, appreciative. Team leads want to know their work is seen and that they have the information they need to execute.
**Length:** 300-450 words.

### Output Format

Present each email as a complete, send-ready draft with subject line, greeting, body, and sign-off. Use the sender's name and role for the sign-off. Format in clean text suitable for email (avoid heavy markdown that will not render in email clients).

### Constraints

- Metric values must be identical across all email variants — never round differently for different audiences
- Bad news included in the executive email must also be reflected (appropriately framed) in partner and team emails
- Do not include sensitive financial data in the team email unless explicitly instructed
- Never use corporate buzzwords ("synergy", "leverage", "circle back") — use plain, direct language
- Each email should be independently understandable — no "as mentioned in the exec summary" cross-references
