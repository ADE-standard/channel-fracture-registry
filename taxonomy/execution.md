# Execution Fractures

Execution and tool failures

## Cases (21 cases)

- [CF-0002](../registry/CF-0002.md) — memory() tool exposed but unavailable at runtime
- [CF-0004](../registry/CF-0004.md) — skip_memory blocks fact_store from all cron jobs
- [CF-0005](../registry/CF-0005.md) — Memory tool exposed but unavailable at runtime
- [CF-0020](../registry/CF-0020.md) — gateway restart doesn't verify old process termination, silent failure
- [CF-0025](../registry/CF-0025.md) — Planned-restart fires during cron delivery — message silently dropped
- [CF-0033](../registry/CF-0033.md) — discord tools silently hidden when DISCORD_BOT_TOKEN only in .env
- [CF-0047](../registry/CF-0047.md) — Honcho provider activates even when dependency is missing
- [CF-0054](../registry/CF-0054.md) — checkpoints never flushed mid-session; data loss on non-graceful exit
- [CF-0055](../registry/CF-0055.md) — durability='sync': put_writes/put order unenforced → inconsistent crash recovery
- [CF-0057](../registry/CF-0057.md) — Checkpoint serialization downcasts defaultdict/Counter to plain dict → losing de
- [CF-0058](../registry/CF-0058.md) — Checkpoint serialization drops deque maxlen → bounded becomes unbounded after ro
- [CF-0059](../registry/CF-0059.md) — Deleting thread leaks channel blobs → unbounded memory growth in long-running se
- [CF-0060](../registry/CF-0060.md) — put_writes/put persistence order unenforced → post-crash recovery host-dependent
- [CF-0069](../registry/CF-0069.md) — error_handler re-raises handled exception when node runs in parallel → execution
- [CF-0079](../registry/CF-0079.md) — Sync BaseCodeExecutor.execute_code called directly on event loop → long executio
- [CF-0083](../registry/CF-0083.md) — AgentGroupChat fails with 'Unknown response format dict' when Azure Monitor enab
- [CF-0086](../registry/CF-0086.md) — Async task LLM failure silently freezes flow → no exception, no log, process han
- [CF-0089](../registry/CF-0089.md) — Tool re-execution on task retry has no idempotency guard → duplicate payments/em
- [CF-0093](../registry/CF-0093.md) — Individual MCP tool failure aborts entire agent run → no error isolation between
- [CF-0095](../registry/CF-0095.md) — RedisJsonCollection.delete() silently fails when prefix_collection_name_to_key_n
- [CF-0103](../registry/CF-0103.md) — Long tool calls (~180s+) silently re-executed from checkpoint on LangGraph Cloud
