# Cline

**Vendor / origin**: Created by Saoud Rizwan as **Claude Dev** in mid-2024, renamed to Cline in late 2024. Now developed by Cline Inc. (Saoud Rizwan, Nik Pash). Written in TypeScript as a VS Code extension; the extension package is the whole agent.
**License / source**: Apache 2.0, open source. Repo: https://github.com/cline/cline. ~5M+ installs and ~61k GitHub stars as of early 2026; currently around v3.81 [VERIFY].
**Surface**: VS Code extension primarily. As of 2026, Cline also ships in JetBrains, Cursor, Windsurf, Zed, Neovim, and a preview CLI for macOS/Linux.

## Install & access
Install from the VS Code Marketplace (`saoudrizwan.claude-dev`) or `code --install-extension saoudrizwan.claude-dev`. JetBrains plugin from JetBrains Marketplace. CLI preview via the install script on cline.bot. Auth is BYOK by default — paste an Anthropic / OpenAI / OpenRouter / Bedrock / Vertex / Ollama / etc. key into settings — or sign in to "Cline Provider" for a hosted billing path. The extension itself is free; Cline Teams is the paid tier for governance and analytics.

## Core architecture
Cline runs entirely inside the VS Code extension host. It maintains a task/turn log and a persistent file-tree summary, then on each turn assembles: system prompt + .clinerules + workspace summary + open file context + tool descriptors → calls the configured provider's API → parses tool calls (read_file, write_to_file, replace_in_file, execute_command, browser_action, use_mcp_tool, ask_followup_question, attempt_completion) → executes them with explicit human approval gates by default. The browser tool drives a real Chromium via Puppeteer for UI verification. Everything is local; no remote indexing service.

## Extension model
- **Rules**: `.clinerules` file or `.clinerules/` directory of markdown files, optionally with conditional/glob scoping; AGENTS.md is also recognized [VERIFY].
- **MCP servers** configurable via the MCP Marketplace inside the extension or `cline_mcp_settings.json`. stdio and SSE transports. Cline can be asked in chat to "create a new MCP server" and it will scaffold + install one.
- **Custom modes** and provider profiles; Cline Provider routes through Cline's gateway.
- No formal sub-agent system, but task/sub-task delegation works through new Plan-mode tasks.

## Interaction model
The main UI is a VS Code sidebar chat. Two modes toggled with **Tab**: **Plan** (read-only — explore code, propose an approach, no edits) and **Act** (apply changes, run commands). Auto-approve toggle (Shift-Tab) and YOLO mode (`-y`) reduce per-step prompts. Every file edit is shown as a diff and must be accepted; every shell command can be approved or denied. Parallel work is done by opening multiple VS Code windows / worktrees — Cline itself does not orchestrate parallel agents in one window.

## How it works (the actual loop)
1. User sends a message; Cline picks Plan or Act based on the mode toggle. 2. System prompt + rules + condensed workspace state + recent tool results + user input go to the chosen LLM. 3. Streamed response is parsed for one tool call at a time (XML-style tool-use tags). 4. The tool runs — file diff awaits approval; shell command awaits approval unless auto-approved; MCP call goes to the server. 5. Tool result is appended to context and the loop fires another model call. 6. Loop ends when the model emits `attempt_completion` or the user pauses. Token usage and cost are shown live.

## What's special / cool
- **Open source, BYOK-first**: every token cost is visible and you own the keys; no hidden routing.
- **Plan/Act split** is unusually disciplined — read-only exploration before any edit cuts a lot of damage.
- **Computer Use via Puppeteer**: the agent can actually click around your running app and screenshot the result.
- **MCP fluency**: it can not only use MCP servers but generate one on request and install it into itself.

## Models supported
30+ providers: Anthropic (Claude 4 Opus / Sonnet 4.6), OpenAI (GPT-5.x), Google (Gemini 3.x), AWS Bedrock, GCP Vertex, Azure OpenAI, OpenRouter, Together, Fireworks, DeepSeek, xAI, Groq, Cerebras, Ollama (local), LM Studio, plus Cline Provider (hosted gateway). Anything that talks an OpenAI-compatible or Anthropic-compatible API generally drops in.

## Pricing / access
Extension: free. API costs pass through to whichever provider you configure (BYOK). Cline Provider: pay-as-you-go via Cline Inc. Cline Teams: paid tier with shared rules, spend limits, audit, SSO [VERIFY pricing tiers]. No usage caps imposed by Cline beyond what your provider enforces.

## Notable & gotchas
- **Token cost**: Cline historically rewrites whole files on edit; large files burn tokens fast. Roo Code (popular fork at github.com/RooCodeInc/Roo-Code) ships an `apply_diff` tool that emits only changed lines and reports ~30% API savings; Kilo Code is a further fork of Roo. If cost matters, evaluate Roo.
- No first-class parallel-agent UX in one window — multi-window/worktree is the workaround.
- Approval fatigue is real on long tasks; auto-approve scoping in `.clinerules` is the right pressure valve.

## References
- https://github.com/cline/cline
- https://cline.bot/
- https://marketplace.visualstudio.com/items?itemName=saoudrizwan.claude-dev
- https://cline.bot/blog/plan-act-model-usage-patterns-in-cline
- https://github.com/RooCodeInc/Roo-Code
