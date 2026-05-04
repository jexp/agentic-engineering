# Gemini CLI

**Vendor / origin**: Google (google-gemini org), announced June 2025; written in TypeScript/Node.js [VERIFY language].
**License / source**: Open source, Apache 2.0 [VERIFY]. Repo: https://github.com/google-gemini/gemini-cli
**Surface**: CLI (terminal-native); also embedded in Cloud Shell and tied to Gemini Code Assist for IDEs.

## Install & access
- `npx @google/gemini-cli` (no install) or `npm install -g @google/gemini-cli`.
- Auth via personal Google account (OAuth) for the free tier, or API key from AI Studio / Vertex.
- Free tier: ~60 requests/min, ~1,000/day against Gemini 2.5 Pro for individuals. Paid via Vertex AI / Gemini API billing for higher limits or enterprise use.

## Core architecture
The binary is a Node-based REPL that runs an agent loop against the Gemini API. Each turn the model can call built-in tools (read/write file, shell, web fetch, Google Search grounding) and MCP servers; results are fed back into the next model call until the model emits a final answer. It leans heavily on Gemini's 1M+ token context window to load large repos directly rather than relying solely on retrieval. ReAct-style loop with explicit tool-call schemas.

## Extension model
- MCP servers (stdio + HTTP) configured via `~/.gemini/settings.json`.
- Custom commands and "skills"/plugins introduced in 2025-2026 [VERIFY skills naming].
- `GEMINI.md` rules file (analog of CLAUDE.md / AGENTS.md) for per-project instructions.
- Hooks and sub-agent style delegation via configuration.

## Interaction model
Single terminal REPL. User types prompts, sees streaming output and tool calls inline. Slash commands (e.g. `/tools`, `/mcp`, `/memory`). Diff-style review for file edits with per-edit confirmation; an auto/yolo mode skips confirmations. Multiple concurrent sessions = multiple terminals.

## How it works (the actual loop)
1. Read prompt + project context (`GEMINI.md`, optionally whole files via huge context).
2. Send to Gemini with tool schemas; model returns tool calls or text.
3. Execute tools (shell, file IO, web, MCP), append results.
4. Repeat until model returns final answer; user confirms edits unless in auto mode.
Distinctive: Google Search grounding as a first-class tool, and 1M-token context that often replaces RAG.

## What's special / cool
- Built-in Google Search grounding tool returning citations.
- Generous free tier on Gemini 2.5/3 Pro (the most generous among major vendor CLIs).
- 1M-token context lets it ingest entire mid-sized repos in one shot.

## Models supported
Native: Gemini 2.5/3 Pro and Flash. BYOK via Vertex AI / AI Studio API keys. No first-party multi-provider; some community forks add Claude/OpenAI [VERIFY].

## Pricing / access
Free with Google account at the limits above. Paid usage via standard Gemini API / Vertex AI per-token rates. No subscription product specifically for the CLI.

## Notable & gotchas
- Free-tier requests are used for telemetry/training unless you switch to a paid API key — read the auth prompt carefully.
- Tooling and skill naming have churned through 2025-2026; check the repo README for the current command set [VERIFY].

## References
- https://github.com/google-gemini/gemini-cli
- https://blog.google/technology/developers/introducing-gemini-cli-open-source-ai-agent/
- https://developers.google.com/gemini-code-assist/docs/gemini-cli
- https://geminicli.com/docs/
