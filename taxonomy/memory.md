# Taxonomy: memory
Count: 8

- [CF-0001] skip_memory=True: cron succeeds, memory empty, exit code 0 (Hermes Agent, A)
- [CF-0003] skip_memory makes mem0 silently unusable (Hermes Agent, A)
- [CF-0006] Maintainer aggregation: read by default, write with opt-in (Hermes Agent, A)
- [CF-0013] Subagents inherit skip_memory, silently lack MEMORY.md (Hermes Agent, A)
- [CF-0019] Background memory review ignores configured provider, writes legacy only (Hermes Agent, B)
- [CF-0046] MEMORY.md exceeding limit silently breaks memory tool (Hermes Agent, C)
- [CF-0066] Async tasks receive empty context due to last_sync_output truncation (CrewAI, B)
- [CF-0072] ChatGroq mutates per-generation token_usage in place → silent clobber across generations (LangChain, B)
