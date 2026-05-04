# Claude Code

**Vendor / origin**: Anthropic. First public research preview Feb 2025 (internal codename "Tengu"); Claude Code 2.0 shipped 2025; widely adopted through 2026. Distributed as a Node.js binary [VERIFY: implementation language is TypeScript/Node].
**License / source**: Closed-source binary; the `anthropics/claude-code` GitHub repo hosts docs, CHANGELOG, plugin/skills examples, and issue tracking, but not the agent core.
**Surface**: Primarily a terminal CLI; first-party IDE extensions for VS Code and JetBrains; GitHub Action for PR review; web/mobile via claude.ai for remote sessions.

## Install & access
`npm install -g @anthropic-ai/claude-code` then run `claude` in a repo. Auth: log in with an Anthropic Console API key, or via Claude Pro/Max/Team subscription OAuth. Also runs against Amazon Bedrock and Google Vertex with the appropriate env vars. Requires Node.js 18+; macOS, Linux, and Windows (WSL recommended) supported.

## Core architecture
Claude Code is an agent loop driving a Claude model (Sonnet/Opus/Haiku) with a fixed set of built-in tools: `Read`, `Edit`, `Write`, `Bash`, `Grep`, `Glob`, `WebFetch`, `WebSearch`, plus task delegation. The binary maintains a transcript, manages auto-compaction when the context fills, enforces a permission system on tool calls, and streams partial tool output back into the conversation. File edits use a structured `old_string`/`new_string` diff applied directly. Tool execution is sandboxed by an allow/deny list configured in `settings.json`.

## Extension model
Five layers: (1) **CLAUDE.md** memory files at user, project, and subdirectory scope for instructions; (2) **slash commands** (markdown files in `.claude/commands/`); (3) **Skills** — bundled prompt + scripts auto-loaded by description match; (4) **MCP servers** for external tools/resources, configured per-project or globally; (5) **Hooks** (PreToolUse, PostToolUse, Stop, etc.) shell-out on lifecycle events for guardrails or automation; (6) **Subagents** — specialized personas with their own context window and tool subset, defined in `.claude/agents/`. Plugins bundle all of the above into one installable unit.

## Interaction model
Interactive REPL in the terminal. Modes: default (asks before edits per permission rules), **plan mode** (read-only — produces a plan before any mutation), and auto-accept. Diffs are previewed inline before being applied. Touches files directly (not patch-proposal style). Supports `git worktree`-style parallel sessions and a built-in `EnterWorktree` tool. `claude --resume` reopens prior sessions.

## How it works (the actual loop)
Read user message → assemble system prompt (memory files + skill descriptions + tool defs) → call model with prompt caching → parse tool-use blocks → check permissions → execute tool (possibly running a hook before/after) → feed tool result back → repeat until model returns plain text. Distinctive features: aggressive prompt caching, plan-mode that gates writes, hook-based deterministic policy, sub-agent forks that don't pollute the parent context, and auto-compaction summarization when nearing the context limit.

## What's special / cool
- Hooks are real shell commands fired on tool lifecycle events — turns the loop into a programmable harness.
- Subagents fork a fresh context window with their own tool allowlist, returning only a summary — keeps long sessions cheap.
- Skills auto-activate by description matching, not manual toggle, so capability surface scales without bloating the system prompt.
- First-class MCP support, both as client and via `claude mcp serve` exposing Claude Code itself.

## Models supported
Native Anthropic Claude family (Opus 4.x, Sonnet 4.x, Haiku 4.x as of 2026 [VERIFY exact versions]). Routes through Anthropic API, AWS Bedrock, or GCP Vertex. Not multi-provider in the OpenAI/Gemini sense — tied to Claude.

## Pricing / access
Included with Claude Pro ($20/mo), Max ($100–$200/mo with much higher quotas), and Team/Enterprise plans. API-key usage is metered per-token at standard Anthropic rates. No free tier beyond trial credits.

## Notable & gotchas
- Closed-source agent binary; you can shape behavior via hooks/skills but not patch the loop.
- Long sessions auto-compact, which can lose subtle context — checkpoint important state into CLAUDE.md.
- Subscription quotas can throttle heavy users; the Max plan exists precisely because Pro hits limits fast.

## References
- Best-practices and CLI docs: https://code.claude.com/docs
- GitHub repo (docs, changelog, plugins): https://github.com/anthropics/claude-code
- Advanced patterns PDF: https://resources.anthropic.com/hubfs/Claude%20Code%20Advanced%20Patterns_%20Subagents,%20MCP,%20and%20Scaling%20to%20Real%20Codebases.pdf
- MCP spec: https://modelcontextprotocol.io
- Community list: https://github.com/hesreallyhim/awesome-claude-code
