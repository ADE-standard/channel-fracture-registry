# ADE Channel Fracture Registry

> A Public Taxonomy of Channel Fracture — Cross-Boundary Communication Failures in Agent Systems
>
> 面向多Agent系统的信道断裂（Channel Fracture）公开分类体系

---

## What is Channel Fracture?

**Channel Fracture** (信道断裂) 是指在多Agent系统的组件边界处，
数据或状态被静默丢失/阻塞/扭曲的一类故障模式。
核心特征：调用方认为操作成功，但接收方实际未收到正确数据 —
且操作者无法通过标准监控察觉。

The term was first introduced in [arXiv:2606.04896](https://arxiv.org/abs/2606.04896).

---

## Current Status

| Metric | Value |
|--------|-------|
| **Total Cases** | 100 |
| **Registry IDs** | CF-0001 ~ CF-0100 |
| **Frameworks** | Hermes, LangGraph, CrewAI, LangChain, Semantic Kernel, AutoGen, Google ADK |
| **Root Cause Categories** | 5 taxonomy groups |

### Taxonomy

| Category | Cases | Description |
|----------|-------|-------------|
| [Communication](taxonomy/communication.md) | 38 | Hook misfire, silent message loss, signal suppression |
| [Configuration](taxonomy/configuration.md) | 34 | Config override, credential bypass, env contamination |
| [Execution](taxonomy/execution.md) | 20 | Tool surface illusion, process lifecycle, resource leaks |
| [Memory](taxonomy/memory.md) | 8 | Memory blindness, context loss, state corruption |
| [Verification](taxonomy/verification.md) | 0 | (open for future cases) |

---

## Entry Schema

Each entry follows a standard 14-field format:

```
CF-0001
├── Title
├── Category
├── Affected System
├── Layer (L1-L5)
├── Failure Mode
├── Trigger
├── Observed Symptom
├── Root Cause
├── Detection (CADVP)
├── Impact
├── Mitigation
├── Reference (arxiv:2606.04896)
├── Issue (GitHub URL)
└── Status
```

Full schema: [schema/fracture-schema.yaml](schema/fracture-schema.yaml)

---

## Project Structure

```
channel-fracture-registry/
├── README.md
├── registry/                    ← Standardized case entries
│   ├── CF-0001.md
│   └── ...
├── taxonomy/                    ← Classification by category
│   ├── communication.md
│   ├── memory.md
│   ├── execution.md
│   ├── verification.md
│   └── configuration.md
├── schema/
│   └── fracture-schema.yaml     ← Entry field definitions
├── references/
│   ├── papers.md                ← Academic references
│   └── incidents.md             ← Source incidents
├── registry.json                ← Machine-readable (JSON)
├── registry.csv                 ← Offline analysis (CSV)
├── CONTRIBUTING.md
└── LICENSE
```

---

## Why a Shared Registry?

Agent systems are growing more complex — more components, more boundaries, more frameworks.
When a message is lost between an orchestrator and a tool, when a checkpoint silently drops state,
when a guardrail registers but never fires — these failures share a common pattern across
LangGraph, CrewAI, AutoGen, Semantic Kernel, and every other agent framework:

**The failure happens at a boundary, but neither side can detect it.**

A shared, framework-independent registry helps the entire field:

- **Recognize patterns** — A channel fracture in LangGraph often looks structurally identical to one in CrewAI. Common vocabulary enables cross-framework understanding.
- **Build better tools** — Detection mechanisms (like CADVP probes) work across frameworks when failures are classified the same way.
- **Bridge research and practice** — Academic papers, benchmarks, and production monitoring can reference the same failure taxonomy.
- **Accelerate debugging** — When your agent silently fails, you can search this registry by symptom and find matching root causes from any framework.

This is an open resource. Every framework maintainer, researcher, and practitioner benefits from recognizing
channel fractures sooner — and every contribution makes the taxonomy more useful for everyone.

---

## Expanding Coverage

This registry currently covers **7 agent frameworks** with 100 classified cases.
We welcome community contributions to help expand coverage:

| Area | What's needed |
|------|---------------|
| **More frameworks** | OpenAI Agents SDK, Claude MCP, Dify, TaskWeaver, MetaGPT, PydanticAI, and others |
| **More cases** | Real-world channel fracture reports from production deployments, incident postmortems |
| **Detection tools** | Cross-framework probes, static analysis rules, integration test patterns |
| **Research** | Quantitative studies, failure rate benchmarks, framework comparison papers |

See [CONTRIBUTING.md](CONTRIBUTING.md) for how to submit a case or suggest a framework.

---

## Citation

```bibtex
@misc{ade-channel-fracture-registry,
  title        = {ADE Channel Fracture Registry v1.1},
  author       = {Dexing Liu},
  year         = {2026},
  howpublished = {GitHub: ADE-standard/channel-fracture-registry},
  note         = {100 classified cases of channel fracture across 7 agent frameworks}
}
```

---

*"You can't fix failures you can't see."*

*Registry Version: 1.1 · Last Updated: 2026-07-10*
*Maintained by [@tobiglevent001](https://github.com/tobiglevent001)*
