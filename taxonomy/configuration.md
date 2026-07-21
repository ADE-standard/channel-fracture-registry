# Configuration Fractures

Configuration and state failures

## Cases (35 cases)

- [CF-0009](../registry/CF-0009.md) — HERMES_CRON_SESSION env var leaks to interactive sessions
- [CF-0010](../registry/CF-0010.md) — FEISHU/WECOM env vars unconditionally override enabled:false
- [CF-0014](../registry/CF-0014.md) — Slack adapter silently disabled by top-level config block
- [CF-0015](../registry/CF-0015.md) — Profile config ignored when TELEGRAM_BOT_TOKEN in env
- [CF-0016](../registry/CF-0016.md) — HASS_TOKEN env force-enables HomeAssistant, overriding enabled:false
- [CF-0017](../registry/CF-0017.md) — STT config ignored, gateway hardcodes Whisper despite enabled:false
- [CF-0018](../registry/CF-0018.md) — title_generation enabled:false ignored, always runs
- [CF-0026](../registry/CF-0026.md) — WhatsApp bridge_port from config.yaml silently ignored
- [CF-0027](../registry/CF-0027.md) — WEBHOOK_* env config silently ignored, reports disabled
- [CF-0030](../registry/CF-0030.md) — Plugin platforms ignore PREFIX_HOME_CHANNEL env var
- [CF-0034](../registry/CF-0034.md) — hermes config set doesn't write to .env, Discord auth silently fails
- [CF-0038](../registry/CF-0038.md) — Secondary profile token leaks from default (os.getenv bypass)
- [CF-0039](../registry/CF-0039.md) — Secondary profiles connect with default profile's token
- [CF-0041](../registry/CF-0041.md) — Bot tokens via os.getenv bypass per-profile secret scope
- [CF-0042](../registry/CF-0042.md) — Groq STT ignores provider-specific model in config.yaml
- [CF-0043](../registry/CF-0043.md) — HERMES_IGNORE_RULES env var silently ignored by gateway
- [CF-0048](../registry/CF-0048.md) — api_server falsely enabled for secondary profiles (os.environ leak)
- [CF-0049](../registry/CF-0049.md) — base_url ending in /anthropic causes /v1/v1 double path → silent 404
- [CF-0050](../registry/CF-0050.md) — config.yaml vs env precedence: context_length override, thinking-block
- [CF-0061](../registry/CF-0061.md) — get_config() async guard silenced on Python < 3.11 → RuntimeError never raised
- [CF-0064](../registry/CF-0064.md) — Agent self-modification in Canvas memory → behavior escapes original constraints
- [CF-0067](../registry/CF-0067.md) — ProviderCapabilities static fallbacks skipped when LiteLLM introspection fails
- [CF-0068](../registry/CF-0068.md) — PostgresStore.search() uses unescaped SQL LIKE → returns rows from foreign names
- [CF-0070](../registry/CF-0070.md) — _resolve_schemas processes repeated state schema at FIRST position → silent fiel
- [CF-0074](../registry/CF-0074.md) — cache_control on tool_use content block silently dropped when matching tool_call
- [CF-0077](../registry/CF-0077.md) — DNS Rebinding bypass in SSRF protection; MCP tools bypass SSRF validation entire
- [CF-0080](../registry/CF-0080.md) — adk api_server --a2a silently mounts no A2A routes → UnboundLocalError swallowed
- [CF-0081](../registry/CF-0081.md) — McpToolset mTLS overrides header_provider's Authorization silently → ambient cre
- [CF-0082](../registry/CF-0082.md) — ReasoningEffort setting lost when invoking orchestration → handoff drops model c
- [CF-0091](../registry/CF-0091.md) — cache_breakpoint injected into messages for non-Anthropic providers (Groq, OpenA
- [CF-0092](../registry/CF-0092.md) — Task(human_input=True) raises AttributeError after default executor swap → silen
- [CF-0096](../registry/CF-0096.md) — Google AI connector leaks thinking/thought text parts into ChatMessageContent → 
- [CF-0097](../registry/CF-0097.md) — Auto Function Invocation lacks runtime RBAC → unauthorized execution via indirec
- [CF-0100](../registry/CF-0100.md) — get_num_tokens_from_messages raises NotImplementedError for OpenAI o1 and o3 mod
- [CF-0107](../registry/CF-0107.md) — Google ADK: --a2a flag silently mounts no A2A routes due to shadowed json import
