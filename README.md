# ADE Channel Fracture Registry

> A Public Taxonomy of Silent Reliability Failures in Agent Systems
>
> 面向多Agent系统的静默可靠性失效公开分类体系

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
| **Total Cases** | 52 |
| **Registry IDs** | CF-0001 ~ CF-0052 |
| **Frameworks** | Hermes Agent |
| **Root Cause Categories** | 9 |

### Taxonomy

| Category | Cases | Description |
|----------|-------|-------------|
| [Configuration](taxonomy/configuration.md) | 19 | Config overrides, credential bypass, env contamination |
| [Communication](taxonomy/communication.md) | 18 | Hook misfire, silent message loss, connection illusion |
| [Memory](taxonomy/memory.md) | 6 | Memory blindness, context loss |
| [Execution](taxonomy/execution.md) | 10 | Tool surface illusion, process lifecycle |
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

## Why a Registry, Not Just a Bug Label?

- **Bug labels** are project-internal management tools.
- **Registry IDs** are domain identifiers — CF-0001 is permanently citable,
  independent of any platform's issue numbering.
- When future papers cite `Channel Fracture Registry Entry CF-0001`,
  it's unambiguous and professional.

---

## Roadmap

| Phase | Goal |
|-------|------|
| v1.0 (current) | 52 Hermes cases, fixed schema, standard template |
| v1.1 | Cross-framework expansion: LangGraph, CrewAI, AutoGen |
| v1.2 | OpenAI Agents SDK, Claude MCP ecosystem |
| v2.0 | Community contributions, self-report mechanism |

---

## Citation

```bibtex
@misc{ade-channel-fracture-registry,
  title        = {ADE Channel Fracture Registry v1.0},
  author       = {Dexing Liu},
  year         = {2026},
  howpublished = {GitHub: ADE-standard/channel-fracture-registry},
  note         = {52 classified cases of silent reliability failures in agent systems}
}
```

---

*"You can't fix failures you can't see."*

*Registry Version: 1.0 · Last Updated: 2026-07-10*
*Maintained by [@tobiglevent001](https://github.com/tobiglevent001)*
