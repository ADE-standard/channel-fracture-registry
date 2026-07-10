---
name: Channel Fracture Report
about: Submit a new Channel Fracture case to the Registry
title: "[CFR] [Framework] Brief description"
labels: new-case
assignees: tobiglevent001
---

Thanks for contributing to the ADE Channel Fracture Registry.

## Required Information

**Framework:** (e.g., Hermes Agent, LangGraph, AutoGen, CrewAI)
**Boundary Pair:** (e.g., Cron ↔ Memory, Hook ↔ Plugin)
**Version:** (if known)

## What Happened

Describe the observable symptom. What did you see (or not see)?

## Channel Fracture Criteria

Confirm each criterion is met by checking the box:

- [ ] **C1 — Cross-boundary**: The failure occurs at the seam between two systems
- [ ] **C2 — Data/State loss**: Data, state, or control signals were lost/blocked/distorted
- [ ] **C3 — Silent**: No obvious error propagated; standard monitoring showed normal
- [ ] **C4 — Root cause at interface**: Failure is in HOW systems connect, not WHAT one system does

## Evidence

- Link to GitHub issue, PR, or discussion:
- Log excerpts (optional):
- Steps to reproduce (if available):

## Recovery

How was it fixed? (Or is it still open?)

## Additional Context

Any other information that helps classify this case.
