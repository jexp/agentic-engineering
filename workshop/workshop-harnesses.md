# Workshop — Agent Harnesses: How They Actually Work

**Block**: Deep dive — agent harnesses (CLI + IDE)
**Duration**: 10–15 min within the deep-dive block (3–4 slides + live tour)
**Position**: After the intro section, before the agents.md/ralphing/own-experience portion of the deep dive
**Goal**: give experienced engineers a clean, vendor-neutral mental model of what a "harness" is, what's in the box, and where the levers are. So they can read any tool's docs and immediately know where to look.

---

## Framing line for the section

> "The model is the brain. The harness is the body — the hands, eyes, memory, and safety boundary. Most of the productivity difference between engineers using these tools comes from how well they understand the body, not how clever the brain is."

---

## Slide 1 — Anatomy of an agent harness

A harness wraps an LLM into a working agent. Strip away the branding and they all have the same six parts:

```
┌─────────────────────────────────────────────────────┐
│  1. SYSTEM PROMPT                                   │
│     Behavior, safety, tool-use protocol, persona    │
├─────────────────────────────────────────────────────┤
│  2. THE LOOP                                        │
│     read user → call model → parse tool calls →     │
│     execute → feed results → repeat                 │
├─────────────────────────────────────────────────────┤
│  3. TOOLS                                           │
│     Bash, file read/edit/write, grep, glob, web,    │
│     LSP, task spawn, MCP, planning, …               │
├─────────────────────────────────────────────────────┤
│  4. CONTEXT MANAGEMENT                              │
│     Cache boundaries, history, compaction,          │
│     deferred tool loading, memory injection         │
├─────────────────────────────────────────────────────┤
│  5. PERMISSION / RISK GATE                          │
│     Mode (plan / accept-edits / bypass), risk       │
│     classifier, protected paths, hooks              │
├─────────────────────────────────────────────────────┤
│  6. STATE & MEMORY                                  │
│     Session, transcript, project files (CLAUDE.md / │
│     AGENTS.md), persistent memory, scratchpad       │
└─────────────────────────────────────────────────────┘
```

**Why this matters for the room**: every "tip" or "best practice" you read about Claude Code, Cursor, Codex, Aider — it's usually a tweak to *one of these six boxes*. Once you have the anatomy, you can read any new tool's docs in 10 minutes.

Optional tangent (1 min): **why coding harnesses converged on this shape.** The shell is universal, ancient, and well-represented in training data. File edits are verifiable. Tools have crisp inputs/outputs. The pattern was inevitable — Anthropic's framing in CC docs is "treat the code as the source of truth, push everything into the model."

---

## Slide 2 — The landscape (CLI + IDE)

Two families. Same anatomy, different ergonomics.

### CLI harnesses — model in your terminal

| Harness | Vendor | Notes |
|---|---|---|
| **Claude Code** | Anthropic | The reference implementation; strong tool design, MCP host, plan mode, hooks, skills, sub-agents, memory. |
| **Codex CLI** | OpenAI | Re-launched May 2025; `apply_patch` format; jumped to #1 on Terminal-Bench in April 2026 with GPT-5.5. |
| **opencode** | Open source (Go) | Provider-agnostic, 75+ LLM backends incl. local Ollama; rich TUI. |
| **Aider** | Open source | Git-native, TDD-friendly, repo-map context strategy; long pedigree. |
| **Gemini CLI** | Google | Google's official CLI, strong on long-context tasks. |
| **Crush** / **Goose** / **Pi** | Various | Niche but interesting; Pi pioneered "ralphing" (loop-with-reset). |

### IDE harnesses — model in your editor

| Harness | Vendor | Notes |
|---|---|---|
| **Cursor** | Anysphere | Agent mode + Composer + cloud agents on VMs (Cursor 3, April 2026); parallel agent tabs, /worktree for branch isolation. |
| **Cline / Roo** | Open source (VS Code) | Open-source agent in VS Code; strong DIY/tinker community. |
| **Windsurf** | Codeium | "Cascade" agent; aggressive autonomy, 5 parallel agents (Feb 2026 wave). |
| **GitHub Copilot agent mode** | GitHub/MSFT | Native VS Code; tight GitHub integration; PR-aware. |
| **JetBrains AI Assistant / Junie** | JetBrains | Native to IntelliJ/PyCharm/etc; Junie is the agent variant. |
| **Antigravity** | Google (Code Assist evolution) | Late-2025 entry, deep IDE+agent integration. |

### CLI vs IDE — which to pick?

| Dimension | CLI wins | IDE wins |
|---|---|---|
| Long autonomous runs | ✓ (background, hooks, cron, sub-agents) | |
| Live code review / inline diffs | | ✓ |
| Parallel sessions / worktrees | ✓ (CC, opencode) | ✓ (Cursor 3) |
| Onboarding for non-CLI engineers | | ✓ |
| Scripting & CI integration | ✓ | partial |
| Team-shared config (AGENTS.md / CLAUDE.md) | ✓ | ✓ (most) |

**My take for the room**: pick *one* CLI harness and *one* IDE harness, learn both deeply. The mental model transfers.

> "In Feb 2026 every major tool shipped multi-agent in the same two-week window: Grok Build (8 agents), Windsurf (5), Claude Code Agent Teams, Codex Agents SDK, Devin parallel sessions. The race is over the orchestration layer now, not the model."

---

## Slide 2a — Architectural patterns worth naming

<!-- Pulled from research/coding-agents/README.md — the per-tool deep-dive synthesis -->

After looking at 14 tools side-by-side, four architectural choices recur — worth naming because each is a deliberate bet:

1. **Context strategy: repo-map vs RAG vs whole-context.**
   - **Aider — repo-map**: ranked, AST-derived, PageRank-over-references symbol graph. Token-efficient on huge repos.
   - **Cursor — workspace vector index**: chunked RAG with embedding lookups; flexible, opaque.
   - **Gemini CLI — whole-context**: 1M-token window often replaces RAG entirely. Simple, expensive on long horizons.
   Each wins on different repo sizes and shapes; many teams use more than one.

2. **Edit format: diff-DSL vs whole-file rewrite.**
   - **Codex CLI**: `apply_patch` — a custom diff DSL the model is RL-trained on. Terse, parsable, big reason it tops Terminal-Bench.
   - **Claude Code**: `old_string`/`new_string` structured edits with surrounding-context anchoring.
   - **Cline (default)**: whole-file rewrite — token-fat. Roo Code's `apply_diff` fork ships ~30% cheaper edits.
   The "small edits without rewriting the file" battle is largely won by diff-DSLs.

3. **Tool architecture: built-in vs MCP-first.**
   - **Goose**: every external capability is an MCP subprocess. Adding tools requires no rebuild.
   - **Claude Code / Cursor / Codex**: built-in tool set + MCP for extension.
   - **Cline**: can *generate and install* its own MCP servers on request.

4. **Code intelligence: shell-and-grep vs LSP.**
   - **Crush, Junie**: spawn language servers per project; the model gets real type-aware navigation (definitions, references, symbols).
   - **Most others**: text search via grep/ripgrep + heuristics.
   For typed languages and large monorepos, LSP is the under-appreciated lever.

Two more patterns worth naming:
- **Server/client split** (opencode) — long-lived backend with thin TUI/IDE/SDK clients sharing sessions.
- **Branchable session tree** (Pi) — first-class fork/rewind across the conversation; ralphing as a UI primitive rather than a `/clear` workaround.

> Per-tool deep dives, comparison tables, and "distinctive bets" for all 14 tools live in `../research/coding-agents/README.md`.

---

## Slide 3 — The craft levers (where the productivity is)

This is the slide that earns you the next 30 minutes of attention. **Same six boxes, but now: where you actually steer.**

### A. Sessions
- **Start fresh per task.** The #1 tip from heavy users. If you've corrected the agent twice on the same point, `/clear` and re-state.
- **One topic per session.** Mixing topics pollutes context and tanks performance.
- **Background sessions / cron** (CC `BG_SESSIONS`, `CronCreate`): for watch-and-respond loops without tying up a terminal.

### B. Planning
- **Plan mode** (CC: `EnterPlanMode`, Cursor: Composer plan, Aider: `/architect`). Read-only investigation phase before any edits. CC's Boris Cherny reportedly uses plan mode for **~80% of tasks**.
- **Pattern**: Plan → Auto-Accept for execution → flip back. *Plan mode is a gate, not magic.*
- **Remote-planning modes** (e.g. CC's long-form remote planning, Cursor cloud agents): offload the plan to a longer-running session on a stronger model for hard problems.

### C. Context management
- **Cache boundary**: every harness has a static-vs-dynamic split. Don't churn the static part. Anthropic's beta header `prompt-caching-scope-2026-01-05` made this explicit; same idea applies everywhere.
- **`/clear` between tasks** — resets context, preserves cache for the next session.
- **`/compact` at ~70% usage** — proactively summarize, don't wait for forced compaction.
- **Deferred tool loading** (CC `ToolSearchTool`): tools registered name-only, full schema fetched on demand. Lets a harness expose 40+ tools without bloating context.
- **Memory injection** — CC's `findRelevantMemories` runs a side-Sonnet call to pick which memory files to inject. Cursor/Cline use AGENTS.md and `.cursorrules`. The mechanism varies; the *principle* — small index, lazy load — is universal.

### D. Model selection
- **Tier the work**: Haiku for cheap classification/glue, Sonnet for the bulk, Opus for hard reasoning + plan mode. Same pattern across vendors (GPT-5 / GPT-5-mini, Gemini Pro / Flash).
- Most harnesses now let you set a per-task model or per-sub-agent model.
- **Fast / premium-tier modes** (across vendors): same flagship model, faster inference, multiple times the price. Use sparingly.

### E. Tools, hooks, skills, MCP
<!-- CE-EDIT #3 (from context-engineering-presentation slide 25): Push vs Pull framing + API design principles -->
- **Push (RAG) vs Pull (Tool Calling)**: two ways context arrives. *Push* = inject relevant info into the prompt before the agent asks (RAG, AGENTS.md, retrieved chunks). *Pull* = give the agent tools and let it fetch on demand (Bash, Read, MCP). Push is cheaper but speculative; pull is precise but slower. **API design principles apply to tool design** — clear names, stable signatures, predictable outputs, terse responses.
- **Tools**: the model's *hands*. ~10 core tools is the sweet spot in the prompt; everything else deferred.
- **Hooks** (CC `PreToolUse`/`PostToolUse`/`UserPromptSubmit`/`SessionStart`/`Stop`/`PreCompact`): **deterministic shell commands at lifecycle points**. The right place for things that *must* happen every time — formatting, linting, security checks. **Block at submit, not at write** — let the agent finish its plan, then validate.
- **Skills**: progressive-disclosure capability bundles (slash-commands + prompt + optional code). Cleaner than stuffing everything into AGENTS.md.
- **MCP** (Model Context Protocol): the universal extension protocol. Computer use, Chrome, GitHub, databases — all just MCP servers. CC, Cursor, Codex, Cline all host MCP now. Learn one MCP server, use it everywhere.
- **Sub-agents / Agent teams**: spawn forks for parallel research/implementation/verification. CC's coordinator, Cursor's parallel tabs, Codex's Agents SDK — same pattern.

### F. Permissions
- **Permission modes**: plan / default / acceptEdits / bypass. Match the mode to the risk of the task, not your patience.
- **Protected paths**: `.gitconfig`, shell rcs, `.mcp.json`, `.claude.json` — never let the agent edit these unattended.
- **Risk classifier** (CC has an ML "YOLO classifier" for low-risk auto-approval). The principle: *automate the boring approvals; never automate the risky ones.*

---

## Slide 4 — The token economy (why this all matters at scale)

Every craft lever above maps to a token economics decision. Engineers ignore this at their own cost.

### What costs tokens
- **Long system prompt** (tools, instructions, memory) — paid every turn, but **cached** if static
- **Conversation history** — grows linearly, paid every turn (cached up to the boundary)
- **Tool results** — file reads, grep output, web fetches: easy to balloon
- **Sub-agent / coordinator calls** — each spawn has its own context

### Where the savings come from

| Lever | Savings | How |
|---|---|---|
| **Prompt caching** | 90%+ on cached input | Keep the static prefix stable; never edit AGENTS.md mid-session |
| **Deferred tool loading** | 30–50% on initial prompt | Tools registered name-only, fetched on use |
| **`/clear` between tasks** | Resets exponentially-growing history | Use it. Aggressively. |
| **`/compact`** | Summarizes history into a small replacement | At ~70% context, not at force-compaction |
| **Tiered models** | 5–15× on most calls | Haiku/Sonnet for routine; Opus only when needed |
| **Token-efficient tools** | ~10–20% on tool-heavy turns | Beta: `token-efficient-tools-2026-03-28` and equivalents |
| **Skills + slash commands** | Replaces verbose prompts | Move recurring instructions into skills |
| **Sub-agents for research** | Keeps main context clean | Pay once for a research fork, return distilled findings |

### Real numbers (rough, public 2026 pricing)
- Sonnet: **$3 in / $15 out** per Mtok (cache read $0.30)
- Opus 4.5/4.6: **$5 in / $25 out** per Mtok (cache read $0.50)
- Opus Fast: **$30 in / $150 out** — yes, really
- Haiku 4.5: **$1 in / $5 out**

> A well-run agent session against a 200-file repo with cache hits costs cents per task. The same session without cache discipline can cost dollars per turn. The difference is *entirely* in the harness craft.

### Three rules of thumb for the room
1. **Cache hit rate is the metric.** If you don't know yours, find out tomorrow.
2. **Don't churn the system prompt.** Every AGENTS.md edit invalidates cache for the whole org.
3. **Use the cheapest model that works.** Opus is impressive; Sonnet is enough for 80% of tasks.

---

## Optional live tour (5 min) — if time permits

If the room is engaged after the four slides, do a live demo of *one* harness showing:
1. `/plan` — show the read-only investigation phase
2. The system prompt structure (CC: `--dump-system-prompt` if internal; otherwise show CLAUDE.md + AGENTS.md)
3. Hook firing on edit (PostToolUse → ruff/prettier)
4. `/clear` → cache hit on next turn (token counter visible)
5. Quick MCP connection (e.g. `context7` for live docs)

This makes the abstract concrete and earns a lot of trust before the next deep-dive section.

---

## Sources & further reading

- [thoughts.jock.pl — Claude Code vs Codex CLI vs Aider vs OpenCode vs Pi vs Cursor (2026)](https://thoughts.jock.pl/p/ai-coding-harness-agents-2026)
- [bradAGI/awesome-cli-coding-agents — directory of CLI harnesses](https://github.com/bradAGI/awesome-cli-coding-agents)
- [Cursor — improving the Cursor agent for OpenAI Codex models](https://cursor.com/blog/codex-model-harness)
- [artificialanalysis.ai — coding agents leaderboard](https://artificialanalysis.ai/agents/coding)
- [Anthropic — Claude Code best practices](https://code.claude.com/docs/en/best-practices)
- [SmartScope — Claude Code advanced best practices: hooks, subagents, context (2026)](https://smartscope.blog/en/generative-ai/claude/claude-code-best-practices-advanced-2026/)
- [Shrivu Shankar — How I Use Every Claude Code Feature](https://blog.sshh.io/p/how-i-use-every-claude-code-feature)
- [Claude Code Plan Mode — when to use it and how to get real value](https://www.claudedirectory.org/blog/claude-code-plan-mode-guide)
- [Mustafa Morbel — Taming Claude Code: a guide to CLAUDE.md and Hooks](https://medium.com/becoming-for-better/taming-claude-code-a-guide-to-claude-md-and-hooks-ed059879991c)
- [augmentcode.com — How to write good AGENTS.md files](https://www.augmentcode.com/blog/how-to-write-good-agents-dot-md-files)
- [claude.md — community CLAUDE.md examples](https://claude.md/)
- [AkitaOnRails — AI Agents: which is best? (Jan 2026)](https://akitaonrails.com/en/2026/01/24/ai-agents-which-is-best-opencode-crush-claude-code-codex-copilot-cursor-windsurf-antigravity/)
- *Internal*: `agentic-engineering/../claude-code/` — architecture.md, findings.md, tools.md (deep CC source-level analysis, March 2026)

---

## Open questions for me to decide before tomorrow

- [ ] Live tour: yes/no? Depends on time and confidence the room is following.
- [ ] Codename trivia — keep entirely out of public slides/handouts; reserve for private Q&A only.
- [ ] Token economics slide — do I want a chart or a table? Table is cleaner for a 1-min slide.
- [ ] Skills + MCP — do I include them here or hold them for the next deep-dive section? **Lean: tease here, deep-dive after.**
- [ ] Mention "ralphing" by name on the landscape slide, or save it for the deep-dive section where I'll demonstrate? **Lean: save for demo.**
