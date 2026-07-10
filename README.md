# ADE Channel Fracture Registry

> A Public Failure Knowledge Base for Multi-Agent Reliability Engineering  
> 面向多Agent可靠性工程的公开故障知识库

---

## What is Channel Fracture? · 什么是Channel Fracture?

**Channel Fracture** (信道断裂) 是指在多Agent系统的组件边界处，数据或状态被静默丢失/阻塞/扭曲的一类故障模式。这类故障的核心特征：调用方认为操作成功，但接收方实际未收到正确数据 — 且操作者无法通过标准监控察觉。

The term was first introduced in [arXiv:2606.04896](https://arxiv.org/abs/2606.04896) and initially reported in [#38647](https://github.com/NousResearch/hermes-agent/issues/38647).

---

## Current Status · 当前状态

| Metric | Value |
|--------|-------|
| **Total Cases** | 52 |
| Tier A — Canonical | 13 |
| Tier B — Strong Match | 31 |
| Tier C — Candidate | 8 |
| **Root Cause Categories** | 9 |
| **System Boundary Pairs** | 39 |
| **Framework** | Hermes Agent |

### Root Cause Categories · 根因分类

| Category | Description |
|----------|-------------|
| **Config override** | Environment variables unconditionally override config.yaml |
| **Tool surface illusion** | Tool is registered and visible but silently non-functional |
| **Hook not firing** | Hook is registered but silently never executes |
| **Silent message loss** | Message appears sent but content is dropped/truncated |
| **Connection illusion** | Adapter appears connected but subscription is lost |
| **Credential scope bypass** | Multi-profile silently uses wrong credentials |
| **Memory blindness** | Agent lacks memory context it should have, no warning |
| **Env contamination** | Environment variables leak across boundaries |
| **Process lifecycle** | Restart/shutdown doesn't verify cleanup |

---

## Registry Structure · 注册表结构

```
channel-fracture-registry/
├── README.md              ← 本文件 (入口文档)
├── registry.json          ← 机器可读格式 (JSON数组, 52条记录)
├── registry.csv           ← 离线分析格式 (UTF-8 BOM, Excel兼容)
├── schema.md              ← 字段定义标准 (ADE Layer映射, Tier分级)
└── cases/
    ├── CF-001.md          ← 详细案例描述 (A类: 完整 · B/C类: 基本)
    ├── CF-002.md
    ├── ...
    └── CF-052.md
```

---

## How to Contribute · 如何贡献

1. **Submit a case**: 在 [#38647](https://github.com/NousResearch/hermes-agent/issues/38647) 分享你遇到的疑似Channel Fracture
2. **Classification review**: 社区评估是否符合四项入选标准 (C1-C4)
3. **Tier assignment**: 初步分配A/B/C/Candidate Tier
4. **Registry entry**: 维护者将其加入本注册表

### Inclusion Criteria · 入选标准

All four must be met (必须同时满足四项):
1. **Cross-boundary** (跨边界) — involves ≥2 system boundaries
2. **Data/state loss at boundary** (边界处数据丢失) — data or state lost/blocked/distorted
3. **Silent or semi-silent** (静默) — caller believes success, no operator-visible error
4. **Root cause at interface/protocol/config/lifecycle** (接口根因) — NOT business logic bug

---

## Citation · 引用

```bibtex
@misc{ade-channel-fracture-registry,
  title        = {ADE Channel Fracture Registry v1.0},
  author       = {Qijing Digital (淇经数科)},
  year         = {2026},
  howpublished = {GitHub Issues: NousResearch/hermes-agent},
  note         = {52 cases: A=13, B=31, C=8. Maintained by @tobiglevent001.}
}
```

**Suggested citation**: 淇经数科. (2026). *ADE Channel Fracture Registry v1.0*. GitHub Issues: NousResearch/hermes-agent. 52 cases.

---

*Registry Version: 1.0 · Last Updated: 2026-07-10*
*Maintained by [@tobiglevent001](https://github.com/tobiglevent001) (Qijing Digital / 淇经数科)*
