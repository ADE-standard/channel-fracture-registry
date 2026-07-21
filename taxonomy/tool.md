# Tool Fractures

Tool invocation, parameter passing, and result interpretation failures.

## Scope

Failures where a tool call appears to succeed but:
- The tool was never actually invoked
- Parameters were silently dropped or corrupted in transit
- The return value was coerced or misinterpreted
- The tool executed with wrong credentials or scope
- Retry/replay lacks idempotency guard

## Cases (0 cases)


## Detection

- CADVP CC-7: Tool availability probe with parameter fidelity check
- CADVP CC-8: Execution boundary verification with idempotency guard
- Pre/post invocation parameter snapshot comparison
