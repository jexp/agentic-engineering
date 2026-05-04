# Workshop — Good Practices for Agentic Engineering

**Block**: Deep dive — practices, AGENTS.md, ralphing, spec-driven, the per-task loop
**Duration**: 20–25 min within the deep-dive block (follows the harnesses section)
**Position**: After the harness anatomy section, before Exercise 2
**Goal**: turn the anatomy into a working method. Give the room a concrete loop they can run tomorrow against their own codebase.

---

## Framing line for the section

> "Treat the agent like the most patient, deepest-diving junior engineer you've ever worked with — who happens to have read every line of public code, knows nothing about *your* code, and has no ego, no fatigue, and no fear of being wrong. Everything that follows is just *good onboarding for that teammate*."

---

## Slide 1 — The mentoring frame

The room knows how to onboard a junior. Use that.

| What an agent has that humans don't | What an agent lacks |
|---|---|
| **Infinite patience** — re-runs, re-reads, re-tries forever | **Project memory** — yesterday's PR is news every morning |
| **No ego** — accepts correction without defensiveness | **Domain experience** — never shipped *your* product |
| **Endurance** — 3am, hour 8, last task of the day, same quality | **Causal reasoning about humans** — why the team made past trade-offs |
| **Depth on any topic** — will read the entire RFC, every linked spec | **Taste calibrated to your codebase** — what "good" looks like *here* |
| **Consistent rule-following** (mostly) — written guidelines actually followed | **Production scars** — knows the failure modes of your specific stack |
| **Massive surface area** — every framework, every language, every API | **Read between the lines of a Slack thread** |

**The implication**: the same things you'd do for a sharp new hire — a good README, a clear style guide, paired-up planning, code review, written-down conventions, a test suite that catches the obvious mistakes — are *exactly* the things that turn an agent from a liability into a teammate. The leverage of doing them well is much higher with an agent than with a human, because the agent ingests them perfectly and applies them tirelessly.

> "Good software design was never for the machine. It was always for the humans who had to read, maintain, and extend it. Now those humans include AI teammates that learned the craft from human-written code."

---

## Slide 2 — The challenges (so the skeptics relax)

<!-- CE-EDIT #4 (from context-engineering-presentation slide 12, sourced to dbreunig.com 2025-06-22): replaced generic 7-failure-mode list with the 5 named failure modes -->

Don't undersell the problems. Naming them earns trust. Five named failure modes of context (Drew Breunig's taxonomy, June 2025):

1. **Context Rot / Semantic Drift.** Long contexts accumulate errors, lose focus on the task at hand, retain less of the relevant. Silent degradation before visible failure.
2. **Context Poisoning.** Hallucinated content gets re-used. *Example*: Gemini playing Pokémon hallucinated an item, then tried to use it later as if it were real.
3. **Context Confusion.** Models perform worse with more tools — especially when tools overlap or have similar names. More ≠ better.
4. **Context Distraction.** At very long contexts (>100k tokens) Gemini favoured *repeating prior actions* over making new plans. The agent stops thinking; it pattern-matches.
5. **Context Clash.** Back-to-back tool calls that contradict each other (e.g. "user is logged in" → "user not found") tank performance. The model can't reconcile.

> Source: Drew Breunig, *How Long Contexts Fail and How to Fix Them*, dbreunig.com/2025/06/22/how-contexts-fail-and-how-to-fix-them.html

Plus two more that don't fit Breunig's taxonomy but the room will recognize:

6. **Plausibly wrong.** Confidently wrong code that compiles, lints, eyeballs fine — and breaks production. Worse than visible errors because nothing alerts you.
7. **Cognitive load shifts to the human.** Reviewing 500 lines of plausible code is harder than writing 200 from scratch. *Jevons paradox*: efficiency gains absorbed by demand for human judgment. Real and unsolved — pace yourself.

The first five are addressed by the practices in the next slides. The last two are *yours to manage*.

---

## Slide 3 — Why practices work: collapsing the latent space

The conceptual heart of the section. One slide.

<!-- CE-EDIT #5 (from context-engineering-presentation slide 8): Lance Martin framing line -->
> *"Context engineering is building dynamic systems to provide the right information and tools in the right format such that the LLM can plausibly accomplish the task."* — **Lance Martin, LangChain**

That's the whole game. Each constraint you give the model is one step toward the right format.

A model holds an enormous distribution over possible continuations. "Write a function that fetches a user" has *millions* of plausible answers. **Every constraint you give it narrows that distribution toward the one you want.**

```
   Unconstrained prompt:        ████████████████████  (huge space, weak signal)
   + AGENTS.md conventions:     ████████████          (your style, your idioms)
   + spec / plan:               ██████                (this feature, these inputs)
   + tests as targets:          ███                   (verifiable success criteria)
   + the existing code:         █                     (matches what's already there)
```

This isn't a metaphor — it's how the model actually works. Each constraint conditions the output distribution.

**Why TDD is suddenly the killer technique it always claimed to be:**
- Tests are *verifiable rewards*. The model was post-trained on exactly that signal.
- A failing test is a precise, machine-readable specification.
- "All tests green" is an unambiguous stopping condition — no more drift.

**Why spec-driven dev is suddenly worth the ceremony:**
- The spec collapses the latent space *before* the agent starts hallucinating.
- It moves the human-judgment work upstream, where it's cheap.
- It makes review a check-against-spec, not a check-against-vibes.

> "Code is throwaway. Specs and tests are the durable artifacts." — Dan North's Replaceable Component Architecture, suddenly very practical now that someone else writes the throwaway code.

The full chain — AGENTS.md → spec → plan → tests → implementation → quality gates — is one long act of latent-space collapse. Good engineering practice was always this; we just couldn't afford the ceremony when every line cost keystrokes.

---

## Slide 4 — AGENTS.md / CLAUDE.md — the team handbook

<!-- CE-EDIT #6a (from context-engineering-presentation slide 13): MVC framing -->
**Frame**: AGENTS.md is the project's **Minimum Viable Context** — the smallest set of facts and rules that lets the agent do good work without overwhelming the prompt. Aim for *high signal-to-noise*. Include only what's needed to perform the next task.

What it is: a Markdown file at the repo root (and optionally in subfolders) that the harness automatically injects into every session's system prompt. Cross-vendor standard now (`AGENTS.md` for the broad ecosystem; CC also reads `CLAUDE.md`; Cursor uses `.cursorrules`).

### What goes in it

- **Project orientation** (3–6 lines): what the system does, which language/framework, where the entry points are
- **Conventions** that aren't obvious from the code: naming, error handling, async patterns, commit format
- **Tool/build/test commands**: `pnpm test`, `make integration`, `bq query --project=...` — *exact* commands so the agent doesn't guess
- **Quality gates**: lint, typecheck, test commands the agent should run before declaring done
- **Guardrails**: what *not* to touch (`.env`, secret stores, generated files, the migration directory)
- **Domain pointers**: where to find the architecture decision records, the API spec, the data dictionary — links, not content
- **Working agreements**: "create a NEW commit, never amend"; "ask before destructive ops"; "no `--no-verify`"

### What does NOT go in it

- Code patterns derivable from reading the code itself
- Long historical narrative (rots fast, bloats every prompt)
- Things you can express better as a hook (formatting, secrets scanning) or as tests (correctness)
- Generic AI advice the agent already knows

### Layering

```
~/.claude/CLAUDE.md         ← personal global (your preferences across all work)
<project>/AGENTS.md         ← project root, team-shared, in git
<project>/<area>/AGENTS.md  ← optional per-area overrides (frontend/, infra/, etc.)
.claude/skills/             ← slash-commands and skill definitions
```

### Operating rules
- **Keep it 50–100 lines at root.** Use `@import` to subfiles for detail. Long files = cache-bloat + signal dilution.
- **Don't churn it mid-session.** Every edit invalidates prompt cache for the whole org if the file is widely used.
- **Treat it like a PR-reviewed artifact.** Bad rules in AGENTS.md propagate silently into every agent run. Review them.
- **One source of truth per rule.** If it's in a hook, don't also put it in AGENTS.md. If it's in a test, don't put it in AGENTS.md either.

<!-- CE-EDIT #6b (from context-engineering-presentation slide 16): Context Structure principles -->
### Structure rules (how to write each section)
- **Group related information** — don't sprinkle conventions across three sections.
- **Label clearly** — use headers, and *XML tags* (`<rules>...</rules>`, `<commands>...</commands>`) when the agent needs to find the section reliably.
- **Build a hierarchy** — short summary at top, detail below. The agent reads top-down on every turn.
- **Concise, relevant only** — Miller's 7±2 still applies; chunked, named groups beat flat lists.
- **Refer back, don't duplicate** — link to docs/ADRs rather than copying their content into AGENTS.md.
- **Reiterate the essence at the end.** This is the rule most people miss: attention weights at the *end* of the prompt are higher than the middle. Close AGENTS.md with a one-line restatement of the most important rule (e.g. *"Always run `pnpm test` and ask before destructive ops."*). The agent sees this immediately before it acts.

### A starter template (paste-ready)

```markdown
# AGENTS.md

## What this is
<3 lines: the system, the stack, the entry points>

## How to run things
- Install: `pnpm install`
- Test:    `pnpm test`           ← always run before declaring done
- Lint:    `pnpm lint`
- Types:   `pnpm typecheck`

## Conventions
- Errors: throw typed errors from `src/errors`; never raw strings
- Async: prefer `async/await`; no `.then()` chains
- Commits: conventional commits, scope prefix required

## Guardrails
- Never edit: `.env*`, `migrations/`, `generated/`
- Never run: `npm publish`, `git push --force`
- Always ask before: `rm -rf`, `DROP TABLE`, schema changes

## References
- ADRs: `docs/adr/`
- API spec: `openapi.yaml`
- Domain glossary: `docs/glossary.md`
```

---

## Slide 5 — Ralphing & context resets

**The technique**: when an agent's context is rotting (drift, rabbit hole, repeated mistakes), don't reason your way out — **reset and re-seed**. Fresh session, distilled context, try again.

Named after Geoff "Ralph" Huntley's 2025 pattern (Pi was the first harness to bake it in). Now standard practice across CC, Cursor, opencode.

### When to ralph
- You've corrected the agent twice on the same point — the third try won't be the charm
- The agent is "fixing" things you didn't ask it to touch
- A long plan-mode investigation has bloated context past 60–70%
- You feel the urge to write a long corrective prompt — that's the signal

### How to ralph (the loop)
1. **Capture state** — `git status`, screenshot the plan, note the goal in 3 lines
2. **`/clear`** — drop the session
3. **Re-seed** — fresh prompt with: goal, current state, *only* the files that matter, the constraints from earlier
4. **Restart in plan mode** — let it re-orient cleanly

### What to keep across the reset
- The *goal* (always)
- The *spec* if you have one (always)
- The *failing test* if there is one (often the cleanest seed)
- One or two key file references — not the whole transcript

### What to drop
- The diagnostic detours
- The wrong-path commits (revert them first if the model wrote any)
- The "let me try once more" energy

### Cousin techniques
- **`/compact` at ~70% usage** — softer reset; summarizes the session into a smaller replacement
- **Plan mode reset** — exit plan mode → `/clear` → re-enter with the plan as the seed
- **Worktree split** — for long parallel tracks, give each its own worktree so contexts don't collide
- **Sub-agent fork** — for a research detour, spawn a sub-agent so the main context stays clean

> "If you're correcting the agent more than twice, you're paying for context rot. Reset is cheaper."

---

## Slide 6 — Spec-driven development & plan mode

The structural answer to "agents go off the rails on big tasks."

### The principle
**Move human judgment upstream.** Decisions are cheap when made before code is written, expensive after. Plan mode and specs are how you front-load the judgment.

### Three task sizes, three patterns

| Task size | Pattern |
|---|---|
| **Small** (≤30 min, single file, clear) | One-shot prompt with strong AGENTS.md context. Skip the ceremony. |
| **Medium** (multi-file, well-understood) | Plan mode → review → execute. The 80% case. |
| **Large** (multi-day, ambiguous, cross-cutting) | Full spec-driven flow: spec doc → task breakdown → per-task loop |

### The spec-driven flow (the workshop's core method)

```
┌────────────────────────────────────────────────────────┐
│ 1. SCOPE & ORIENT                                     │
│    What problem? Whose problem? Boundaries?           │
├────────────────────────────────────────────────────────┤
│ 2. GATHER CONTEXT                                     │
│    Read the relevant code, ADRs, similar past work    │
│    (plan mode does this without touching anything)    │
├────────────────────────────────────────────────────────┤
│ 3. SURFACE QUESTIONS                                  │
│    Agent asks; human decides. Resolve before code.    │
├────────────────────────────────────────────────────────┤
│ 4. WRITE THE SPEC                                     │
│    Goals, non-goals, API shape, data shape,           │
│    invariants, error modes, test outline              │
├────────────────────────────────────────────────────────┤
│ 5. BREAK INTO TASKS                                   │
│    Each task: scope, acceptance criteria, deps        │
│    Each task: small enough to fit one clean context   │
├────────────────────────────────────────────────────────┤
│ 6. PER-TASK LOOP (Slide 7)                            │
└────────────────────────────────────────────────────────┘
```

### Why this is also good for the *model*
- Plan mode produces exactly the kind of structured intermediate state that **reasoning models were trained to consume**
- A spec is the kind of artifact post-training rewarded the model for producing
- Per-task scoping matches the agentic loop the model was RL-trained on: clear goal → take steps → verify → done
- A clean per-task context is a fresh prompt-cache prefix — both fast *and* accurate

### Plan mode tactics
- **Always plan-mode first for medium+ tasks.** CC's creator reportedly does this for ~80% of tasks. Trust the data.
- **Read the plan critically.** A plan that says "I'll figure out X during implementation" is a plan that will rabbit-hole. Push back; resolve X now.
- **Distill before exiting.** A 40-step plan is a smell. Either it's too big a task (split it) or the plan needs collapsing.
- **Check it cites real code.** A plan that references made-up function names will produce made-up code.

### Reference
- Use `hone:prd`, `hone:prd-to-tasks`, `hone:run` (your own skill set) for medium-to-large work — that's exactly this loop, automated.

---

## Slide 7 — The per-task execution loop

<!-- CE-EDIT #7 (from context-engineering-presentation slides 22 + 23): wrap loop in 3-Phase / 3-Context frame -->
**Frame first.** Every agent turn lives in one of three phases, each with its own context need:

| Phase | What the agent needs in context | Maps to loop step(s) |
|---|---|---|
| **Reason / Plan** — *what to do?* | Goals, role, task breakdown, memory, metadata, tool selection | 1–5 (scope, prereqs, local context, questions, plan) |
| **Act / Execute** — *how?* | Parameter conversion, multi-tool execution, error handling, initial result processing | 6–7 (safety net, implement) |
| **Observe / Process** — *integrate results* | Extract & integrate results, judging/eval, compress, update memory, decide next loop | 8–11 (test, gates, diff, feedback) |

The 11 steps below are *implementations* of these three phases. Recognising which phase you're in tells you what context the agent actually needs — and what it doesn't.

Same loop, every task, every time. Boring is the point.

```
┌──────────────────────────────────────────────────────────┐
│  PER-TASK LOOP                                           │
│                                                          │
│   1. Determine scope        ← What exactly is "done"?    │
│   2. Verify prerequisites   ← Is the env ready? Deps?    │
│   3. Gather local context   ← Files, types, neighbours   │
│   4. Resolve questions      ← Ask before coding          │
│   5. Plan execution         ← 5–10 step plan, no more    │
│   6. Establish safety net   ← Tests / types / lint       │
│   7. Implement              ← Smallest change that works │
│   8. Run tests              ← Loop until green ─┐        │
│   9. Run quality gates      ← Lint/types/security────┐   │
│  10. Show diff + msg        ← Human reviews         │   │
│  11. Feedback               ← Refine, or commit     │   │
│                                                     │   │
│   ↑──────── loop until all gates green ────────────┘   │
└──────────────────────────────────────────────────────────┘
```

### Notes on each step

1. **Scope** — written in 1–2 sentences. If the agent rephrases it back wrong, fix it now, not later.
2. **Prerequisites** — does the database run? Are env vars set? Has the previous task been merged? Trivial-looking but kills hours when skipped.
3. **Local context** — the *neighbouring* code: types it'll touch, similar patterns elsewhere, the file's existing tests. **Not the whole repo.**
4. **Questions** — the most undervalued step. Encourage the agent to ask. Disable "just try it" instincts in AGENTS.md if needed: *"When unsure, ask before guessing."*
5. **Plan** — a 5–10 step plan that *cites real symbols*. Bigger than that, the task is too big — split.
6. **Safety net first** — the test (or type, or assertion) goes in *before* the implementation when possible. This is TDD, and it's a free latent-space collapse.
7. **Implement** — smallest change that makes the test pass. No drive-by refactors.
8. **Test loop** — run the relevant test, not the whole suite, until green. Then run the broader suite once at the end.
9. **Quality gates** — lint, typecheck, security scan, format. **As hooks, not prose instructions.** Hooks always run; prompt rules sometimes don't.
10. **Diff + commit message** — show the human a unified diff and a draft commit message. *Never auto-commit.* (your CLAUDE.md rule, and the right one)
11. **Feedback** — accept the commit, or refine. If refine: stay in the loop with the *same* fresh task context.

### What the loop buys you
- **Determinism in an indeterministic system.** The model is probabilistic; the loop isn't.
- **Recoverability.** Any step can fail and be retried without losing the whole task.
- **Reviewable units.** Every commit is one task, one diff, one reasoning trail.
- **Cache-friendly.** Each task starts from a clean, similar prefix → high cache hit rate → cheap and fast.
- **Trains *you*.** After 30 of these, you'll know which tasks the agent eats whole and which need spec work.

---

## Slide 8 — Putting it together: the daily rhythm

What this looks like as a practice, not a presentation.

| When | What |
|---|---|
| **Project start** | AGENTS.md, hooks, test/lint commands, key skills committed before any agent work |
| **Each new feature** | Spec → tasks (PR-sized each) → checked into `.plans/` |
| **Each task** | Fresh session → plan mode → spec excerpt → per-task loop → diff → commit |
| **When stuck** | Ralph. Don't reason your way out. |
| **End of day** | Review what landed, update AGENTS.md if a new convention emerged, prune stale plans |
| **End of week** | Look at cache hit rate, token spend, and where the agent struggled most |

### The mindset shift, restated

- **Before**: I write code; AI completes lines.
- **Vibe coding**: I describe; AI builds; I run.
- **Agentic engineering**: I spec, I gate, I review; AI does the work; *the system* — practices, tests, hooks, AGENTS.md, the loop — is what makes it production-grade.

The model gets better every six months. The *system* is what you build.

---

## Optional callouts to weave in

- **Kent Beck — "augmented coding"** as the term for this middle ground (better than "vibe coding" for production)
- **Kevlin Henney — tests as specifications**: never more true than now
- **Dan North — Deliberate Discovery**: the spec/plan phase *is* the discovery; the implementation is the cheap part
- **Grady Booch — third golden age of software**: the practices persist; the leverage is new
- **Karpathy retiring "vibe coding"** for serious work: even the inventor moved on

---

## Sources & further reading

- [Anthropic — Claude Code best practices (CLAUDE.md, hooks, plan mode)](https://code.claude.com/docs/en/best-practices)
- [augmentcode.com — How to write good AGENTS.md files](https://www.augmentcode.com/blog/how-to-write-good-agents-dot-md-files)
- [claude.md — community CLAUDE.md examples](https://claude.md/)
- [Plan Mode guide — when and how (2026)](https://www.claudedirectory.org/blog/claude-code-plan-mode-guide)
- [SmartScope — hooks, subagents, context (advanced 2026)](https://smartscope.blog/en/generative-ai/claude/claude-code-best-practices-advanced-2026/)
- [Shrivu Shankar — How I use every Claude Code feature](https://blog.sshh.io/p/how-i-use-every-claude-code-feature)
- [Mustafa Morbel — Taming Claude Code: CLAUDE.md and Hooks](https://medium.com/becoming-for-better/taming-claude-code-a-guide-to-claude-md-and-hooks-ed059879991c)
- Dan North on Deliberate Discovery (search: "Dan North deliberate discovery")
- Kent Beck — "augmented coding" Substack posts (late 2025–2026)
- *Internal*: `agentic-engineering/../claude-code/findings.md` (memory + dream consolidation as a case study in the loop applied to the harness itself)
- *Internal skills*: `hone:prd`, `hone:prd-to-tasks`, `hone:run` — your own implementation of the spec-driven flow

---

## Open questions for me to decide before tomorrow

- [ ] Slide 7 (per-task loop) is the most important one. Show as a static graphic, or walk through it in a live demo on a tiny task? **Lean: live demo on a 5-min task — shows it's not theoretical.**
- [ ] How explicit do I get about "the model was RL-trained on this exact loop shape"? Engineers love it; it's the kind of "aha" that wins skeptics. But it risks getting too inside-baseball. **Lean: one sentence on Slide 3, don't dwell.**
- [ ] Should I introduce `hone` here or hold for the deep-dive's own-experience portion? **Lean: name-drop on Slide 8, demo in own-experience.**
- [ ] AGENTS.md template on a slide vs in a handout. Slide 4 currently has it inline — long for a slide. **Maybe: slide shows the section headings; full template in a printed/QR-linked handout.**
- [ ] Slide 2 (challenges) — be careful not to lose 5 minutes here. Skeptics will want to engage. Hard time-box: 3 minutes max.
