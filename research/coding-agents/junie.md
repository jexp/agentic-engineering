# Junie

**Vendor / origin**: JetBrains. Launched January 2025 as the agentic counterpart to JetBrains AI Assistant; **Junie CLI** beta March 2026. Implemented in Kotlin/JVM (it's a JetBrains plugin) with TypeScript/Node for the CLI [VERIFY CLI stack].
**License / source**: Closed source. Plugin: https://plugins.jetbrains.com/plugin/26104-junie.
**Surface**: JetBrains IDEs (IntelliJ IDEA, PyCharm, WebStorm, GoLand, Rider, RubyMine, etc.) plus the new Junie CLI for terminal / CI / GitHub-GitLab use.

## Install & access
- IDE: built into recent JetBrains IDEs or installable from the Marketplace; sign in with a JetBrains Account.
<!-- VERIFIED-EDIT: agent verification could not find the npm package in the public registry. Install path is via JetBrains' own installer, not npm. -->
- CLI: install path is via the JetBrains-provided installer (no public npm package found as of May 2026 — confirm with the [Junie CLI beta announcement](https://blog.jetbrains.com/junie/2026/03/junie-cli-the-llm-agnostic-coding-agent-is-now-in-beta/) before quoting an install command). Beta as of March 2026.
- Tiers: free (limited credits + unlimited completions), AI Pro (~$10/mo or $100/yr), AI Ultimate (~$30/mo or $300/yr). Credit-based; agentic tasks consume credits, multi-file tasks consume more.

## Core architecture
Junie is a plan -> act -> verify agent that uses the host IDE itself as its primary toolbox. It reads the task, drafts a plan, edits across files, then uses the IDE's static analysis, inspections, and test runner to verify — feeding inspection failures back into the loop. This deep IDE coupling is its defining trait: it gets type info, refactor primitives, and run/debug for free. The CLI variant brings the same loop outside the IDE using its own tool harness.

## Extension model
- MCP support added in 2025-2026 [VERIFY].
- Project rules via guidelines/instructions files in the project root [VERIFY exact filename].
- Inherits IDE plugin ecosystem indirectly (linters, formatters, language servers it can invoke).
- Custom commands / prompts in the IDE chat panel.

## Interaction model
- IDE side panel with prompt box, plan preview, and per-step diff review.
- Modes: an interactive ("Ask"/Code) mode and an autonomous "Brave" mode that runs without per-step approval.
- Diffs reviewed inline using the standard JetBrains diff viewer.
- Junie CLI adds a terminal REPL and a non-interactive mode usable in CI and GitHub/GitLab actions, with parallel sessions per terminal.

## How it works (the actual loop)
1. Read task + project context (open files, indexed symbols).
2. Generate a plan, show it in the panel.
3. Execute steps: edit files, run tests, run inspections through IDE APIs.
4. If inspections/tests fail, iterate; otherwise present diff for review.
Distinctive: leverages JetBrains' code intelligence (PSI, inspections, refactors) rather than re-implementing static analysis via shell.

## What's special / cool
- Uses the IDE's own type system and inspections as a verifier — fewer hallucinated APIs in strongly-typed projects.
- Junie CLI (March 2026) makes Junie LLM-agnostic and usable in CI without an IDE.
- Tight integration with JetBrains' run/debug and test runner across many languages.

## Models supported
Multiple frontier models selectable in-app: Anthropic Claude (Sonnet/Opus), OpenAI GPT-5/4.1, Google Gemini 2.5/3 [VERIFY exact list]. Junie CLI is explicitly LLM-agnostic and supports BYOK. Local models via the CLI are emerging [VERIFY].

## Pricing / access
Credit consumption can escalate fast on multi-file refactors — heavy users complain Pro caps are tight. AI Ultimate is the practical tier for daily agent use.

## Notable & gotchas
- Pre-CLI, Junie was JetBrains-only — a non-starter if your team is on VS Code.
- Credit consumption is non-obvious; large-context tasks can drain a month's allowance in days.

## References
- https://www.jetbrains.com/junie/
- https://blog.jetbrains.com/junie/2026/03/junie-cli-the-llm-agnostic-coding-agent-is-now-in-beta/
- https://plugins.jetbrains.com/plugin/26104-junie-the-ai-coding-agent-by-jetbrains
- https://www.jetbrains.com/ai-ides/buy/
