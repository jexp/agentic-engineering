# Keynote & Blog Plan
_Last updated: 2026-05-18_

## Status key
- [ ] pending · [→] in progress · [x] done · [!] blocked

---

## A — Research (background agents)

| ID | Task | Status | Output |
|---|---|---|---|
| A10 | Verify all keynote source URLs (resolve + right content) | [x] | research/verify-report.md |
| A20 | Harness-eng transcript — extract key quotes/patterns (harness-eng.txt already read) | [x] | notes below |
| A30 | GitLab Act 2 research + GitLab handbook engineering practices | [x] | research/gitlab-act2.md |
| A40 | Notable AI-assisted rewrites beyond Bun (Ladybird, others) + OSS relicensing concern | [x] | research/rewrites.md |
| A50 | Ralphing: origin, naming, downstream discussion, inner-loop framing | [x] | research/pair-programming-ralphing.md |
| A60 | Pair programming navigator/driver + knowledge transfer at boundaries + Simon Brown C4 | [x] | research/pair-programming-ralphing.md |

## B — Keynote v4 updates

| ID | Task | Status | Note |
|---|---|---|---|
| B10 | Source citations: verify URLs, add `[source]` footer per slide | [→] | A10 done; inline per slide in draft |
| B20 | Expand history (Slide 4) — GitHub tsunami data + 4-phase timeline detail | [x] | Slide 13 agent tsunami data; Slides 7-12 four phases |
| B30 | Open/close Act III with "practices for the maintainer" framing | [x] | New Slide 18 added as Act III opener |
| B40 | Add specs slide — PRD vs task breakdown, right level of detail + waterfall warning | [x] | Slide 20 expanded with waterfall warning + PRD→tasks framing |
| B50 | Slide 12 — APIs as boundaries + DSLs for type-safe constrained interactions | [ ] | deferred — type systems slide (21) covers constraints |
| B60 | Slide 11 — tests as guidance (API/arch usage) AND safety nets (self-steering) | [ ] | Slide 21 and navigator slide cover this; can expand |
| B70 | Slide 13 — ownership/accountability still with humans | [ ] | Slides 38/39 "what stays human" cover this |
| B80 | Add harness-eng "ship a spec" content (Ryan Lopopolo / OpenAI Frontier) | [x] | New Slide 21 added |
| B90 | GitLab Act 2 integration | [x] | New Slide 34 added (org restructure + handbook principles) |
| B100 | Expand exhaustion slide — pair programming parallel, ADHD/addiction, compensating | [x] | Slide 36 expanded with addiction pattern, navigator discipline |
| B110 | Add pair programming as explicit narrative (human=navigator, agent=driver) | [x] | New Slide 25 added (Kent Beck anchor) |
| B120 | Add learning/impact on learning slide (River + personalized courses) | [x] | New Slide 38 (Lehrwerkstatt / River) |
| B130 | Add future slide — parallel agents, hosted systems, emergent systems | [ ] | Slides 30-34 cover agent topologies/future |
| B140 | Reframe James Shore maintenance as opportunity (agents great at maintenance, GH Actions) | [ ] | Open question in keynote — one line to add to Slide 22 |
| B150 | Slide 24 — PM/design/support/security scaling under agent load | [ ] | deferred — Slide 35 security covers partially |
| B160 | Notable rewrites + OSS relicensing concern slide | [x] | Slides 32-33 (reversibility + chardet controversy) |
| B170 | Knowledge transfer at task boundaries (start/end framing, C4, show/tell) | [x] | Slide 28b added to notes file (briefing/handoff + C4 vocabulary) |
| B180 | Design patterns/DSLs as closing research note | [ ] | deferred |

## C — Blog series (10–15 weeks)

| ID | Task | Status | Note |
|---|---|---|---|
| C10 | Draft blog series: 10–15 titles + outlines | [x] | blog/blog-series-outline.md — 12 posts with full outlines |
| C20 | Blog 1 draft — "What Is Agentic Engineering?" | [ ] | outline done; draft pending |

## D — Priority reading list

| ID | Item | Link |
|---|---|---|
| D1 | Simon: vibe-AE convergence + normalization of deviance | https://simonw.substack.com/p/vibe-coding-and-agentic-engineering |
| D2 | Simon: Agentic Engineering Patterns guide | https://simonwillison.net/guides/agentic-engineering-patterns/ |
| D3 | Simon: James Shore maintenance costs | https://simonwillison.net/2026/May/11/james-shore/ |
| D4 | Simon: Mitchell Hashimoto / reversibility | https://simonwillison.net/2026/May/14/not-so-locked-in/ |
| D5 | Simon: Shopify Lehrwerkstatt | https://simonwillison.net/2026/May/11/learning-on-the-shop-floor/ |
| D6 | TW retreat PDF | research/thoughtworks-retreat.md |
| D7 | Harness engineering / ship a spec (Ryan Lopopolo) | research/harness-eng.txt · https://www.latent.space/p/harness-eng |
| D8 | GitLab Act 2 | https://simonwillison.net/2026/May/11/gitlab-act-2/ |
| D9 | Claire Vo / management skills | https://www.lennysnewsletter.com/p/how-openclaw-changed-my-life-claire-vo |
| D10 | Max Schoening / agency + malleable software | workshop/agentic-engineering-ideas.md |
| D11 | Simon: Lenny's Newsletter podcast highlights | https://simonwillison.net/2026/Apr/2/lennys-podcast/ |
| D12 | Workshop source files | workshop/workshop-intro.md · workshop/workshop-practices.md |
| D13 | Workshop slides | workshop/slides/agentic-engineering-workshop.md |

---

## A20 — Harness-eng notes (Ryan Lopopolo, OpenAI Frontier / Latent Space)

**Source**: https://www.latent.space/p/harness-eng  
**Key thesis**: "Ship a spec, not code" — the human writes specs and constraints; agents write all the code.

Key quotes and patterns for the keynote:
- "The only way I could do my job was to get the agent to do my job." — started with constraint: zero lines of code written by humans.
- 5 months, ~1M LOC, ~1500 PRs, team of 3, zero human-written code.
- "The only fundamentally scarce thing is the synchronous human attention of my team."
- **The inner loop constraint**: builds must complete in under 1 minute. Enforced by the agent — if build exceeds 1 min, decompose until it fits. Ratchet discipline.
- **Inverted entry point**: "Instead of setting up an environment to spawn the coding agent into, we spawn the coding agent as the entry point." Agent boots the stack itself.
- **Short AGENTS.md (100 lines) + skills**: table of contents pointing to skills, not a monolith. Each skill is a small scaffold.
- **Quality score artifact**: markdown table that a code review agent uses to assess all business logic against documented guardrails, propose follow-up work.
- **Durably encoding process knowledge**: when a bug is fixed, update the reliability docs to encode the invariant. Agent uses this for future code review.
- **Post-merge review**: humans review post-merge, not pre-merge. Review agents run on PR sync and must acknowledge all review feedback.
- **Convergence discipline**: reviewer agents biased toward merging (>P2 surfaced, not everything); author agents given optionality to defer or push back.
- "Models fundamentally crave text." Everything is represented as text — reliability docs, quality scores, tech tracker, skills.
- Human bottleneck framing: "systems thinking mindset — where is the agent making mistakes? Where am I spending my time? How can I not spend that time going forward?"

**For keynote**: Slide on "ship a spec, not code" — the spec is the input, the loop produces the code. Pairs with hone-ai demo. Also: the inner-loop optimization angle (builds under 1 min) reinforces the "practices for the agent as maintainer" frame.
