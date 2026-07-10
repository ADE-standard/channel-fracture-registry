# State Fractures

State machine, checkpoint, and consistency failures.

## Scope

Failures where agent state is believed to be consistent but:
- Checkpoint data was silently dropped or corrupted
- State machine transition was skipped or duplicated
- Cross-component state diverged without detection
- Persistence layer reports success but data is unrecoverable

## Cases (0)

*(Open for community contributions — state fractures from any agent framework welcome.)*

## Detection

- CADVP CC-4: End-to-end state hash verification after transitions
- CADVP CC-5: Checkpoint integrity validation with replay test
- State machine invariant monitoring at each boundary crossing
