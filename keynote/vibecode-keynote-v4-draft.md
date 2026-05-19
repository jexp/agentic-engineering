# From Vibe Coding to Agentic Engineering
## Keynote Draft v4 — VibeCode Conference
**Duration**: 40 min · ~30s/slide · 10–15 min demo in two blocks  
**Talk slides**: ~54 · **Demo time**: ~12 min

---

## TIMING BUDGET

| Block | Min | Demo | Slides |
|---|---|---|---|
| Act 0 — Read the room | 2 | — | 4 |
| Act I — Opening demo (O'Reilly cover) | 5 | ✓ 5 min | 2 narrated |
| Act II — The moment we're in (history) | 8 | — | 16 |
| Act III — Where does the rigor go | 6 | — | 12 |
| Act IV — Hone-ai demo (spec-driven loop) | 7 | ✓ 7 min | 3 narrated |
| Act V — Future / TW retreat | 5 | — | 10 |
| Act VI — The human in the loop | 4 | — | 8 |
| Close | 3 | — | 6 |
| **Total** | **40** | **12 min** | **~61** |

---

## ACT 0 — READ THE ROOM (2 min)

---

**SLIDE 1** — Title

> From Vibe Coding  
> to Agentic Engineering

*[Michael Hunger, VP Product Innovation / AI — Neo4j]*

*Notes: No preamble. Stand, wait a beat, then go straight to Slide 2.*

---

**SLIDE 2** — Hands up

> Quick read of the room

- Used an LLM to help with code in the last 7 days?
- Shipped something where an agent wrote most of the code?
- Got burned — agent broke something you wish it hadn't?
- Still on the fence?

*Notes: 60 seconds. Read each question, let hands settle, don't editorialize. Note the skeptics — name their experience later. "Skeptics in this room are the most useful people here."*

*Bridge: "Before any argument — let me show you something."*

---

## ACT I — OPENING DEMO (5 min, narrated)

---

**SLIDE 3** — Demo setup (on screen while demo runs)

> LIVE DEMO  
> O'Reilly Book Cover Generator  
> One prompt. Single HTML file. Ninety seconds.

*[Decision: O'Reilly generator over wikilinks — wikilinks was last week's workshop opener. The O'Reilly meme is universally recognized in this room and becomes a running theme.]*

*Notes: The prompt on screen while it builds:*

```
Ok I want to create an O'Reilly cover page generator. Single self contained HTML page, no react, CDN deps, draw on canvas, have PNG export. top-text, title, subtitle, author, color, image picker. No extra controls. Use the new style of books see @oreilly-cover.jpg. Use "Oh'Really?" as fake publisher name on the cover, top-left in red. The animal images to pick from are in the images folder should be large in the center. Be quick.
```

*Narrate while building:*
- *Specificity: what you want, set the limits (for personal tools)
- *"Three years ago — fails. 18 months ago — partial. Today — first-try, 90 seconds."*
- *When it builds: generate a cover live. Title: "Agentic Engineering: With Reliable Non-Human Teammates". Animal: "Confused Owl at Laptop".*
- *Generate one more: "Normalizing Deviance: And Other Productive Mistakes".*

*Bridge: "My actual O'Reilly book on GraphRAG comes out this month. [show real cover] This is the one that took slightly longer than 90 seconds. But same tools, same discipline, same loop — just applied over months. That's what the rest of this talk is about."*

---

**SLIDE 4** — The O'Reilly theme card (running visual)

> "The practices that matter in the AI era are the ones we've been  
> ignoring for decades — because we finally can't afford not to."

*[This is the thesis card. Will return to this layout for each section transition.]*

---

## ACT II — THE MOMENT WE'RE IN (8 min)

---

**SLIDE 5** — Quote, standing start

> "It's not about getting work done faster.  
> It's about being able to ship projects I wouldn't have been able  
> to justify spending time on."
>
> — Simon Willison, March 2025

*Notes: The real shift is not 10× lines per hour. It's the collapse of the cost-of-trying threshold. The WikiLinks / O'Reilly tool you just watched built — that would have taken half a day of fiddling in 2022.*

---

**SLIDE 5b** — The gatekeeper that just left the building

Cost of building used to do two jobs at once — and we're only celebrating one of them.

**The bad gatekeeper** (we're glad it's gone):
- "The TAM is too small — we can't justify the engineering cost"
- "Our team is already maxed out, we can't take this on"
- "Who's going to maintain it?" — used to kill dozens of genuinely valuable tools
- Niche software, internal tooling, personalized experiences: all chronically underbuilt because the economics never pencilled out

**The good gatekeeper** (we need to replace it deliberately):
- Cost of building forced the conversation: *is this worth building?*
- Marty Cagan's four questions — valuable? feasible? viable? usable? — had natural enforcement: you couldn't just build and find out, so you had to think first
- The friction of engineering capacity made "should we build this?" a real decision with real stakes

When building becomes cheap, the bad gatekeeper disappears — great. But so does the discipline enforced by the good one. Nobody stops to ask "is this the right thing to build?" when the cost of trying is near zero.

**What this means for the agentic era:** product thinking, discovery, and "should we build this?" judgment become *more* critical, not less — because the friction that used to force those conversations is gone. The speed of execution has outpaced the speed of deciding what deserves to be executed.

**One more thing about cost:** many of the engineering practices we're about to discuss weren't invented as ceremonies or craft ideals. They were invented as **cost-reduction tools** — specifically to reduce the cost of maintaining code over time.

- Unit tests: reduce cost of regressions
- Code review: reduce cost of defects reaching production
- Clean code and small functions: reduce cost of future changes
- Documentation: reduce cost of knowledge transfer
- TDD: reduce cost of debugging

Simon Willison's observation: *"the cost to churn out initial working code has dropped to almost nothing — how does that impact our existing intuitions?"*

The answer: when generation is near-free, the economic case for maintenance-reducing practices becomes *stronger*, not weaker — because you're generating 10× more code that still has to be read, changed, and kept working.

This is why Act III isn't nostalgia. It's economics.

*Notes: This is a 30-second beat — don't dwell. The point is to acknowledge the audience's real experience: they know both sides of the cost barrier. Then move into the history. The Marty Cagan reference will land with anyone who's worked with product managers. The "cost-reduction tools" framing gives Act III its through-line — these practices exist because maintenance is expensive and generation was expensive. Now only one of those is still true.*

*Source: simonwillison.net/guides/agentic-engineering-patterns/ — "Cost-Reduction Engineering" section*

---

**SLIDE 6** — Three years, four phases (divider)

> Three years. Four phases.  
> From "saving keystrokes" to "engineering with non-human teammates."

---

**SLIDE 7** — Phase 1: Completion (2021–2024)

> **Phase 1 — Completion**  
> "Saving keystrokes"

- Copilot, technical preview 2021
- Single-file context, line-to-block completions
- Mindset: smarter IntelliSense. Engineer in the seat at every line.
- What broke: subtly wrong completions that compiled. The hallucinated import.

---

**SLIDE 8** — Phase 2: Vibe coding (Feb 2025)

> **Phase 2 — Vibe Coding**  
> "Give in to the vibes"

- Sonnet 3.5/3.7. Cursor. ChatGPT desktop.
- Designers, PMs, scientists shipping working tools without engineers.
- Mindset: describe, accept, run. Code is throwaway; the prompt is the artifact.
- What broke: production. Security. Maintenance. Multi-user concurrency.

*Notes: Don't dismiss it. Vibe coding for yourself, for learning, for throwaway prototypes — that's fine. The mistake is treating it as an SDLC.*

---

**SLIDE 9** — Karpathy quote

> "There's a new kind of coding I call 'vibe coding,' where you fully  
> give in to the vibes, embrace exponentials,  
> and forget that the code even exists."
>
> — Andrej Karpathy, 2 February 2025

*Notes: Six months later he posted the bracketing tweet. And by 2026 he retired the term for serious work. The inventor walked back the vocabulary — that tells you something.*

---

**SLIDE 10** — Phase 3: Agent harnesses (summer–fall 2025)

> **Phase 3 — Agent Harnesses**  
> "The model gets a shell"

- Claude Code, Codex, Cursor agent, Aider, opencode
- The defining feature: they can **generate and execute code** — test it, iterate on it, independent of turn-by-turn guidance. That's what makes them agents, not assistants.
- Filesystem + shell + loop. Read, edit, run, test — without a human between every step.
- Engineer becomes director, not typist. A week of work → an afternoon.
- What broke: context rot, ralphing, silent test deletion. New craft needed.

---

**SLIDE 11** — Karpathy context engineering quote

> "Context engineering — the delicate art and science of filling  
> the context window with just the right information for the next step."
>
> — Andrej Karpathy, 18 June 2025

*Notes: February: "forget the code." June: "obsess over what's around the code." Two sides of the same year. This is the bridge into Phase 4.*

---

**SLIDE 12** — Phase 4: Agentic engineering (Dec 2025→)

> **Phase 4 — Agentic Engineering**  
> "New teammates. Old practices."

*Definition (Simon Willison):* Professional software engineers using coding agents to improve and accelerate their work — by **amplifying their existing expertise**. The experience you spent years building becomes a multiplier, not a liability.

This is the other end of the scale from vibe coding. Vibe coding: pay no attention to the code — often non-programmers, throwaway output. Agentic engineering: professionals who care deeply about the code, using agents to go further, faster, without giving up accountability.

- Reasoning models: Sonnet 4.5, Opus 4.5/4.6/4.7. Plan, self-correct, hold long arcs.
- Agents reliable enough that the *practices around them* start to matter again.
- Spec-driven dev. TDD. AGENTS.md. Hooks. Code review. The old practices — back as leverage, not ceremony.
- The realization: good design was never for the machine.

*Source: simonwillison.net/2026/Feb/23/agentic-engineering-patterns/*

---

**SLIDE 13** — The data (agent tsunami)

> The agent tsunami — April 2026

| | |
|---|---|
| 275M | Commits / week (up from ~20M) |
| 14× | Annual commit growth in one year |
| 17M+ | AI agent PRs opened in a single month |
| 80% | New Neon databases created by agents |

*Notes: GitHub's servers are "starting to crack" under agent traffic — built for human scale, breaking at agent scale. This is no longer a tooling wave. It's an infrastructure wave that tooling triggered.*

---

**SLIDE 14** — Why coding runs ahead of every domain

> Why coding, specifically

- **Verifiable** — compiles, tests pass, or they don't. A ground truth the model can check itself against.
- **Tight RL loop** — generate → run → observe → correct. Densest reward signal in any domain.
- **Ancient tools** — bash, grep, git, make. Stable for 30 years. Linux is the lingua franca.
- **Test time > train time** — the model's context is where the work happens. That's why context engineering pays.

---

**SLIDE 15** — Simon's honest realization (new — from Heavybit, May 2026)

> "Weirdly though, those things [vibe coding and agentic engineering]  
> have started to blur for me already. Which is quite upsetting."
>
> — Simon Willison, Heavybit High Leverage podcast, May 2026

*Notes: The most credible practitioner in the field is having the same discomfort you might be having. As agents get more reliable, he's not reviewing every line of code he ships to production anymore. He named what this is: "normalization of deviance." Every successful unreviewed deployment raises the risk of misplaced trust at exactly the wrong moment.*

*This is the most honest thing anyone has said publicly about agentic engineering. It's also the setup for Act III.*

---

**SLIDE 16** — The pivot question

> "I can churn out 10,000 lines of code in a day.  
> And most of it works."
>
> — Simon Willison, Lenny's Newsletter podcast, April 2026

> "The bottleneck has moved to testing.  
> How do we get from 'most of it works' to 'all of it works'?"

*If output is cheap, verification is the engineering. So where does the rigor go?*

*Source: lennysnewsletter.com/p/an-ai-state-of-the-union*

---

**SLIDE 17** — Section O'Reilly card

> 📖 **"Where Does the Rigor Go?  
> Practices for Non-Deterministic Teammates"**
>
> *[O'Reilly-style card — animal: Confused Archaeologist]*

*Notes: The Thoughtworks Future of Software Engineering retreat (50 senior practitioners, Deer Valley, Feb 2026) ran every session with this question on the wall: "If AI handles the code, where does the engineering actually go?" Nobody had the same answer. Everybody agreed the question was urgent.*

---

## ACT III — WHERE DOES THE RIGOR GO? (6 min)

---

**SLIDE 18** — Act III opener: practices serve the maintainer

> The practices that follow aren't new.  
> What's new is who they serve.  
>
> Increasingly, the maintainer is an agent.

The engineering practices that emerged from XP, TDD, and clean code weren't invented for humans to type less. They were invented so that whoever opened this codebase six months later could understand it.

That "whoever" now includes a coding agent. And agents are, if anything, *more* dependent on good practices than humans — they have no intuition to fall back on.

*The paradox: the same discipline that makes AI output trustworthy is the discipline that made human code maintainable. They're the same thing.*

---

**SLIDE 19** — The five destinations

> Where does the rigor go?  
> Engineering discipline migrates — it doesn't disappear.

Five destinations (TW retreat, Feb 2026):

1. **Upstream → specs** — bad specs produce bad code at scale
2. **Into tests** — TDD is the strongest form of prompt engineering
3. **Into constraints** — type systems, lint, make incorrect code unrepresentable
4. **Into risk tiering** — verification proportional to blast radius
5. **Into continuous comprehension** — code changes faster than humans can build mental models

*Notes: Work through these quickly, 20s each. They are the five slides that follow.*

---

**SLIDE 20** — Destination 1: Specs (and the waterfall trap)

> Move human judgment upstream.  
> But: upstream ≠ waterfall.

- The spec is the knowledge artifact that endures. Code is the proof you learned something.
- **PRD → tasks, not PRD → code** — a spec that prescribes implementation is waterfall. A spec that defines *what done looks like* (goals, non-goals, acceptance criteria, API shape) — that's engineering. The agent figures out how.
- Right level of detail: enough to specify what "done" looks like. Not enough to prescribe HOW.
- Plan mode → review → execute. Resolve questions before code is written — that's when decisions are cheap. A plan that says "I'll figure out X during implementation" is a plan that will rabbit-hole.
- Philip Armour / Dan North: software is captured knowledge, not lines of code. The spec is the knowledge.
- Ryan Lopopolo (OpenAI Frontier): "The only fundamentally scarce thing is the synchronous human attention of my team." The spec is how you extend your attention without multiplying your time.

---

**SLIDE 21** — "Ship a spec, not code" (Ryan Lopopolo / OpenAI Frontier, 2026)

> "The only way I could do my job  
> was to get the agent to do my job."
>
> — Ryan Lopopolo, OpenAI Frontier team, Latent Space podcast, April 2026

5 months. ~1M lines of code. ~1,500 PRs. Team of 3. Zero human-written code.

- "Ship a spec, not code" — the human writes specs and constraints; agents write all the code
- The inner loop constraint: builds must complete in under 1 minute. Enforced by the agent — if the build exceeds 1 min, decompose the task until it fits. Ratchet discipline.
- Short AGENTS.md (100 lines) + skills: a table of contents pointing to small scaffolds. "Models fundamentally crave text."
- When a bug is fixed, update the reliability docs to encode the invariant. Agent uses this for future code review — durably encoding process knowledge.
- Post-merge review: humans review *after* merging, not before. Review agents run on PR sync.

*Notes: This is the most extreme articulation of the "spec-driven" model. The hone-ai demo this afternoon is the same thesis at workshop scale. Point to it explicitly.*

*Source: https://www.latent.space/p/harness-eng (April 7, 2026) [VERIFIED — resolves]*

---

**SLIDE 20** — Destination 2: Tests as prompt engineering

> TDD is the strongest form of prompt engineering.  
> — TW retreat, Feb 2026

- A failing test is a *precise, machine-readable specification*. The model was post-trained on exactly that signal.
- When tests exist before code, agents can't cheat by writing a test that verifies broken behavior.
- "I've gotten better results from TDD and agent coding than I've ever gotten anywhere else." — retreat participant
- Kent Beck (TDD inventor): TDD is a "superpower" with agents. Without tests, agents cheerfully *delete* tests to make them pass.

---

**SLIDE 21** — Destination 3: Type systems and constraints

> Specs say what should change.  
> Constraints say what must not.

- Languages that make incorrect code *unrepresentable* help both agents produce correct output and humans verify it.
- What is good for AI is good for humans. The practices align.
- Constraint = bounded context. When a constraint must be broken, it signals a new system boundary → refactor.
- "Limits blast radius. When the constraint must be broken, that's the signal to redesign."

---

**SLIDE 22** — Destination 4: Risk tiering

> Is our verification proportional to the blast radius?

Not "did someone review this?" — that's the craft model.  
The new question: risk management model.

| Risk tier | Verification level |
|---|---|
| Internal tool, one user | Smoke test, PR diff |
| Team-facing service | Full test suite + manual walkthrough |
| External-facing / auth / data | Security review + adversarial testing |
| Safety-critical | Formal verification, staged rollout |

---

**SLIDE 22b** — The maintenance math (James Shore, 2026)

> "The math only works if the LLM decreases your maintenance costs,  
> and by exactly the inverse of the rate it adds code.  
> If you're producing twice as much code,  
> you need code that costs half as much to maintain."
>
> — James Shore, *You Need AI That Reduces Your Maintenance Costs*, 2026  
> [jamesshore.com/v2/blog/2026/you-need-ai-that-reduces-your-maintenance-costs]

Without that: *"You're trading a temporary speed boost for permanent indenture."*

Speed is cheap. The compounding maintenance bill is not. Every practice in this section — specs, tests, constraints, comprehension — is what bends that curve.

*Source via simonwillison.net/2026/May/11/james-shore/*

---

**SLIDE 23** — Destination 5: Continuous comprehension

> Code review was doing four things at once.  
> Each one needs a new home.

- Mentorship → pair programming, ensemble programming (XP renaissance — TW retreat)
- Knowledge sharing → Shopify's Lehrwerkstatt: agents operate in public Slack channels; the whole shop floor is the classroom
- Correctness → tests, gates, type checks
- Architecture consistency → weekly architecture retros; AI comprehension tools
- **Documentation** → ADRs, AGENTS.md, inline docs, reliability notes. Not ceremony — the durable knowledge layer that survives context resets, onboards the next agent session, and encodes what the codebase expects. Ryan Lopopolo: when a bug is fixed, update the reliability docs to encode the invariant — the agent uses it for future code review.

*Notes: When code review is the only place where knowledge transfers, removing it creates a comprehension gap that compounds silently. Name each function and give it a new home. Documentation is the one that bridges human ↔ human AND human ↔ agent — AGENTS.md is documentation, it just has a new audience.*

---

**SLIDE 24** — The good-design insight (the core)

> "Good software design was never for the machine.  
> It was always for the next human who had to read, maintain, and extend it."

Now there's a new kind of teammate.  
LLMs were trained on human communication about code:  
Stack Overflow, docs, code reviews, commit messages, blog posts.

So: clear specs → better agent prompts.  
Good naming → better agent comprehension.  
Tests as specs → agents that verify their own work.  
Consistent patterns → agents that follow your conventions.

*The practices that made code readable for colleagues make it navigable for agents. For exactly the same reason.*

---

**SLIDE 25** — The navigator role didn't disappear. It got promoted.

> Human = navigator.  
> Agent = driver.

In classic pair programming: the driver types, the navigator holds the bigger picture, spots mistakes, directs.

With an AI driver, the asymmetry is even sharper:
- The agent never tires and generates code instantly — but has no architectural context, no judgment about your business, no taste.
- The human provides direction, catches drift, holds quality standards, defines what "done" means.
- Kent Beck: *"I make more consequential programming decisions per hour, fewer boring vanilla decisions."*

**TDD as the navigator's pacing mechanism:**
- One failing test = one bounded spec = one bounded agent task
- Human writes the red test (strategic): this is the requirement
- Agent drives to green (mechanical): this is the implementation
- Human reviews and steers the refactor: this is the judgment call
- The test defines "done" before the agent starts. No ambiguity. No rabbit-holes.

*Notes: This is the cleanest mental model for the workshop audience. They already understand pair programming. The agent is just the best driver they've ever had — as long as they stay in the navigator seat.*

*Sources: Kent Beck [Augmented Coding — Substack]; Simon Willison [Red/green TDD — Agentic Engineering Patterns guide]*

---

## ACT IV — HONE-AI DEMO (7 min, narrated)

---

**SLIDE 25** — Demo setup

> LIVE DEMO  
> Spec-driven development in action  
> The implementation loop — fresh context, every task

*[Show the hone-ai workflow diagram: PRD → tasks → Implement agent → Review agent → Finalize + Commit → next task]*

*Notes: This is the middle loop that nobody has named yet (TW retreat). Not the inner loop (write/test/debug) and not the outer loop (CI/CD/deploy) — the supervisory engineering in between. Directing, evaluating, fixing agent output.*

---

**SLIDE 26** — Demo narration cues (on screen during demo)

> hone prd "< feature >"  
> hone prd-to-tasks  
> hone run

*Walk through live:*
1. *Describe a small feature in one sentence*
2. *`hone prd` generates a structured PRD: goals, non-goals, API shape, test outline*
3. *Review the PRD critically — "a plan that says 'I'll figure out X during implementation' is a plan that will rabbit-hole"*
4. *`hone prd-to-tasks` → tasks-feature.yml with acceptance criteria per task*
5. *`hone run` → three agents in sequence: Implement (code + tests) → Review (suggest changes) → Finalize + commit. Fresh context per task.*
6. *Show a commit landing. Show the diff. Clean, reviewable, task-sized.*

*Notes: Key point to make: you're engineering the spec and the loop, not the code. The model is more reliable, but your architecture — the spec, the task breakdown, the acceptance criteria — is what makes it production-grade.*

---

**SLIDE 27** — The loop, restated

The model gets better every six months.  
The system is what you build.

- AGENTS.md → the team handbook (what every fresh session inherits)
- Spec → the upstream judgment call (cheap to make, expensive to skip)
- Tests → the safety net and the spec in one artifact
- Hooks → quality gates that always run (lint, typecheck, security scan)
- Per-task loop → determinism in an indeterministic system

*Notes: This isn't new. It's old engineering discipline applied to a new kind of teammate. The workshop this week: this is exactly what we built over 4 hours. You can start with just the AGENTS.md and the ralph rhythm, and add the rest over weeks.*

---

## ACT V — THE FUTURE (5 min)

---

**SLIDE 28** — Section card

> 📖 **"Agent Topologies: Conway's Law Didn't Retire"**
>
> *[O'Reilly card — animal: Overextended Octopus]*

*Notes: The TW retreat material is the most forward-looking content nobody else in the field has surfaced yet. Use sparingly — 3-4 key concepts, not a full review.*

---

**SLIDE 29** — The middle loop (TW retreat, new concept)

> The middle loop  
> Nobody has named this yet.

- **Inner loop**: write, test, debug (you and your IDE)
- **Outer loop**: CI/CD, deployment, operations
- **Middle loop** (new): direct, evaluate, and fix agent output — *supervisory engineering*

This is where experienced engineers have the structural advantage. You know what "done" looks like. You know when a plausible result is wrong. You can decompose problems into agent-sized work packages.

*The career question isn't "will agents take my job?" It's "have I built the skills for the middle loop?"*

---

**SLIDE 30** — Agent topologies + Conway's Law

> Conway's Law didn't retire.  
> It got more complicated.

- Agents can be duplicated instantly, deployed across multiple teams without onboarding friction.
- But: clear a backlog in days → hit walls of cross-team dependencies, architecture reviews, human-speed decision-making. Same delivery speed, more frustration. Bottleneck has moved.
- **Agent drift**: agents that learn from context diverge over time. Database agent on e-commerce vs. ERP system accumulates different patterns. Mirrors team norms, but on an accelerated timeline.
- **Decision fatigue as bottleneck**: agents produce work faster than leaders can approve it.

---

**SLIDE 31** — Cognitive debt (new named concept)

> Technical debt is becoming cognitive debt.

Cognitive debt = the gap between system complexity and human understanding.

Code changes faster than humans can build mental models of it. Code review was where knowledge transferred. When code comes in at agent speed, in large batches, that channel breaks.

The DORA regression nobody is talking about: AI makes large changesets easy. Some teams are drifting back toward waterfall-like patterns — big, infrequent releases. Direct reversal of a decade of small-batch research. Watch for it in your org.

---

**SLIDE 32** — Agent-enabled reversibility: the new engineering superpower

> "Programming languages used to be LOCK IN.  
> They're increasingly not so."
>
> — Mitchell Hashimoto, May 2026 [VERIFIED — simonwillison.net/2026/May/14/mitchell-hashimoto/]

**The evidence:**
- **Bun**: Zig → Rust, ~1M lines, ~1–2 weeks with coding agents. Anthropic's team merged the PR in May 2026.
- **Ladybird browser**: JavaScript engine C++ → Rust, ~25K lines, 2 weeks with Claude Code and Codex. Zero regressions against 52,898 ECMAScript tests and 12,461 regression tests. February 2026.
- **iOS + Android → React Native**: a mid-sized company ported both apps with agents in weeks — and noted they could reverse it if needed.

**What enables this — it's not AI, it's tests:**
Ladybird chose the JS engine first precisely because it had the best test coverage. The test suite was what made the rewrite verifiable. Bun used its own test suite for the same reason.

> "The only way to verify correctness of a rewrite isn't human review — it's a test suite that proves bit-for-bit equivalence."

Technology choices are becoming experiments, not commitments. Architectural lock-in drops. What used to be a 6-month risk is now a 2-week experiment — IF you have the tests.

---

**SLIDE 33** — The uncomfortable side: OSS relicensing

> The economic assumption underlying copyleft is gone.

**The chardet controversy (March 2026):**
- chardet (Python character encoding library, used by `requests`, millions of projects) was rewritten using Claude Code in 5 days
- Released under MIT — relicensed from LGPL
- JPlag: only 1.29% similarity to prior versions
- The original author called it an LGPL violation

**The legal question is unresolved.** Is AI-generated output trained on/prompted with GPL code a derivative work? No court ruling yet.

**Why this is structurally new:**
> "The GPL family of licenses has always depended on one practical assumption: rewriting a large codebase from scratch is so expensive that nobody bothers."

That assumption is gone. What took a team months now takes one developer days.

*Notes: This is a "here be dragons" slide, not a doom slide. Flag it and move on — it belongs on the radar of anyone maintaining or depending on OSS. Don't dwell.*

*Sources: simonwillison.net/2026/Mar/5/chardet/ · theregister.com/2026/03/06/ai_kills_software_licensing/ · ladybird.org/posts/adopting-rust/ [all VERIFIED]*

---

**SLIDE 33** — The future of roles (TW retreat)

> Juniors: more valuable than ever.  
> Mid-levels: at risk.  
> Staff engineers: most effective agent supervisors — if freed from coordination.

- AI gets juniors past the initial net-negative phase faster. They're profitable sooner. Better at agent tools than seniors (no habits to unlearn).
- Mid-levels from the decade-long hiring boom: may lack the fundamentals to thrive in the middle loop. Hardest to retrain. No org has solved this yet.
- Staff engineers: broader context makes them better supervisors. But many trapped in human coordination — the TW recommendation: **become a friction killer**. Use your deep knowledge of where the skeletons are buried to remove the impediments that slow both humans and agents.

---

**SLIDE 34** — GitLab Act 2: the first major org to restructure for the agentic era

> "Software will be built by machines, directed by people.  
> AI is the substrate on which future software gets built."
>
> — Bill Staples, GitLab CEO, May 11, 2026 [VERIFY exact wording]

GitLab explicitly framed Act 2 as "not a cost-cutting exercise" — a repositioning for the agentic era:
- **Up to 3 management layers** removed in some functions
- **~30% country presence** reduced (from ~60 countries)
- R&D reorganized into **~60 smaller, empowered teams** — nearly doubling the number of independent teams
- Business model shift: **per-seat licensing → usage-based credits** ($1/credit). Value metric changes from "human seats" to "workflow throughput."
- New operating principles replacing the old CREDIT values: Speed with Quality, Ownership Mindset, Customer Outcomes

**GitLab's handbook (public, March 2026) — their engineering principles:**
- "Constraints are multipliers" — one CI gate catches more bugs than a thousand lines of prompt instructions
- "Fix the environment, not the prompt" — lint rules and tests persist; prompts don't
- "Failing test before every feature" — the test defines "done" for the agent
- **Internal proof:** Knowledge Graph Orbit — 135K-line Rust codebase, 95% AI-generated, 4 engineers, 259 MRs in 2 weeks. CI + AGENTS.md + architecture docs in place from day one.

*Notes: Simon Willison notes GitLab's financial incentive to frame this positively (stock was ~$52→~$26 over the year). Take the framing with that context. The handbook practices are the real gold — GitLab is eating their own cooking and publishing the recipe publicly.*

*Sources: about.gitlab.com/blog/gitlab-act-2/ · handbook.gitlab.com/handbook/engineering/workflow/ai-assisted-development/ [VERIFIED]*

---

**SLIDE 35** — Security (the uncomfortable slide)

> "We've been using these systems in increasingly unsafe ways.  
> My prediction is that we're going to see a Challenger disaster."
>
> — Simon Willison, Lenny's Newsletter podcast, April 2026  
> [lennysnewsletter.com/p/an-ai-state-of-the-union]

*The full context: "We haven't had a headline-grabbing story yet — which means we keep taking risks. This is normalization of deviance."*

Security had the lowest attendance at the TW retreat. That tells you something.

- Granting an agent email access enables password resets → account takeovers.
- Full machine access for dev tools = full machine access for whatever the agent decides to do.
- Platform engineering should drive **secure defaults**: make safe behavior easy and unsafe behavior hard.
- Don't rely on individual developers making security-conscious choices when configuring agent access.

*Notes: The Challenger reference connects back to the normalization of deviance thread from Slide 15 — every successful unreviewed deployment raises the threshold for trust. Now connect it to security specifically.*

---

## ACT VI — THE HUMAN IN THE LOOP (4 min)

---

**SLIDE 36** — The exhaustion problem

> "I'm getting more time, but I'm exhausted.  
> My brain is exhausted."
>
> — Simon Willison, Lenny's Newsletter podcast, April 2026

> "Using coding agents well is taking every inch  
> of my 25 years of experience as a software engineer,  
> and it is mentally exhausting."
>
> — Simon Willison, Lenny's Newsletter podcast, April 2026  
> [lennysnewsletter.com/p/an-ai-state-of-the-union]

- The middle loop is cognitively brutal. Reviewing 500 lines of *plausible* code is harder than writing 200 from scratch. You're evaluating, not creating — and evaluation at speed is exhausting.
- 3–4 focused hours is a realistic ceiling for sustained agent orchestration. (HBR "When Using AI Leads to Brain Fry," March 2026)
- **Jevons Paradox**: AI makes cognitive output cheaper, so demand expands — but human judgment doesn't scale.

> "There's an element of gambling and addiction  
> to how we're using some of these tools."
>
> — Simon Willison, Lenny's Newsletter podcast, April 2026

Variable reward, fast feedback loops, the dopamine hit of watching code appear. Plan for it — it's not a personal failing.

- **The navigator's discipline**: reserve peak cognitive hours for architectural decisions. Reserve AI for documentation, testing, boilerplate during lower-energy periods.
- Sustainable practice: know your cognitive ceiling *and stop being a hero about it*.

---

**SLIDE 36** — The productivity / experience paradox (TW retreat)

> Productivity and developer experience are decoupling.

Organizations can get more output while developers report lower satisfaction, less flow, more cognitive load.

*If you only optimize for output, you lose something real — and you don't see the cost until it compounds.*

The TW retreat proposed a reframe: **stop calling it developer experience; call it agent experience.** Wallets open faster. And the overlap with what makes humans thrive turns out to be nearly complete.

---

**SLIDE 37** — The management skill most engineers don't have (Claire Vo, Lenny's Newsletter 2026)

> "I have 20 years of management experience.  
> I know how to make an employee successful.  
> That is what you need to make these agents work."
>
> — Claire Vo, *How OpenClaw Changed My Life*, Lenny's Newsletter, 2026

The irony: the skill most required for agentic engineering is the one most engineers explicitly decided *not* to develop.

- **Role scoping** — what is this agent responsible for? What is explicitly out of scope?
- **Onboarding** — context-setting, AGENTS.md, the team handbook. Good managers do this instinctively. Engineers often skip it.
- **Trust calibration** — where does the agent earn more latitude? Where do you verify tightly? Same question you ask of a new hire.
- **Feedback loops** — corrections that improve future work, not just fix the current task. What's in AGENTS.md after this task?

*The good news: if you've ever mentored a junior — onboarded someone, set expectations, reviewed their work, given feedback that stuck — you already have the muscle. You just need to point it at a new kind of teammate.*

*The exercise for Monday: treat your AGENTS.md like an onboarding doc for a sharp new hire who has read every public repo but has never met your team. What do they need to know?*

---

**SLIDE 38 / 39** — What stays human

> The things AI can't do (yet):

- **Agency** — deciding what problems to take on. Simon Willison: *"The one thing AI can never have is agency — it doesn't have human motivations."*
- **Taste** — knowing which of three agent-generated variants actually solves the business problem
- **Deliberate discovery** — surfacing the unknown unknowns. AI accelerates answers to known questions. Finding what you don't know you don't know still requires human curiosity and judgment.
- **Systems thinking** — the forces in tension (performance vs. cost, security vs. usability, speed vs. reliability) require human judgment about human values
- **Skepticism** — the judgment to say "this is wrong" without reading every line. The TW retreat: ~10× the defect rate per KLOC in AI-generated code. Healthy skepticism isn't resistance. It's quality engineering.

---

**SLIDE 38** — The Matthew Yglesias line

> "Five months in, I think I've decided that I don't want to vibecode —  
> I want professionally managed software companies to use AI coding assistance  
> to make more/better/cheaper software products  
> that they sell to me for money."
>
> — Matthew Yglesias, May 2026

*Notes: Best single-line rebuttal to "vibe-code everything." The world needs both — people who build tools for themselves and professionals who build systems that other people can trust. Both are valid. The question is which you're doing and whether your practices match.*

---

## CLOSE (3 min)

---

**SLIDE 38** — How organizations learn alongside their agents

> The shop floor as the classroom.

Shopify's **River** runs in public Slack channels — every developer and agent prompt is visible to everyone. Tobias Lütke named it after the German concept of **Lehrwerkstatt** (the teaching workshop): apprentices learn by watching masters, masters improve by explaining to apprentices.

When agents run in the open, learning is a side effect of work.

**What this unlocks:**
- Junior engineers learn from watching senior engineers direct agents — not just from reading code
- Organizational patterns become visible and discussable ("our agent always hits this constraint — why?")
- The team's collective experience shapes the agent's behavior, not just one developer's prompts

**The parallel:** River is not a tool. It's an organizational habit that happens to be enabled by a tool.

**For agentic engineering teams:** agent observability at the team level is the Lehrwerkstatt. If your agents run only in private, individual sessions, you're missing the organizational learning layer.

*Notes: This is a short, memorable slide. Point to it as the contrast with "developer in isolation" — which is where most orgs are today. The keynote closes on "build the system." This slide is the human-system layer.*

*Source: simonwillison.net/2026/May/11/learning-on-the-shop-floor/ [VERIFIED — "Learning on the Shop Floor"]*

---

**SLIDE 39** — The spectrum

> Vibe Coding · Augmented Coding · Agentic Engineering

All valid. The question is: do you know where you are, and does your practice match what you're building?

- **Vibe coding**: for yourself, for learning, for the throwaway prototype that proves the idea. Go wild.
- **Augmented coding** (Beck's term): you care about code quality; you type less but maintain standards.
- **Agentic engineering**: you spec, you gate, you review; AI does the work; the *system* — practices, tests, hooks, AGENTS.md, the loop — is what makes it production-grade.

*Different parts of your org can and should operate at different levels. Prototype for yourself? Vibe away. Shipping to production? Slide right.*

---

**SLIDE 40** — Monday morning

> Monday morning checklist

- Write the spec before the code — PRD → tasks, not PRD → code
- Define "done" with a failing test before the agent starts
- Start with a thin template — agents match existing patterns
- "Use red/green TDD" — five words that change agent output
- Navigate, don't drive — set direction, let the agent execute, catch drift
- Ralph when you're correcting the agent twice on the same point
- Review via PRs, not by watching the agent type
- Know your cognitive ceiling — 3–4 focused hours, then stop
- Treat AGENTS.md like an onboarding doc for a sharp new hire
- Build the system, not the code

---

**SLIDE 41** — The closer

The TW retreat didn't produce a roadmap.  
It produced a shared understanding that the map is being redrawn —  
and that the people best positioned are those engaging with the hard questions now.

— Thoughtworks retreat, Deer Valley, February 2026

Then:

Simon Willison: *"I don't just want cheap code. I want really good code that I can extend in the future — all of those characteristics of code that's useful and can be used in production."*  
— Lenny's Newsletter podcast, April 2026

---

**SLIDE 42** — O'Reilly callback + QR

> 📖 **"GraphRAG: Building AI Applications with Knowledge Graphs"**  
> *[Your actual O'Reilly cover]*

This one took longer than 90 seconds.

> 📖 **"Agentic Engineering: New Teammates, Old Practices"**  
> *[Generated cover from demo — same animal, same layout]*

This one took 90 seconds.

*[QR code to github.com/jexp/agentic-engineering — the public repo with the workshop materials, reading list, and the things we built today]*

---

## OPEN QUESTIONS FOR ITERATION

- [ ] **Demo choice confirmed**: O'Reilly generator is the recommendation. Wikilinks available as fallback or quick reference ("we built something like this in the workshop").
- [ ] **Hone demo**: need a small pre-prepared feature to run live. What's the subject? (Suggestion: "add a retry mechanism to the Wikipedia fetch" — small, concrete, shows the spec + tasks well.)
- [x] **"Ship a spec, not code" (Latent Space/OpenAI)**: added as new slide (Slide 21). Source: latent.space/p/harness-eng — Ryan Lopopolo / OpenAI Frontier, April 7, 2026. URL VERIFIED.
- [ ] **Ralphing slide**: currently mentioned in the checklist. Does it need its own dedicated 30s slide with just the name + Simpsons origin? It was a big hit in the workshop. Could sit between Act III and IV as a palate cleanser.
- [ ] **Max Schoening / malleable software**: not currently in the keynote. Could add as a half-slide in Act V (future): "Max Schoening from Notion calls this direction 'malleable software' — software that works closer to the interest of the people using it than the corporation that built it." Decision: add or drop?
- [ ] **Slide numbering pass**: inserted ~6 new slides; slide numbers need a final renumbering pass after content is locked.
- [ ] **Timing check**: ~52 slides now (added ~10 new). With 12 min of demos and 3 min close, that's ~25 min for 40 slides of content = ~37s each. Act III is densest — may need to cut Destinations 3+4 to one slide. Decide in rehearsal.
- [ ] **O'Reilly running theme**: Slides 17, 28, 42 use the O'Reilly card. Add one more as a section break for Act VI? Suggestion: *"The Middle Loop: Supervisory Engineering for the Rest of Us"*
- [ ] **James Shore maintenance reframe**: slide 22 notes cover this ("2× output × constant maintenance = 2× debt") but doesn't frame agents as the solution. Consider: "The good news — agents are excellent at maintenance. GitHub Actions as headless agent infrastructure for the maintenance layer." One sentence to add.
- [ ] **GitLab June 2 earnings**: specific headcount reduction % not yet disclosed. Update slide 34 after June 2 if presenting later.
- [ ] **"Building is now cheap" quote (URL 3 — Lenny's Newsletter)**: not confirmed in accessible web content, may be paywalled/audio. Cross-check against simonwillison.net/2026/Apr/2/lennys-podcast/ (Simon's own highlights post — confirmed accessible). May want to use the Lenny's highlights version for this quote.

---

## MATERIALS TO PREPARE BEFORE TOMORROW

- [ ] **Pre-run the O'Reilly demo** on a fresh Claude Code session tonight. Time it. Have screenshots as fallback.
- [ ] **Pre-run hone on the feature you'll demo live**. Know what the PRD looks like, what the task list looks like, what the first commit looks like.
- [ ] **[VERIFY]** Simon's exact wording: "normalization of deviance" — confirm from the Heavybit podcast highlights post (simonw.substack.com/p/vibe-coding-and-agentic-engineering).
- [ ] **[VERIFY]** TW retreat "TDD as strongest form of prompt engineering" — exact wording from the PDF (retrieved, should be verbatim).
- [ ] **QR code** for github.com/jexp/agentic-engineering — generate and add to Slide 42.
- [ ] **Your real O'Reilly cover** — confirm file available for Slide 42.
