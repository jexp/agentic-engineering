# Progress Log — Vibecode Workshop & Keynote

**Workshop**: tomorrow, 4hr session, experienced engineers / team leads
**Keynote**: in 2 weeks, VibeCode conference

> **Update 2026-05-04**: repo restructured for public push to **github.com/jexp/agentic-engineering**. Files moved into `workshop/`, `keynote/`, `research/`, `assets/`. See `README.md` for the new layout, or the per-section file list below (paths show the original flat structure but everything is now under the appropriate folder).

## Overall plan

Workshop agenda (sent to organizers):

| Block | Time | Status |
|---|---|---|
| Intro / background / state of agentic engineering | 30–45 min | drafting |
| Exercise 1 — small HTML tool or mini-course | 30 min | not started |
| Deep dive — agents.md/claude.md, setup, ralphing, context, plan mode, own experience | 30–45 min | not started |
| Exercise 2 — nasty bug / new feature / different language / MCP server | 60 min | not started |
| Q&A | 30 min | not started |

Keynote (separate track, draft v3 already exists in `vibecode-keynote-v3.md`):
- Status: v3 reviewed, not yet final. Re-visit closer to event.

## Open risks / decisions

- [ ] Workshop runs 3hrs of content in a 4hr slot — confirm whether intro/deep-dive flex up to 45min each, or hard-cap at 30 to leave transition headroom.
- [ ] Pre-flight checklist (Claude Code installed, API key, repo cloned) — needs to be sent to attendees in advance, otherwise first 20 min of Exercise 1 will be setup chaos.
- [ ] Exercise 2 — pre-pick 2–3 concrete starter options, otherwise people burn 15min deciding.
- [ ] Decide if a Go-CLI starter scaffold needs to be prepared for Exercise 2 cross-language option.

## Files

- `prompt.md` — original keynote brief + history of v1/v2/v3 iterations
- `agentic-engineering-ideas.md` — raw notes for the workshop
- `vibecode-keynote-v1.md` / `v2.md` / `v3.md` — keynote drafts (v3 current)
- `workshop-intro.md` — intro section draft (30–45 min block)
- `workshop-harnesses.md` — harness anatomy section (3–4 slides + optional live tour)
- `workshop-practices.md` — good practices section (mentoring frame, AGENTS.md, ralphing, spec-driven, per-task loop)
- `workshop-resources.md` — curated resources / handout for the deep-dive close (practitioners, craftspeople, books, vendor docs, MCPs, communities, QR slide plan)
- `workshop-own-experience.md` — 6-slide cue cards for the live-demo own-experience portion (research/learning, content gen, codebase analysis, simple greenfield, OSS, larger greenfield)
- `workshop-exercise-1.md` — Exercise 1 brief: "build the tool you wished existed" (Simon Willison frame, HTML tool / skill / CLI, 30-min time-box)
- `coding-agents/` — folder with 14 per-tool deep dives + consolidated `README.md` overview & comparison tables
- `workshop-benchmarks.md` — 5-slide section on SWE benchmarks: landscape, current leaders, pros/cons, how to read like a senior engineer, honest take
- `workshop-cost-tokens.md` — **NEW** 5-slide section on cost & token economics: where tokens go by phase, savings levers in priority order, tools (ccusage, RTK, headroom, caveman, etc.), 2026 pricing, three rules of thumb
- `context-engineering-presentation.pdf` — user's existing context-engineering deck (40 slides + research material)
- `context-engineering-mining.md` — **NEW** mining doc: maps reusable CE deck pieces to specific workshop sections + verified quote bank + 14 numbered surgical edits to apply across existing files
- `workshop-tool-use.md` — 4–5 slide section on the tool-use ladder: built-in → Linux CLI → code snippets → REST → skills → MCP, with cost/capability/fragility matrix and climb-the-ladder heuristic
- `workshop-exercise-2.md` — 60-min main exercise brief: 4 task archetypes (nasty bug, new feature, MCP on hume surface, cross-language port), explicit 0:00–1:00 minute breakdown, AGENTS.md starter template, 5 execution rules, success metrics, facilitator notes, anti-patterns
- `workshop-outline.md` — **NEW** master running order & structure doc: at-a-glance agenda table, per-block timing/source-doc/slide budget, hand-off lines between sections, slide generation guidance, Q&A section with my opening question + 13 hand-raiser questions in 3 difficulty tiers + closing reflection, day-before pre-flight checklist
- `CLAUDE.md` — repo-level Claude memory file (eating own dog food)
- `progress.md` — this file

External research sources used:
- `../claude-code/architecture.md`, `findings.md`, `tools.md` — deep CC source-level analysis (March 2026)
- Web research (May 2026) on Cursor, Codex, opencode, Aider, Cline, Windsurf, Antigravity comparison + best practices for hooks, plan mode, context management

## Done

- 2026-05-04: Created progress log + workshop-intro.md draft (intro section: why-now, timeline 2023→2026, why-coding-is-good-for-LLMs, hand-raiser questions, quote bank).
- 2026-05-04: Created workshop-harnesses.md — 4-slide section: anatomy of a harness, CLI+IDE landscape, craft levers (sessions/plan/context/models/tools/hooks), token economy. Includes optional 5-min live tour and source list. Codenames kept off slides by default.
- 2026-05-04: Created workshop-practices.md — 8-slide section covering: mentoring/junior-dev frame, agent strengths vs challenges, "collapsing the latent space" as the conceptual heart, AGENTS.md/CLAUDE.md authoring with starter template, ralphing & context resets, spec-driven flow with plan mode, the per-task execution loop (1→11), daily rhythm. RL-training tie-in to plan mode and TDD. Hooks for Beck/Henney/North/Booch/Karpathy callouts.
- 2026-05-04: Created workshop-resources.md — curated resources / handout for the deep-dive close. Sections: practitioners (Simon, Addy, Shrivu, Yegge, Huntley, Orosz, Mollick), craftspeople (Beck, Henney, Booch, Fowler, North, Karpathy), books, Anthropic/CC official, other harnesses, comparisons, deep-dive references, talks/podcasts, MCP servers worth installing, communities, research. Includes QR-slide layout proposal (4 codes).

- 2026-05-04: Created workshop-own-experience.md — 6-slide cue cards for live-demo portion. Each slide: shape of work, examples found in `~/d/llm/` and `~/Downloads/`, what works well, what fails, demo move (60–120 sec), one-line lesson for the room. Mapped to user's actual projects (Sather-K, vibe-haskell, Elixir; neo4j-skills, agent-integrations; claude-code, mongot, cocoindex; openalex-neo4j, clauditopia, multidb; inferrs, aura-cli; agent-intelligence, neo4j-skills cypher authoring, aura-agent-memory-gateway).
- 2026-05-04: Created workshop-exercise-1.md — 3 slides + brief. Frame on Simon Willison's "no longer afraid of starting" + his Dec 2025 *Useful patterns for building HTML tools* + tools.simonwillison.net (150+ examples). Three valid build shapes: HTML tool / skill / CLI script. Time-boxed 30-min plan (decide → plan → confirm → implement → use → save). Tactical tips, escape hatches, show-and-tell format. Open question: pre-pick 3 starter ideas in case room freezes (suggested: regex tester with explanation, JSON→Cypher, markdown TOC generator).
- 2026-05-04: Mined the context-engineering-presentation.pdf (40 slides). Wrote context-engineering-mining.md with: (a) reuse-grade slide map (~20 reusable concepts), (b) verified-wording quote bank (Karpathy June 2025 CE tweet, Lance Martin x2, Jason Liu, Jaya Gupta, Lisa Maria Martin, Beyond Prompts, Miller chunking — all confirmed-attribution, no [VERIFY] needed), (c) 14 numbered surgical edits to apply to existing workshop docs. Highlights: Context Pyramid (CE 18) replaces my cost-tokens Slide 1 visual; 5 named failure modes (CE 12) replace my generic challenges list in practices Slide 2; 3-Phase Agent Loop + 3-Context Problem (CE 22-23) wraps my 11-step per-task loop with the missing conceptual layer; AGENTS.md gets MVC framing + "reiterate at end (attention)" rule from CE 13/16; keynote v3 gets the "Communication is all you need" Lance Martin quote and the Beyond Prompts "too much control collapses the context" quote for the design-as-communication thread. Lean: surgical edits, skip the standalone CE mini-section unless dry-run reveals a gap.
- 2026-05-04: Created workshop-outline.md — the master structure document. At-a-glance table maps 12 blocks across the 4hr workshop with timing (welcome 5m → intro 30m → ex1 30m → break 10m → harnesses+tool-use 20m → cost 10m → benchmarks 5m → practices 20m → own-exp 10m → break 10m → ex2 60m → Q&A 25m → resources 5m). Per-block: source doc reference, framing line, section flow with sub-timings, pull-from-mining-doc references, and verbatim hand-off lines into the next block. Q&A section: my opening question ("what will you try Monday?"), 13 hand-raiser questions in 3 tiers (easy on-ramps → mid-depth → deeper) + closing redirect, plus 3-beat closing reflection. Slide generation guidance: ~59 slide budget across 12 blocks, per-block subtotals, visual/styling notes, trim-to-50 plan if dry-run runs over. Day-before pre-flight checklist (12 items) consolidating all open TODOs from individual section docs.
- 2026-05-04: Created workshop-exercise-2.md — 60-min main exercise. 4 task archetypes (A: nasty bug, B: small-but-real new feature, C: MCP server on hume surface — ETL-orchestra/graph-backend/admin/infra, D: cross-language port). Explicit minute-by-minute breakdown: 0:05 pick task, 0:15 setup with AGENTS.md, 0:25 plan mode, 0:35 task breakdown, 0:55 execution loop with ≤5min subtasks, 1:00 review. Target: 5+ commits, one per subtask. Includes paste-ready AGENTS.md starter, 5 execution rules (plan mode every subtask, one subtask = one commit, agent suggests-you decide, ralph after 2 corrections, 5-min time-box per subtask), success-tier table, 3-question show-and-tell, pre-flight email checklist (harness installed, repo with write access, task in mind, rg/jq/gh installed, test command verified, optional MCP), facilitator notes (walk the room, time announcements at 15/25/35/55, stuck backup task, MCP scaffold ready), 5 anti-patterns to surface in wrap-up.
- 2026-05-04: Created workshop-tool-use.md — 4-5 slide section on the tool-use ladder. Six rungs: built-in tools (Read/Edit/Bash/Grep/etc.) → Linux CLI (jq/sed/awk/rg) → code snippets (python -c) → REST APIs (curl) → Skills → MCP. Per-rung table of capability/effort/cost/latency/fragility. "When to climb" decision tree. 7 rules of thumb (Bash is universal escape hatch; jq+rg are force multipliers; don't reach for MCP when curl would do; skill the 3rd repetition; MCP for platforms, skills for procedures; code snippets are throwaway; watch verbose API token cost). Anti-patterns table. Optional worked example: "find which PRs touched auth code last week" across all 6 rungs. Lean: insert as Slide 2a in workshop-harnesses.md between landscape and craft levers.
- 2026-05-04: Created CLAUDE.md for this repo (eating our own dog food — was missing until user pointed it out).
- 2026-05-04: Created workshop-cost-tokens.md — 5-slide section on cost & token economics. Slides: (1) where tokens go across the 6 phases of a session with rough orders of magnitude per phase; (2) 10 savings levers in priority order (caching > /clear > tiered models > plan mode > /compact > sub-agents > deferred tools > token-efficient-tools beta > apply-diff > skills); (3) the tools — measurement (ccusage), active reduction (RTK, headroom, caveman — last two flagged [VERIFY] for user to confirm), built-in protocol-level (Anthropic/OpenAI/Google caching), harness-level levers, multi-provider routing (LiteLLM, OpenRouter); (4) 2026 pricing table with key ratios + real-task cost snapshots showing 10× discipline gap; (5) three rules of thumb + Monday-morning action. Lean: place after harness landscape before practices section.
- 2026-05-04: Created workshop-benchmarks.md — 5-slide section on SWE benchmarks. 5 benchmark families (function-level, contest, repo-level/SWE-bench, terminal/agentic, real-work/METR/SWE-Lancer); current leaderboard snapshot with caveats; pros (directionality, comparability, reproducibility) vs cons (contamination, RL leakage, single-repo bias, scaffolding asymmetry, pass@k inflation, test-set tuning, cost/latency-blind); 9-point rubric for reading benchmarks like a senior engineer; closing call to run your own 3-task internal eval. Lean: place inside harness landscape after comparison table. Skeptics will raise this if not addressed.
- 2026-05-04: Created `coding-agents/` folder via 4 parallel research subagents (each researching 3-5 tools). Per-tool files: claude-code, codex-cli, aider, cursor, windsurf, cline, opencode, goose, crush, gemini-cli, antigravity, github-copilot-agent, junie, pi. Each file: vendor/origin, install, architecture, extension model, interaction, loop, what's special, models, pricing, gotchas, references. Consolidated `coding-agents/README.md` adds a 4-cluster grouping, 8 cross-cutting observations (MCP won, AGENTS.md as cross-vendor convention, plan mode universal, hooks as differentiator, repo-map vs RAG vs whole-context, sandboxing leaders), and three comparison tables: basics (vendor/license/surface/models/pricing), capabilities (MCP/AGENTS.md/hooks/plan/sub-agents/parallel/local/sandbox), and distinctive bets per tool. Plus opinionated picking guidance. Notable findings: Pi = Mario Zechner's pi-mono (Armin Ronacher's OpenClaw harness, branchable session tree as the ralphing primitive); Junie CLI March 2026 beta; Antigravity = Google's Nov 2025 VS Code-fork IDE with Manager Surface; Codex `apply_patch` is its load-bearing primitive.

## Decisions made

- **Own-experience section**: live demo only — slides are cue cards, not content. Confirmed mapping of demos to actual projects in `~/d/llm/` and `~/Downloads/`.

## Next up (suggested order)

1. Review all 5 workshop docs (intro, harnesses, practices, resources, own-experience) → tighten quotes, decide cuts for time-box.
2. Pick the *one* artifact to demo per own-experience slide (TODO listed in that doc).
3. Confirm mongot analysis is OK to show publicly (otherwise swap to claude-code analysis as the only Slide 3 demo).
4. Exercise 1 brief — pick concrete prompt + success criteria + fallback if attendees finish fast/slow.
5. Exercise 2 briefs — 2–3 ready-to-go options with starter context.
6. Pre-flight checklist for attendees.
7. Slide deck assembly + host the resources doc somewhere stable for QR.
