# Devin

**Vendor / origin**: Cognition AI (a.k.a. Cognition Labs), founded 2023 by Scott Wu and team. Devin debuted March 2024 with a viral demo as the "first fully autonomous AI software engineer." Backend stack is largely Python/TypeScript on Linux VMs [VERIFY]. Cognition's valuation passed $10B in 2025; the company also acquired Windsurf's product, brand, and ~210 staff in 2025 (~$250M).
**License / source**: Closed source, fully hosted SaaS. No public repo.
**Surface**: Cloud — web UI at app.devin.ai, plus Slack, Linear, Jira, GitHub/GitLab integrations, IDE extensions (VS Code/JetBrains) and a v3 API. Each Devin session runs in an isolated cloud VM with its own browser, shell, and editor.

## Install & access
No local install. Sign up at devin.ai with a work email. Auth via SSO/OAuth; connect GitHub/GitLab, Slack, Linear/Jira from settings. Free trial credits, then paid. Pricing as of 2026: **Core** pay-as-you-go (entry from $20/mo since Devin 2.0 in April 2025), **Team** ~$500/mo with 250 ACUs and API access, **Enterprise** custom (VPC, SSO, advanced security). Billing unit is the **ACU** (Agent Compute Unit) — bundles compute time, model inference, and tool calls; ~one ACU ≈ a few minutes of active agent work.

## Core architecture
Devin is a long-running autonomous agent that lives inside a sandboxed Linux VM ("Devin's machine") with a browser, terminal, code editor, and a planner. The orchestration loop reads a task (from Slack/Linear/Jira/web), drafts an interactive plan, then iterates: read code, edit, run, browse docs, run tests, push a branch, open a PR, and respond to review feedback. The model is called per step against a frontier provider (Claude / GPT family) with Cognition's planner/scaffolding wrapped around it. v3 of Devin (2026) added dynamic re-planning when tasks stall, plus a Fast Mode option (~2× faster, 4× ACU).

## Extension model
- **Knowledge** — Cognition's term for project-level rules, snippets, and pinned facts the agent recalls across sessions.
- **Playbooks / Procedures** — saved reusable workflows (deploy steps, repro recipes) the agent can invoke.
- **Integrations** — first-class connectors for GitHub, GitLab, Linear, Jira, Slack, Notion, Sentry, Datadog, AWS, and 20+ others.
- **Devin API (v3)** — programmatic session creation, useful for CI-driven autonomous fixes.
- **MCP support** — Devin can connect to external MCP servers [VERIFY].
- No local CLI, no rules-file convention like AGENTS.md (knowledge lives in Cognition's UI).

## Interaction model
Primary surface is a chat-style web UI showing the agent's plan, live terminal, browser, and editor side-by-side. You can spin up many Devins in parallel, each in its own VM. Sessions are typically launched **asynchronously** — assign a Linear ticket, get pinged in Slack when the PR is ready. You can intervene any time: pause, edit the plan, take over the shell. Diffs surface as PRs in your normal git host, not as inline editor patches.

## How it works (the actual loop)
1. Task arrives (Slack mention, Linear ticket, web prompt, API call). 2. Devin clones the repo into the VM and produces a plan. 3. The agent loops: pick a step → call the model with current context + tool registry → execute (file edit, shell, browser, test) → observe → update plan. 4. On test/lint failure it self-iterates; on ambiguity it asks a question in the originating channel. 5. When done, push branch + open PR; respond to PR review comments as further turns. Distinctive bits: long-horizon execution measured in hours, the dedicated VM with browser for live web research, and end-to-end testing via computer-use (2026 Desktop Mode) for any Linux GUI app.

## What's special / cool
- **Truly async, ticket-driven**: assign work like you would a junior engineer; receive a PR. Lifecycle integration with Linear/Slack is the polished case.
- **Persistent VM with browser**: it can read documentation pages, log into dashboards, and reproduce bugs through a UI — most rivals can't.
- **Multi-Devin parallelism**: dozens of simultaneous sessions per org, each isolated.
- **Cognition's vertical integration**: same team owns Windsurf (IDE-side) plus SWE-1.5 — Devin is the async cloud sibling.

## Models supported
Frontier models via Cognition's gateway — Claude (Sonnet/Opus) and GPT-5 class are the documented options [VERIFY]. No BYOK: model selection is limited to what Cognition exposes (Fast Mode swaps in a smaller/faster model). Internal SWE-1.5 from the Windsurf acquisition is reportedly being threaded into Devin's loop [VERIFY].

## Pricing / access
Core from $20/mo PAYG; Team $500/mo (250 ACUs); Enterprise custom. ACU consumption per task varies wildly — a 30-minute autonomous run can burn 5–15 ACUs, and overage stacks fast. The Register and others have flagged "wallet-wrecking" cost surprises on long autonomous runs; budget caps and session timeouts are essential.

## Notable & gotchas
- ACU costs are opaque until after a run — set hard spend caps and prefer scoped tasks over open-ended ones.
- Despite the marketing, real-world success rate on novel codebases is well below the demo; Devin shines on well-scoped, well-tested repos with good CI signal.
- Closed system: no offline, no local model option, all work happens in Cognition's VMs.

## References
- Cognition company site: https://cognition.ai/
- Devin product & docs: https://devin.ai/ , https://docs.devin.ai/
- 2026 release notes: https://docs.devin.ai/release-notes/2026
- VentureBeat — "Devin 2.0 is here…" (April 2025): https://venturebeat.com/programming-development/devin-2-0-is-here-cognition-slashes-price-of-ai-software-engineer-to-20-per-month-from-500
- The Register on Devin/Kiro pricing surprises (Aug 2025): https://www.theregister.com/2025/08/18/aws_updated_kiro_pricing/
