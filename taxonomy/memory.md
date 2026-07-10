# Memory Fractures

Memory and context failures

## Cases (8)

- [CF-0001](../registry/CF-0001.md) — skip_memory=True: cron succeeds, memory empty, exit code 0
- [CF-0003](../registry/CF-0003.md) — skip_memory makes mem0 silently unusable
- [CF-0006](../registry/CF-0006.md) — Maintainer aggregation: read by default, write with opt-in
- [CF-0013](../registry/CF-0013.md) — Subagents inherit skip_memory, silently lack MEMORY.md
- [CF-0019](../registry/CF-0019.md) — Background memory review ignores configured provider, writes legacy only
- [CF-0046](../registry/CF-0046.md) — MEMORY.md exceeding limit silently breaks memory tool
- [CF-0066](../registry/CF-0066.md) — Async tasks receive empty context due to last_sync_output truncation
- [CF-0072](../registry/CF-0072.md) — ChatGroq mutates per-generation token_usage in place → silent clobber across generations
