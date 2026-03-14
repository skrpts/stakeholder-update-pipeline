---
type: skill
id: data-summarisation
title: Data Summarisation
description: "Distilling complex data into concise, audience-appropriate summaries that highlight what matters most"
tags: [Production, Tested]
connections:
  - target: llm-service
    type: runs_on
metadata:
  estimated_duration: "3-5 minutes"
  avg_tokens: 2000
  trigger: manual
---

## Data Summarisation

This skill enables the transformation of raw, complex data sets into clear, concise summaries that communicate the essential story to the intended audience. It covers quantitative metric interpretation, trend identification, and contextual framing.

### Core Capabilities

#### Metric Interpretation

Raw numbers are meaningless without context. When summarising metrics:

- **Compare to targets:** "Monthly active users reached 45,000" means nothing. "Monthly active users reached 45,000, exceeding the Q1 target of 40,000 by 12.5%" tells a story.
- **Show trends:** "Revenue was $2.3M" is a snapshot. "Revenue was $2.3M, up 18% quarter-on-quarter and 45% year-on-year" is a trajectory.
- **Contextualise against benchmarks:** Where possible, compare against industry benchmarks, competitor performance, or historical averages. A 5% churn rate might be excellent in consumer SaaS but alarming in enterprise.
- **Distinguish leading and lagging indicators:** Highlight whether a metric tells you about what has happened (lagging) or what is likely to happen (leading). New trial sign-ups are leading; revenue recognised is lagging.

#### Trend Identification

When analysing time-series data or comparing periods:

- Identify the direction: improving, declining, or stable
- Assess the rate of change: accelerating, decelerating, or linear
- Note inflection points: when did the trend change, and what might have caused it?
- Flag anomalies: data points that deviate significantly from the trend deserve explanation, not smoothing

#### Information Hierarchy

Not all data points are equally important. Structure summaries using an inverted pyramid:

1. **Lead with the headline:** The single most important finding or metric
2. **Supporting evidence:** 3-5 key data points that substantiate the headline
3. **Detail layer:** Additional context, caveats, and secondary findings
4. **Appendix-level detail:** Raw data, methodology notes, edge cases — available if needed but not in the main flow

#### Compression Without Distortion

The goal of summarisation is to reduce volume while preserving meaning. Common distortions to avoid:

- **Cherry-picking:** Selecting only favourable metrics while omitting unfavourable ones
- **False precision:** Presenting estimates with unwarranted decimal places
- **Averaging away variance:** Reporting averages without noting the spread — "average response time of 200ms" hides the fact that p99 is 3 seconds
- **Omitting uncertainty:** Presenting projections as certainties

### Constraints

- Never present a summary that contradicts the underlying data
- Always include enough context that the reader can assess the significance of the findings
- Flag any data quality issues (missing data, sampling bias, known measurement errors) prominently
- Adapt the level of technical detail to the audience — executives need the story, analysts need the methodology
