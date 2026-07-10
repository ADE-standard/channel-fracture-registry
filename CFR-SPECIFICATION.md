# Channel Fracture Registry Specification v1.0

> **Canonical reference**: cite this document when referencing the Channel Fracture Registry
> in academic papers, benchmarks, or tooling.
>
> Preferred citation: *"Channel Fracture Registry Specification v1.0"*

---

## 1. Definition

**Channel Fracture** (信道断裂) is a class of failure in multi-agent systems where
data or state is silently lost, blocked, or distorted at component boundaries.

Three diagnostic signatures:
1. The caller believes the operation succeeded.
2. The receiver did not receive the correct data or state.
3. Neither side can detect the failure through standard monitoring.

The term was introduced in [ADE: Agent Delivery Engineering](https://arxiv.org/abs/2606.04896).

---

## 2. Scope

This registry covers failures occurring at **component boundaries** in agent systems:

| Boundary | Examples |
|----------|----------|
| Agent ↔ Memory | Write returns success, read returns empty |
| Agent ↔ Tool | Tool invocation appears successful but parameters are dropped |
| Agent ↔ Agent | Message passed but silent delivery failure |
| Agent ↔ Platform | API returns 200 but state transition not applied |
| Agent ↔ Guard | Guardrail registered but never fires |

**Out of scope**: functional bugs (wrong output with correct state), performance issues,
prompt engineering failures, and non-silent errors with clear error messages.

---

## 3. Taxonomy Model

The registry classifies fractures into 7 taxonomic categories, forming the
**Agent Failure Classification System (AFCS)** — analogous to CWE for software.

| Category | Description | Cases |
|----------|-------------|-------|
| Communication | Cross-boundary message delivery and signaling failures | 38 |
| Configuration | Configuration propagation and state initialization failures | 34 |
| Execution | Process lifecycle and resource management failures | 20 |
| Memory | Context, session, and knowledge storage failures | 8 |
| Tool | Tool invocation, parameter passing, and result interpretation failures | 0 |
| State | State machine, checkpoint, and consistency failures | 0 |
| Verification | Detection, monitoring, and observability gaps | 0 |

See [taxonomy/](taxonomy/) for detailed breakdowns per category.

---

## 4. Entry Schema

### 4.1 Required Fields

| Field | Type | Description |
|-------|------|-------------|
| `cf_id` | CF-NNNN | Permanent registry identifier |
| `title` | string | Short descriptive name |
| `category` | enum | Taxonomy category (see §3) |
| `layer` | enum | Affected architectural layer |
| `failure_pattern` | enum | Classification of failure mechanism |
| `affected_system` | string | Framework or system |
| `trigger` | string | Conditions triggering the fracture |
| `observed_symptom` | string | Observable (or unobservable) effect |
| `root_cause` | string | Underlying boundary-level cause |
| `detection` | string | CADVP verification method |
| `impact` | string | Consequence of undetected failure |
| `mitigation` | string | Prevention or recovery approach |
| `evidence_level` | enum | Evidence quality rating (see §5) |
| `status` | enum | Confirmed / Fixed / Open |

### 4.2 Machine Schema

Formal definition in [schema/fracture-schema.yaml](schema/fracture-schema.yaml).

---

## 5. Evidence Model

Every entry carries an evidence quality rating:

| Level | Name | Criteria |
|-------|------|----------|
| `observed` | Observed | Directly observed in production or development; no external report |
| `reported` | Reported | Documented in at least one public issue, bug report, or incident |
| `reproduced` | Reproduced | Independently reproduced; fix available or root cause confirmed |
| `verified` | Verified | Same fracture pattern validated across ≥2 independent frameworks |

**Current distribution** (100 entries):
- `reported`: 86 (acknowledged by framework maintainers)
- `reproduced`: 8 (fixed with merged PR)
- `verified`: 0 (open for cross-framework validation)

---

## 6. Versioning Policy

| Component | Versioning | Meaning |
|-----------|-----------|---------|
| Registry entries | Monotonic CF-NNNN | Never reused, never renumbered |
| Specification | Semantic (MAJOR.MINOR) | MAJOR = breaking schema change; MINOR = new field/category |
| Data format | Same as specification | registry.json/CSV track specification version |

---

## 7. Contribution Process

```
1. Open an issue describing the fracture
        ↓
2. Submit a PR with:
   - registry/CF-XXXX.md (entry file)
   - Updated registry.json
   - Updated registry.csv
   - Updated registry-index.md (if new entry)
        ↓
3. GitHub Actions validates:
   - CF-ID uniqueness
   - Schema compliance
   - JSON/CSV/Index sync
        ↓
4. Maintainer reviews evidence level and taxonomy fit
        ↓
5. Merge → new CF-ID is permanent
```

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines.

---

## 8. Governance

The Channel Fracture Registry is maintained as **public infrastructure**:
- Framework-independent: covers Hermes, LangGraph, CrewAI, LangChain, AutoGen, Semantic Kernel, Google ADK
- Open for contribution: any practitioner or researcher can submit cases
- ADE provides the theoretical framework; the registry is community-governed

---

*Specification Version: 1.0 · Registry Version: 1.1 · Last Updated: 2026-07-10*
