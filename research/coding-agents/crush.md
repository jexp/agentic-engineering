# Crush

**Vendor / origin**: Built by **Charm** (charmbracelet), the team behind Bubble Tea, Glow, Soft Serve, Lip Gloss, and Wish — i.e. the people who set the modern bar for Go TUIs. Crush appeared in mid-2025 as their take on an agentic coding harness and has been on a fast release cadence (v0.64 in April 2026 [VERIFY]). Written in Go.
**License / source**: Open source, MIT. Repo: https://github.com/charmbracelet/crush.
**Surface**: TUI-first CLI. No desktop app, no hosted service. Runs anywhere a Go binary runs: macOS, Linux, Windows (PowerShell + WSL), Android, FreeBSD, OpenBSD, NetBSD.

## Install & access
`brew install charmbracelet/tap/crush`, `npm i -g @charmland/crush`, `yay -S crush-bin` (Arch), `pkg install crush` (FreeBSD), `nix run nixpkgs#crush`, or download a release binary. Auth is fully BYOK via env vars or interactive setup; no Charm-hosted account is required. The provider/model catalog (Catwalk) auto-updates from a public source so new models show up without a Crush release.

## Core architecture
Crush is a single Go binary that hosts both the TUI (Bubble Tea) and the agent loop. It picks a provider, registers built-in tools (read/write/edit, bash, search, LSP-driven navigation, MCP-bridged tools), and runs a standard tool-use loop against the model. **LSP integration is first-class**: Crush spawns language servers per project so the model gets real type-aware navigation (definitions, references, symbols) instead of grep heuristics. Sessions are local SQLite-backed.

## Extension model
**MCP** is the main extension surface, with stdio, http, and SSE transports. **Agent skills** can be configured to scope behavior or specialize sub-agents [VERIFY current API]. Project rules go in `AGENTS.md` and `.crush` config files. Custom providers are added by pointing Crush at any OpenAI- or Anthropic-compatible endpoint, and there is ongoing work on Crush as an **ACP** client to talk to other agent runtimes.

## Interaction model
You spend almost all your time in the TUI: a chat pane, a tool/diff viewer, and a sidebar. Edits arrive as diffs you accept or reject inline; bash commands prompt for approval by default. Multiple sessions can be opened and switched between within one Crush instance. There is a plan-style mode and an auto-approve toggle for trusted loops. Charm's UI sense shows: the styling, animations, and keymaps are unusually polished for a terminal tool.

## How it works (the actual loop)
1. Load config, attach LSPs and MCP servers, build the tool manifest. 2. Read user input, append to session, persist to SQLite. 3. Call the provider with messages + tools (streaming). 4. Parse tool calls; for file edits, generate a diff, prompt the user, then apply; for bash, prompt and run; for LSP/MCP, dispatch and capture results. 5. Append results, loop until the model finalizes. Distinctive bits: LSP-as-a-tool, the Catwalk auto-updating model registry, and the Charm UI layer.

## What's special / cool
- **The best-looking TUI** in the agent space — the Charm pedigree is visible in every screen.
- **First-class LSP** integration gives the model precise code intelligence rather than text search alone.
- **Catwalk** keeps the provider/model list current without binary upgrades.
- Cleanly portable: same single binary on Windows PowerShell, WSL, every BSD, even Android.

## Models supported
Anthropic, OpenAI, Google Gemini, Amazon Bedrock, GitHub Copilot, Vercel AI Gateway, Z.AI/GLM, MiniMax, Groq, OpenRouter, Hyperbolic, plus any OpenAI- or Anthropic-compatible endpoint — including local Ollama / llama.cpp servers via the OpenAI-compatible adapter.

## Pricing / access
Free and open source; BYOK only. You pay providers directly. Vercel AI Gateway support gives a single billing point and spend monitoring across providers if you want it.

## Notable & gotchas
- Newer than opencode and Goose; APIs and config keys still shift between minor releases.
- LSP startup adds latency on first use of a project; large monorepos can be heavy.
- No hosted/managed offering — if you want a "just works, no keys" experience, Crush is not it; pair with opencode Go or a gateway.

## References
- https://github.com/charmbracelet/crush — repo
- https://github.com/charmbracelet/crush/blob/main/README.md — README
- https://github.com/charmbracelet/crush/releases — releases
- https://vercel.com/docs/agent-resources/coding-agents/crush — Vercel AI Gateway integration
- https://docs.z.ai/devpack/tool/crush — Z.AI provider setup
