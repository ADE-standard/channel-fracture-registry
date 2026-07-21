# 非CF候选清单

> 以下 GitHub issues 在 2026-07-21 搜索中被审阅，按 C1-C4 标准严格评估后判定**不满足 Channel Fracture 定义**。
> 保留在此供未来参考（可能含非静默故障、性能问题、用户错误等）。

| Issue | 框架 | 摘要 | 拒绝理由 |
|-------|------|------|----------|
| [#430](https://github.com/crewAIInc/crewAI/issues/430) | CrewAI | SerperDevTool._run() missing argument | 错误明确抛出并回显给用户（非静默） |
| [#7714](https://github.com/langchain-ai/langgraph/issues/7714) | LangGraph | Checkpoint serialization 85% storage bloat + silent pass | 核心是性能问题，silent pass 仅为附带提及 |
| [#6439-B2](https://github.com/crewAIInc/crewAI/issues/6439) | CrewAI | after_kickoff_callbacks replaces result with None | 用户回调未return是用户代码缺陷，非跨边界断裂 |
| [#7851](https://github.com/microsoft/autogen/issues/7851) | AutoGen | MCP tool error isolates entire agent | 抛致命异常，非静默（显式 abort） |

---
> 最后更新: 2026-07-21 | 审批标准: CFR C1-C4
