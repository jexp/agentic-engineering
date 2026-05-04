# opencode

**Vendor / origin**: Originally created by the opencode-ai org (Go) in early 2025; the active project at opencode.ai is maintained by SST (the team behind the SST IaC framework) and is written in TypeScript [VERIFY: original Go repo still exists at github.com/opencode-ai/opencode but development momentum has shifted to sst/opencode].
**License / source**: Open source, MIT. Repo: https://github.com/sst/opencode (active), https://github.com/opencode-ai/opencode (original Go).
**Surface**: CLI with rich TUI; also exposes an HTTP server with a typed JS/TS SDK so it can be embedded or driven from editors.

## Install & access
`npm i -g opencode-ai`, `brew install sst/tap/opencode`, or `curl -fsSL https://opencode.ai/install | bash`. Auth is BYOK via env vars or `opencode auth login` per provider; an opencode-managed subscription called **opencode Go** ($5 first month, then $10/month [VERIFY current pricing]) gives access to curated low-cost open-source models without configuring keys. Free tier: bring any provider key (including free Ollama).

## Core architecture
opencode runs a long-lived local server process that owns sessions, tool execution, and provider calls; the TUI is a thin client that talks to it over HTTP. The agent loop sends the conversation plus tool schemas to the chosen model, parses tool calls from the response, executes them locally (file reads/writes, bash, search, LSP), and feeds results back. Multiple clients (TUI, IDE, SDK) can attach to the same server, so a session survives terminal restarts.

## Extension model
Four layers: **MCP servers** (stdio, http, sse) attach external tools; **plugins** are TypeScript modules loaded at startup that can add tools, hooks, or commands; **rules files** (`AGENTS.md`, `.opencoderc`, `opencode.json`) carry per-project instructions; **custom commands** are markdown prompt templates surfaced as `/foo` in the TUI; **sub-agents** can be defined to handle delegated tasks with their own model/tools.

## Interaction model
Primary surface is the TUI: a chat pane, file/diff viewers, and a session sidebar. Edits are applied as patch operations and shown as inline diffs the user can accept, reject, or revise. Modes include normal chat, plan-only, and an auto/yolo mode that skips most confirmations. Multiple sessions run in parallel against the same server, and you can detach/reattach the TUI without losing state.

## How it works (the actual loop)
1. Read user input in TUI, append to session. 2. Build messages from conversation + system prompt + AGENTS.md rules + tool schemas (built-ins plus MCP). 3. Stream from provider. 4. Parse tool-use blocks, ask for approval if required, execute (file edit, bash, glob, grep, LSP, MCP). 5. Append tool results, loop until the model returns a final assistant message. Distinctive: the server/client split, the OpenAPI-described HTTP API, and first-class IDE plugins reusing the same backend.

## What's special / cool
- Genuinely provider-agnostic with 75+ backends [VERIFY count] and a Catwalk-style auto-updating model catalog.
- Server-process design enables IDE plugins, SDK use, and shared sessions across clients.
- Rich TUI is among the most polished in the open-source agent space.
- Optional opencode Go subscription gives a Claude-Code-like experience without bringing your own key.

## Models supported
BYOK across Anthropic (Claude), OpenAI (GPT), Google (Gemini), Bedrock, Azure OpenAI, Groq, Mistral, OpenRouter, DeepSeek, xAI, plus local models via Ollama and any OpenAI-compatible endpoint. The "opencode Go" plan exposes hosted open-source models (Qwen, Kimi, GLM family) [VERIFY exact lineup].

## Pricing / access
Free when you bring your own keys (you pay providers directly). opencode Go subscription: $5 intro, then $10/month for managed access to open-weights models [VERIFY]. No per-seat enterprise tier advertised.

## Notable & gotchas
- Two repos confuse newcomers: the Go-based `opencode-ai/opencode` and the TypeScript SST-led `sst/opencode`. opencode.ai points at the SST one.
- Plugin API and config schema have moved fast; pin a version if you script against it.
- Some providers' tool-use quality varies; agentic loops on smaller local models often stall.

## References
- https://opencode.ai/ — landing page and docs
- https://opencode.ai/docs/ — full documentation
- https://github.com/sst/opencode — active TypeScript repo
- https://github.com/opencode-ai/opencode — original Go repo
- https://opencode.ai/go — opencode Go subscription details
