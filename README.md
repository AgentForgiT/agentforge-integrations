# agentforge-integrations

**Reference hub for AgentForge integrations: IDE, CLI, providers, and tools.**

Per DEC-0007 the canonical implementation lives in the
[`agentforge` monorepo](https://github.com/AgentForgiT/agentforge).
This repository documents integration surfaces and tracks integration plans.

## What exists (shipped, canonical)

### Provider adapters (gateway)

| Provider | Type | ADR |
| --- | --- | --- |
| `mock` | deterministic, offline | — |
| `ollama` | keyless local, OpenAI-compatible `/v1` | [ADR-0017](https://github.com/AgentForgiT/agentforge/blob/main/.agentforge/adrs/0017-ollama-local-provider-boundary.md) |
| `openrouter` | cloud (OpenAI-compatible) | ADR-0011/0016 |
| `anthropic` | outbound provider, Messages API | [ADR-0021](https://github.com/AgentForgiT/agentforge/blob/main/.agentforge/adrs/0021-anthropic-outbound-provider.md) |

### Client surfaces
- OpenAI-compatible `POST /v1/chat/completions` (+ SSE streaming)
- Anthropic Messages `POST /v1/messages` (translated at the edge)
- MCP `POST /mcp` (JSON-RPC 2.0)
- Python SDK (`apps/sdk`, thin client, both surfaces)

### IDE / AI-tool registration
The **compatibility matrix** — what each tool & IDE supports — is live on the
site: [compatibility.html](https://agentforgit.github.io/agentforge-docs-site/compatibility.html).
Verified fact base for Claude Code, Codex CLI, OpenCode, Cursor, Cline, and
the AgentForge gateway is published in the
[compatibility matrix](https://agentforgit.github.io/agentforge-docs-site/compatibility.html)
(Sprint 22 rule: every cell web-verified and cited).

## Planned

- VS Code / JetBrains / Neovim integration recipes (Epic 5, IDE Compatibility)
- MCP client mode + more provider adapters (Epic 3)

## Contributing

New providers/integrations: ordinary governed changes in the monorepo — see
[CONTRIBUTING.md](https://github.com/AgentForgiT/agentforge/blob/main/CONTRIBUTING.md)
and the Sprint-20 provider-adapter pattern (`references/provider-adapter-pattern.md`).