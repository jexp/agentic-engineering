# OpenAI Codex CLI

**Vendor / origin**: OpenAI. Relaunched May 2025 as a fresh, agentic terminal tool (sharing the "Codex" name with the 2021 model but otherwise unrelated). Written primarily in Rust, with a TypeScript variant earlier in its life [VERIFY current language status].
**License / source**: Open source, Apache-2.0. Repo: https://github.com/openai/codex.
**Surface**: Terminal CLI primarily; Codex also exists as a cloud agent product (codex.openai.com) and an IDE extension, but the CLI is the canonical local surface.

## Install & access
`npm install -g @openai/codex` or `brew install codex`; standalone binaries on the GitHub Releases page. Auth: `codex login` via ChatGPT account (Plus/Pro/Business/Enterprise tiers grant Codex usage), or `OPENAI_API_KEY` for pay-as-you-go API billing. Runs on macOS, Linux, and Windows.

## Core architecture
A Rust binary that drives an OpenAI reasoning model (GPT-5.x family by default) through an agent loop. The model is called via the Responses API with tool definitions for shell execution, file reading, and patch application. Codex has a strong sandboxing story: on macOS it uses Seatbelt, on Linux Landlock/seccomp, restricting file writes and (optionally) network access by default. Approval modes (`suggest`, `auto-edit`, `full-auto`) gate when the agent can run commands without asking.

## Extension model
- **AGENTS.md**: project-level instructions Codex auto-loads (the OpenAI counterpart to CLAUDE.md / .cursorrules; OpenAI helped popularize the cross-tool AGENTS.md convention).
- **MCP**: Codex CLI is an MCP client and can also be exposed as an MCP server (`codex mcp`).
- **Custom prompts/profiles** in `~/.codex/config.toml` for per-project model, sandbox, and approval defaults.
- Hooks/notifications via `notify` config for desktop alerts on completion.

## Interaction model
Interactive TUI in the terminal (or one-shot `codex exec "..."`). Three approval modes from cautious to fully autonomous. Diffs are shown inline as `apply_patch` envelopes before being committed to disk. Supports git worktrees and parallel sessions; the cloud product extends this to fully detached background tasks. The local agent edits files directly through the patch tool rather than emitting raw rewrites.

## How it works (the actual loop)
Read prompt → load AGENTS.md + repo context → call the model with the `shell` tool and the `apply_patch` tool definition → model emits either a shell command or an `apply_patch` payload using its distinctive heredoc-style envelope (`*** Begin Patch / *** Update File: foo.py / @@ ... *** End Patch`) → CLI parses, runs through sandbox, returns stdout/stderr or success → loop. The `apply_patch` format is the load-bearing primitive: it's terse, easy for the model to produce, and unambiguous to parse, which is a big reason Codex tops Terminal-Bench.

## What's special / cool
- `apply_patch` format — a tiny custom diff DSL that consistently outperforms unified diffs for model accuracy.
- Strong native sandboxing (Seatbelt/Landlock) so `full-auto` mode is genuinely safer than competitors letting the agent run arbitrary shell.
- Open source and Rust-fast — the whole loop is auditable and hackable.
- Topped Terminal-Bench in April 2026 with GPT-5.5 (per public reports) [VERIFY exact ranking and date].

## Models supported
Native: OpenAI models via the Responses API — GPT-5, GPT-5.2-Codex (a Codex-tuned variant), GPT-5.5 as the current frontier model in 2026, plus o-series reasoning models. BYOK via `OPENAI_API_KEY`. Also documented support for Azure OpenAI and Bedrock-hosted GPT models. Not designed for Anthropic/Gemini, though community forks exist.

## Pricing / access
ChatGPT Plus ($20/mo), Pro, Business, and Enterprise plans include Codex quota; heavy use spills into API metered billing at standard token rates. No standalone free tier beyond ChatGPT Free's limited inclusion [VERIFY current free-tier policy].

## Notable & gotchas
- Releases move fast; the 0.117.0 series had `apply_patch` execution-path regressions tracked on GitHub — pin a known-good version for CI use.
- Sandboxing defaults can block legitimate commands (e.g., network, writing outside repo); the right approval mode and `--allow-net` flags matter.
- Tied to OpenAI models — using non-OpenAI providers is unsupported on the official path.

## References
- Repo: https://github.com/openai/codex
- Docs hub: https://developers.openai.com/codex/
- CLI features: https://developers.openai.com/codex/cli/features
- Changelog: https://developers.openai.com/codex/changelog
- GPT-5.5 announcement: https://openai.com/index/introducing-gpt-5-5/
