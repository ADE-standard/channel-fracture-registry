# Communication Fractures

Cross-boundary communication failures

## Cases (38)

- [CF-0007](registry/CF-0007.md) — post_tool_call registered but turn_id never passed → silent no-op
- [CF-0008](registry/CF-0008.md) — session_id not propagated to pre_tool_call → silent no-op
- [CF-0011](registry/CF-0011.md) — errcode 846609: send fails, adapter appears connected
- [CF-0012](registry/CF-0012.md) — DM keeps watchdog alive, group chat silently dropped
- [CF-0021](registry/CF-0021.md) — OpenViking on_memory_write mirroring silently fails
- [CF-0022](registry/CF-0022.md) — lark-streaming suppresses send_message output (messages dropped)
- [CF-0023](registry/CF-0023.md) — Messages silently dropped under iLink rate limiting
- [CF-0024](registry/CF-0024.md) — WeChat replies >10 segments silently truncated
- [CF-0028](registry/CF-0028.md) — on_session_finalize not fired on idle-timeout expiry
- [CF-0029](registry/CF-0029.md) — QQBot WebSocket hangs on stale CLOSE-WAIT, gateway frozen
- [CF-0031](registry/CF-0031.md) — Weixin rate limit causes message loss — no backoff + reconnect
- [CF-0032](registry/CF-0032.md) — pre_tool_call and on_session_finalize don't fire in kanban-worker
- [CF-0035](registry/CF-0035.md) — Gateway status doesn't expose platform health — stale adapters appear healthy
- [CF-0036](registry/CF-0036.md) — Slack Socket Mode aiohttp leaks closed sessions — unhealthy reconnect
- [CF-0037](registry/CF-0037.md) — transform_llm_output hook not firing on non-default profiles
- [CF-0040](registry/CF-0040.md) — WeCom stale req_id causes 846605 on reconnect — no fallback
- [CF-0044](registry/CF-0044.md) — send_message omits MEDIA attachments for email targets
- [CF-0045](registry/CF-0045.md) — _write_status_dot causes silent message loss when agent_status is directory
- [CF-0051](registry/CF-0051.md) — TUI eagerly persists empty sessions — ghost sessions clutter /resume
- [CF-0052](registry/CF-0052.md) — Kanban dashboard resurrects archived/deleted boards as empty stubs
- [CF-0053](registry/CF-0053.md) — local_read() returns live mutable channel state → silent state corruption
- [CF-0056](registry/CF-0056.md) — GraphInterrupt not re-raised in awrap_tool_call → signal silently swallowed
- [CF-0062](registry/CF-0062.md) — ToolCallResult auto-coerces structured outputs to str() → losing type info
- [CF-0063](registry/CF-0063.md) — AI guardrails silently fail: 32 violations over 56 days despite all configured
- [CF-0065](registry/CF-0065.md) — Fabricated-Observation recovery dead code → tool calls silently discarded
- [CF-0071](registry/CF-0071.md) — Structured output with raw JSON-schema dict never validated → ToolStrategy handle_errors unreachable
- [CF-0073](registry/CF-0073.md) — ChatAnthropic drops thinking field from empty thinking blocks → replay fails with 400
- [CF-0075](registry/CF-0075.md) — SummarizationMiddleware preserves orphan ToolMessages → provider 400 on next call
- [CF-0076](registry/CF-0076.md) — model_to_tools router returns 'model' but path_map omits it → KeyError silently aborts
- [CF-0078](registry/CF-0078.md) — before/after_kickoff_callbacks do not support async callables in akickoff → silently skipped
- [CF-0084](registry/CF-0084.md) — ChatHistory broken when LLM calls multiple tools in one message → history unusable for subsequent requests
- [CF-0085](registry/CF-0085.md) — $defs not preserved in AIFunctionKernelFunction → MCP tool schema incomplete to LLM
- [CF-0087](registry/CF-0087.md) — Agent execution loop crashes with TypeError when custom tool returns nested dict → no graceful fallback
- [CF-0088](registry/CF-0088.md) — @listen(or_(A,B,C)) multi-source OR listener only fires once → blocking cyclic flow re-triggering
- [CF-0090](registry/CF-0090.md) — Reasoning plan always detects 'NOT READY' even when model indicates 'READY' → plan stuck in loop
- [CF-0094](registry/CF-0094.md) — Bedrock connector rejects parallel tool calls → toolResult blocks not merged into single Converse message
- [CF-0098](registry/CF-0098.md) — ChatFireworks._combine_llm_outputs raises TypeError on nested token_usage dicts in batched generate()
- [CF-0099](registry/CF-0099.md) — chroma similarity_search returns raw distances instead of normalized relevance scores
