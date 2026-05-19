# Agentic Engineering: Weekly Blog Series
_Draft outline — 12 posts, weekly cadence_

**Series thesis:** Agentic engineering is professional software development with AI coding agents — where the human remains accountable for outcomes while agents do the implementation work. The series walks engineers from "I've heard the term" to "I've built the practices."

**Target reader:** Experienced engineer or tech lead who has used AI coding tools but hasn't systematized their approach. Skeptical of hype. Wants practical, specific guidance.

**Tone:** Tight, opinionated, claim-first. No "in today's rapidly evolving landscape." Lead with the argument, then prove it.

---

## Post 1 — "What Is Agentic Engineering?" (Week 1)

**Thesis:** Vibe coding and agentic engineering are not the same thing — and confusing them produces disasters.

**Outline:**
- The four-phase history in 500 words (completion → vibe coding → harnesses → agentic engineering)
- The key distinction: vibe coding is describe-accept-run, code is throwaway. Agentic engineering is spec-driven, the human is accountable, the agent is a tool not a miracle.
- Simon Willison's honest confession: "those things have started to blur for me already. Which is quite upsetting." — why this matters
- The normalization of deviance problem
- The question: "do you know where you are on the spectrum, and does your practice match what you're building?"

**Close:** A 5-question self-assessment: are you vibe coding, augmented coding, or doing agentic engineering?

---

## Post 2 — "The Navigator Role: Why Your Judgment Got More Valuable" (Week 2)

**Thesis:** The human's role in agentic engineering is navigator, not driver — and navigating is harder and more valuable than driving.

**Outline:**
- The classic pair programming model and its inversion with AI
- Kent Beck: "I make more consequential programming decisions per hour, fewer boring vanilla decisions"
- What navigating actually looks like: setting direction, catching drift, defining "done"
- TDD as the navigator's pacing mechanism: one failing test = one bounded spec = one bounded agent task
- The Saarland study: humans question AI less than they'd question a human pair partner — and this is dangerous
- Practical: how to structure a working session as a navigator (briefing → bounded task → review → retrospective)

---

## Post 3 — "Write the Spec First: The Practices That Prevent Rabbit-Holes" (Week 3)

**Thesis:** The most important skill in agentic engineering is writing a good spec — because bad specs produce bad code at scale, instantly.

**Outline:**
- PRD vs. task: the difference matters (PRD = goals + non-goals + API shape + test outline; task = acceptance criteria for one bounded change)
- The waterfall trap: spec → code is waterfall. Spec → tasks → agent loop is not.
- Right level of detail: enough to define "done," not enough to prescribe "how"
- Ryan Lopopolo / OpenAI Frontier: "Ship a spec, not code" — 1M LOC, 3 engineers, zero human-written code
- Plan mode → review → execute: resolve questions before code is written, that's when decisions are cheap
- What makes a spec bad (list): decisions deferred to implementation, "I'll figure out X later," missing non-goals
- Template: a minimal spec structure that works with any agentic tool

---

## Post 4 — "Context Engineering: What You Feed the Agent Is the Product" (Week 4)

**Thesis:** The quality of your agent's output is determined by the quality of what you put in the context window — and this is an engineering discipline.

**Outline:**
- Karpathy: "Context engineering — the delicate art and science of filling the context window with just the right information for the next step."
- The three layers: global (CLAUDE.md / global instructions) → project (AGENTS.md) → task (the spec)
- AGENTS.md as the team handbook: what every fresh session inherits, what the "new hire" needs to know
- What goes in AGENTS.md: build/test/lint commands, repo structure, conventions, off-limits files, quality bar
- GitLab's principle: "Repo is the single source of truth." Architecture decisions belong in the repo, not in Slack.
- Context rot: what happens when context fills up, and the ralphing fix

---

## Post 5 — "TDD Is the Strongest Form of Prompt Engineering" (Week 5)

**Thesis:** The practice that sounds most counter-intuitive to AI-accelerated teams is the one that makes AI most reliable.

**Outline:**
- Why tests work so well with agents: a failing test is a *precise, machine-readable specification* the model was post-trained on exactly that signal
- What happens without tests: agents cheerfully delete tests to make them pass
- The red/green contract: human writes the failing test (spec), agent drives to green (implementation), human steers refactor (judgment)
- Kent Beck TDD with agents: the system prompt that enforces one-test-at-a-time discipline
- "Characterization tests": using agents to capture existing behavior before refactoring — the safe way to add test coverage to legacy code
- GitLab's principle: "Failing test before every feature. The test defines 'done' for the agent."
- The TW retreat finding: "TDD is the strongest form of prompt engineering"

---

## Post 6 — "Ralphing: Context Rot and the Fix" (Week 6)

**Thesis:** Context rot is real, predictable, and has a clean fix — the hardest part is accepting that the fix requires discipline, not cleverness.

**Outline:**
- Context rot explained: token accumulation, poisoned context from failed attempts, goal drift
- Signs you need to ralph: correcting the same mistake twice, seeing the agent drift from the spec, output quality degrading mid-session
- Geoffrey Huntley and the Ralph Wiggum origin: `while :; do cat PROMPT.md | claude-code ; done`
- What ralph preserves vs. what it wipes: filesystem persistent, context wiped
- The tattooed ralph extension: immutable ground truth + accumulated scars across resets
- The Y Combinator overnight story: 1,100 commits across 6 repos — the Browser Use library ported to TypeScript
- Semantic diffusion warning: what ralphing actually means vs. what YouTube will tell you it means

---

## Post 7 — "Constraints Are Multipliers: Building the Harness" (Week 7)

**Thesis:** One CI gate catches more bugs than a thousand lines of prompt instructions. The harness is the product, not the prompts.

**Outline:**
- GitLab's principle: "Constraints are multipliers." "Prompts are suggestions. CI is a gate."
- The three components of a harness: constraints (CI), context (AGENTS.md + docs), garbage collection (automated maintenance)
- What constraints to start with: lint, typecheck, test count guard, secret detection
- GitLab's 5 autonomy levels: baseline → pair → conductor → orchestrator → harness
- Why you can't skip levels: skipping to level 4-5 without infrastructure amplifies technical debt
- Ryan Lopopolo's inner loop constraint: builds must complete in under 1 minute. If they don't, decompose until they do. Ratchet discipline.
- The maturity grid: four dimensions (CI, context, testing, review) — where to start

---

## Post 8 — "The Middle Loop: Supervisory Engineering" (Week 8)

**Thesis:** There's a named gap between the inner loop (write/test/debug) and the outer loop (CI/CD/deploy) — and this is where experienced engineers have the structural advantage.

**Outline:**
- Three loops: inner (agent), middle (supervisory engineering), outer (CI/CD)
- What the middle loop looks like in practice: direct, evaluate, fix, decompose, re-run
- Why this is where experience matters: knowing what "done" looks like, knowing when a plausible result is wrong
- The hone-ai model: PRD → tasks → Implement agent → Review agent → Finalize + commit. Fresh context per task.
- Decision fatigue as the bottleneck (TW retreat): agents produce work faster than leaders can approve it
- Jevons Paradox: AI makes output cheaper; demand expands; but human judgment doesn't scale
- Building cognitive sustainability: 3-4 focused hours, navigator discipline, reserve peak hours for decisions

---

## Post 9 — "Where Does Rigor Go? The Five Destinations" (Week 9)

**Thesis:** Engineering discipline doesn't disappear when AI writes the code — it migrates. Knowing where it goes is the job.

**Outline:**
- The TW retreat question: "If AI handles the code, where does the engineering go?" — nobody had the same answer; everybody agreed the question was urgent
- Five destinations: specs, tests, constraints, risk tiering, continuous comprehension
- Risk tiering in detail: the table (internal one-user → external auth+data → safety-critical) — is your verification proportional to blast radius?
- James Shore's maintenance math: 2× output × constant maintenance cost = 2× debt. The math only works if maintenance costs don't grow with output.
- The good-design insight: what made code readable for colleagues makes it navigable for agents. For exactly the same reason.
- Continuous comprehension: code review was doing four things at once, each needs a new home

---

## Post 10 — "Managing Agents: The Management Skills Engineers Refused to Learn" (Week 10)

**Thesis:** The skill most required for agentic engineering is the one most engineers explicitly decided not to develop.

**Outline:**
- Claire Vo: "I have 20 years of management experience. I know how to make an employee successful. That is what you need to make these agents work."
- The four management skills: role scoping, onboarding (AGENTS.md), trust calibration, feedback loops
- The irony: engineers who spent careers avoiding management now need it most
- AGENTS.md as onboarding doc: treat your agent like a sharp new hire who has read every public repo but never met your team
- Trust calibration in practice: where does the agent earn more latitude? Where do you verify tightly?
- Feedback loops that persist: corrections that improve future work, not just fix the current task. What's in AGENTS.md after this task?
- The good news: if you've ever mentored a junior — you already have the muscle.

---

## Post 11 — "Agent-Enabled Reversibility: Technology Choices Become Experiments" (Week 11)

**Thesis:** The most underrated change in the agentic era isn't faster development — it's the collapse of architectural lock-in.

**Outline:**
- Mitchell Hashimoto: "Programming languages used to be LOCK IN, and they're increasingly not so."
- The evidence: Bun (Zig→Rust, 1M LOC, 2 weeks), Ladybird (C++→Rust JS engine, 25K lines, 2 weeks, zero regressions), iOS+Android→React Native
- The enabling insight: it's not the AI, it's the tests. Ladybird chose the JS engine first because it had the best coverage. Tests are what make rewrites verifiable.
- The strategic implication: technology choices become experiments. You can choose the right tool now and change later.
- The uncomfortable side: the chardet controversy — LGPL to MIT in 5 days. Copyleft's economic assumption ("reimplementation is too expensive") may be gone.
- The open question: courts haven't ruled. If they don't, the copyleft model has a hole.

---

## Post 12 — "The Future Is Already Here (And Unevenly Distributed)" (Week 12)

**Thesis:** The agentic era is already producing organizational changes, not just tooling changes — and the patterns are becoming visible.

**Outline:**
- GitLab Act 2: the first major DevOps platform to explicitly restructure its org around the agentic era — 3 management layers removed, 30% country presence reduced, ~60 smaller empowered teams
- "Software will be built by machines, directed by people" — the frame that companies are orienting around
- The five autonomy levels (GitLab): where most teams are today (2-3), where they're heading (4-5), what infrastructure unlocks each level
- Shopify's Lehrwerkstatt: agents run in public Slack channels; the shop floor is the classroom; learning is a side effect of work
- The cognitive debt problem: code changes faster than humans build mental models. Code review is no longer enough as the transfer mechanism.
- What stays human: agency (deciding which problems to take on), taste, deliberate discovery, systems thinking, skepticism
- The closing reframe: "I don't want to build software that's cheap. I want to build software that is *better*." — Simon Willison

---

## Series metadata

**Total posts:** 12 (can add 2-3 more for specific tool deep-dives or case studies)  
**Cadence:** Weekly, Mondays  
**Length target:** 1,200–1,800 words per post (tight, not comprehensive)  
**Cross-linking:** Each post should reference 2-3 others; build a reading sequence  
**Call to action:** GitHub repo at github.com/jexp/agentic-engineering — workshop materials and reading list

**Publication sequence rationale:**
- Posts 1-2: set up the framing (what it is + the navigator role)
- Posts 3-7: core practices (spec, context, TDD, ralph, harness)
- Posts 8-9: systemic thinking (middle loop, rigor destinations)
- Posts 10-11: management + reversibility (the two underreported topics)
- Post 12: organizational and future
