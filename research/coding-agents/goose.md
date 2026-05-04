# Goose

**Vendor / origin**: Built by Block (the company formerly known as Square, parent of Cash App) and announced as "codename goose" in January 2025. Written in Rust, with an Electron desktop UI. In December 2025 Block contributed Goose to the Linux Foundation's Agentic AI Foundation for neutral governance.
**License / source**: Open source, Apache 2.0. Repo: https://github.com/block/goose. Docs: https://block.github.io/goose/ (now also https://goose-docs.ai).
**Surface**: CLI plus a desktop app (Electron). No proprietary cloud; everything runs on your machine.

## Install & access
One-liner: `curl -fsSL https://github.com/block/goose/releases/download/stable/download_cli.sh | bash`, plus a Desktop installer for macOS/Windows/Linux. Configuration via `goose configure` writes `~/.config/goose/config.yaml`, which is shared between CLI and Desktop. Auth is BYOK per provider; you can also use existing Anthropic/OpenAI/Google subscriptions via ACP. Free to run; you pay your model provider.

## Core architecture
Goose is a Rust-based agent runtime. The core loop assembles system prompt + conversation + enabled extension tool schemas, calls the configured provider, parses tool calls, and dispatches them. A defining choice: **tools are not built into the binary** — almost every capability (developer tools, computer-controller, memory, JetBrains, GitHub, Google Drive, etc.) is implemented as an MCP server that Goose launches as a subprocess. The agent is a thin orchestrator over MCP.

## Extension model
**MCP-first**: 70+ official and community extensions speak the Model Context Protocol. Add them with `goose session --with-extension 'cmd'`, `--with-builtin name`, or via `goose configure`. Beyond extensions, **recipes** are YAML files that package instructions, extensions, and parameters into a reusable, shareable agent configuration; recipes can be scheduled (`goose schedule add ... --cron`). Project-level instructions live in `.goosehints` / `AGENTS.md`.

## Interaction model
Primary surface is `goose session` in the terminal: an interactive chat where the agent reads, writes, and runs code with confirmation prompts (configurable). The Desktop app gives the same loop with a chat window, file pickers, and a one-click extension manager. Plan/edit/auto behavior is governed by per-tool approval policies in the config rather than an explicit mode switch. Sessions are persisted by name; you can resume with `goose session --resume`.

## How it works (the actual loop)
1. Load config, start enabled MCP extension subprocesses, gather their tool manifests. 2. Read user message, append to session. 3. Send messages + system prompt + tool schemas to provider. 4. Parse tool calls, route each to the owning MCP server, prompt user if policy requires confirmation. 5. Stream tool results back into the conversation. 6. Loop until the model produces a final answer or hits a stop condition. Distinctive: every external capability is an MCP subprocess, so adding tools requires no rebuild.

## What's special / cool
- The most committed MCP-native open agent — Block's bet on MCP predates much of the ecosystem and shapes the whole design.
- **Recipes** turn agent setups into versionable, shareable, schedulable artifacts — closer to "infrastructure as code" for agents than most competitors offer.
- Now under Linux Foundation governance with backing from AWS, Anthropic, Google, Microsoft, OpenAI — unusually broad neutrality for a coding agent.
- Equal parity between CLI and Desktop, sharing one config.

## Models supported
15+ providers: Anthropic, OpenAI, Google, Azure OpenAI, Amazon Bedrock, Databricks, Groq, OpenRouter, Ollama (local), plus any OpenAI-compatible endpoint. Provider and model are selected at config time and switchable per session.

## Pricing / access
Free and open source. You pay only your chosen LLM provider. Block does not run a hosted Goose service; ACP support means you can route through existing Claude/ChatGPT/Gemini subscriptions [VERIFY current ACP coverage].

## Notable & gotchas
- Because every tool is an MCP subprocess, startup is slower than monolithic agents, and a misbehaving extension can block the loop.
- Tool-use quality depends heavily on the provider; small local models via Ollama often fail to call MCP tools reliably.
- The repo recently moved/renamed (`block/goose` → `aaif-goose/goose` redirect appears in some links) due to the Linux Foundation transition [VERIFY canonical location after GA].

## References
- https://github.com/block/goose — main repo
- https://block.github.io/goose/ — original docs
- https://goose-docs.ai/ — new docs site
- https://block.xyz/inside/block-open-source-introduces-codename-goose — launch post
- https://github.com/block/goose/blob/main/AGENTS.md — agent/contributor guide
