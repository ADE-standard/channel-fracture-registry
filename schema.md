# ADE Channel Fracture Registry — Schema Definition v1.0

> 字段定义标准 · Field Definition Standard  
> ADE (Agent Delivery Engineering) Channel Fracture Registry  
> Maintained by Qijing Digital · 淇经数科维护

---

## 1. CF-ID 编号体系

**格式**: `CF-NNN`（CF = Channel Fracture，NNN = 三位数字编号）

**分段规则**:
| 范围 | Tier | 说明 |
|------|------|------|
| CF-001 ~ CF-013 | A — Canonical | 教科书级Channel Fracture，四项标准无可争议 |
| CF-014 ~ CF-044 | B — Strong Match | 四项标准全部满足，社区可讨论边界细节 |
| CF-045 ~ CF-052 | C — Candidate | 当前判定符合，等待维护者或社区确认 |

编号一旦分配即永久锁定（即使案例被重新分类，编号不变）。

---

## 2. 核心字段定义

### cf_id
- **类型**: `string`
- **格式**: `CF-NNN`
- **说明**: 案例唯一标识符，全局不可变
- **示例**: `"CF-001"`

### tier
- **类型**: `enum<string>`
- **取值**: `"A"` | `"B"` | `"C"`
- **说明**: 案例确定性分级
  - **A — Canonical**: 四项入选标准无可争议，代表Channel Fracture最纯粹形态
  - **B — Strong Match**: 四项标准全部满足，边界细节可以讨论
  - **C — Candidate**: 当前判定符合，等待社区确认
- **示例**: `"A"`

### github_issue
- **类型**: `string`
- **格式**: `#NNNNN`
- **说明**: GitHub Issue编号（不含URL前缀）
- **示例**: `"#38647"`

### github_url
- **类型**: `string` (URL)
- **格式**: `https://github.com/NousResearch/hermes-agent/issues/{N}`
- **说明**: GitHub Issue完整URL
- **示例**: `"https://github.com/NousResearch/hermes-agent/issues/38647"`

### reported_by
- **类型**: `string`
- **格式**: `@github_username`
- **说明**: 最初报告该Issue的GitHub用户
- **示例**: `"@tobiglevent001"`

### title
- **类型**: `string`
- **说明**: 从Issue推断的故障简述（≤80字符）
- **示例**: `"skip_memory=True: cron succeeds, memory empty, exit code 0"`

### date
- **类型**: `string`
- **格式**: `YYYY-MM`
- **说明**: Issue报告或讨论活跃月份（精确到月）
- **示例**: `"2025-07"`

### framework
- **类型**: `string`
- **说明**: 发生Channel Fracture的Agent框架
- **示例**: `"Hermes Agent"`

### boundary_pair
- **类型**: `string`
- **格式**: `ComponentA↔ComponentB[↔ComponentC]`
- **说明**: 故障发生所在的系统边界对。使用 `↔` (U+2194) 连接。对于多边界案例，列出最核心的两个或三个组件
- **示例**: `"Cron↔Memory"`, `"Config↔Profile↔Platform"`

### failure_mode
- **类型**: `string`
- **说明**: 故障模式的人类可读描述，描述"系统以什么方式失效"
- **示例**: `"Memory Injection Lost"`, `"Hook Not Firing (missing param)"`

### failure_category
- **类型**: `enum<string>`
- **取值** (9类):
  | 值 | 中文 | 说明 |
  |---|---|------|
  | `Config override` | 配置覆盖 | 环境变量无条件覆盖config.yaml |
  | `Tool surface illusion` | 工具表面幻觉 | 工具/hook已注册可见但运行时静默失效 |
  | `Hook not firing` | Hook未触发 | Hook已注册但静默不执行 |
  | `Silent message loss` | 静默消息丢失 | 消息发送表面成功但内容被丢弃/截断 |
  | `Connection illusion` | 连接幻觉 | 适配器显示已连接但服务端订阅已丢失 |
  | `Credential scope bypass` | 凭证作用域绕过 | 多Profile静默使用错误Profile的凭证 |
  | `Memory blindness` | 记忆盲区 | Agent运行缺少应有的记忆上下文，无警告 |
  | `Env contamination` | 环境变量污染 | 环境变量跨越会话/Profile边界泄露 |
  | `Process lifecycle` | 进程生命周期 | 重启/关闭未验证清理，导致静默状态损坏 |
- **示例**: `"Memory blindness"`

### is_silent
- **类型**: `boolean`
- **说明**: 故障是否完全静默（操作者通过标准监控无法察觉）
- **示例**: `true`

### is_cross_agent
- **类型**: `boolean`
- **说明**: 故障是否涉及多个Agent实例间的边界（如Subagent↔Parent, Cron↔Interactive Session）
- **示例**: `false`

### ade_layer
- **类型**: `enum<string>`
- **取值**: `"L1"` | `"L2"` | `"L3"` | `"L4"` | `"L5"`
- **说明**: ADE五层架构中的归属层（详见第3节）
- **示例**: `"L1"`

### root_cause
- **类型**: `string`
- **说明**: 根因简述（≤120字符），描述"为什么系统以这种方式失效"
- **示例**: `"Cron jobs with skip_memory=True silently discard all memory operations"`

### evidence_url
- **类型**: `string` (URL)
- **说明**: 主要证据来源URL（通常与github_url相同）
- **示例**: `"https://github.com/NousResearch/hermes-agent/issues/38647"`

### pr
- **类型**: `string`
- **格式**: `#NNNNN` 或空字符串
- **说明**: 关联的修复PR编号。空字符串表示尚无PR
- **示例**: `"#45769"`

---

## 3. ADE Layer 五层架构

ADE (Agent Delivery Engineering) 将Channel Fracture按系统边界所在层次分为五层：

### L1 — 认知与记忆层 (Cognition & Memory)
Agent的记忆、上下文、知识管理相关边界。

**包含的边界对**:
- Cron↔Memory
- Memory↔Provider
- Memory↔Plugin
- Subagent↔Memory
- FS↔Memory↔Agent
- Plugin↔Memory↔Dependency

### L2 — 通信与事件层 (Communication & Events)
消息传输、Hook触发、会话生命周期相关边界。

**包含的边界对**:
- Hook↔Plugin（所有Hook类型）
- Transport↔Agent
- Transport↔Gateway
- Transport↔Session
- Transport↔App
- Transport↔Agent↔File
- Transport↔Gateway↔Watchdog
- Hook↔Gateway↔Session
- Hook↔Kanban↔Agent

### L3 — 状态与配置层 (State & Configuration)
配置管理、Profile隔离、凭证作用域、CLI/TUI交互相关边界。

**包含的边界对**:
- Config↔Platform
- Profile↔Credential
- Profile↔Config
- Config↔Profile
- Profile↔Credential↔Platform
- Agent↔CLI/TUI
- Cron↔Session
- Process↔Gateway
- Config↔Env↔Agent
- Profile↔Config↔Platform
- Gateway↔Platform↔Monitor
- Hook↔Profile↔Plugin
- CLI↔Config↔Platform

### L4 — 工具与能力层 (Tools & Capabilities)
工具注册、能力配置、辅助功能、API端点相关边界。

**包含的边界对**:
- Config↔Tool↔Platform
- Config↔Auxiliary
- Config↔STT
- Config↔Webhook
- Config↔Auxiliary↔API
- Config↔Gateway↔Rules
- Config↔STT↔Provider
- Config↔Plugin↔Platform

### L5 — 调度与编排层 (Scheduling & Orchestration)
定时任务调度、看板管理、多Agent编排相关边界。

**包含的边界对**:
- Scheduler↔Transport
- CLI↔FS↔Agent
- Kanban↔StateDB
- Kanban↔StateDB↔Dashboard

### 多边界案例的层归属规则

当一个案例涉及多个边界对时（如 `Cron↔Memory↔Tool`），选择**最核心**的边界对来确定ADE Layer：
1. 优先选择故障的**根本发生位置**（root cause所在边界）
2. 其次选择对故障影响**最大**的边界
3. 同一ADE Layer内的多边界不产生歧义

---

## 4. Tier 分级标准

### 入选标准（必须全部满足）

| 标准 | 代号 | 含义 |
|------|------|------|
| 跨边界 | C1 | 涉及≥2个系统边界（Agent, Memory, Plugin, Transport, Scheduler, Config, Profile, Credential等） |
| 边界处数据/状态丢失 | C2 | 数据或状态在跨越边界时被丢失、阻塞或扭曲 |
| 静默或半静默 | C3 | 调用方认为操作成功，操作者无感知 |
| 根因在接口/协议/配置/生命周期 | C4 | 根因是系统间交互方式的问题，非单一组件内部逻辑错误 |

### 分级判定

| Tier | 标签 | 判定条件 |
|------|------|---------|
| A — Canonical | 经典案例 | 四项标准无可争议，不存在合理分歧空间 |
| B — Strong Match | 强匹配 | 四项标准全部满足，边界细节可讨论 |
| C — Candidate | 候选 | 当前判定符合，等待维护者或社区确认 |

---

## 5. 文件格式规范

### registry.json
- JSON数组，每个元素一个案例对象
- 编码: UTF-8（无BOM）
- 缩进: 2空格
- 字段: 所有上述字段

### registry.csv
- CSV格式，首行为字段名
- 编码: UTF-8 with BOM（兼容Excel）
- 分隔符: 逗号
- 字段: 与JSON相同

### cases/CF-NNN.md
- Markdown格式
- A类案例：完整描述（背景、故障链、ADE Layer分析、修复状态）
- B/C类案例：基本信息 + 简要分析

---

*Schema Version: 1.0 · Last Updated: 2026-07-10*
*Maintained by Qijing Digital (淇经数科)*
