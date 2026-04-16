---
type: skill
id: narrative-framing
title: Narrative Framing
description: "Framing product updates as compelling narratives for different audiences, connecting data to strategic context"
tags: [Production, Tested, Audience, Communication]
context_params:
  stakeholder_audience:
    label: "Stakeholder Audience"
    description: "Who will receive this update or presentation"
    default: ""
    required: true
connections:
  - target: llm-service
    type: runs_on
  - target: stakeholder-comms-framework
    type: references
metadata:
  estimated_duration: "3-5 minutes"
  avg_tokens: 2000
  trigger: manual
---

## Narrative Framing

This skill enables the construction of compelling narratives around product data, transforming dry updates into strategic stories that resonate with different stakeholder groups. Good narrative framing connects what happened to why it matters and what comes next.

### Core Capabilities

#### The Strategic Narrative Arc

Every stakeholder update should follow a narrative arc:

1. **Context:** Where we are in the broader journey — remind the audience of the strategic direction and what success looks like
2. **Progress:** What has happened since the last update — concrete achievements, milestones reached, metrics moved
3. **Challenges:** What is not going well — framed honestly but constructively, with emphasis on what is being done about it
4. **Outlook:** What comes next — upcoming milestones, expected trajectory, decisions needed
5. **Ask:** What the audience needs to do — approve, decide, provide resources, remove blockers

This arc ensures updates are not just information dumps but purposeful communications that drive action.

#### Framing Techniques

**Progress framing:** Present achievements in terms of outcomes rather than outputs. "Shipped 47 features" is output. "Reduced average onboarding time from 14 days to 3 days" is an outcome that stakeholders care about.

**Challenge framing:** Present challenges as problems being actively managed, not as excuses. "The mobile redesign is delayed by three weeks because we underestimated the complexity of the offline sync feature. We have re-scoped to ship a simplified version by the original deadline and deliver full offline sync in the following release."

**Risk framing:** Frame risks with a clear structure: what the risk is, what triggers it, what the impact would be, what mitigation is in place, and what decision (if any) is needed. Never hide risks — stakeholders who discover unreported risks lose trust permanently.

**Confidence framing:** Be explicit about what you know vs. what you believe vs. what you are guessing. "Our analytics confirm a 23% increase in engagement" is different from "We believe the new onboarding flow contributed to the increase" which is different from "We expect this trend to continue next quarter."

#### Narrative Consistency

Across multiple outputs (executive summary, board deck, team update):

- The core narrative should be consistent — the same story told at different levels of detail
- Metrics should be identical across all documents — never round differently for different audiences
- Risk severity should be consistent — a risk classified as "high" in the executive summary should not be described as "moderate" in the board deck
- Tone should adapt to the audience while the substance remains unchanged

### Constraints

- Never spin — present reality accurately, even when it is uncomfortable
- Frame bad news directly; burying it destroys credibility when it surfaces later
- Separate facts from interpretation — make it clear which statements are data-backed and which are analysis
- Avoid jargon in executive and board communications unless the audience is known to be technically fluent
