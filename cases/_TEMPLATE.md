# CF-XXX: [Brief Title]

## Basic Information

| Field | Value |
|-------|-------|
| **CF-ID** | CF-XXX |
| **Tier** | A / B / C |
| **Framework** | Hermes Agent / LangGraph / AutoGen / CrewAI |
| **Date** | YYYY-MM-DD |
| **Reported By** | @github_username |
| **Source** | [Issue URL](https://github.com/...) |

## Failure Classification

| Field | Value |
|-------|-------|
| **Boundary Pair** | e.g., Cron ↔ Memory |
| **Failure Category** | e.g., Config override / Tool surface illusion / Hook not firing |
| **ADE Layer** | L1 / L2 / L3 / L4 / L5 |
| **Silent?** | Yes / No / Partial |
| **Cross-Agent?** | Yes / No |

## Description

[What happened. Describe the symptom visible to the operator.]

## Failure Chain

1. [Step 1: What the system intended to do]
2. [Step 2: Where the boundary crossing occurred]
3. [Step 3: What was lost/blocked/distorted at the boundary]
4. [Step 4: Why no error was propagated]

## Root Cause

[Brief analysis of root cause at the interface/protocol/config/lifecycle level]

## ADE Layer Analysis

[Why this maps to a specific ADE layer (L1-L5)]

## Recovery

[Was it fixable? How? Link to PR if applicable.]

## Evidence

- [Link to GitHub Issue]
- [Link to PR if fixed]
- [Relevant log excerpts or screenshots]

## References

- Liu, D. *Channel Fracture in Long-Horizon LLM-Driven Multi-Agent Systems.* arXiv:2606.04896, 2026.
