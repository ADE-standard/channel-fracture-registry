# Contributing to the ADE Channel Fracture Registry

Thank you for helping build the first public failure knowledge base for
Multi-Agent Reliability Engineering.

## What is a Channel Fracture?

A **Channel Fracture** is a failure where data or state is silently lost
when it crosses a boundary between two systems in an agent framework. The
system reports success, but the data never reaches its destination.

**Four criteria must ALL be met:**

| Criterion | Description | Test |
|-----------|-------------|------|
| **C1 — Cross-boundary** | Involves ≥2 system components interacting across an interface | "Does the failure occur at the seam between two systems?" |
| **C2 — Data/state loss** | Data, state, or control signals are lost, blocked, or distorted at the boundary | "Did the sender think it succeeded, but the receiver never got the right thing?" |
| **C3 — Silent or semi-silent** | No obvious error propagated to the operator | "Would an operator looking at standard monitoring notice anything wrong?" |
| **C4 — Root cause at interface** | Failure is in HOW systems connect, not WHAT one system does | "Is this a failure of connection, not of logic?" |

**NOT Channel Fracture:** single-component crashes, visible errors, design
decisions, business logic bugs, high-CPU symptoms, or intentional limits.

## How to Submit a Case

### Option 1: Open an Issue (Recommended)

1. Go to [Issues](https://github.com/ADE-standard/channel-fracture-registry/issues)
2. Click **New Issue** → **Channel Fracture Report**
3. Fill in the template with as much detail as possible

### Option 2: Pull Request

1. Fork this repository
2. Copy `cases/_TEMPLATE.md` and rename to `CF-XXX.md`
3. Fill in all fields
4. Add entry to `registry.json` and `registry.csv`
5. Submit a PR

### What to Include

- **System/Framework**: Hermes Agent, LangGraph, AutoGen, CrewAI, etc.
- **Components involved**: Which two boundaries? (e.g., Cron ↔ Memory)
- **What happened**: The observable symptom
- **Why it's Channel Fracture**: How it meets the four criteria
- **Evidence**: GitHub issue link, log excerpt, reproduction steps
- **Recovery**: Was it fixable? How?

## Tier Classification

The maintainers classify each submission:

| Tier | Label | Meaning |
|------|-------|---------|
| **A** | Canonical | All four criteria undeniable; textbook example |
| **B** | Strong Match | All four criteria met; minor edge discussion possible |
| **C** | Candidate | Fits criteria; awaiting community confirmation |

Maintainers reserve the right to reclassify or exclude submissions that
don't meet the inclusion criteria. Tier A classification is intentionally
rare — it represents the most unambiguous cases.

## Maintainers

- [@tobiglevent001](https://github.com/tobiglevent001) — Dexing Liu, Qijing Digital

## Code of Conduct

Be respectful. Focus on the failure pattern, not the framework or its
maintainers. The goal is to help the community build more reliable
agent systems — not to assign blame.
