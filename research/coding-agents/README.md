# Agentic Coding Tools — A 2026 Overview

A reference companion to the workshop & keynote. Per-tool deep dives are individual files in this folder; this README is the **map and the comparison tables**.

> "The model is the brain. The harness is the body. By 2026 the bodies have converged on the same anatomy, and the differentiation is in the ergonomics."

---

## What's in this folder

Each of the following is a 0.5–1 page deep dive with the same structure (vendor, install, architecture, extension model, interaction model, the loop, what's special, models, pricing, gotchas, references):

### CLI-first
- [Claude Code](./claude-code.md) — Anthropic; the reference implementation
- [OpenAI Codex CLI](./codex-cli.md) — OpenAI's open-source Rust harness; `apply_patch` champion
- [Aider](./aider.md) — open-source Python; the original; repo-map context strategy
- [opencode](./opencode.md) — open-source server/client TS; 75+ providers
- [Goose](./goose.md) — Block / Linux Foundation; MCP-first Rust harness
- [Crush](./crush.md) — Charm; the prettiest TUI; first-class LSP
- [Pi](./pi.md) — Mario Zechner; tiny, hackable; branchable session tree (the ralphing primitive)
- [Gemini CLI](./gemini-cli.md) — Google; 1M-token context, generous free tier

### IDE-first
- [Cursor](./cursor.md) — Anysphere; VS Code fork; cloud agents on VMs (Cursor 3, April 2026)
- [Windsurf](./windsurf.md) — Codeium → Cognition; "Cascade" agent + SWE-1.5
- [Cline](./cline.md) — open-source VS Code extension; Plan/Act discipline
- [GitHub Copilot agent mode](./github-copilot-agent.md) — GitHub/MSFT; tightest GitHub integration; async Coding Agent
- [Junie](./junie.md) — JetBrains; uses the IDE's own type system as a verifier
- [Antigravity](./antigravity.md) — Google; new VS Code-fork IDE with a Manager Surface for parallel agents
- [Kiro](./kiro.md) — AWS; Code OSS-based agentic IDE built around spec-driven development

### Cloud / async-first
- [Devin](./devin.md) — Cognition; the original "autonomous AI software engineer," cloud VMs, ticket-driven async

---

## How they cluster

After reading 14 of these, four real clusters emerge:

### 1. Reference & polish (CC, Cursor, Codex CLI, Antigravity)
Vendor-backed, frontier-model-aligned, large engineering teams behind them. Most innovation lands here first; closed-source binaries (except Codex). These set the bar; the rest react.

### 2. Open & hackable (Aider, opencode, Goose, Crush, Cline, Pi)
BYOK, multi-provider, repo on GitHub, configurable down to the prompt. Pick these if you want to run locally, audit the loop, or build your own variant. Goose is the most "platform-y," Pi the most "personal tool," Aider the most battle-tested.

### 3. IDE-native productivity (Cursor, Windsurf, Cline, Junie, Copilot agent, Kiro)
Where the user is already typing. Strongest UX for inline edits, diff review, autocomplete-plus-agent flow. Cursor and Windsurf are the leading paid products; Cline owns the OSS niche; Junie owns JetBrains; Copilot owns GitHub-integrated workflow; Kiro owns the spec-first discipline.

### 4. Async / multi-agent orchestration (Cursor 3 cloud agents, Antigravity Manager, Copilot Coding Agent, Devin, Windsurf Wave 13/14)
The Feb 2026 multi-agent convergence: every major vendor shipped parallel sessions or remote-VM agents within a 2-week window. This is where the next year of differentiation will happen.

---

## Cross-cutting observations

- **The anatomy is universal** — system prompt + loop + tools + context mgmt + permissions + state/memory. Every tool maps cleanly to the 6-box model from the harness slide.
- **MCP won.** Every tool except Aider supports MCP as a first-class extension surface. Goose is fully MCP-native (every capability is an MCP subprocess). Cline can *generate* MCP servers on demand.
- **AGENTS.md is the cross-vendor rules-file convention** — Codex helped popularize it; CC accepts it alongside `CLAUDE.md`; Cursor's `.cursor/rules/` directory recognizes it; Crush, opencode, Goose, Cline use it natively. Holdouts: GEMINI.md, .cursorrules (legacy), .windsurfrules, .clinerules.
- **Plan mode is universal** — under different names: Plan Mode (CC, Cline), Architect (Aider), Composer Plan (Cursor), Cascade Chat (Windsurf), Junie's plan step. The discipline is the convergence; the UX varies.
- **Hooks are the differentiator** for production teams — CC and Windsurf have first-class hooks; most others rely on prompts that "should" run lint/test (less reliable). Goose's recipes are an interesting alternative — pre-baked agent configs.
- **Repo-map vs RAG vs whole-context** — three context strategies: Aider's repo-map (PageRank over symbol graph, token-efficient), Cursor's vector index (chunk-based RAG), Gemini CLI's million-token whole-context. Each wins on different repo sizes.
- **Sandboxing**: Codex (Seatbelt/Landlock) and Antigravity (controlled VM) are ahead. Most others rely on permission prompts plus hooks — fine for trusted users, weak for autonomous loops.
- **Pricing is fragmenting**: per-token (BYOK), credit pools (Cursor, Junie), premium-request currency (Copilot), daily caps (Windsurf since March 2026), subscription bundles (CC Pro/Max). Watch for opaque cost amplification on long agent runs.

---

## Comparison table — the basics

| Tool | Vendor | License | Surface | Native models | Multi-provider | Pricing model |
|---|---|---|---|---|---|---|
| **Claude Code** | Anthropic | closed | CLI + IDE ext | Claude (Opus/Sonnet/Haiku) | via Bedrock/Vertex | sub ($20–200) + API metered |
| **Codex CLI** | OpenAI | OSS Apache-2.0 | CLI + cloud | GPT-5/5.2/5.5 | no (official) | ChatGPT Plus/Pro/Biz/Ent + API |
| **Cursor** | Anysphere | closed | IDE (VS Code fork) + CLI | Multi-frontier via Anysphere gateway | yes + BYOK | $0/20/60/200 + credits |
| **Windsurf** | Cognition (was Codeium) | closed | IDE (VS Code fork) | SWE-1.5 + Claude/GPT/Gemini | yes + BYOK | $0/20+ + daily caps |
| **Cline** | Cline Inc. | OSS Apache-2.0 | VS Code ext (+JB, Zed, CLI preview) | none native | 30+ providers | free + BYOK; Cline Provider hosted |
| **GitHub Copilot agent** | GitHub/MSFT | closed | VS Code, JB, web, CLI | GPT-5/Claude/Gemini | multi via picker | $0/10/39 + premium-request currency |
| **Junie** | JetBrains | closed | JetBrains IDEs + CLI (beta) | Claude/GPT/Gemini selectable | yes; CLI is LLM-agnostic | AI Pro $10 / Ultimate $30 |
| **Antigravity** | Google | closed | IDE (VS Code fork) + cloud | Gemini 3, Claude 4.5, GPT-OSS | yes (3 models) | free preview |
| **opencode** | SST (also opencode-ai) | OSS MIT | CLI/TUI + HTTP server + SDK | none native | 75+ providers | free + BYOK; "opencode Go" $5–10/mo |
| **Aider** | Paul Gauthier / community | OSS Apache-2.0 | CLI (+ browser UI) | none native | LiteLLM (anything) | free + BYOK |
| **Goose** | Block → Linux Foundation | OSS Apache-2.0 | CLI + Desktop (Electron) | none native | 15+ providers | free + BYOK |
| **Crush** | Charm | OSS MIT | CLI/TUI | none native | many incl. local | free + BYOK |
| **Pi** | Mario Zechner (indep.) | OSS [VERIFY MIT] | CLI/TUI | none native | many + local | free + BYOK |
| **Gemini CLI** | Google | OSS Apache-2.0 | CLI | Gemini 2.5/3 | mostly Gemini | free tier + Vertex API |
| **Devin** | Cognition | closed | Cloud (web + Slack/Linear/IDE ext + API) | via Cognition gateway (Claude/GPT) | no BYOK | $20 PAYG / $500 Team / Ent + ACUs |
| **Kiro** | AWS | closed (Code OSS base) | IDE (VS Code fork) + CLI | Claude Sonnet 4.x / 3.7 | no BYOK (preview) | Free 50 / $20 / $40 / $200 + credits |

---

## Comparison table — capabilities

✅ first-class · 〰️ partial / via config · ❌ not natively

| Tool | MCP | AGENTS.md (or eq.) | Hooks | Plan mode | Sub-agents | Parallel sessions | Local LLMs | Sandbox |
|---|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Claude Code** | ✅ | ✅ (CLAUDE.md) | ✅ | ✅ | ✅ | 〰️ worktree | via BYOK | 〰️ permissions |
| **Codex CLI** | ✅ | ✅ | 〰️ notify | 〰️ approval modes | ❌ | ✅ | ❌ | ✅ Seatbelt/Landlock |
| **Cursor** | ✅ | ✅ (`.cursor/rules/`) | 〰️ | ✅ | ✅ Agent Tabs | ✅ ≤8 + cloud VMs | via BYOK | 〰️ |
| **Windsurf** | ✅ | ✅ (`.windsurfrules`) | ✅ Cascade Hooks | ✅ Chat mode | 〰️ | ✅ ≤5 panes | via BYOK | 〰️ |
| **Cline** | ✅ + can generate MCP servers | ✅ (`.clinerules`) | ❌ | ✅ Plan/Act | ❌ | 〰️ multi-window | ✅ Ollama/LM Studio | ❌ approval-only |
| **Copilot agent** | ✅ | ✅ (`.github/copilot-instructions.md`) | ❌ | 〰️ | 〰️ Coding Agent | ✅ chat tabs + async | ❌ | ✅ Coding Agent VM |
| **Junie** | ✅ [VERIFY] | ✅ | ❌ | ✅ | ❌ | 〰️ | 〰️ via CLI | 〰️ |
| **Antigravity** | ✅ | ✅ [VERIFY name] | ❌ | ✅ | ✅ Manager | ✅ async multi-agent | ❌ | ✅ controlled browser |
| **opencode** | ✅ | ✅ | 〰️ via plugins | ✅ | ✅ | ✅ shared sessions | ✅ Ollama | ❌ |
| **Aider** | ❌ [VERIFY] | ✅ (CONVENTIONS.md) | 〰️ lint/test cmds | ✅ Architect | ❌ | ✅ git-based | ✅ Ollama / vLLM / LM Studio | ❌ |
| **Goose** | ✅ (everything is MCP) | ✅ (`.goosehints`) | 〰️ via recipes | 〰️ | ❌ | 〰️ | ✅ Ollama | ❌ |
| **Crush** | ✅ | ✅ | 〰️ | ✅ | 〰️ skills | 〰️ in-TUI switch | ✅ Ollama / llama.cpp | ❌ |
| **Pi** | ✅ | ✅ [VERIFY] | ❌ | ✅ | ✅ | ✅ session tree | ✅ Ollama / Gemma | ❌ |
| **Gemini CLI** | ✅ | ✅ (GEMINI.md) | 〰️ | 〰️ | 〰️ | 〰️ | ❌ official | ❌ |
| **Devin** | ✅ [VERIFY] | 〰️ Knowledge UI | 〰️ Procedures | ✅ Interactive Plan | ✅ multi-Devin | ✅ many parallel VMs | ❌ | ✅ isolated VM |
| **Kiro** | ✅ [VERIFY] | ✅ (`.kiro/steering/`) | ✅ Agent Hooks | ✅ Spec mode | ❌ | 〰️ | ❌ preview | 〰️ |

---

## Comparison table — distinctive bets

What each tool is *for*. Pick by the bet that matches your situation.

| Tool | Distinctive bet |
|---|---|
| **Claude Code** | Hooks + skills + MCP as the most programmable harness; Anthropic's reference design |
| **Codex CLI** | `apply_patch` format + native sandboxing → safest autonomous mode |
| **Cursor** | Best-in-class autocomplete + Cursor 3 cloud agents + best-of-N native UI |
| **Windsurf** | Real-time workspace awareness + SWE-1.5 fast model + aggressive autonomy |
| **Cline** | Open-source MCP power-user tool inside VS Code; can author MCP servers |
| **Copilot agent** | Native GitHub workflow: issue → assigned async agent → PR |
| **Junie** | IDE's own static analysis as the verifier — fewer hallucinated APIs in typed code |
| **Antigravity** | Manager Surface for many concurrent async agents + native browser tool |
| **opencode** | Server/client architecture — one backend, many surfaces (TUI/IDE/SDK) |
| **Aider** | Repo-map for million-line repos; atomic git-commit-per-edit; battle-tested |
| **Goose** | MCP-native, Linux Foundation–governed, recipes as versionable agent configs |
| **Crush** | Charm-grade TUI + first-class LSP integration |
| **Pi** | Branchable session tree (ralphing as a primitive) + tiny enough to read in an evening |
| **Gemini CLI** | 1M-token context replacing RAG; Google Search grounding as a tool |
| **Devin** | True async, ticket-driven autonomy in a persistent VM with browser; PRs as the deliverable |
| **Kiro** | Spec-driven by default — requirements/design/tasks as durable repo artifacts before any code |

---

## Picking guidance (opinionated)

- **Just starting out, on Anthropic stack** → Claude Code. Reference design, well-documented, hooks + skills + MCP all first-class.
- **Just starting out, IDE-native** → Cursor or Cline. Cursor for the polish, Cline for the open-source/BYOK ethos.
- **Cost-conscious, OSS-first, multi-provider** → Aider for stability, opencode or Crush for modern UX, Goose if MCP is your religion.
- **Heavy GitHub workflow** → Copilot agent. Nothing else integrates as tightly with issues/PRs/Actions.
- **JetBrains shop** → Junie. The CLI lets you escape the IDE for CI.
- **Want maximum autonomy / parallel** → Cursor 3 (cloud agents), Windsurf (parallel Cascade), or Antigravity (Manager). The async-multi-agent space is where the action is in 2026.
- **Want to *build your own*** → Pi is the readable starting point. opencode if you want a server/client base.
- **OpenAI shop, terminal-first** → Codex CLI. Open source, Rust-fast, sandboxed.
- **Deep Google integration / huge context** → Gemini CLI or Antigravity.

---

## Open questions / things to verify before quoting in slides

The individual files mark every uncertain claim with `[VERIFY]`. The most worth checking before tomorrow:

- Codex CLI exact Terminal-Bench ranking & date
- Junie CLI exact npm package name & current beta status
- Antigravity post-preview pricing tier (if any announced)
- Cursor 3 self-hosted cloud agents tier eligibility
- Goose's canonical repo URL after the Linux Foundation transition
- Aider current MCP support status (was none as of early 2026; may have changed)

---

*Generated 2026-05-04 from parallel research across 14 tools, distilled into structured per-tool files in this directory. See per-file references for primary sources.*
