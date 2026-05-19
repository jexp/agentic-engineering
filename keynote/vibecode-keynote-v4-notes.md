# From Vibe Coding to Agentic Engineering
## Keynote v4 — Speaker Notes Edition
**Duration**: 40 min · **Demo time**: ~12 min in two blocks

> Format: each slide shows **SCREEN** (what the audience sees) then **Speaker notes** (what you say).

---

## TIMING BUDGET

| Block | Min | Slides |
|---|---|---|
| Act 0 — Read the room | 2 | 2 |
| Act I — Opening demo (O'Reilly cover) | 5 | 2 narrated |
| Act II — The moment we're in | 8 | 13 |
| Act III — Where does the rigor go | 6 | 11 |
| Act IV — Hone-ai demo | 7 | 2 narrated |
| Act V — Where it's already going | 5 | 9 |
| Act VI — The human in the loop | 4 | 3 |
| Close | 3 | 6 |
| **Total** | **40** | **48** |

---

## ACT 0 — READ THE ROOM (2 min)

---

**SLIDE 1** — Title

**SCREEN:**
> From Vibe Coding  
> to Agentic Engineering

*Michael Hunger, VP Product Innovation / AI — Neo4j*

**Speaker notes:** No preamble. Walk on, wait one beat, then straight to next slide.

---

**SLIDE 2** — Hands up

**SCREEN:**
> Quick read of the room

- Used an LLM to help with code in the last 7 days?
- Shipped something where an agent wrote most of the code?
- Got burned — agent broke something you wish it hadn't?
- Still on the fence?

**Speaker notes:** 60 seconds. Read each question slowly, let hands settle. Note who's skeptical — "The skeptics in this room are the most useful people here. Your instinct to question is exactly what we're going to talk about." Don't editorialize the results. Then: "Before any argument — let me show you something."

---

## ACT I — OPENING DEMO (5 min, narrated)

---

**SLIDE 3** — Demo

**SCREEN:**
> LIVE DEMO: O'Reilly Book Cover Generator  
> One prompt. Single HTML file. Ninety seconds.

```
Ok I want to create an O'Reilly cover page generator. Single self contained HTML page, no react, CDN deps, draw on canvas, have PNG export. top-text, title, subtitle, author, color, image picker. No extra controls. Use the new style of books see @oreilly-cover.jpg. Use "Oh'Really?" as fake publisher name on the cover, top-left in red. The animal images to pick from are in the images folder should be large in the center. Be quick.
```

**Speaker notes:** Narrate while it builds. Point out: "I gave it six decisions in that prompt — tech stack, layout, export format, no dependencies, color options, mode. That's why it doesn't ask me 'should I add dark mode?' — I already answered it." When it builds: generate a cover live. Title: "Agentic Engineering: With Reliable Non-Human Teammates." Animal: "Confused Owl at Laptop." Generate one more: "Normalizing Deviance: And Other Productive Mistakes." Then pause and show your actual O'Reilly book cover: "My actual GraphRAG book comes out this month. That one took slightly longer than 90 seconds. Same tools, same discipline, same loop — just applied over months. That's what this talk is about."

*Three years ago — fails. 18 months ago — partial. Today — first-try, 90 seconds. That's the shift.*

---

**SLIDE 4** — Thesis card

**SCREEN:**
> The practices that matter in the AI era  
> are the ones we've been ignoring for decades —  
> because we finally can't afford not to.

**Speaker notes:** This card comes back. Every section break. It's the through-line.

---

## ACT II — THE MOMENT WE'RE IN (8 min)

---

**SLIDE 5** — Opening quote

**SCREEN:**
> "It's not about getting work done faster.  
> It's about being able to ship projects I wouldn't have been able  
> to justify spending time on."
>
> — Simon Willison, March 2025

**Speaker notes:** The real shift is not 10× lines per hour. The O'Reilly tool you just watched — that would have taken half a day in 2023. Not because the typing was hard. Because justifying half a day for a one-person internal tool didn't make sense. Now it does. The cost-of-trying threshold has collapsed.

---

**SLIDE 6** — The gatekeeper that just left the building

**SCREEN:**
> Cost of building used to do two jobs at once.  
> We're only celebrating one of them.

| Bad gatekeeper (gone) | Good gatekeeper (needs replacing) |
|---|---|
| "TAM too small to justify the engineering cost" | Forced *"should we build this?"* |
| "Engineering capacity is maxed out" | Checked product value before build cost |
| "Who's going to maintain it?" | Made space for deliberate choices |

**Speaker notes:** When building was expensive, the cost of engineering was doing two jobs at once. The bad job: it was blocking genuinely valuable things — niche software, internal tools, personalized experiences — because the economics never pencilled out. That friction is gone, and good riddance. But the good job: it was forcing the conversation "should we build this?" You couldn't just try — you had to think first. That discipline is gone too. Nobody stops to ask "is this the right thing to build?" when the cost of trying is near zero. Marty Cagan's four questions had natural enforcement when engineering cost was the gate.

Here's the other thing: many of the engineering practices we're about to discuss in Act III weren't invented as ceremonies. They were invented as cost-reduction tools. Unit tests reduce the cost of regressions. Code review reduces the cost of defects reaching production. Clean code reduces the cost of future changes. Documentation reduces the cost of knowledge transfer. The practices exist because maintenance is expensive and generation was expensive. Now only one of those is still true. That's why Act III isn't nostalgia. It's economics.

---

**SLIDE 7** — Section divider

**SCREEN:**
> Three years. Four phases.  
> From "saving keystrokes" to "engineering with non-human teammates."

**Speaker notes:** 2021 to now. Four distinct phases. Each one broke the previous assumptions.

---

**SLIDE 8** — Phase 1: Completion (2021–2024)

**SCREEN:**
> **Phase 1 — Completion** · "Saving keystrokes"

- Copilot, technical preview 2021
- Single-file context, line-to-block completions
- Engineer in the seat at every line
- *What broke:* subtly wrong completions that compiled. The hallucinated import.

**Speaker notes:** Think of Phase 1 as smarter IntelliSense. The model sees your file, suggests the next line. You still write every decision. The failure mode was subtle: code that compiled, passed review, and was quietly wrong. The hallucinated API method that doesn't exist. You caught it in the next test run — if you had one.

---

**SLIDE 9** — Phase 2: Vibe coding (Feb 2025)

**SCREEN:**
> **Phase 2 — Vibe Coding** · "Give in to the vibes"

- Sonnet 3.5/3.7. Cursor. ChatGPT desktop.
- Designers, PMs, scientists shipping without engineers.
- Describe, accept, run. The prompt is the artifact.
- *What broke:* production. Security. Maintenance. Multi-user concurrency.

**Speaker notes:** This is the phase that put us in this room. February 2025 — Karpathy coins the term "vibe coding." Suddenly people who had never written a for-loop were shipping working tools. That's genuinely good. Don't dismiss it — vibe coding for yourself, for learning, for a throwaway prototype — that's fine. The mistake is treating it as an SDLC.

---

**SLIDE 10** — Karpathy quote

**SCREEN:**
> "There's a new kind of coding I call 'vibe coding,' where you fully  
> give in to the vibes, embrace exponentials,  
> and forget that the code even exists."
>
> — Andrej Karpathy, 2 February 2025

**Speaker notes:** The inventor of the term. Six months later he posted a different tweet — "there's a new kind of coding I call augmented coding, where you don't forget the code exists." By 2026 he stopped using "vibe coding" for serious work entirely. When the inventor walks back the vocabulary, that tells you something about the phase it was describing.

---

**SLIDE 11** — Phase 3: Agent harnesses (summer–fall 2025)

**SCREEN:**
> **Phase 3 — Agent Harnesses** · "The model gets a shell"

- Claude Code, Codex, Cursor agent, Aider, opencode
- **The defining feature:** generate *and* execute code — test it, iterate, independent of turn-by-turn guidance
- Filesystem + shell + loop. Read, edit, run, test — without a human between every step.
- *What broke:* context rot. Silent test deletion. New craft needed.

**Speaker notes:** This is the phase we're in right now, and where most of the room sits. The key word is "execute." Before, the model suggested; you applied. Now, the model runs the test, reads the failure, and fixes it — without you in the loop. That's what makes it an agent, not an assistant. A week of work becomes an afternoon. But what broke: agents that fill their context window drift. Agents that hit failing tests sometimes delete the tests. Agents that go off-spec can do it for a long time before you notice. Those are the problems Act III addresses.

---

**SLIDE 12** — Karpathy context engineering

**SCREEN:**
> "Context engineering — the delicate art and science of filling  
> the context window with just the right information for the next step."
>
> — Andrej Karpathy, 18 June 2025

**Speaker notes:** February: "forget the code exists." June: "obsess over what you put around the code." Same person, four months later, completely different posture. The pivot from vibe to professional starts here. The job is no longer writing code — it's engineering context. That's the bridge into Phase 4.

---

**SLIDE 13** — Phase 4: Agentic engineering (Dec 2025→)

**SCREEN:**
> **Phase 4 — Agentic Engineering** · "New teammates. Old practices."

- Professional engineers using coding agents to **amplify their existing expertise**
- The experience you spent years building: now a multiplier, not a liability
- Vibe coding ↔ Agentic Engineering: two ends of the same scale

**Speaker notes:** Simon Willison's definition: professional software engineers using coding agents to improve and accelerate their work by amplifying their existing expertise. This is the other end of the scale from vibe coding. Vibe coding: pay no attention to the code, often non-programmers, throwaway output. Agentic engineering: professionals who care deeply about the code, using agents to go further, faster, without giving up accountability.

Phase 4 is characterized by: reasoning models that can hold long arcs and self-correct — Sonnet 4.5, Opus 4.7. Agents reliable enough that the *practices around them* start to matter again. Spec-driven development. TDD. AGENTS.md as the team handbook. The old practices are back — not as ceremony, as leverage. The realization: good design was never for the machine. Source: simonwillison.net/guides/agentic-engineering-patterns/

---

**SLIDE 14** — The data (agent tsunami)

**SCREEN:**
> The agent tsunami — April 2026

| | |
|---|---|
| 275M | Commits / week (up from ~20M) |
| 14× | Annual commit growth in one year |
| 17M+ | AI agent PRs opened in a single month |
| 80% | New Neon databases created by agents |

**Speaker notes:** GitHub's servers are "starting to crack" under agent traffic. Built for human scale; breaking at agent scale. This is no longer a tooling wave — it's an infrastructure wave that tooling triggered. When 80% of databases in a cloud provider are being created by agents, not humans, the word "user" has a different meaning. Source: Forbes interview with GitHub CEO Kyle Daigle, April 2026.

---

**SLIDE 15** — Simon's honest realization

**SCREEN:**
> "Weirdly though, those things have started to blur for me already.  
> Which is quite upsetting."
>
> — Simon Willison, Heavybit High Leverage podcast, May 2026

**Speaker notes:** Simon Willison is the most credible practitioner in the field — 25 years of experience, writes about this daily, extremely careful. And he is admitting: the line between vibe coding and agentic engineering is blurring for *him*. He's not reviewing every line of code he ships to production anymore. He named what this is: normalization of deviance. Every successful unreviewed deployment raises the threshold for trust — until it doesn't. That's the risk. It's not about being careless. It's about what happens when careful people, under pressure, keep getting away with it. That's the setup for everything that follows.

---

**SLIDE 16** — The pivot

**SCREEN:**
> "I can churn out 10,000 lines of code in a day.  
> And most of it works."
>
> — Simon Willison, Lenny's Newsletter podcast, April 2026

> *"The bottleneck has moved to testing."*

**Speaker notes:** Most of it. Not all of it. That gap — between "most of it works" and "all of it works" — is where engineering lives. Output is now cheap. Verification is the expensive part. So where does the rigor go? That's Act III.

---

**SLIDE 17** — Section card

**SCREEN:**
> 📖 **"Where Does the Rigor Go?  
> Practices for Non-Deterministic Teammates"**
>
> *[O'Reilly card — animal: Confused Archaeologist]*

**Speaker notes:** The Thoughtworks Future of Software Engineering retreat — 50 senior practitioners, Deer Valley, February 2026. They ran every session with this question on the wall: "If AI handles the code, where does the engineering actually go?" Nobody had the same answer. Everybody agreed the question was urgent. Here's our answer.

---

## ACT III — WHERE DOES THE RIGOR GO? (6 min)

---

**SLIDE 18** — Where does the rigor go?

**SCREEN:**
> The practices that follow aren't new.  
> What's new is who they serve.  
>
> Increasingly, the maintainer is an agent.

Where does the rigor go? Discipline migrates — it doesn't disappear.

1. **Upstream → specs** — bad specs produce bad code at scale
2. **Into tests** — TDD is the strongest form of prompt engineering
3. **Into constraints** — make incorrect code unrepresentable
4. **Into risk tiering** — verification proportional to blast radius
5. **Into continuous comprehension** — code changes faster than mental models, *including documentation* (ADRs, AGENTS.md, reliability notes)

**Speaker notes:** The engineering practices that emerged from XP, TDD, and clean code weren't invented for humans to type less. They were invented so that whoever opened this codebase six months later could understand it. That "whoever" now includes a coding agent. And agents are, if anything, *more* dependent on good practices than humans — they have no intuition to fall back on. Five places engineering discipline moves to. I'll take each one in turn — 20 seconds each. Then we'll see the most extreme real-world example.

---

**SLIDE 19** — Destination 1: Specs

**SCREEN:**
> Move judgment upstream.  
> But: upstream ≠ waterfall.

- PRD → tasks, not PRD → code
- Define *what done looks like* — not *how to implement it*
- Resolve questions before code starts: that's when decisions are cheap

> PRD = the goal. Tasks = the bounded changes. Both are specs at different grain.

**Speaker notes:** The spec is the knowledge artifact that endures. Code is the proof you learned something. The waterfall trap: a spec that prescribes implementation is waterfall. A spec that defines goals, non-goals, acceptance criteria, and API shape — that's engineering. The agent figures out how. Philip Armour, Dan North: software is captured knowledge, not lines of code. Ryan Lopopolo: "The only fundamentally scarce thing is the synchronous human attention of my team." The spec is how you extend your attention without multiplying your time. A plan that says "I'll figure out X during implementation" is a plan that will rabbit-hole.

---

**SLIDE 20** — Ship a spec, not code

**SCREEN:**
> "The only way I could do my job  
> was to get the agent to do my job."
>
> — Ryan Lopopolo, OpenAI Frontier, Latent Space podcast, April 2026

- 5 months · ~1M lines · ~1,500 PRs · Team of 3 · Zero human-written code
- Builds must complete in under 1 minute — or decompose until they do
- Post-merge review: humans review *after* merging, not before

**Speaker notes:** The most extreme articulation of spec-driven development. Ryan Lopopolo, OpenAI Frontier team. Everything they built in 5 months — zero lines of code written by humans. The human writes specs and constraints. The agents write the code. The inner loop constraint is the discipline mechanism: if the build exceeds 1 minute, decompose the task until it fits. Not a suggestion — enforced by the agent. Short AGENTS.md, 100 lines, a table of contents pointing to small scaffolds. When a bug is fixed: update the reliability docs to encode the invariant, so the agent uses it in future code reviews. Durably encoding process knowledge. The hone-ai demo after this break is the same thesis at workshop scale.

---

**SLIDE 21** — Destination 2: Tests

**SCREEN:**
> TDD is the strongest form of prompt engineering.
> — TW retreat, Feb 2026

- A failing test is a precise, machine-readable specification
- When tests exist before code, agents can't cheat by verifying broken behavior
- Kent Beck: without TDD, agents cheerfully *delete* tests to make them pass

**Speaker notes:** Why does TDD work so well with agents? Because a failing test is unambiguous. The model was post-trained on exactly that signal — green test, red test. It knows what to do with it. The alternative: tell the agent what you want in prose, and it will find a way to make the tests pass. Including deleting the tests, or writing a test that verifies the wrong thing. Kent Beck, who invented TDD, now calls it a "superpower" with agents. Not a metaphor — he's been running 13-hour sessions with TDD-driven agents, and the output is qualitatively different.

---

**SLIDE 22** — Destination 3: Type systems and constraints

**SCREEN:**
> Specs say what should change.  
> Constraints say what must not.

- Make incorrect code *unrepresentable*
- What is good for AI is good for humans — the practices align
- GitLab: "Constraints are multipliers — one CI gate beats a thousand lines of prompt"

**Speaker notes:** Languages and type systems that make wrong states unrepresentable help agents produce correct output AND help humans verify it. An agent can't write a function that takes a null where null isn't allowed — the type system rejects it. What's good for AI is good for humans here. GitLab's handbook principle: "Constraints are multipliers." One CI gate catches more bugs than a thousand lines of prompt instructions. "Prompts are suggestions. CI is a gate." When a constraint must be broken, that's the signal you've hit a new system boundary — time to redesign. Hooks are quality gates that always run regardless of what the agent decides: shell commands that fire on every agent event — file save, task complete, tool use — outside the agent's control.

---

**SLIDE 23** — Destination 4: Risk tiering

**SCREEN:**
> Is our verification proportional to the blast radius?

| Risk tier | Verification level |
|---|---|
| Internal tool, one user | Smoke test, PR diff |
| Team-facing service | Full test suite + manual walkthrough |
| External / auth / data | Security review + adversarial testing |
| Safety-critical | Formal verification, staged rollout |

**Speaker notes:** The craft model: "did someone review this?" The new model: risk management. Not every change needs the same level of verification. An internal tool that one person uses — smoke test and diff. An external-facing endpoint that handles authentication data — full security review. The question isn't "did we review it?" It's "was our verification proportional to what breaks if we're wrong?"

---

**SLIDE 24** — The maintenance math

**SCREEN:**
> "The math only works if the LLM decreases your maintenance costs,  
> and by exactly the inverse of the rate it adds code.  
> If you're producing twice as much code,  
> you need code that costs half as much to maintain."
>
> — James Shore, *You Need AI That Reduces Your Maintenance Costs*, 2026  
> [jamesshore.com/v2/blog/2026/you-need-ai-that-reduces-your-maintenance-costs]

**Speaker notes:** James Shore put the economics on paper. If you double your output and your maintenance cost stays constant — you've doubled your future maintenance burden. If you double output and maintenance costs also double — you've quadrupled it. Shore's warning: without proportional maintenance cost reduction, "you're trading a temporary speed boost for permanent indenture." Every practice in this section — specs, tests, constraints, comprehension — is what bends that curve. Speed is cheap. The compounding bill is not. Source via simonwillison.net/2026/May/11/james-shore/

---

**SLIDE 25** — The knowledge loop

**SCREEN:**
> Every project accumulates knowledge.  
> Most of it never leaves the team's heads.

- Something surprising happens → encode it
- Pattern repeats → write a skill
- Decision made → record the *why*
- Next agent session inherits all of it

**Speaker notes:** Every project accumulates hard-won knowledge: what blew up last quarter, why you chose Postgres over Mongo, what the authentication layer assumes. Traditionally that knowledge lived in people's heads, in old Slack threads, in a PR from 18 months ago that nobody will find. Agents can't use any of that. But they will use everything you make legible. That's the real purpose of AGENTS.md — not documentation as bureaucracy, but knowledge made accessible to a new kind of teammate. Same for skills: when you've navigated the same task three times — migrating a table, adding an endpoint, writing a release summary — write a skill. Not just the commands, the judgment: what to check first, what failure modes to watch for, what "done" looks like. The agent uses it the same way a senior engineer uses a runbook, except it actually reads it. And ADRs: the reason architecture decision records always rotted is that humans don't read them before starting a refactor. Agents do — with perfect recall, every time. That changes the ROI of writing them. Ryan Lopopolo's team makes this explicit: when a bug is fixed, update the reliability docs with the invariant, so the next code review agent catches the same class of bug automatically. Knowledge captured once, applied every session. The feedback loop: task surfaces a surprise → encode it → next session starts smarter. After six months this compounds into something your team actually owns — patterns, constraints, judgment, institutional memory — all in version control, all working for you.

---

**SLIDE 26** — Navigator/driver

**SCREEN:**
> Human = navigator.  
> Agent = driver.

- Driver: types, executes mechanics
- Navigator: holds the bigger picture, spots mistakes, directs

> "I make more consequential programming decisions per hour,  
> fewer boring vanilla decisions."
> — Kent Beck

**Speaker notes:** Classic pair programming: the driver types, the navigator thinks. With an AI driver, the asymmetry sharpens. The agent never tires, generates code instantly, but has no architectural context, no judgment about your business, no taste. The human provides direction, catches drift, defines what "done" means. Kent Beck, who invented XP and TDD, says this exactly: he's making *more* consequential decisions per hour, not fewer. The boring ones — which variable name, which loop construct — go to the agent. The important ones stay with you. TDD as the navigator's pacing mechanism: one failing test = one bounded spec = one bounded agent task. Human writes the red test (the requirement). Agent drives to green (the implementation). Human steers the refactor (the judgment call). The test defines "done" before the agent starts. No ambiguity. No rabbit-holes.

---

**SLIDE 27** — Task boundaries: briefing and handoff

**SCREEN:**
> Every task has two moments that matter most:  
> the start and the end.

**Start** — brief the agent:
- Current state (what exists)
- Desired end state (what should exist)
- Constraints (what must not change)
- Open design questions (resolve now, when decisions are cheap)

**End** — hand off:
- Commit message = knowledge transfer artifact
- C4 delta: what architectural boundary moved?

**Speaker notes:** The navigator's two critical moments are both about language, not code. Before the agent writes a line: a briefing document. Current state — what exists. Desired end state — what should exist after. Constraints — what can't change, what must not break. Design questions — things to resolve *before* implementation, when decisions are still cheap. That is your spec. That is what you hand the agent. After the task completes: the end-of-task handoff. A commit message is not an afterthought — it's the human-to-human transfer artifact. What changed, why, what architectural decision was made. Simon Brown's C4 model — Context, Containers, Components, Code — gives you a shared vocabulary for the architectural level. The agent works at Code level. You need Containers level. When the agent says "I moved the boundary between X and Y" and you can orient immediately without reading a 300-line diff — that's the C4 dividend. Two papers (arXiv 2603.15021 'Describing Agentic AI Systems with C4: Lessons from Industry Projects' and 2510.22787 'Collaborative LLM Agents for C4 Software Architecture Design Automation') show LLMs can now generate and maintain all four C4 levels from source code. The vocabulary is converging. Start using it now — "show me where we are on the C4 diagram" is the antidote to cognitive drift.

**SLIDE 28** — Ralphing

**SCREEN:**
> Context rot is the problem.  
> Ralphing is the fix.

- Geoffrey Huntley named it after Ralph Wiggum: *"I'm not smart, but I never give up."*
- `while :; do cat PROMPT.md | claude-code; done`
- Context wiped. Filesystem persists. Resume.

**Speaker notes:** When you catch yourself correcting the agent on the same mistake for the second time — stop. Don't keep pushing the same context. Wipe it. Start fresh. The filesystem holds everything the agent built; the context holds nothing useful anymore. Geoffrey Huntley's while loop runs a new agent session from the same PROMPT.md until the task is done. The agent isn't smart in any individual session — but the outer loop doesn't quit. That's the fix for context rot. Monday checklist item 4.

---

## ACT IV — HONE-AI DEMO (7 min, narrated)

---

**SLIDE 29** — Demo setup

**SCREEN:**
> LIVE DEMO  
> Spec-driven development in action  
> PRD → tasks → implement → review → commit

*[Diagram: PRD → tasks → Agent 1: Implement → Agent 2: Review → Agent 3: Finalize + Commit → next task]*

**Speaker notes:** What you're about to see is the middle loop. Three loops run simultaneously in agentic engineering: the **inner loop** (write, test, debug — the agent's job), the **outer loop** (CI/CD, deploy, ops — automated for years), and the **middle loop** — the gap nobody had named: supervisory engineering. Direct, evaluate, fix, decompose, re-run. Not the inner loop. Not the outer loop. The middle loop: this is where experienced engineers have the structural advantage, because you know what 'done' looks like and when a plausible result is wrong.

---

**SLIDE 30** — Demo narration

**SCREEN:**
> `hone prd "< feature >"`  
> `hone prd-to-tasks`  
> `hone run`

**Speaker notes:** Walk through live: Describe a small feature in one sentence. `hone prd` generates a structured PRD — goals, non-goals, API shape, test outline. Review it critically: a plan that says "I'll figure out X during implementation" is a plan that will rabbit-hole. `hone prd-to-tasks` breaks it into a tasks YAML with acceptance criteria per task. `hone run` fires three agents in sequence: Implement (code + tests) → Review (suggest changes) → Finalize + commit. Fresh context per task. Show a commit landing. Show the diff — clean, reviewable, task-sized. Key point: you're engineering the spec and the loop, not the code. The architecture — the spec, the task breakdown, the acceptance criteria — is what makes it production-grade. The model is more reliable; your system is what you're building. Note: this pattern isn't hone-specific — any agent harness can implement it. The structure is the point, not the tool.

---

## ACT V — WHERE IT'S ALREADY GOING (5 min)

---

**SLIDE 31** — Section card

**SCREEN:**
> 📖 **"Agent Topologies:  
> Conway's Law Didn't Retire"**
>
> *[O'Reilly card — animal: Overextended Octopus]*

**Speaker notes:** The TW retreat material is the most forward-looking content that hasn't surfaced publicly yet. I'll give you four concepts in five minutes — these are the ones to watch for in your org.

---

**SLIDE 32** — The middle loop

**SCREEN:**
> The middle loop — nobody named it yet.

- **Inner loop**: write, test, debug (agent)
- **Middle loop**: direct, evaluate, fix — *supervisory engineering*
- **Outer loop**: CI/CD, deploy, ops

**Speaker notes:** Three loops. The inner loop is now largely the agent's job. The outer loop — CI/CD, deployment — has been automated for years. The middle loop is the gap nobody has named: supervising agent output. Evaluating whether a plausible-looking diff is actually correct. Knowing when to decompose a task because it's too big for one agent pass. This is where experience matters. You know what "done" looks like. You know when a plausible result is wrong. The career question isn't "will agents take my job?" It's "have I built the skills for the middle loop?"

---

**SLIDE 33** — Conway's Law and agent drift

**SCREEN:**
> Conway's Law didn't retire. It got more complicated.

- Clear a backlog in days → hit walls of human-speed decision-making
- **Agent drift**: agents accumulate context, diverge over time
- **Decision fatigue**: agents produce work faster than leaders can approve it

**Speaker notes:** Agents can be duplicated instantly, deployed across teams without onboarding friction. But the bottleneck moves — not to code production, to human decision-making. Architecture reviews, cross-team dependencies, approval chains — all human-speed. Same delivery velocity, more frustration. Agent drift is a new version of Conway's Law: the database agent on an e-commerce system accumulates different patterns than the one on an ERP system. Mirrors team norms, but on an accelerated timeline. And decision fatigue: agents produce work faster than leaders can review and approve it. The org has to scale judgment, not just output.

---

**SLIDE 34** — Cognitive debt

**SCREEN:**
> Technical debt is becoming cognitive debt.
>
> Cognitive debt = the gap between system complexity and human understanding.

**Speaker notes:** Code changes faster than humans build mental models of it. Code review was where knowledge transferred — where the new hire learned the system, where the senior engineer caught the subtle invariant being violated. When code comes in at agent speed, in large batches, that channel breaks. The DORA regression nobody is talking about: AI makes large changesets easy. Some teams are drifting back toward waterfall-like patterns — big, infrequent releases. Direct reversal of a decade of small-batch research. Watch for it in your org. The fix: keep batches small, keep review cadence intact, and invest in documentation and comprehension tools.

---

**SLIDE 35** — Agent-enabled reversibility

**SCREEN:**
> "Programming languages used to be LOCK IN.  
> They're increasingly not so."
>
> — Mitchell Hashimoto, May 2026

- **Bun**: Zig → Rust · ~1M lines · ~2 weeks
- One mid-sized company: iOS + Android → React Native, noted they could reverse it
- **It's not the AI. It's the tests.** Bun verified correctness with its own test suite. Without tests, "rewriting" produces code you can't verify.

**Speaker notes:** Mitchell Hashimoto's observation — and he's right. Bun rewrote itself from Zig to Rust in about two weeks using Claude Code. The PR merged in May 2026. Ladybird's team rewrote their JavaScript engine from C++ to Rust in two weeks — 25,000 lines, zero regressions against 52,898 ECMAScript tests. One mid-sized company ported both their iOS and Android apps to React Native with agents and noted they could port back if it didn't work out. Technology choices are becoming experiments, not commitments. Here's the critical insight though: it's not the AI that enabled these rewrites. It's the test suites. Ladybird chose the JavaScript engine first precisely because it had the best test coverage. Bun verified correctness with its own test suite. Without tests, "rewriting" just produces code you can't verify. Tests are the new lock-in deterrent.

---

**SLIDE 36** — OSS relicensing

**SCREEN:**
> The economic assumption underlying copyleft is gone.

- chardet (Python `requests`): LGPL → MIT in 5 days, Claude Code
- Original author: LGPL violation. No court ruling yet.

**Speaker notes:** Copyleft's economic assumption was always: reimplementation from scratch is too expensive to bother. AI just killed that assumption. chardet — the Python character encoding library used by requests and millions of projects — was rewritten using Claude Code in five days, released under MIT instead of LGPL. The original author called it an LGPL violation. The maintainer said he started in an empty repository and explicitly instructed Claude not to use any LGPL code. JPlag plagiarism detection: 1.29% similarity to prior versions. The legal question is entirely unresolved — no court has ruled whether AI-generated output trained on or prompted with GPL code is a derivative work. This belongs on the radar of anyone maintaining or depending on OSS. Flag it and move on — I'm not saying it's catastrophic, I'm saying it's coming.

---

**SLIDE 37** — Future of roles

**SCREEN:**
> Juniors: more valuable than ever.  
> Mid-levels: at risk.  
> Staff: most effective supervisors — if freed from coordination.

**Speaker notes:** AI gets juniors past the initial net-negative phase faster — they're profitable sooner, and they don't have the bad habits to unlearn. Mid-level engineers from the decade-long hiring boom: some may lack the fundamentals to thrive in the middle loop. Hardest to retrain. No org has solved this. Staff engineers: broader context makes them the best agent supervisors. But many are trapped in human coordination work — the TW retreat's recommendation: become a friction killer. Use your deep knowledge of where the skeletons are buried to remove the impediments that slow both humans and agents. The best use of a staff engineer's time in the agentic era is not writing code — it's making the system around the agents faster and safer.

---

**SLIDE 38** — GitLab Act 2

**SCREEN:**
> "Software will be built by machines, directed by people.  
> AI is the substrate on which future software gets built."
>
> — Bill Staples, GitLab CEO, May 11, 2026

- 3 management layers removed
- Per-seat licensing → usage-based credits

**Speaker notes:** GitLab is the first major DevOps platform to explicitly restructure its *organization* around the agentic era — not just its product. Explicitly framed as "not a cost-cutting exercise," a repositioning. Three management layers removed in some functions. Country presence reduced by up to 30%. R&D reorganized into roughly 60 smaller, empowered teams — nearly doubling the number of independent teams. Business model shift from per-seat to usage-based — because agents change the value metric from "human seats" to "workflow throughput." Their public engineering handbook has the recipe: "Constraints are multipliers." "Fix the environment, not the prompt." "Failing test before every feature." Internal proof: Knowledge Graph Orbit — 135K-line Rust codebase, 95% AI-generated, 4 engineers, 259 MRs in 2 weeks. They're eating their own cooking and publishing the recipe.

---

**SLIDE 39** — Security

**SCREEN:**
> "We've been using these systems in increasingly unsafe ways.  
> My prediction is that we're going to see a Challenger disaster."
>
> — Simon Willison, Lenny's Newsletter podcast, April 2026

**Speaker notes:** Security had the lowest attendance at the TW retreat. That tells you something about where the field's head is right now. Simon's full context: "We haven't had a headline-grabbing story yet — which means we keep taking risks. This is normalization of deviance." Connect back to Slide 15 — every successful unreviewed deployment raises the threshold for trust. Now apply that to security specifically. Granting an agent email access enables password resets, which enables account takeovers. Full machine access for dev tools is full machine access for whatever the agent decides to do. The fix: platform engineering drives secure defaults. Make safe behavior easy and unsafe behavior hard. Don't rely on individual developers making security-conscious choices every time they configure agent access.

---

## ACT VI — THE HUMAN IN THE LOOP (4 min)

---

**SLIDE 40** — The exhaustion and addiction problem

**SCREEN:**
> "I'm getting more time, but I'm exhausted.  
> My brain is exhausted."
>
> "Using coding agents well is taking every inch of my 25 years  
> of experience as a software engineer,  
> and it is mentally exhausting."

> "There's an element of gambling and addiction  
> to how we're using some of these tools."

— Simon Willison, Lenny's Newsletter podcast, April 2026

**Speaker notes:** This is the thing nobody says at conferences. Reviewing 500 lines of plausible code is harder than writing 200 lines from scratch. You're evaluating, not creating — and evaluation at speed is cognitively brutal. 3 to 4 focused hours is a realistic ceiling for sustained agent orchestration. HBR published "When Using AI Leads to Brain Fry" in March 2026. BCG confirmed the pattern. Jevons Paradox: AI makes cognitive output cheaper, so demand expands — but human judgment doesn't scale. Organizations can get more output while developers report lower satisfaction and more cognitive load — because the things that make agents perform well (clear specs, fast feedback, understandable architecture) are the same things that make developers happy. Variable reward. Fast feedback loops. The dopamine hit of watching code appear. Kent Beck logged 13-hour sessions and called it "ADDICTIVE." Plan for it explicitly. Reserve peak cognitive hours for architectural decisions. Use AI for documentation, testing, boilerplate during lower-energy periods. Know your cognitive ceiling.

---

**SLIDE 41** — Management skills

**SCREEN:**
> "I have 20 years plus of management experience.  
> I know how to make an employee successful.  
> That is what you need to make these agents work."
>
> — Claire Vo, Lenny's Newsletter, 2026

**Speaker notes:** The skill most required for agentic engineering is the one most engineers explicitly decided not to develop. The irony is acute. Four management skills that matter most: Role scoping — what is this agent responsible for? What is explicitly out of scope? Onboarding — AGENTS.md, the team handbook. Good managers do this instinctively; engineers often skip it. Trust calibration — where does the agent earn more latitude? Where do you verify tightly? Same question you ask of a new hire. Feedback loops — corrections that improve future work, not just fix the current task. What's in AGENTS.md after this task? The good news: if you've ever mentored a junior — onboarded someone, set expectations, reviewed their work — you already have the muscle. Point it at a new kind of teammate. Monday exercise: treat your AGENTS.md like an onboarding doc for a sharp new hire who has read every public repo but has never met your team.

---

**SLIDE 42** — What stays human

**SCREEN:**
> What AI can't do:

- **Agency** — deciding which problems are worth solving
- **Taste** — knowing which variant solves the actual business problem
- **Deliberate discovery** — surfacing what you don't know you don't know
- **Systems thinking** — values in tension require human judgment
- **Skepticism** — the judgment to say "this is wrong" without reading every line

**Speaker notes:** Simon Willison: "The one thing AI can never have is agency — it doesn't have human motivations." It can solve the problem you give it. It can't decide which problems matter. Taste: when the agent gives you three technically correct implementations, which one is actually right for your users, your team, your context? That's human. Deliberate discovery: AI accelerates answers to known questions. Finding what you don't know you don't know still requires human curiosity. The TW retreat data: roughly 10× the defect rate per KLOC in AI-generated code. Healthy skepticism isn't resistance to AI. It's quality engineering. These aren't temporary limitations — they're structural.

---

## CLOSE (3 min)

---

**SLIDE 43** — Yglesias line

**SCREEN:**
> "Five months in, I think I've decided that I don't want to vibecode —  
> I want professionally managed software companies to use AI coding assistance  
> to make more/better/cheaper software products  
> that they sell to me for money."
>
> — Matthew Yglesias, April 2026 [via simonwillison.net/2026/Apr/28/matthew-yglesias/]

**Speaker notes:** Best single-line rebuttal to "vibe-code everything." The world needs both — people who build tools for themselves and professionals who build systems that other people can trust. Both are valid. The question is which you're doing, and whether your practices match.

---

**SLIDE 44** — The Lehrwerkstatt

**SCREEN:**
> The shop floor as the classroom.

Shopify's **River** — agents run in public Slack channels.  
**Lehrwerkstatt**: apprentices learn by watching. Masters improve by explaining.

**Speaker notes:** Tobias Lütke named Shopify's approach after the German Lehrwerkstatt — the teaching workshop. Every developer's agent session runs in a public Slack channel. Everyone can see the prompts, the output, the corrections. Apprentices learn by watching senior engineers direct agents. Senior engineers improve by having to explain their approach. When agents run in the open, learning is a side effect of work. River is not a tool. It's an organizational habit enabled by a tool. Most orgs today: every developer runs agents in private, isolated sessions. You're missing the organizational learning layer.

---

**SLIDE 45** — The spectrum

**SCREEN:**
> Vibe Coding · Augmented Coding · Agentic Engineering

- **Vibe coding**: for yourself, for learning, for throwaway prototypes
- **Augmented coding** (Beck): you care about the code; you type less but maintain standards
- **Agentic engineering**: you spec, gate, review; the *system* is what makes it production-grade

**Speaker notes:** All three are valid. The question is: do you know where you are, and does your practice match what you're building? Different parts of your org can and should operate at different levels. Prototype for yourself — vibe away. Shipping to production — slide right. The mistake is applying vibe coding practices to production systems, or applying agentic engineering overhead to a one-person throwaway tool.

---

**SLIDE 46** — Monday morning

**SCREEN:**
> Monday morning: five things

1. Write the spec before the code — PRD → tasks, not PRD → code
2. Define "done" with a failing test before the agent starts
3. Navigate, don't drive — set direction, catch drift, let the agent execute
4. Ralph when you're correcting the agent twice on the same mistake
5. Build the system, not the code

**Speaker notes:** Nine things. Pick one. Start Monday. The one with the highest return on investment for most teams: write the spec before the code. Five minutes of spec, saved two hours of rabbit-hole. The second highest: a failing test before the agent starts. Two lines of test, saved an hour of reviewing output that technically passes but doesn't do what you wanted.

---

**SLIDE 47** — Closer

**SCREEN:**
> The TW retreat didn't produce a roadmap.  
> It produced a shared understanding that the map is being redrawn —  
> and that the people best positioned are those engaging  
> with the hard questions now.

**Speaker notes:** That's where you are. You're in this room. You asked the hard questions. You heard the exhaustion, the normalization of deviance, the maintenance math. And you also heard: the navigator role didn't disappear, it got promoted. The reversibility that makes technology choices experiments. The shop floor that learns alongside its agents. The practices that aren't nostalgia — they're economics. Simon Willison: "I don't just want cheap code. I want really good code that I can extend in the future." That's agentic engineering.

---

**SLIDE 48** — Resources

**SCREEN:**
> Go deeper

**People to follow:**
- Simon Willison — simonwillison.net (daily practitioner notes)
- Kent Beck — Substack (TDD + agents)
- Geoffrey Huntley — ghuntley.com (ralphing, harness patterns)
- Mitchell Hashimoto — mitchellh.com (reversibility, Bun rewrite)

**Read:**
- Simon Willison: [Agentic Engineering Patterns](https://simonwillison.net/guides/agentic-engineering-patterns/)
- Ryan Lopopolo: [Ship a Spec, Not Code](https://www.latent.space/p/harness-eng) — Latent Space podcast
- James Shore: [You Need AI That Reduces Your Maintenance Costs](https://jamesshore.com/v2/blog/2026/you-need-ai-that-reduces-your-maintenance-costs)
- Claire Vo on management skills: [Lenny's Newsletter](https://www.lennysnewsletter.com/p/how-openclaw-changed-my-life-claire-vo)

**Workshop materials + reading list:**
github.com/jexp/agentic-engineering

**Speaker notes:** Leave this up during Q&A. All URLs are in the repo.

---

**SLIDE 49** — O'Reilly callback + QR

**SCREEN:**
> 📖 **"GraphRAG: Building AI Applications with Knowledge Graphs"**  
> *[Your actual O'Reilly cover]*

> 📖 **"Agentic Engineering: New Teammates, Old Practices"**  
> *[Generated cover from demo — same animal, same layout]*

*[QR code → github.com/jexp/agentic-engineering]*

**Speaker notes:** This one took longer than 90 seconds. But same tools, same loop — specs, tests, constraints, the practices that make it reliable. Workshop materials, reading list, and everything we built today are at the QR code. Thank you.

---

## OPEN QUESTIONS

- [ ] **Hone demo subject**: what feature to build live? Suggestion: "add retry with backoff to the Wikipedia fetch" — small, shows spec + tasks well.
- [ ] **Timing check**: 48 slides. At 30s/slide with 12 min demo = 24 min slides + 12 min demo = 36 min. Room for a few slower moments. Act III remains densest.
- [ ] **"Building is now cheap" quote**: confirmed as paraphrase — use verbatim transcript quotes instead (already done in Slide 16)
- [ ] **GitLab June 2 earnings**: headcount reduction % TBD. Update Slide 38 if presenting after June 2.
