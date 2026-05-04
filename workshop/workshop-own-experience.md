# Workshop — Own Experience: 6 Modes of Working with Agents

**Block**: Deep dive — own experience portion (live demos)
**Duration**: 10–15 min, ~2 min per slide + demo
**Position**: Closes the deep-dive block before Exercise 2
**Format**: 1 slide per mode, sparse text — all the substance is in the live demo. Each slide is a *cue card* for me, not a presentation in itself.

---

## Framing line

> "These are the six shapes of work I've found agentic engineering changes most. I'm going to show you one of each — what I tried, what worked, what I'd do differently. The artifacts are real; the mistakes are mine."

Order is roughly **simple → complex** so the room can calibrate. Cut one or two if time is tight (suggested cut order: 2, then 5 — keep 1, 3, 4, 6).

---

## Slide 1 — Research & generating learning content

**The shape of the work**: I want to learn (or teach) a topic. Agent reads sources, synthesizes, drafts a course/notes/exercises.

**Examples to demo**:
- **Sather-K** — Sather language revival course
- **vibe-haskell** — Haskell from a working-engineer's POV
- **Elixir course** materials (PDFs in `~/Downloads`: Nerves, OTP, Phoenix, GraphQL/Absinthe, metaprogramming, genetic algorithms)

**What works well**:
- Agent is an *infinite-patience* tutor — happy to re-explain, adjust the level, work through one more example
- Great at producing *first* drafts of explanations and worked examples
- Extracts structure from messy source material (PDFs, papers, scattered docs) very well
- Honest about what it doesn't know if you ask it to be — and will go read

**What doesn't / watch out for**:
- Confident hallucination on **niche languages and historical facts** (Sather is a perfect example — half the "history" is plausible-sounding fiction)
- Drifts toward generic introductions; needs nudging to keep depth
- Will pad. Aggressively. Cut 30–50% of every output.
- Bad at *taste* — what makes Haskell *feel* like Haskell, not Python with weird syntax

**Demo move** (60 sec): show one course chapter that landed well + one paragraph I had to throw out (and why I caught it).

**Lesson for the room**: this is the *safest* mode to start in. No production stakes. Great way to calibrate trust.

---

## Slide 2 — Content generation (skills, kickoffs, scaffolds)

**The shape of the work**: I have a clear template / shape. Agent fills it in across many instances.

**Examples to demo**:
- **neo4j-skills** — generating Claude skills for Neo4j workflows (Cypher patterns, schema authoring, ingest pipelines, etc.)
- **neo4j-agent-integrations** — kickoff scaffolds for agent + Neo4j combos
- The **agent-skills.ai** entries I've contributed
- The skill files in `~/Downloads/` (excalidraw, neo4j-pptx-generation, cloud-architecture-diagrammer)

**What works well**:
- Once *one* skill is written well and you've shown the agent why each section exists, generating the next 10 is fast and consistent
- Agent picks up your house style and applies it consistently — better than I do, honestly
- Catches inconsistencies across the set ("you call it `nodes` here and `entities` there")

**What doesn't / watch out for**:
- The first one is the hard one. If you generate it sloppily and use it as the template, every subsequent one is sloppy.
- "Plausible but generic" is the failure mode — skills that look right but produce bland output
- Needs a real test (run the skill, see what it generates) before declaring done — don't trust the *artifact*, trust the *behavior*

**Demo move** (60 sec): show two neo4j-skills side by side, point at the consistency, then run one to show the actual output.

**Lesson for the room**: invest 10x in the first instance. The rest is leverage.

---

## Slide 3 — Research & insights on a codebase

**The shape of the work**: I want to understand a system I didn't write. Agent explores, takes notes, structures findings.

**Examples to demo**:
- **claude-code source analysis** (the `~/d/llm/claude-code/` work — `architecture.md`, `findings.md`, `tools.md`) — entire CC codebase mapped via public source analysis
- **cocoindex** — incremental indexing system analysis
- *(swap in another large public codebase you've explored if either of the above doesn't fit)*

**What works well**:
- This is where agents are *transformatively* better than humans. A 700-file codebase analyzed in an evening.
- Pattern: `<topic>-findings.md` (raw) → `<topic>-analysis.md` (structured) → `<topic>-summary.md` (executive). Append-only findings, then distill.
- Surfaces things you'd never find by reading — codenames, feature gates, evolutionary signals (e.g. "TodoWriteTool marked Legacy", "ExitPlanModeV2 implies V1 was insufficient")
- Excellent at building a graph of *what calls what* — entry points, layering, hotspots

**What doesn't / watch out for**:
- Will confidently misattribute things across files (check the citations)
- "Found X" sometimes means "found a string that looks like X" — verify before basing decisions on it
- Bigger codebases need sub-agent fan-out, otherwise you blow the context budget

**Demo move** (90 sec): open `architecture.md`, scroll through the layered diagram + the design-decisions section, show how it was generated incrementally and how I'd verify a claim.

**Lesson for the room**: this is a 10x mode. Use it the next time you join a new team or evaluate a library. The findings file is durable; the agent is throwaway.

---

## Slide 4 — Simple greenfield tools

**The shape of the work**: I want a small useful thing. ~1 day, single-purpose, mostly mine.

**Examples to demo**:
- **openalex-neo4j** — OpenAlex (academic graph) integration into Neo4j
- **neo4j multi-db file** — `MultiDB FAQ.pdf` and the related tooling
- **clauditopia** — small Claude-related utility
- **agent-skills.ai** entries

**What works well**:
- This is what Karpathy meant — and what Simon Willison meant when he wrote about *"shipping projects I wouldn't have been able to justify spending time on"* ([Mar 2025](https://simonwillison.net/2025/Mar/11/using-llms-for-code/))
- Cost of *trying* an idea has collapsed. From 4 hours to 30 minutes for a working v0.
- Agent handles the boring parts (CLI parsing, error handling, basic tests, README) so I can focus on the interesting part
- New language? Fine — agent knows them all. Pick the right one for the problem, not the one I happen to know.

**What doesn't / watch out for**:
- Easy to ship something that *works for the demo* and breaks in week 2 (no error handling for the long tail, no observability, no graceful upgrades)
- The "looks done" trap is strongest here — small enough that no one reviews, big enough to break
- Don't skip AGENTS.md just because it's small — even a 20-line one keeps the agent on rails

**Demo move** (60 sec): show openalex-neo4j or clauditopia working end-to-end, then point at the AGENTS.md that kept it on track.

**Lesson for the room**: the smaller the project, the more *value* per hour you'll get from agents. This is your gateway drug.

---

## Slide 5 — OSS contributions

**The shape of the work**: someone else's codebase, their conventions, their review bar. I'm a guest.

**Examples to demo**:
- **inferrs** — Rust inference utilities, OSS contribution
- **aura-cli** (agents) — Neo4j Aura CLI agent integration
- Other PRs into Neo4j ecosystem projects

**What works well**:
- Agent reads the project conventions from `CONTRIBUTING.md`, existing PRs, lint config, *better than I do under time pressure*
- Lowers the activation energy of contributing — I can poke at a Rust project without being a Rust expert
- Test-first works *especially* well here — match the project's test style first, then implement
- Faster turnaround on review feedback (agent applies the change, I check)

**What doesn't / watch out for**:
- Agent has no idea about the project's *political* context (recent rewrites, contested decisions, in-flight refactors). Read the issue tracker yourself first.
- Will sometimes "improve" things outside the scope of the PR. **Lock the scope hard.** Reviewers hate scope creep, especially from drive-by contributors.
- Generated commit messages are too long/AI-flavored by default — strip back to the project's style
- Be honest in the PR description — don't pretend humans wrote what agents wrote, but also don't make a song and dance

**Demo move** (60 sec): show one merged PR, point at the scope discipline; show the AGENTS.md or CLAUDE.md that I added locally to enforce the project's style.

**Lesson for the room**: OSS is a great calibration ground. Real reviewers will tell you when the agent's output isn't good enough — and you'll learn faster than from any blog post.

---

## Slide 6 — Larger greenfield projects

**The shape of the work**: real project, multi-week, real architecture decisions, real users. The full agentic-engineering loop applies.

**Examples to demo**:
- **agent-intelligence** — the larger system in `~/d/llm/agent-intelligence/`
- **Cypher authoring skills** in **neo4j-skills** — non-trivial multi-file skill set
- **aura-agent-memory-gateway** — memory infrastructure for Aura agents
<!-- CE-EDIT #13 (from context-engineering-presentation slide 33): create-context-graph.dev as a larger-greenfield demo option -->
- **create-context-graph.dev** — "AI agents with graph memory, scaffolded in seconds." Pick your domain, pick your framework, get a full-stack app with streaming chat, graph visualization, and decision tracing. Strong demo of the "agent + graph memory" thread that bridges into the keynote's neo4j touch.

**What works well**:
- *Everything from the previous sections* compounds. AGENTS.md, hooks, plan mode, ralphing, spec-driven, the per-task loop — all of it pays off here.
- Sub-agent fan-out for research and parallel implementation
- The discipline of "spec → tasks → per-task loop → diff → commit" produces a *cleaner* git history than I'd produce by hand. Each commit is one task.
- Agent's tireless willingness to write tests means coverage is genuinely higher than my human-only projects

**What doesn't / watch out for**:
- **Architecture decisions are still mine.** Agents confidently propose architectures that look good and are subtly wrong (wrong service boundaries, wrong consistency model, wrong trust boundary). Treat AI architecture suggestions as *one engineer's opinion* — a junior one.
- Without spec discipline, large projects rot fast. The bigger the project, the higher the cost of skipping the spec phase.
- Review fatigue is real on big projects. I now schedule "review-only" sessions where I don't accept any agent work, just read what's been done.
- Cache hit rate matters. A loose AGENTS.md and a churning system prompt can quietly cost 10x more than a disciplined setup.

**Demo move** (2 min): open agent-intelligence, walk through one feature from `.plans/` (spec → tasks → commit log → tests), show the AGENTS.md, then a hook firing. The "this is what the loop looks like at scale" demo.

**Lesson for the room**: this is what the workshop has been preparing you for. *Everything* in the prior sections is just sub-machinery for running this loop on real work.

---

## Closing slide / transition (30 sec)

> "Six modes, same toolbox. The mistakes are real and yours to make. Now you're going to make some — that's Exercise 2."

---

## Demo logistics — checklist for me

- [ ] Have terminals pre-opened in the right directories (one per demo, not switching mid-flow)
- [ ] AGENTS.md / CLAUDE.md files visible in each — point at them as part of the demo
- [ ] Pre-cleared session per demo (don't surprise myself with stale context mid-talk)
- [ ] Have *one* failure ready to show per category — credibility comes from showing the warts
- [ ] Backup screenshots / saved transcripts for any demo that depends on network or API state
- [ ] Time-box per demo — 90 sec for the simple ones, 2 min max for agent-intelligence

## Open questions for me to decide before tomorrow

- [ ] Cut from 6 to 4 if time is tight? **Lean: keep all 6 if I can budget 12 min; otherwise drop slides 2 and 5 (content generation + OSS).**
- [ ] For each slide, which is the *one* artifact I demo? **TODO: pick one per slide tonight.**
- [ ] Show a failure per slide, or only one or two failures total? **Lean: at least one failure per category — keeps me honest, builds trust.**
- [ ] If revisiting Slide 3, decide whether to demo claude-code analysis only, or pair with cocoindex / another large codebase you've recently explored.
