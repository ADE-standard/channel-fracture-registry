# Channel Fracture Registry

> A public taxonomy of silent reliability failures in autonomous agent systems.
>
> 面向自主Agent系统的静默可靠性失效公开分类体系。

---

## Purpose

To document, classify, and analyze **cross-boundary delivery failures** — cases where
agent systems report success without achieving the intended state transition.

This registry is **public infrastructure**: framework-independent, permanently citable,
and open for community contribution. It serves researchers building benchmarks,
engineers debugging silent failures, and framework maintainers hardening their boundaries.

The classification methodology draws from the **ADE (Agent Delivery Engineering)** framework
([arXiv:2606.04896](https://arxiv.org/abs/2606.04896)), but the registry itself is
framework-agnostic — channel fractures appear in every agent system regardless of
implementation.

---

## What is Channel Fracture?

**Channel Fracture**（信道断裂）is a failure class where data or state is silently
lost, blocked, or distorted at component boundaries within a multi-agent system.

Core signature:
- The caller believes the operation succeeded.
- The receiver did not receive the correct data.
- Neither side can detect the failure through standard monitoring.

For a detailed taxonomy and detection methodology, see
[ADE Paper: Channel Fracture in Autonomous Agent Systems](https://arxiv.org/abs/2606.04896).

---

## Registry at a Glance

| | |
|---|---|
| **Entries** | 100 (CF-0001 ~ CF-0100) |
| **Frameworks covered** | Hermes, LangGraph, CrewAI, LangChain, Semantic Kernel, AutoGen, Google ADK |
| **Taxonomy categories** | 7 |
| **Severity scale** | S1 (Critical) ~ S4 (Low) |
| **Open for contributions** | [CONTRIBUTING.md](CONTRIBUTING.md) |

### Taxonomy

| Category | Cases | Scope |
|----------|-------|-------|
| [Communication](taxonomy/communication.md) | 38 | Hook misfire, silent message loss, signal suppression, connection illusion |
| [Configuration](taxonomy/configuration.md) | 34 | Config override, credential bypass, env contamination |
| [Execution](taxonomy/execution.md) | 20 | Process lifecycle failures, resource leaks |
| [Tool](taxonomy/tool.md) | 0 | Tool surface illusion, parameter corruption, result coercion |
| [Memory](taxonomy/memory.md) | 8 | Memory blindness, context loss |
| [State](taxonomy/state.md) | 0 | State corruption, checkpoint failure, consistency violation |
| [Verification](taxonomy/verification.md) | 0 | Detection gap, monitoring blind spots |

---

## Why CF-IDs?

Each entry receives a permanent `CF-NNNN` identifier that is **independent of any
platform's issue numbering**:

- `CF-0001` is citable in academic papers, regardless of which GitHub issue inspired it.
- The same fracture pattern often spans issues across multiple frameworks — a CF-ID
  unifies them under one domain identifier.
- As the taxonomy evolves, CF-IDs remain stable references for benchmarks, tooling,
  and cross-framework analysis.

> `Channel Fracture Registry CF-0001` — a citable domain identifier, not a bug label.

---

## Entry Schema

Every entry conforms to a standardized schema. New contributions must pass schema
validation before acceptance.

| Field | Description |
|-------|-------------|
| `cf_id` | Permanent registry identifier (CF-NNNN) |
| `name` | Short descriptive name |
| `category` | Taxonomy category |
| `layer` | Affected architectural layer |
| `severity` | S1 (Critical) ~ S4 (Low) |
| `failure_pattern` | Classification of failure mechanism |
| `affected_system` | Framework or system |
| `trigger` | Conditions that trigger the fracture |
| `observed_symptom` | What the operator observes |
| `root_cause` | Underlying cause at the boundary |
| `detection` | CADVP verification method |
| `impact` | Consequence of undetected failure |
| `mitigation` | Prevention or recovery approach |
| `evidence` | GitHub issue, commit, reproduction steps |
| `status` | Confirmed / Fixed / Open |

Full schema definition: [schema/channel-fracture-schema.yaml](schema/channel-fracture-schema.yaml)

---

## Project Structure

```
channel-fracture-registry/
├── README.md
├── registry/                         ← Case entries (CF-0001.md ~ CF-0100.md)
├── taxonomy/                         ← Classification by category (7 categories)
│   ├── communication.md
│   ├── configuration.md
│   ├── execution.md
│   ├── tool.md
│   ├── memory.md
│   ├── state.md
│   └── verification.md
├── schema/
│   └── channel-fracture-schema.yaml  ← Machine-readable entry schema
├── references/
│   ├── papers.md                     ← Academic references
│   └── incidents.md                  ← Source incidents
├── registry.json                     ← Machine-readable (JSON)
├── registry.csv                      ← Offline analysis (CSV)
├── CONTRIBUTING.md
└── LICENSE
```

---

## Expanding Coverage

100 cases across 7 frameworks is a start. The taxonomy is designed to grow.

| Area | What's needed |
|------|---------------|
| **More frameworks** | OpenAI Agents SDK, Claude MCP, Dify, TaskWeaver, MetaGPT, PydanticAI |
| **More cases** | Production incident reports, postmortems, community submissions |
| **Detection tools** | Cross-framework probes, static analysis rules, integration patterns |
| **Research** | Quantitative studies, failure-rate benchmarks, framework comparisons |

See [CONTRIBUTING.md](CONTRIBUTING.md) to submit a case.

---

## Citation

```bibtex
@misc{channel-fracture-registry,
  title        = {Channel Fracture Registry},
  author       = {Dexing Liu},
  year         = {2026},
  howpublished = {GitHub: ADE-standard/channel-fracture-registry},
  note         = {100 classified cases of channel fracture across 7 agent frameworks}
}
```

---

*"You can't fix failures you can't see."*

*Registry Version: 1.1 · Taxonomy Version: 1.0 · Last Updated: 2026-07-10*
