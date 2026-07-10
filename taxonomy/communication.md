# Communication Fractures

Cross-boundary communication failures — messages, events, hooks, signals that are lost or blocked at system boundaries.

## Cases (20)

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
