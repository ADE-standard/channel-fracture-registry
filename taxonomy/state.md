# State Fractures

State machine, checkpoint, and consistency failures.

## Scope

Failures where agent state is believed to be consistent but:
- Checkpoint data was silently dropped or corrupted
- State machine transition was skipped or duplicated
- Cross-component state diverged without detection
- Persistence layer reports success but data is unrecoverable

## Cases (3 cases)

- [CF-0101](../registry/CF-0101.md) — Checkpoint deserialization silently loses state when JsonPlusSerializer encounte
- [CF-0102](../registry/CF-0102.md) — langgraph dev: checkpoints never flushed mid-session; data loss on non-graceful 
- [CF-0104](../registry/CF-0104.md) — Run Cancellation Causes Loss of Streamed State Not Yet Persisted as a Checkpoint
## Detection

- CADVP CC-4: End-to-end state hash verification after transitions
- CADVP CC-5: Checkpoint integrity validation with replay test
- State machine invariant monitoring at each boundary crossing
