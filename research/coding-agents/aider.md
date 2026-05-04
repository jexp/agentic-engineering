# Aider

**Vendor / origin**: Created by Paul Gauthier; first released mid-2023. Now maintained as the `Aider-AI/aider` org on GitHub with broader contributor base. Written in Python.
**License / source**: Open source, Apache-2.0. Repo: https://github.com/Aider-AI/aider. ~40k+ GitHub stars as of 2026; one of the longest-running terminal AI coding tools.
**Surface**: Terminal CLI. No first-party IDE extension (community plugins exist); also exposes a browser-based chat UI via `aider --browser` and a programmable Python API.

## Install & access
`pip install aider-install && aider-install`, or `pipx install aider-chat`, or via Homebrew. Auth is BYOK: set `OPENAI_API_KEY`, `ANTHROPIC_API_KEY`, `GEMINI_API_KEY`, etc., or point at any OpenAI-compatible endpoint (Ollama, OpenRouter, DeepSeek, local vLLM). No subscription, no telemetry account — just API credits with the provider of your choice.

## Core architecture
Aider is a Python program that pairs an LLM with a git repo. On startup it scans the repo, builds a **repo-map** (a ranked, AST-derived summary of symbols and call graph using tree-sitter), and uses that map plus an explicit `/add`-ed file list as the model's context. Edits come back from the model as one of several **edit formats** — `whole`, `diff`, `udiff`, `editor-diff`, or `architect` — which the CLI parses and applies. After every successful edit, Aider runs `git commit` with an LLM-written message. Optional lint and test commands gate commits.

## Extension model
- **CONVENTIONS.md** / read-only files via `/read` for project rules and style guides.
- **`.aider.conf.yml`** for per-repo defaults (model, edit format, lint/test commands).
- **`/commands`** built into the REPL: `/add`, `/drop`, `/run`, `/test`, `/lint`, `/architect`, `/ask`, `/code`, `/web`, `/voice`, `/map`.
- Pluggable model backends through LiteLLM — anything LiteLLM speaks, Aider speaks.
- Scripting/Python API for embedding Aider into other workflows.
- No formal MCP support as of early 2026 [VERIFY].

## Interaction model
A REPL where the user chats and either says what to change or uses `/architect` to split planning from editing. Aider only edits files the user has explicitly added with `/add`; everything else is context-only via the repo-map. Diffs are applied directly and immediately committed to git, so review happens through `git diff HEAD~` / `git revert` rather than a pre-commit approval prompt. `/undo` rolls back the last commit. Multiple sessions on the same repo are fine because everything funnels through git.

## How it works (the actual loop)
Read user message → refresh repo-map (token-budgeted ranked symbols) → assemble prompt with system instructions, repo-map, contents of added files, and conversation history → call LLM with the chosen edit-format protocol → parse edit blocks → apply to disk → run optional lint/test → on success, `git commit` with an LLM-generated message → loop. Aider's distinctive piece is the repo-map: it lets the model navigate million-line repos without dumping everything into context, by surfacing only the most relevant symbols based on PageRank over references.

## What's special / cool
- The repo-map is genuinely novel and still ahead of most competitors for large-codebase context efficiency.
- Atomic git-commit-per-change yields a reviewable, bisectable history — AI work as first-class git history.
- Architect mode separates a strong reasoning model (planner) from a cheap fast model (editor), saving tokens.
- Provider-agnostic via LiteLLM; runs fully offline against local models with no account anywhere.

## Models supported
Anything LiteLLM supports: OpenAI (GPT-4o, GPT-5, o-series, GPT-5.5), Anthropic Claude (Sonnet/Opus 4.x), Google Gemini 2.x/3.x, DeepSeek, xAI Grok, Mistral, plus local via Ollama, vLLM, or LM Studio. Leaderboard at aider.chat tracks edit-format success rates per model.

## Pricing / access
Free, open source. Cost is the underlying model's API tokens (or zero with local models). No subscription tier exists.

## Notable & gotchas
- You must `/add` files explicitly — forgetting this is the #1 frustration; the model will hallucinate around missing context.
- Auto-commit can flood history on noisy sessions; configure `--no-auto-commits` or squash later.
- Architect mode roughly doubles token cost since two model calls happen per turn.

## References
- Project site: https://aider.chat
- Repo: https://github.com/Aider-AI/aider
- Repo-map design notes: https://aider.chat/docs/repomap.html
- Edit-format leaderboards: https://aider.chat/docs/leaderboards/
- LLM provider config: https://aider.chat/docs/llms.html
