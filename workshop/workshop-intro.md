# Workshop Intro — From Vibe Coding to Agentic Engineering

**Block**: Intro / background / state of the art
**Duration**: 30–45 min (target 35; flex to 45 if discussion runs)
**Audience**: experienced engineers, team leads — many will be skeptical, several already burned by hype
**Goal**: meet them where they are, give a shared map of how we got here, set up the rest of the workshop without lecturing

---

## Slide 0 — Title & framing (1 min)

> **From Vibe Coding to Agentic Engineering**
> *A tool, a shift, a craft.*

One sentence to set tone:
> "The goal today isn't to convince you AI will write all your code. It's to give you the same operating mental model and muscle memory I use, so you can decide for yourselves what's real and what's hype."

---

## Slide 1 — Hand-raisers (3–4 min)

Goal: read the room, make people active in the first 60 seconds, surface the skeptical voices early so we can address them.

Ask the room (literal hands up, no slides full of text):

1. **"Who first used an LLM to help with code before mid-2024?"** *(separates the early adopters from the rest — usually a third of the room)*
2. **"Who used an agentic harness — Claude Code, Codex, Cursor agent mode, opencode, Aider — in the last 7 days?"** *(real signal of who's currently in the loop)*
3. **"Who has shipped something to production this year where an agent wrote the majority of the code?"** *(the real bar — usually fewer hands than expected)*
4. **"Who has had an agent silently break something and wished they'd never started?"** *(invites the skeptics to speak — make this safe to admit)*

Optional 5th if the room is quiet:
> "What's the project type — quick task, greenfield, OSS contribution, legacy refactor?"

Note for me: don't rush past the 4th question. If hands go up, name one or two of those experiences explicitly later in the talk. Skeptics in the room are the workshop's best signal.

---

## Slide 2 — Why are we doing this? (3 min)

**Core message**: SWE agents are a *tool*, like IDEs, refactoring, TDD, CI/CD, linters. Each of those required a mindset shift; this one is bigger because the leverage is bigger.

Two frames side by side:

| Tool | What it changed |
|---|---|
| IDE / refactoring | Code became malleable — rename without fear |
| Testing / TDD | Behavior became a contract, not a wish |
| CI/CD | Shipping became continuous, not ceremonial |
| Linters / type systems | Errors moved left, before runtime |
| **SWE agents** | **Intent → working code in hours, not weeks** |

Then the Simon Willison quote (paraphrased — verify exact wording):
> "I used to dread starting a project in a language I didn't know. Now I just start. The cost of trying has collapsed."
> — Simon Willison

What's different about this one:
- The **leverage** is order-of-magnitude bigger than any prior tool
- The **failure mode** is also new: confidently wrong, plausibly wrong, fast
- The **mindset shift** is not "learn the tool" — it's "learn to delegate, review, and steer"

Why the room should care: **the engineers who treat this seriously now will be the ones writing the playbooks the rest of the industry uses next year.** Not because of FOMO — because nobody else has the experience yet to do it well.

---

## Slide 3 — A quick history (the spine of the talk) — 8–12 min

Four phases. For each: a date, what enabled it, what it changed in *practice*, one quote, one thing that broke.

### Phase 1 — Completion (2021–2024): "saving keystrokes"

- **Started**: GitHub Copilot, technical preview June 2021, GA June 2022
- **What it was**: in-IDE autocomplete on steroids, single-file context, line-to-block completions
- **What it enabled**: shaved 20–30% off boilerplate, made unfamiliar APIs discoverable
- **Mindset**: "AI as smarter IntelliSense" — engineer still in the driver's seat at every line
- **What broke**: subtly wrong completions that compiled but were wrong; copyright noise; the "hallucinated import" meme
- **Quote candidate** (Simon Willison, ~2023):
> "Copilot is the most useful tool I've adopted in a decade. It's also the most likely to lie to me. Both things are true."
> *(verify exact wording — Simon writes about this regularly)*

### Phase 2 — Vibe coding (early/mid 2025): "give in to the vibes"

- **The moment**: Andrej Karpathy's tweet, **2 February 2025**
> "There's a new kind of coding I call 'vibe coding,' where you fully give in to the vibes, embrace exponentials, and forget that the code even exists."
> — Andrej Karpathy, Feb 2 2025
- **What enabled it**: Sonnet 3.5/3.7 strong enough to one-shot small apps; Cursor/Copilot Chat in the IDE; ChatGPT desktop with code execution
- **What it enabled**: democratization of greenfield app dev — designers, PMs, scientists shipping working tools without engineers
- **Mindset**: "describe, accept, run" — code becomes throwaway, the prompt is the artifact
- **What broke**: production. Anything that needed maintenance, security, integration, multi-user concurrency, or compliance.
- **Important nuance for this room**: vibe coding is genuinely valuable — for prototypes, for learning a new framework, for the first 80% of a tool you'll throw away in a week. The mistake is treating it as an SDLC.
- **Karpathy himself retired the term for serious work** in early 2026 — gives the vocabulary shift authority from its inventor.
<!-- CE-EDIT #1 (from context-engineering-presentation slide 5): the June 2025 follow-up that bracketed the year -->
- **The bracketing tweet** — June 18 2025, also Karpathy: *"+1 for 'context engineering' over 'prompt engineering'. Context engineering is the delicate art and science of filling the context window with just the right information for the next step."* The Feb tweet said "forget the code"; the June tweet said "obsess over what's *around* the code." Together they set up Phase 4.

### Phase 3 — Agent harnesses (summer–fall 2025): "the model gets a shell"

- **Trigger**: models cross the threshold where multi-step tool use becomes reliable
- **The wave**: Claude Code (Feb 2025 research preview, GA later), OpenAI Codex (relaunch May 2025), Cursor agent mode, opencode, Aider, Cline, Roo
- **What changed**: the model now has a filesystem, a shell, and a loop. It can read, edit, run, test, iterate — without a human between every step
- **What it enabled**: the engineer becomes the *director*, not the typist. Tasks that took a week now take an afternoon
- **Mindset shift**: from "AI helps me write code" to "AI does the work, I review and steer"
- **Quote candidate** (Anthropic / Boris Cherny, on the Claude Code design philosophy):
> "Treat the code as the source of truth. The model is good at Linux tools because they've been around a long time. Push everything into the model."
> *(paraphrased from CC podcast — verify before using)*
- **What broke**: context windows, token budgets, agents going off the rails on long tasks, "ralphing" behavior, silent test deletion. New craft was needed.

### Phase 4 — Agentic engineering (Dec 2025 → now): "engineering, just with new teammates"

- **Trigger**: Sonnet 4.5 / Opus 4.5 (late 2025), Opus 4.6/4.7 (early 2026) — reasoning models that plan, self-correct, hold longer arcs
- **What changed**: agents are now reliable enough that the *practices around them* — spec-driven development, TDD, code review, architecture, testing pyramids — start to matter again. The old practices weren't wrong. They were just unreachable when each line cost you keystrokes.
- **The realization**: good software design was never for the machine. It was always for *other humans* who had to read, maintain, and extend the code. Now LLM agents are another kind of teammate that reads the same code, the same docs, the same tests — and benefits from the same clarity.
- **Mindset shift**: from "vibe coding faster" to **engineering, with a new kind of collaborator**
- **Quote candidate** (Addy Osmani, Google, late 2025):
> "Vibe coding is a suitcase term. Pack it carefully — for prototypes, fine. For production, you need spec-driven development."
> *(verify wording — Addy's been writing on this regularly)*
- **What's still breaking**: cognitive load on the human (review fatigue), responsibility boundaries (the Amazon Q incident), trust calibration, team coordination when half the PRs are agent-authored

---

## Slide 3.5 — What this looks like in the data (1 min)

Before *why* coding is so good for LLMs — quick look at *how much* the field has grown in the last 12–24 months. The numbers are larger than most engineers realise.

**GitHub — the agent tsunami:**

| Metric | 2023 | 2025 | 2026 |
|---|---|---|---|
| Commits/week | — | ~20M | **275M** (April 2026) |
| Annual commits | — | 1B (full year) | **~14B projected** |
| AI agent PRs opened | — | ~4M (Sep 2025) | **17M+** (March 2026) |
| Actions compute min/week | 500M | 1B | **2.1B** |

That's **14× annual commit volume in one year**. AI-agent PRs **4×'d in 6 months** (Sep 2025 → March 2026). GitHub itself has reported **repeated outages and performance degradation** from AI-driven traffic — servers built for human-scale usage can't handle agent-scale, forcing crisis-mode capacity work. *(Source: GitHub disclosures + analysis at quasa.io, April 2026.)*

**Beyond GitHub:**
- **Language shift**: in **August 2025, TypeScript overtook Python and JavaScript** as the most-used language on GitHub — the largest ranking shift in over a decade, attributed to AI-assisted full-stack work.
- **Neon (serverless Postgres)**: from **~20K databases in 2023 to 700K+ by April 2024**, with **~80% of new databases created by AI agents** — often one per task, per branch, per session. "Ephemeral, programmatically-created databases at scale" isn't a phrase anymore; it's the default workload.
- **Supabase, Railway, Render, Fly.io, Vercel** — all reporting agent-driven creation patterns and reshaping pricing for ephemeral / spawned-by-agent workloads.
- **The Dec 2025 → 2026 inflection.** Growth that was already record-breaking *accelerated again* once Sonnet 4.5/Opus 4.5 + the new harness wave (CC GA, Codex+GPT-5.5, Antigravity, Cursor 3) shipped. The Feb 2026 multi-agent wave (Grok Build, Windsurf, Codex Agents SDK, Devin parallel, Antigravity Manager) added a *second* growth engine: parallel agents per developer.

The point: **the cost of *trying* a software idea has collapsed** — Simon's "no longer afraid of starting" — and the *infrastructure layer* is reshaping itself around that fact. New databases per second, fresh worktrees per task, ephemeral preview environments per PR. We're not in a tooling wave; we're in an infrastructure wave that tooling triggered.

[VERIFY numbers before quoting verbatim — they grow quarterly.]

---

## Slide 4 — Why is coding such a good domain for LLMs? (3–4 min)

The short answer: **coding is the perfect RL playground.**

Five properties that make code uniquely well-suited:

1. **Verifiable** — does it compile? do the tests pass? does the type check? Unlike prose, code has a *ground truth* the model can check itself against.
2. **Reasoning surface** — code forces explicit causality. The model can't hand-wave; it has to commit to a structure.
3. **Tight RL loop** — generate → run → observe → correct. The training signal is dense and cheap, which is why coding capability has improved faster than almost any other domain.
4. **Tools are universal and ancient** — the shell, grep, find, git, make. The model has read every man page and every Stack Overflow answer about them. Linux is the lingua franca, and it doesn't change much.
5. **Clear goals** — "tests pass, lint clean, feature works." Most other domains don't have this.
<!-- CE-EDIT #2 (from context-engineering-presentation slide 6): "Test Time > Train Time" -->
6. **Test time > train time** — most of an agent's value comes from its task-time *reasoning and tool use*, not from baked-in knowledge. The model's training is a foundation; the *context* is where the work happens. That's why context engineering pays off, and why the practices we're about to discuss matter.

Plus a sixth, more philosophical one worth mentioning:
6. **The training data is the artifact** — code on GitHub *is* the thing the model is producing. Unlike, say, medicine or law, there's no gap between what the model learned from and what it's asked to make.

> "Code is the universal interface."
> — *(common Anthropic / Claude Code framing — verify attribution)*

This is also why the **agentic loop** works for code in a way it doesn't yet for, say, design or research: the safety net is built in. Tests catch most regressions. Lint catches most style drift. Type checks catch most contract violations. The model can fail fast and recover — exactly the conditions under which RL training works.

---

## Slide 5 — So where does that leave us today? (2 min) — bridge into the rest of the workshop

Three honest claims:

1. **Vibe coding is real and useful** — for prototypes, learning, throwaway tools, democratization. Don't dismiss it.
2. **Agentic engineering is the next phase for production work** — and it brings the old engineering disciplines back, not as overhead, but as the way agents stay useful.
3. **The craft is new and undocumented** — we're all figuring it out. That's why we're here.

What we'll do for the rest of today:
- Hands-on with a small build (Exercise 1) — to feel what the loop is like *now*, in 2026
- Deep dive into the craft — agents.md, claude.md, ralphing, context, plan mode, the things that turn "agent demos" into "agent workflow"
- Hands-on with something harder (Exercise 2) — bug fix, new feature, or unfamiliar language
- Q&A — especially the things that broke for you, that you wish someone would explain

Closing line for the intro:
> "I'm not here to sell you anything. I'm here because I've been doing this every day for a year, and the practices are real enough now to share."

---

## Quote bank — for me to pick from

Mark each as **[VERIFY]** before using on a slide. Quotes change meaning when paraphrased.

**Karpathy**:
- Feb 2 2025 vibe coding tweet: "give in to the vibes, embrace exponentials, forget that the code even exists" — well-attested, screenshot widely available
- Early 2026 retirement of the term for serious work — verify exact source

**Simon Willison** (his blog at simonwillison.net is the canonical source — most quotes are direct from there):
- "no longer afraid to start projects in unfamiliar languages" — paraphrase, find exact post
- His agentic-engineering tag: https://simonwillison.net/tags/agentic-engineering/
- "Coding agents are the most exciting development in our field in years" — verify

**Anthropic / Claude Code team**:
- Boris Cherny on CC design philosophy — from podcast appearances, paraphrase carefully
- "Code is the source of truth" — common CC framing, verify a primary source

**swyx (Shawn Wang)**:
- "AI Engineer" framing — coined the term, has written extensively
- Latent Space podcast on the rise of agentic harnesses — pull a clean quote

**Addy Osmani** (Google):
- "Suitcase term" critique of vibe coding — late 2025 blog posts
- Spec-driven development as the production answer

**Steve Yegge / Gergely Orosz / others**: rich material but all need verification before use on a slide.

**For the skeptic camp** (use one in the timeline to show I'm not selling):
- Dan North on deliberate discovery — relevant but no public AI position yet
- Kent Beck "unpredictable genie" — Substack, late 2025
- Grady Booch "third golden age" + the Amodei pushback

---

## Timing budget

| Slide | Min | Cumulative |
|---|---|---|
| 0 — Title & framing | 1 | 1 |
| 1 — Hand-raisers | 4 | 5 |
| 2 — Why we're doing this | 3 | 8 |
| 3 — History (4 phases × ~2.5 min) | 11 | 19 |
| 4 — Why coding is good for LLMs | 4 | 23 |
| 5 — Bridge to rest of workshop | 2 | 25 |

Lands at ~25 min, leaving 5–10 min headroom for questions, asides, and the discussion the hand-raisers will spark. If running long, **cut Phase 1 (completion era) hardest** — most of the room lived through it, doesn't need much air.

---

## Open questions for me to decide before tomorrow

- [ ] Which 2 quotes go on actual slides (vs. the ones I just paraphrase)? Verify wording before printing.
- [ ] Do I want a slide showing the *capability* progression (a mini timeline image) or talk it through?
- [ ] Hand-raiser #4 — am I willing to genuinely engage with whatever skeptic story comes back, or skip it if the room feels closed?
- [ ] Do I open with a 30-second personal demo (e.g. show Claude Code editing a file live) before Slide 0, to set the "this is a working tool" tone?
