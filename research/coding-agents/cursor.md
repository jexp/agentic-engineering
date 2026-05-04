# Cursor

**Vendor / origin**: Anysphere (founded 2022, San Francisco). First public release 2023; Cursor 3 shipped April 2, 2026. The editor is a fork of VS Code (TypeScript/Electron); core agent and indexing services are written in a mix of TypeScript and Rust [VERIFY].
**License / source**: Closed source. The fork is not publicly redistributed; only signed binaries from cursor.com.
**Surface**: Desktop IDE (macOS, Linux, Windows). As of Cursor 3 also a web-accessible cloud agents dashboard and a thin CLI used to hand off / resume cloud sessions [VERIFY].

## Install & access
Download from https://cursor.com/download or `brew install --cask cursor` on macOS. Sign in via Cursor account (Google/GitHub OAuth). Free Hobby tier (limited Tab + 1-week Pro trial), Pro $20/mo, Pro+ $60/mo, Ultra $200/mo, Teams $40/user/mo, Enterprise custom. Self-hosted cloud agents (March 25, 2026) are Enterprise-only.

## Core architecture
Cursor wraps VS Code with an in-process agent runtime. The editor maintains an embedding index of the workspace (vector + symbol graph) hosted by Cursor's backend. Each chat turn assembles a prompt from user input, recent edits, retrieved code chunks, and rules files, then streams a model call (OpenAI/Anthropic/Google through Anysphere's gateway, or a user BYOK key). Tool calls (read_file, edit_file, run_terminal, codebase_search, web_search) are parsed from the response and executed in the editor or, in Cursor 3, on a remote VM. Auto mode picks a model dynamically and is not credit-billed.

## Extension model
- Rules: legacy `.cursorrules` plus newer `.cursor/rules/*.mdc` (scoped, glob-attached, AGENTS.md compatible).
- MCP servers via `~/.cursor/mcp.json` or per-project `.cursor/mcp.json`.
- Custom slash commands and a Composer-era prompts library; team-shared prompts on Teams plan.
- Sub-agents via parallel Agent Tabs and the Agents Window (Cursor 3).
- VS Code extensions still install (Cursor stays compatible with the OpenVSX marketplace).

## Interaction model
Three primary surfaces: inline Tab autocomplete, Cmd-K inline edit, and the Chat/Agent panel (Composer was the older multi-file edit UI; Agent mode superseded it through 2025). Cursor 3 added the **Agents Window** — a dedicated workspace with side-by-side Agent Tabs (up to 8 parallel) running locally, in `/worktree` isolated git worktrees, on remote SSH, or on cloud VMs. Diffs surface inline with accept/reject per hunk. `/best-of-n` runs N agents on the same task and lets you pick the winner.

## How it works (the actual loop)
1. User sends a message in an Agent Tab. 2. Cursor gathers context: open files, retrieved chunks via the workspace index, attached rules, MCP tool descriptors. 3. Prompt streams to the chosen model. 4. Tool calls parsed line-by-line; file edits show as pending diffs, shell commands prompt unless auto-run is on. 5. Tool results feed back into a new model turn. 6. Loop continues until the model emits a stop or the user pauses. Cloud agents run the same loop on an isolated VM and stream the diff back; the user can promote a cloud session to local at any time.

## What's special / cool
- **Agent Tabs + /worktree**: parallel agents on isolated git worktrees, so review diffs are clean from the start.
- **Self-hosted cloud agents** (Mar 2026): the VM, source, and build artifacts stay inside the customer's cloud — rare in the closed-source IDE space.
- **Best-of-N** native UI for comparing model outputs side by side.
- Tab autocomplete remains best-in-class for next-edit prediction across multi-line refactors.

## Models supported
Frontier models routed through Anysphere's gateway: GPT-5.x, Claude 4 Opus / Sonnet 4.6, Gemini 3.x Pro, plus Cursor's own `cursor-small` for fast tasks [VERIFY]. Auto mode picks per turn. BYOK supported for OpenAI, Anthropic, Google; with BYOK, Cursor adds no markup but you lose the credit pool.

## Pricing / access
Hobby free; Pro $20/mo with $20 credit pool; Pro+ $60/mo (3x credits); Ultra $200/mo (20x); Teams $40/user/mo with admin/SSO; Enterprise custom (adds self-hosted cloud agents, privacy mode enforcement). Manual model choice burns credits at multipliers (GPT-5.4 ~1x, Claude Opus up to 10x, Max Mode higher). Auto mode is unmetered.

## Notable & gotchas
- Credit-pool model is opaque: a single Max-Mode Opus session can drain a Pro plan in hours.
- The workspace index ships chunks to Anysphere unless privacy mode is on; check before using on regulated code.
- Cursor 3's Agents Window is a UX rewrite — older muscle memory (dropdown model picker, Composer panel) is gone or rebadged.

## References
- https://cursor.com/changelog/3-0
- https://cursor.com/blog/self-hosted-cloud-agents
- https://cursor.com/docs/models-and-pricing
- https://cursor.com/pricing
- https://www.datacamp.com/blog/cursor-3
