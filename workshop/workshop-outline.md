# Workshop Outline & Master Structure

**Event**: 4-hour workshop, experienced engineers / team leads
**Title**: *From Vibe Coding to Agentic Engineering — Hands-on*
**This doc**: master running order, timing, framing for each section, hand-off lines between sections, slide-count budget. **Use this to drive slide generation** — each section points at its detailed source doc.

---

## At a glance — the day

| # | Block | Duration | Cumulative | Source doc | Slides |
|---|---|---|---|---|---|
| 0 | Welcome, framing, hand-raisers | 5 min | 0:05 | [`workshop-intro.md`](./workshop-intro.md) (Slide 0–1) | 2 |
| 1 | **Intro** — From Vibe Coding to Agentic Engineering | 30 min | 0:35 | [`workshop-intro.md`](./workshop-intro.md) (Slide 2–5) | 8–10 |
| 2 | **Exercise 1** — Build the tool you wished existed | 30 min | 1:05 | [`workshop-exercise-1.md`](./workshop-exercise-1.md) | 3 + brief |
| 3 | *Break* | 10 min | 1:15 | — | 1 |
| 4 | **Deep dive — A: Harnesses & tool use** | 20 min | 1:35 | [`workshop-harnesses.md`](./workshop-harnesses.md) + [`workshop-tool-use.md`](./workshop-tool-use.md) | 7–9 |
| 5 | **Deep dive — B: Cost & tokens** | 10 min | 1:45 | [`workshop-cost-tokens.md`](./workshop-cost-tokens.md) | 4–5 |
| 6 | **Deep dive — C: Benchmarks** | 5 min | 1:50 | [`workshop-benchmarks.md`](./workshop-benchmarks.md) | 2–3 |
| 7 | **Deep dive — D: Practices** | 20 min | 2:10 | [`workshop-practices.md`](./workshop-practices.md) | 8 |
| 8 | **Deep dive — E: Own experience demos** | 10 min | 2:20 | [`workshop-own-experience.md`](./workshop-own-experience.md) | 6 (cue cards) |
| 9 | *Break* | 10 min | 2:30 | — | 1 |
| 10 | **Exercise 2** — Real work, real discipline | 60 min | 3:30 | [`workshop-exercise-2.md`](./workshop-exercise-2.md) | 7 + brief |
| 11a | **Mental load, roles & career** (Q&A starter) | 5–7 min | 3:37 | [`workshop-mental-safety.md`](./workshop-mental-safety.md) | 3 |
| 11b | **Q&A + closing reflection** | 18–20 min | 3:55 | this doc § Q&A | 1–2 |
| 12 | **Resources** — final QR slide | 5 min | 4:00 | [`workshop-resources.md`](./workshop-resources.md) | 1 |

**Total slide count target**: ≈45–55 slides for ~3:30 of content + 30 min Q&A. Aim low — the demos and exercises do the work.

---

## Block 0 — Welcome, framing, hand-raisers (0:00–0:05)

**Source**: [`workshop-intro.md`](./workshop-intro.md) Slides 0–1
**Energy**: high, conversational, set tone immediately
**Goal**: meet the room where they are; pull skeptics into the room early via hand-raisers

**Framing line for me**:
> "The goal today isn't to convince you AI will write all your code. It's to give you the same operating mental model and muscle memory I use, so you can decide for yourselves what's real and what's hype."

**Hand-raisers** (4 questions — stop after 60 seconds):
1. Used an LLM for code before mid-2024?
2. Used an agentic harness in the last 7 days?
3. Shipped to production this year where the agent wrote most of the code?
4. Had an agent silently break something and wished you'd never started?

**Hand-off into Block 1**:
> "Some of you came in skeptical, some excited, some both. Let me tell you how we got here — three years compressed into ten minutes — so we share a map before we walk."

---

## Block 1 — Intro: From Vibe Coding to Agentic Engineering (0:05–0:35)

**Source**: [`workshop-intro.md`](./workshop-intro.md) Slides 2–5
**Energy**: storytelling, opinionated
**Goal**: shared timeline of how the field arrived here, set up *why* the rest of the workshop matters

**Section flow**:
- *Why we're doing this* — SWE agents are a tool, but with bigger leverage than any prior tool (3 min)
- *History — 4 phases* — completion (2021–24) → vibe coding (Karpathy Feb 2025) → agent harnesses (summer 2025) → agentic engineering (late 2025–2026) (12 min)
- *Why coding is uniquely good for LLMs* — verifiable, reasoning surface, tight RL loop, ancient universal tools, clear goals (4 min)
- *Bridge into the rest of the day* — what we'll do, why this isn't dismissal of vibe coding (2 min)

**Pull from [`context-engineering-mining.md`](../research/context-engineering-mining.md)**:
- Add Karpathy June 2025 "context engineering" tweet alongside Feb 2025 "vibe coding" — bracket the year (Edit #1)
- Add "Test Time > Train Time" to the why-coding-is-good section (Edit #2)

**Hand-off into Block 2**:
> "Enough talk. Simon Willison wrote a piece in December 2025 that's the cleanest version of where this is heading — and it gives us a concrete first exercise. You're going to build something useful in 30 minutes."

---

## Block 2 — Exercise 1: Build the tool you wished existed (0:35–1:05)

**Source**: [`workshop-exercise-1.md`](./workshop-exercise-1.md)
**Energy**: room shifts — laptops out, hands on keyboards
**Goal**: feel the "cost of trying collapsed" first-hand. Ship a personal HTML tool, skill, or CLI script in 30 min.

**Three slides + brief**:
- Slide A — Frame (Simon's quote, "make the tool you wish existed")
- Slide B — The exercise (constraints, what to build)
- Slide C — How to do it well in 30 min (time-boxed plan)
- Brief sheet — paste-ready ideas + escape hatches

**Show-and-tell at 0:55–1:05**: 3 volunteers, 20 sec each.

**Hand-off into the break**:
> "Take 10 minutes. Get coffee. Come back ready for the deep end."

---

## Block 3 — Break (1:05–1:15)

Single transition slide with "back at <time>" — visible from the back of the room.

---

## Block 4 — Deep Dive A: Harnesses & tool use (1:15–1:35)

**Sources**: [`workshop-harnesses.md`](./workshop-harnesses.md) + [`workshop-tool-use.md`](./workshop-tool-use.md)
**Energy**: rebuild attention, re-engage the analytical brain after the break
**Goal**: give a vendor-neutral, anatomical mental model of harnesses; show the 6-rung tool-use ladder; calibrate the room on what each rung costs

**Section flow**:
- *Anatomy of a harness* — six boxes (system prompt, loop, tools, context, permissions, state/memory) (3 min)
- *Landscape* — CLI vs IDE, who's who, multi-agent convergence (4 min)
- **Insert: tool-use ladder** — built-in → CLI → snippets → REST → skills → MCP, with cost/capability matrix and "climb only when current rung doesn't reach" heuristic (5 min)
- *Craft levers* — sessions, plan mode, context, model selection, tools/hooks/skills/MCP (8 min)

**Pull from [`context-engineering-mining.md`](../research/context-engineering-mining.md)**:
- Push (RAG) vs Pull (Tool Calling) framing on the craft-levers slide (Edit #3)

**Hand-off into Block 5**:
> "Every lever I just listed maps to a token cost decision. Let me show you where the tokens actually go."

---

## Block 5 — Deep Dive B: Cost & tokens (1:35–1:45)

**Source**: [`workshop-cost-tokens.md`](./workshop-cost-tokens.md)
**Energy**: practical, numbers-driven
**Goal**: make the room cost-literate. Show the Context Pyramid, savings levers, key tools (ccusage, RTK, headroom, caveman), real prices.

**Section flow**:
- *Context Pyramid + where tokens go by phase* (2 min)
- *10 savings levers in priority order, framed as Offload / Consolidate / Retrieve* (3 min)
- *The tools* — ccusage, RTK, headroom, caveman, prompt caching, harness-level levers (3 min) — *brief live demo of ccusage on my own data*
- *2026 pricing + 3 rules of thumb + Monday-morning action* (2 min)

**Pull from [`context-engineering-mining.md`](../research/context-engineering-mining.md)**:
- Replace Slide 1 visual with Context Pyramid (Edit #8)
- Frame Slide 2 with Offload/Consolidate/Retrieve (Edit #9)

**Hand-off into Block 6**:
> "Two minutes on benchmarks before we get to the practices — because the room will ask, and I want us literate on the numbers before we hit them in the wild."

---

## Block 6 — Deep Dive C: Benchmarks (1:45–1:50)

**Source**: [`workshop-benchmarks.md`](./workshop-benchmarks.md)
**Energy**: critical, calibrating
**Goal**: a literate take on benchmarks — directional yes, absolute no. Inoculate against the leaderboard reflex.

**Compress aggressively** — this is a 5-minute section, not 7:
- *5 benchmark families along a realism axis* (1 min)
- *Where the leaders sit + the (model × harness × scaffolding) caveat* (1 min)
- *The honest pros and cons* (2 min)
- *9-point rubric for reading benchmarks like a senior engineer + closing line* (1 min)

If running ahead: spend the spare minute. If running behind: cut to 3 slides — landscape, caveat, "run your own."

**Hand-off into Block 7**:
> "Numbers are directionally right. They don't tell you what to do tomorrow. Practices do."

---

## Block 7 — Deep Dive D: Practices (1:50–2:10)

**Source**: [`workshop-practices.md`](./workshop-practices.md)
**Energy**: this is the conceptual heart of the day — slow down, let it land
**Goal**: turn anatomy + cost knowledge into a working method. The mentoring frame, AGENTS.md, ralphing, spec-driven, the per-task loop.

**Section flow**:
- *Mentoring frame* — agent as junior dev with infinite patience but no project memory (2 min)
- *Challenges* — 5 named failure modes (rot, poisoning, confusion, distraction, clash) (3 min)
- *Collapsing the latent space* — why constraints work; TDD and spec-driven dev as RL-aligned (3 min)
- *AGENTS.md / CLAUDE.md as MVC* — what goes in, layering rules, paste-ready template (4 min)
- *Ralphing* — when, how, what to keep across the reset (2 min)
- *Spec-driven + plan mode* — three task sizes, three patterns; the spec flow (3 min)
- *The per-task loop* — wrapped in the 3-Phase Agent Loop frame; 11 concrete steps (3 min)

**Pull from [`context-engineering-mining.md`](../research/context-engineering-mining.md)** — apply edits #4 (5 named failure modes), #5 (Lance Martin "right info, right format" quote), #6 (MVC + reiterate-at-end rule for AGENTS.md), #7 (3-Phase Agent Loop frame around the 11-step loop).

**Hand-off into Block 8**:
> "Now let me show you what this looks like for me, every day, on real work."

---

## Block 8 — Deep Dive E: Own-experience demos (2:10–2:20)

**Source**: [`workshop-own-experience.md`](./workshop-own-experience.md) (cue cards, no slide content — live demos)
**Energy**: storytelling, demo-driven, builds trust and concreteness
**Goal**: ground all the theory in real artifacts. Show the warts.

**Six modes, ~90 seconds each + light intro/outro**:
1. Research & learning content (Sather-K / vibe-haskell / Elixir)
2. Content generation (neo4j-skills, agent-integrations)
3. Codebase research (claude-code analysis, cocoindex, or another large public codebase)
4. Simple greenfield (openalex-neo4j, clauditopia)
5. OSS contributions (inferrs, aura-cli)
6. Larger greenfield (agent-intelligence, neo4j-skills cypher authoring, create-context-graph.dev)

If running tight: cut to 4 (drop 2 + 5 per the cue-card recommendation).

**Hand-off into the break**:
> "Take 10 minutes. When you come back, you're going to do this on something real."

---

## Block 9 — Break (2:20–2:30)

Same transition slide as before.

**Quietly, while the room is on break**: have my walk-the-room checklist visible ([`workshop-exercise-2.md`](./workshop-exercise-2.md) facilitator notes).

---

## Block 10 — Exercise 2: Real work, real discipline (2:30–3:30)

**Source**: [`workshop-exercise-2.md`](./workshop-exercise-2.md)
**Energy**: focused, hands-on, room is heads-down
**Goal**: 60 minutes of real work under the discipline. Aim for 5 commits.

**Slides**:
- Slide A — The challenge (3 rules)
- Slide B — Pick a task archetype (4 shapes — bug, feature, MCP-on-surface, cross-language)
- Slide C — The 60-minute breakdown (visible the whole hour)
- Slide D — AGENTS.md starter template (paste-ready, photographable)
- Slide E — 5 execution rules
- Slide F — Success tiers (read aloud at 0:55)
- Slide G — Show-and-tell prompts

**My role**: walk the room, time announcements at 0:15, 0:25, 0:35, 0:55. Catch attendees skipping plan mode at minute 8, not minute 30.

**Show-and-tell** (last 5 min): 3 volunteers, 30 sec each — 3 questions.

**Hand-off into Block 11**:
> "We've been talking the whole time. Now your turn. What's on your mind?"

---

## Block 11 — Q&A + closing reflection (3:30–3:55)

The Q&A is unstructured by design, but a quiet room is bad TV. Open with a question of *my own* to model the right register, then keep priming with the questions below if the room stalls.

### My opening question (always ask, even if hands are up)

> "Before I take questions — let me ask one back. **What's the thing you saw or did today that you want to try Monday morning?** Just shout it out."

This buys 30 seconds of genuine engagement, surfaces what landed, and signals I want a conversation, not a presentation. It also tells me what to emphasize in the closing.

### Hand-raiser / leading questions (use if needed, don't burn through them)

In rough order of "easy to engage" → "harder, deeper":

#### Easy on-ramps
1. **Practice swap** — "Who's about to switch their primary harness based on something they heard today? To what?"
2. **Surprise** — "What's something the agent has done well for you that genuinely surprised you?"
3. **Bite** — "What's the failure mode that bites you most? What did you change after?"

#### Mid-depth
4. **Where AI doesn't fit** — "Where in your stack do you *not* use AI today? Why? Would you reconsider after today?"
5. **The unconvinced** — "Skeptics in the room — what would convince you to try this on production work?"
6. **Onboarding** — "For team leads: how would you onboard a new team member to agentic workflows? What changes vs. last year?"
7. **Review fatigue** — "How are you handling reviewing agent-authored PRs at scale? What's working, what isn't?"
8. **Measurement** — "What do you actually measure to know your AI tooling is helping? Not feeling, measuring."

#### Deeper
9. **Architecture** — "Has the agent ever proposed an architecture that was technically right but you knew was wrong for your team or product? How did you handle it?"
10. **The next year** — "What capability do you most want from these tools in the next 12 months that doesn't exist yet?"
11. **The job** — "How is *your job* different than it was a year ago because of these tools? Better, worse, both?"
12. **Production scars** — "What's the worst production incident you can attribute to agentic work — yours or your team's?"

#### Closing redirect
13. **One thing** — "If you take exactly **one** thing from today and apply it next week, what is it?"

### Closing reflection (last 2–3 min)

After Q&A winds down (signal: third silence > 5 sec), pivot:

> "Three things to take with you, then we wrap.
>
> One — the practices that work with agents are the practices that always worked with humans. Spec, test, review, commit small. We just couldn't afford the ceremony before.
>
> Two — the system you build around the model is the moat. The model gets better every six months. The system is yours.
>
> Three — the failure modes are real, the discipline is real, and the leverage is real. Don't dismiss any of the three.
>
> Resources are in the QR — take a picture before you stand up. Thank you."

---

## Block 12 — Resources / closing slide (3:55–4:00)

**Source**: [`workshop-resources.md`](./workshop-resources.md)
**One slide**: 4 QR codes (this resources doc, Anthropic CC best practices, Simon Willison's agentic-engineering tag, awesome-cli-coding-agents directory).

Plus my email / Mastodon / X handle small at the bottom.

---

## Slide-generation guidance

When I (or a tool) turn this into a deck:

### Per-section assembly rules
- Each block's section header → **section divider slide** (1 slide, large title)
- Use `workshop-<topic>.md` as the source of truth for slide *content*
- Use this outline for *order, hand-off lines, and timing*
- Pull [`context-engineering-mining.md`](../research/context-engineering-mining.md) edits #1–#14 *during* slide generation, not after — saves a re-pass

### Slide-count budget per block (target)

| Block | Section dividers | Content slides | Subtotal |
|---|---|---|---|
| 0 — Welcome | 0 | 2 | 2 |
| 1 — Intro | 1 | 8 | 9 |
| 2 — Exercise 1 | 1 | 3 | 4 |
| 3 — Break | 1 | 0 | 1 |
| 4 — Harnesses + tool use | 1 | 8 | 9 |
| 5 — Cost & tokens | 1 | 4 | 5 |
| 6 — Benchmarks | 1 | 2 | 3 |
| 7 — Practices | 1 | 7 | 8 |
| 8 — Own experience | 1 | 6 | 7 |
| 9 — Break | 1 | 0 | 1 |
| 10 — Exercise 2 | 1 | 6 | 7 |
| 11 — Q&A | 1 | 1 | 2 |
| 12 — Resources | 0 | 1 | 1 |
| | | **Total** | **≈59** |

Trim toward 50 if dry-run runs over. First cuts: benchmarks → 1 slide; own-experience → 4 demos; combine harnesses + tool-use into one shared section.

### Visual / styling notes
- Section dividers: large white text on blue, neo4j logo top-right, no body text
- Content slides: 6–10 lines max, no walls of text
- Quotes: full-bleed, attribution below, no other content
- Tables: pull straight from the workshop docs — they're already sized
- Code blocks: monospace, dark background, 18pt minimum
- Hand-raiser slides: literal numbered questions, nothing else

---

## Pre-flight reminders for me (the day before)

- [ ] Print the 60-min Exercise 2 breakdown as a 2-page handout (one per attendee)
- [ ] Pre-build the MCP server scaffold for Exercise 2 option C
- [ ] Confirm mongot analysis is OK to show publicly (otherwise drop from own-experience Slide 3)
- [ ] Pick the 3 starter ideas for Exercise 1 (suggest: regex tester, JSON→Cypher, markdown TOC)
- [ ] Verify the headline benchmark numbers against current leaderboards
- [ ] Confirm host location for [`workshop-resources.md`](./workshop-resources.md) (gist? own site?) so the QR is stable
- [ ] Apply the 14 surgical edits from [`context-engineering-mining.md`](../research/context-engineering-mining.md) to the workshop docs (or do during slide-gen)
- [ ] Open one of Simon Willison's tools in a browser tab as ambient inspiration during arrival
- [ ] Pre-clear my own demo terminals; one per own-experience demo
- [ ] Test ccusage live demo with my own data
- [ ] Have backup screenshots for any network-dependent demo
- [ ] Final sanity check on all `[VERIFY]` quotes and numbers

---

## Open questions for me to decide before tomorrow

- [ ] **Order of Deep Dive sub-blocks** — currently Harnesses → Cost → Benchmarks → Practices → Own experience. Alternative: move Practices before Cost so the *why* of cost is grounded in the practices first. **Lean: keep current — anatomy → cost → benchmarks → method → demos is the natural arc.**
- [ ] **Skip benchmarks block entirely** if running tight? **Lean: keep it but compress to 3 minutes if needed; skeptics will raise it if I don't.**
- [ ] **Closing reflection wording** — current draft is three "one/two/three" beats. Tighter: drop to two beats? **Lean: keep three. It bookends the workshop.**
- [ ] **Q&A opening question** — start with "what will you try Monday?" or "what surprised you?" **Lean: Monday — more actionable, models the register I want.**
- [ ] **Resources slide handle** — include my email / Mastodon? **Lean: yes, small font, bottom of slide.**
