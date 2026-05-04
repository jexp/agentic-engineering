# GitHub Copilot (Agent Mode + Coding Agent)

**Vendor / origin**: GitHub / Microsoft. Completion Copilot launched 2021; Chat 2023; **Agent Mode** GA in VS Code and JetBrains by March 2026; the autonomous **Coding Agent** GA in 2025-2026. Implemented in TypeScript (VS Code extension) plus server-side services.
**License / source**: Closed source product; Copilot Chat extension client is partially open (MIT) [VERIFY current scope]. Repo home: https://github.com/features/copilot.
**Surface**: VS Code, Visual Studio, JetBrains IDEs, GitHub.com (web for the autonomous agent), and `gh copilot` CLI.

## Install & access
- VS Code: install "GitHub Copilot" + "GitHub Copilot Chat" extensions, sign in with GitHub.
- JetBrains: plugin from the marketplace.
- CLI: `gh extension install github/gh-copilot`.
- Tiers (April 2026): Free (limited), Pro $10/mo, Pro+ $39/mo, Business $19/user/mo, Enterprise $39/user/mo. Pro includes unlimited completions + 300 premium requests/month. Moves to usage-based billing June 1, 2026.

## Core architecture
Two distinct agentic surfaces share branding. **Agent Mode** is in-IDE: a planner-executor loop that edits files, runs terminal commands, and runs tests inside your local workspace, with diff confirmation. The **Coding Agent** is server-side: assign it a GitHub issue and it spins up a sandboxed VM, branches, edits, runs CI, and opens a PR asynchronously. Both consume "premium requests"; complex tasks burn several per session.

## Extension model
- MCP servers configured per-workspace; broad MCP support landed in 2025-2026.
- Custom instructions via `.github/copilot-instructions.md` and per-prompt `.prompt.md` files.
- Custom chat modes / agents and "skills" via repo configuration [VERIFY exact naming].
- Deep GitHub-native integration: Issues, PRs, Actions, code review all callable as tools.

## Interaction model
- **Inline / Chat / Edit / Agent** modes in VS Code, selectable per request.
- Agent Mode runs locally with diff review and per-tool confirmation prompts.
- Coding Agent runs on GitHub-hosted runners — you assign an issue, walk away, and review the PR.
- Agentic Code Review (March 2026) gathers full project context before suggesting changes and can hand fixes to the Coding Agent automatically.
- Parallel sessions = multiple issues or multiple chat tabs.

## How it works (the actual loop)
Agent Mode: prompt -> model proposes plan -> executes tool calls (read/edit file, run terminal, run tests, MCP) -> verifies (build/test) -> presents diff -> user accepts. Coding Agent: issue assigned -> ephemeral VM clones repo -> agent loops as above against CI -> opens PR with summary and run logs.

## What's special / cool
- Tightest GitHub integration of any agent: PR-aware, Actions-aware, issue-driven.
- Asynchronous Coding Agent with hosted compute is a first-party "delegate to a teammate" experience.
- Semantic code search (2026) finds conceptually related code, not just keyword matches.

## Models supported
Multi-model picker: GPT-5 / GPT-4.1 / o-series, Claude Sonnet 4.5, Gemini 2.5/3 Pro [VERIFY exact lineup]. BYOK not generally supported in the consumer plans; Enterprise has model selection controls. No local models.

## Pricing / access
See above. Premium-request currency powers Chat, Agent Mode, code review, and model picker. Heavy agent users hit caps quickly on Pro.

## Notable & gotchas
- Premium-request accounting is opaque; one Agent Mode task can quietly consume many requests.
- Coding Agent runs in a sandboxed VM with limited network — flaky if your build needs custom infra.

## References
- https://github.com/features/copilot
- https://docs.github.com/en/copilot/get-started/features
- https://code.visualstudio.com/docs/copilot/overview
- https://docs.github.com/en/copilot/reference/copilot-billing/models-and-pricing
