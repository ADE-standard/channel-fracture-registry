# Configuration Fractures

Configuration and state failures — config values, env vars, and credentials that are silently overridden or misapplied.

## Cases (19)

- [CF-0009](registry/CF-0009.md) — HERMES_CRON_SESSION env var leaks to interactive sessions
- [CF-0010](registry/CF-0010.md) — FEISHU/WECOM env vars unconditionally override enabled:false
- [CF-0014](registry/CF-0014.md) — Slack adapter silently disabled by top-level config block
- [CF-0015](registry/CF-0015.md) — Profile config ignored when TELEGRAM_BOT_TOKEN in env
- [CF-0016](registry/CF-0016.md) — HASS_TOKEN env force-enables HomeAssistant, overriding enabled:false
- [CF-0017](registry/CF-0017.md) — STT config ignored, gateway hardcodes Whisper despite enabled:false
- [CF-0018](registry/CF-0018.md) — title_generation enabled:false ignored, always runs
- [CF-0026](registry/CF-0026.md) — WhatsApp bridge_port from config.yaml silently ignored
- [CF-0027](registry/CF-0027.md) — WEBHOOK_* env config silently ignored, reports disabled
- [CF-0030](registry/CF-0030.md) — Plugin platforms ignore PREFIX_HOME_CHANNEL env var
- [CF-0034](registry/CF-0034.md) — hermes config set doesn't write to .env, Discord auth silently fails
- [CF-0038](registry/CF-0038.md) — Secondary profile token leaks from default (os.getenv bypass)
- [CF-0039](registry/CF-0039.md) — Secondary profiles connect with default profile's token
- [CF-0041](registry/CF-0041.md) — Bot tokens via os.getenv bypass per-profile secret scope
- [CF-0042](registry/CF-0042.md) — Groq STT ignores provider-specific model in config.yaml
- [CF-0043](registry/CF-0043.md) — HERMES_IGNORE_RULES env var silently ignored by gateway
- [CF-0048](registry/CF-0048.md) — api_server falsely enabled for secondary profiles (os.environ leak)
- [CF-0049](registry/CF-0049.md) — base_url ending in /anthropic causes /v1/v1 double path → silent 404
- [CF-0050](registry/CF-0050.md) — config.yaml vs env precedence: context_length override, thinking-block
