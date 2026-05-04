# Pi (pi-coding-agent)

**Vendor / origin**: Independent — built by Mario Zechner (badlogic), public from late 2025. Deliberately "un-Google-able" name. Written in TypeScript/Node.js. Notably the harness powering Armin Ronacher's "OpenClaw" experiments.
**License / source**: Open source. Repo: https://github.com/badlogic/pi-mono (monorepo with `pi-ai`, `pi-agent-core`, `pi-tui`, `coding-agent`). MIT [VERIFY].
**Surface**: CLI / terminal-only. No IDE plugin.

## Install & access
- `npm install -g @mariozechner/pi-coding-agent` then `pi`.
- BYOK: set provider API keys in the environment (Anthropic, OpenAI, Google, OpenRouter, local).
- No subscription, no telemetry — you pay only the upstream model costs.

## Core architecture
A small, opinionated three-layer stack: `pi-ai` (unified multi-provider LLM client), `pi-agent-core` (the agent loop — tool schemas, validation, event streaming), and `pi-tui` (terminal UI). The coding agent on top adds hash-anchored edits (edits are validated against a content hash so concurrent file changes are caught), an LSP-aware tool set, Python and browser tools, and sub-agents. The whole thing is intentionally small enough to read in an evening.

## Extension model
- MCP servers via config.
- Custom tools added in TypeScript by writing a small tool definition.
- Sub-agents (delegate a self-contained task to a fresh context) as a first-class primitive.
- Project rules files [VERIFY exact filename, likely `PI.md` or `AGENTS.md`].

## Interaction model
- Single terminal REPL with a TUI built on `pi-tui`.
- **Session tree**: every turn is a node; `/tree` lets you navigate, branch, or rewind to any earlier point — all persisted in one file. This is the "ralphing" / loop-with-reset story: take a side-quest to fix tooling without polluting the main session, then rewind.
- Diff confirmation per edit; an auto mode for trusted loops.
- Parallel sessions = multiple terminals (each session file is standalone).

## How it works (the actual loop)
1. Read prompt + rules + project context.
2. Model proposes tool calls; `pi-agent-core` validates and executes (file edits with hash check, shell, LSP, Python REPL, browser, sub-agent).
3. Stream results back into the model.
4. Each turn is appended to the session tree; user can `/tree` to rewind, branch, or reset and re-run with adjusted context.
Distinctive: hash-anchored edits + branchable session tree make "ralphing" a UI primitive instead of a workaround.

## What's special / cool
- First-class branchable session tree — you can fork the agent, try a fix, abandon it, and resume the trunk.
- Hash-anchored edits stop the agent from blindly clobbering files that changed under it.
- Tiny, hackable, and explicitly anti-bloat — the author treats it as a personal tool, which keeps the surface area small.

## Models supported
Anthropic Claude, OpenAI GPT, Google Gemini, plus anything OpenAI-compatible (OpenRouter, Groq, local Ollama / llama.cpp / Gemma). BYOK only — no hosted plan.

## Pricing / access
Free, OSS. You pay your model provider directly.

## Notable & gotchas
- Solo-maintainer project — bus factor of one and limited support; treat it as a "build your own harness" starting point rather than a product.
- Terminal-only and Node-only; no IDE integration, and the TUI assumes a real terminal (poor experience inside some embedded shells).

## References
- https://github.com/badlogic/pi-mono
- https://mariozechner.at/posts/2025-11-30-pi-coding-agent/
- https://lucumr.pocoo.org/2026/1/31/pi/
- https://www.npmjs.com/package/@mariozechner/pi-coding-agent
