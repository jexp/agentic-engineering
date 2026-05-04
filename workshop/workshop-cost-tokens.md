# Workshop — Cost & Token Economics

**Block**: Deep dive — sub-section, ~7–10 min
**Position**: Best slotted right after the harness landscape, before the practices section. Token costs are the *why* under most of the practices.
**Goal**: make the room cost-literate. Show where tokens go by phase, what each saving lever buys, and what tools exist to measure and reduce.

---

## Framing line

> "In 2026 the new top skill for AI engineers is **token economy**. Same model, same task, same outcome — 10× cost difference between someone who knows the levers and someone who doesn't. This section is the levers."

---

## Slide 1 — Where the tokens go

<!-- CE-EDIT #8 (from context-engineering-presentation slide 18): Context Pyramid as the primary visual -->
The **Context Pyramid** — three layers, by *stability*, with caching efficiency increasing toward the base:

```
                    ▲ EPHEMERAL  — every turn, never cached
                   ╱  • tool outputs
                  ╱   • current reasoning / chain-of-thought
                 ╱    • the user's latest message
                ╱─────────────────────────────────────────────
               ╱  DYNAMIC  — changes occasionally, partially cached
              ╱   • few-shot examples
             ╱    • injected memory / retrieved context
            ╱     • metadata, tool list (when stable)
           ╱──────────────────────────────────────────────────
          ╱   PERSISTENT  — stable across turns, fully cached
         ╱    • system prompt, role, persona
        ╱     • policies, guardrails
       ╱      • core facts (AGENTS.md, project rules)
      ▼─────────────────────────────────────────────────────── CACHING ↑
```

**The economic insight**: caching applies most strongly at the *base*. Stable layers compound discounts; churn at the bottom invalidates everything above.

<!-- TWEET-EDIT #1 (from @mnilax 90-day Claude Code audit, Apr 2026): the "long invoice" mental model -->
> **The mental-model shift, from a 90-day instrumented audit (430 hours, 6M input tokens, $1,340 spend):**
>
> *"The mistake I was making: treating every Claude Code session as a fresh blank slate. In reality, every session is a long invoice that pre-charges you for your CLAUDE.md, every active plugin's hooks, every active skill's SKILL.md, every connected MCP's tool schema, conversation history up to that turn, and cache-miss recompilation. **Productive tokens are the residual** — what's left after all that overhead."*
>
> The audit found **27% productive / 73% overhead** — and crucially, the bigger model wasn't the lever. *Cheaper model on bloated context still costs more than expensive model on lean context.*

A typical agentic coding session has 6 distinct phases. They have *very different* token shapes.

```
                    INPUT      OUTPUT     CACHE-FRIENDLY?
PHASE
─────────────────────────────────────────────────────────────
1. Boot (system prompt, tools, AGENTS.md)
                    ████████   ░          ✅ static, caches well
2. Plan mode / research (read code, think)
                    ████████   ███        ✅ good caching potential
3. Tool calls (grep/glob/read)
                    ███        █          ✅ schemas cached, results small
4. MCP calls
                    ███        ██         〰️ depends on server response size
5. Code generation (the actual edit)
                    ██         ████       ✅ if context is stable
6. Test / lint loop (iterate to green)
                    ████       ██         ✅ huge cache wins per iteration
─────────────────────────────────────────────────────────────
```

### Concrete shape of a "medium" task (~20 minutes, ~50 turns)

Rough orders of magnitude — your numbers will vary 2–5×:

| Phase | Tokens in | Tokens out | Notes |
|---|---|---|---|
| Boot (per session) | 30–80k | 0 | Cached after first turn |
| Plan mode | 50–200k | 5–20k | One big read pass; outputs the plan |
| Code search | 5–20k | 1–5k | grep/glob results are small |
| MCP (per call) | 5–30k | 2–10k | Depends entirely on server |
| Generation (per edit) | 20–80k | 3–15k | Context + diff out |
| Test/lint loop | 20–80k × N | 1–5k × N | The N kills you |

**The two failure modes that dominate cost:**
1. **The `N` in step 6** — every iteration of the test loop re-sends growing history. Without compaction or `/clear`, history grows linearly, total cost grows **quadratically**.
2. **Cache misses on the boot phase** — every edit to AGENTS.md, every change to the system prompt, throws away 30–80k of cached input.

> A well-disciplined session against a 200-file repo costs **cents** per task with cache hits. The same session without cache discipline costs **dollars** per turn. The difference is entirely in the harness craft.

---

## Slide 2 — The savings levers (in priority order)

<!-- CE-EDIT #9 (from context-engineering-presentation slide 17): Offload / Consolidate / Retrieve frame -->
Every saving lever is one of three moves: **Offload** (push state out of context), **Consolidate** (compress what's in context), **Retrieve** (cache or fetch on demand).

| Move | What it is | Example levers |
|---|---|---|
| **Offload** | Get information *out* of the prompt and into a side store | Filesystem notes, vector DB (episodic), graph (structural), `/clear` between tasks |
| **Consolidate** | Reduce what's already in context | `/compact` summarization, sub-agent forks that return a digest, prune at boundaries |
| **Retrieve** | Bring exactly what's needed, no more | Prompt caching, tool-schema deferred loading, RAG/GraphRAG, reconstructive memory |

These compound. Fix the top three and you'll cut spend 5–10× before touching any tool.

| # | Lever | Typical savings | What it is |
|---|---|---|---|
| 1 | **Prompt caching** | 90% on cached input | Anthropic, OpenAI, Google all cache. Stable static prefix → 10× cheaper reads on subsequent turns |
| 2 | **`/clear` between tasks** | Resets quadratic growth | Single biggest behavioural lever. Free. Use it. |
| 3 | **Tiered models** | 5–15× on routine calls | Haiku/Mini for glue; Sonnet for bulk; Opus for hard. |
| 4 | **Plan mode discipline** | 30–50% per task | Resolve questions in plan mode (cheap reads) before writing (expensive turns) |
| 5 | **`/compact` at ~70%** | Replaces history with summary | Softer reset; preserves task continuity |
| 6 | **Sub-agents for research** | Pays once, returns distilled | Fork takes the read-heavy hit; main session stays lean |
| 7 | **Deferred tool loading** | 30–50% on initial prompt | Tools name-only, schema fetched on demand (CC's `ToolSearchTool`) |
| 8 | **Token-efficient tools** | 10–20% on tool-heavy turns | Anthropic beta `token-efficient-tools-2026-03-28` and equivalents |
| 9 | **Apply-diff vs whole-file** | 30% on edits | Roo Code's pitch over Cline; Codex's `apply_patch`. Don't rewrite a file to change two lines. |
| 10 | **Skills + slash commands** | Replace verbose prompts | Move recurring instructions into one-line invocations |

### Tactical specifics worth saying out loud

- **Don't churn AGENTS.md mid-session.** Every edit invalidates the cache for everyone using that prefix. Edit it between sessions.
- **One topic per session.** Cache hit rate halves when topics mix.
- **Architect/Editor split** (Aider's pattern): big model plans, small model edits. Often 5× cheaper with no quality loss on small edits.
- **Use the cheapest model that works.** Sonnet is enough for ~80% of tasks. Opus is 5× the cost; only use it when you've measured it makes a difference.
- **Watch the hidden premium costs**: Cursor "Max Mode," Claude Code Fast mode (multiple times standard Opus pricing), Copilot's premium-request currency. These pop up unexpectedly.

---

## Slide 3 — The tools

A field guide. Mark `[USING]` for the ones I personally rely on.

### Measurement / observability

- **[ccusage](https://github.com/ryoppippi/ccusage)** — Ryoppippi's de facto standard for Claude Code usage analytics. `npx ccusage` reads the local JSONL files in `~/.claude/projects/` and produces reports: tokens per model, tokens by type, costs by day/hour/project, cache hit rate. **First tool to install.** No API roundtrip; runs entirely offline against your own logs.

- **claude-code-cost / claude-cost** — alternative trackers in the same niche; ccusage has won mindshare but a few alternatives exist for non-CC harnesses. Search "<harness> usage tracker" before assuming nothing exists.

- **Built-in token meters** — most modern harnesses now show running token cost in the TUI: Cline shows it live, Cursor shows it in the agent panel, Claude Code shows it via `/cost`. Watch them.

<!-- TWEET-EDIT #2 (from @mnilax thread): the 9 invisible patterns + audit script -->
- **The 9 invisible patterns audit** ([thread by @mnilax, Apr 2026](https://x.com/mnilax/status/2050261839653556522)) — a 90-day instrumented breakdown of where tokens *actually* go on a typical Claude Code workflow. The categories with their measured share of total tokens:

| # | Pattern | % of total | 30-second fix |
|---|---|---|---|
| 1 | **CLAUDE.md / AGENTS.md bloat** | **14%** | Target combined <1,500 tokens (`wc -w ~/.claude/CLAUDE.md`). Cut to imperatives; move framework rules to project-level; promote repeated patterns into skills |
| 2 | **Conversation history re-reads** | **13%** | Edit prior message instead of follow-up; cap chats at ~20 messages; `/compact` (not `/clear`) when continuity matters |
| 3 | **Hook injection waste** (`UserPromptSubmit`) | **11%** | Audit `cat ~/.claude/settings.json \| jq '.hooks.UserPromptSubmit'` — kill any hook you can't justify |
| 4 | **Cache misses on session resume** (5-min default TTL) | **10%** | Hotkey-bound "ping" prompt to keep cache warm; or upgrade to 1-hour cache (writes 2× / reads 0.1×) |
| 5 | **Skill loading on irrelevant tasks** | **7%** | Audit which skills you actually invoke over a week; disable the rest. 9 skills × ~1,500 tokens each adds up fast |
| 6 | **"Just-in-case" MCP tool definitions** | **6%** | `/mcp disable <server>` for ones not in this session's task; keep 3 always-on, enable rest per-session |
| 7 | **Extended thinking on simple questions** | **5%** | Default OFF; toggle ON per-message for genuinely hard tasks (Alt+T in CC) |
| 8 | **Wrong-direction generation** | **4%** | Cmd+. / Ctrl+. stops generation; double-Esc opens checkpoint scroller in CC terminal |
| 9 | **Plugin auto-update / SessionStart noise** | **3%** | Kill any SessionStart hook that's just a "loaded" notification |

**Headline result from the audit, before → after fixes**: avg input tokens per prompt **18,400 → 6,100 (-67%)**; productive token share **27% → ~65%**; days until weekly limit **4.2 → 7+**; ~$130/month saved on the same workload.

> **Counter-intuitive finding**: the obvious advice didn't help. *Switching to Haiku for "simple" tasks* saved ~3% (the bloat is in context, not model choice). *Aggressive `/clear`* lost context that cost more in re-prompting. *Disabling all skills* led to manually re-typing 200-token instructions every prompt. The *patterns above* are where the real waste lives — they compound, they're invisible without instrumentation, and the obvious blog advice never names them.

### Active token reduction (proxy / wrapper / hook layer)

- **[RTK — Rust Token Killer](https://github.com/...)** [USING — already in user's CLAUDE.md] — Rust CLI proxy that intercepts common dev commands (git, ls, grep, etc.) and rewrites them to token-efficient equivalents. Quoted savings: **60–90%** on dev operations. Hook-based, transparent (zero token overhead at the tool boundary). `rtk gain` shows your savings; `rtk discover` finds missed opportunities. **The "free 5×" lever**, especially valuable on noisy commands like `npm test` or verbose `git log`.

- **[caveman](https://github.com/...)** [USING] — token-saving harness wrapper. [VERIFY exact mechanism — likely a system-prompt-stripping or context-compaction proxy]. Position in the stack and exact savings worth the user describing in the demo.

- **[headroom](https://github.com/...)** [USING] — token-aware harness layer. The user has this in their CLAUDE.md / RTK.md note: works alongside RTK and caveman. [VERIFY: appears to do automatic compression/elision of stale tool output, surfacing a hash for retrieval if needed — this matches the `headroom_retrieve` capability seen in some harness builds]. One-line summary worth confirming with the user.

### Built-in protocol-level savings

- **Anthropic prompt caching** — `cache_control` markers on system prompt sections; 5-minute TTL by default, 1-hour with the right beta header. Cache reads at $0.30/Mtok vs $3 input on Sonnet — **10× discount**.
- **`token-efficient-tools-2026-03-28`** beta header — reduces tool-schema overhead on tool-heavy turns. ~10–20% on those turns.
- **OpenAI prompt caching / cached_tokens billing** — same idea, server-side, automatic for repeated prefixes. Surfaced in the API response.
- **Google context caching** — explicit cache objects you can reuse across calls (Gemini API).

### Harness-level levers worth knowing

- **Claude Code**: `/clear`, `/compact`, plan mode, sub-agents (TaskCreate), deferred tools (`ToolSearchTool`), Skills (replace long prompts with one-line invocations), hooks at PreCompact for re-injecting key context after compaction.
- **Aider**: `--architect` mode (cheap edit model, expensive reason model), `/clear`, `/tokens` shows current usage.
- **Cline / Roo Code**: Roo's `apply_diff` saves ~30% over Cline's whole-file rewrite; Cline's per-rule scoping in `.clinerules` reduces noise.
- **Cursor**: Privacy mode also affects context (less retrieval), credit pool dashboard for visibility.
- **Codex CLI**: `apply_patch` format is itself token-efficient (no whole-file rewrites).
- **opencode / Crush**: model registry (Catwalk) auto-tracks per-token pricing across providers — easy to swap in cheaper models.

### Provider-routing & multi-model

- **LiteLLM / OpenRouter / Vercel AI Gateway** — proxy layer that lets you route requests to the cheapest model that satisfies a spec. Useful for shops running across multiple providers.
- **Continue.dev cost-aware routing** [VERIFY current feature naming] — IDE-level cost optimization including model selection per task type.

### Prompt-level discipline (not a tool, a habit)

- **Lazy file reads** — read fewer, smaller chunks; resist the urge to dump whole files into context
- **Skill-ified instructions** — one-line slash command beats a paragraph of instructions every turn
- **Tight task scope** — bigger task = more context = quadratic growth. Smaller tasks = many small cheap caches.

---

## Slide 4 — The numbers (rough 2026 pricing for orientation)

Per million tokens. Memorize this table; you'll use it weekly.

| Model | Input | Cached read | Output |
|---|---|---|---|
| **Haiku 4.5** | $1 | $0.10 | $5 |
| **Sonnet (4.5/4.6)** | $3 | $0.30 | $15 |
| **Opus 4.5/4.6** | $5 | $0.50 | $25 |
| **Opus 4.6 Fast tier** | $30 | $3 | $150 |
| **GPT-5** [VERIFY] | ~$3 | ~$0.30 | ~$15 |
| **GPT-5.5** [VERIFY] | ~$5 | ~$0.50 | ~$25 |
| **Gemini 3 Pro** [VERIFY] | ~$2.50 | ~$0.25 | ~$12.50 |

**Key ratios to internalize:**
- Cache read is **10×** cheaper than fresh input — this is why caching matters
- Output is **5×** more expensive than input — bias toward terse outputs
- Opus is **~5×** more expensive than Sonnet — only when needed
- Fast/Premium tiers are **~6×** the standard model — almost never worth it

### Real-task cost snapshots (rough, my own runs)

| Task shape | Disciplined session | Sloppy session |
|---|---|---|
| Small bug fix (~10 turns) | $0.05 | $0.50 |
| Medium feature (~50 turns) | $0.50 | $5 |
| Big refactor (~200 turns) | $3–5 | $30–60 |

The 10× gap is *entirely* discipline — same model, same outcome.

---

## Slide 5 — Three rules of thumb + Monday-morning action

### Three rules

1. **Cache hit rate is the metric.** If you don't know yours, you can't improve it. Install ccusage tomorrow morning.
2. **Don't churn the system prompt.** Every AGENTS.md edit invalidates cache for the whole org. Edit between sessions.
3. **Use the cheapest model that works.** Measure, don't assume. 80% of tasks don't need Opus.

<!-- TWEET-EDIT #3 (from @mnilax thread): the 30-second audit script -->
### The 30-second audit (run this Monday)

```bash
# CLAUDE.md / AGENTS.md size — target combined < 1,200 words (~1,500 tokens)
wc -w ~/.claude/CLAUDE.md .claude/CLAUDE.md AGENTS.md 2>/dev/null

# What's being injected on every prompt — kill anything you can't justify
cat ~/.claude/settings.json 2>/dev/null | jq '.hooks.UserPromptSubmit'
cat .claude/settings.json   2>/dev/null | jq '.hooks.UserPromptSubmit'

# How many MCPs auto-load — target 3, enable rest per-session
cat ~/.claude/settings.json 2>/dev/null | jq '.mcpServers // {} | keys'

# Plugin / skill inventory — anything you didn't invoke this week → disable
ls ~/.claude/plugins/ ~/.claude/skills/ 2>/dev/null
```

If you have *any* line over target, that's where the next hour of cleanup pays back the most.

### Monday-morning action

- [ ] Install ccusage (or your harness's equivalent) — `npx ccusage` is one command
- [ ] Look at your last week's spend — identify the 20% of sessions that consumed 80% of cost
- [ ] Pick **one** lever from Slide 2 and apply it for a week
- [ ] Re-check ccusage; verify the savings
- [ ] Repeat

---

## Where this section goes in the deck

**Lean: place after the harness landscape (workshop-harnesses.md Slide 4 Token Economy expands into this), before the practices section.** Token cost is the *why* behind the practices — leading with cost makes the practices feel like leverage, not bureaucracy.

Alternative: collapse to 2 slides and slot directly inside the harness section's "token economy" slide, keeping this longer doc as a handout.

---

## Sources & references

- [ccusage on GitHub](https://github.com/ryoppippi/ccusage) — the Claude Code usage analyzer
- [Anthropic prompt caching docs](https://docs.anthropic.com/en/docs/build-with-claude/prompt-caching)
- [Anthropic — token-efficient-tools beta](https://docs.anthropic.com/en/release-notes/api) [VERIFY exact docs page]
- [OpenAI prompt caching](https://platform.openai.com/docs/guides/prompt-caching)
- [Google Gemini context caching](https://ai.google.dev/gemini-api/docs/caching)
- [Aider architect mode](https://aider.chat/docs/usage/modes.html)
- [Roo Code apply_diff](https://github.com/RooCodeInc/Roo-Code) — see release notes for the 30% savings claim
- [LiteLLM](https://litellm.ai) / [OpenRouter](https://openrouter.ai) — multi-provider routing
- *Internal*: `~/.claude/CLAUDE.md` — RTK, headroom, caveman setup notes
- *Internal*: `~/.claude/RTK.md` — full RTK command reference

---

## Open questions & TODOs for me to decide before tomorrow

- [ ] **User to confirm** the one-line description of headroom and caveman — I have placeholders flagged [VERIFY].
- [ ] **Show the demo**: live `ccusage` output on my own logs, ideally with a "before discipline / after discipline" chart. Strongest demo of the section.
- [ ] **The numbers in Slide 4 need verification** before printing — pricing moves and the GPT-5/5.5/Gemini 3 figures are rough.
- [ ] **Slide 2 vs Slide 3 emphasis**: I have ~10 levers and ~12 tools; which 3 levers and 3 tools get the most stage time? **Lean: levers 1, 2, 3 (caching, /clear, tiered models). Tools: ccusage, RTK, prompt caching.**
- [ ] **Cost snapshots in Slide 4** — do I quote my actual numbers or stay generic? **Lean: my actual numbers. Concrete > abstract every time.**
- [ ] **Where to demo headroom/RTK/caveman** — own-experience portion or here? **Lean: here, in this section, as the 1-minute "this is what I personally use" moment.**
