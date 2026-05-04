# Windsurf

**Vendor / origin**: Originally built by Codeium (founded 2021 as Exafunction). Windsurf Editor launched November 2024 as the first "agentic IDE" from the Codeium team. In 2025, Cognition (the Devin team) acquired Windsurf's IP, product, brand, and ~210 employees for ~$250M. The editor is a VS Code fork; the agent stack is a mix of TypeScript and Go [VERIFY].
**License / source**: Closed source. Some companion plugins (legacy Codeium extensions for JetBrains/Vim) remain free.
**Surface**: Desktop IDE (macOS/Linux/Windows). JetBrains plugin still maintained; web changelog at windsurf.com.

## Install & access
Download at https://windsurf.com/ or `brew install --cask windsurf` on macOS. Sign in with Codeium/Windsurf account. Free tier (Tab autocomplete + limited Cascade); Pro $20/mo with daily premium-model quota; Teams and Enterprise tiers above. Since March 2026, SWE-1.5 is free for all users for ~3 months as Cognition migrates the billing model from prepaid credits to daily caps.

## Core architecture
Windsurf's distinguishing piece is **Cascade**, an agent that maintains a continuously-updated mental model of the workspace via Codemaps (a symbol/graph index) and "real-time awareness" — file system + editor activity feeds into the agent's context as you work. Each turn calls a model (Cognition's SWE-1.5, or Claude/GPT/Gemini), parses tool calls (read, edit, run, browser, MCP), and applies changes with checkpointing so any step can be rolled back. SWE-1.5 is a proprietary fast model claimed at ~950 tokens/sec.

## Extension model
- **Rules**: `.windsurfrules` (project) and global rules in settings; AGENTS.md is also honored [VERIFY].
- **MCP servers** configurable via Cascade settings UI; stdio and HTTP transports.
- **Cascade Hooks** (Nov 2025): pre/post-tool hooks that run shell commands — analogous to Claude Code hooks.
- **Workflows**: reusable saved prompts/recipes pinned to Cascade.
- VS Code extensions install through OpenVSX.

## Interaction model
Three modes: Tab autocomplete, Command (inline edits, Cmd-I), and **Cascade** (the agent panel). Cascade has Write mode (autonomous edits) and Chat mode (read-only Q&A). Wave 13 (Dec 2025) added **parallel multi-agent sessions** — side-by-side Cascade panes, each with its own git worktree and a dedicated terminal profile. The Feb 2026 release wave (Wave 14 [VERIFY]) extended this to up to 5 simultaneous Cascade agents. Diffs are presented as a Flow timeline you can scrub through; checkpoints let you snap back.

## How it works (the actual loop)
1. User message lands in a Cascade pane. 2. Codemaps + recent activity + open files + rules assembled into context. 3. Model call streams. 4. Tool calls parsed; file edits applied directly with a checkpoint snapshot, terminal commands run in the pane's terminal profile (auto-approve depending on mode). 5. Tool output rejoins context. 6. Loop runs aggressively — Cascade is biased toward continuing without asking. 7. Hooks fire pre/post tool. The agent's autonomy is the deliberate design point: Codeium pitched it as "AI flow" — the tool keeps moving while you watch.

## What's special / cool
- **Codemaps + real-time awareness**: the agent observes your manual edits and folds them into context without an explicit @mention.
- **Cascade Hooks**: lets teams enforce lint/test/format gates around every tool call.
- **SWE-1.5**: a fast in-house model tuned for the Cascade loop; latency is noticeably better than frontier models on small edits.
- **Aggressive autonomy**: defaults lean toward "just keep going" — productive on greenfield work, hazardous on legacy code.

## Models supported
SWE-1, SWE-1.5 (proprietary, Cognition); Claude Sonnet 4.6; GPT-5 / GPT-5.4; Gemini 3.1 Pro. BYOK is supported on Pro and above with overage billed at provider API rates.

## Pricing / access
Free: Tab + limited Cascade + free SWE-1.5 (promo through ~mid-2026). Pro $20/mo, daily premium-model quota that resets at 00:00 UTC. Teams and Enterprise tiers add SSO, admin controls, and higher quotas. Pre-purchased credits from the old system convert into extra usage under the daily-cap model.

## Notable & gotchas
- Quota model changed in March 2026: hitting the daily cap pauses premium models until UTC midnight — surprises users in non-UTC zones.
- Real-time awareness sends activity signals to Windsurf's backend by default; review privacy mode settings for sensitive repos.
- Cognition acquisition has shifted roadmap priorities toward Devin-like autonomous workflows; some longtime Codeium features (e.g., JetBrains parity) lag.

## References
- https://windsurf.com/
- https://docs.windsurf.com/windsurf/cascade/cascade
- https://windsurf.com/changelog
- https://docs.windsurf.com/windsurf/models
- https://www.digitalapplied.com/blog/windsurf-swe-1-5-cascade-hooks-november-2025
