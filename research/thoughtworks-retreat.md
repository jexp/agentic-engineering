# Thoughtworks Future of Software Engineering Retreat
## Mining notes for workshop & keynote

**Source**: [Thoughtworks Retreat Key Takeaways PDF](https://www.thoughtworks.com/content/dam/thoughtworks/documents/report/tw_future%20_of_software_development_retreat_%20key_takeaways.pdf)  
**Martin Fowler bliki**: [FutureOfSoftwareDevelopment](https://martinfowler.com/bliki/FutureOfSoftwareDevelopment.html)  
**Date**: February 2026 (Deer Valley, Utah)  
**Format**: ~50 invited senior practitioners — Thoughtworkers, analysts, enterprise clients — one-and-a-half day Open Space conference. **Chatham House Rule** (no names/affiliations attributed).

---

## TL;DR — most useful new concepts for the workshop

1. **"Where does the rigor go?"** — the single biggest question. Engineering quality doesn't disappear when AI writes the code; it *migrates*. Five named destinations. Drops into [`workshop-practices.md`](../workshop/workshop-practices.md) as the organizing frame for the whole practices section.
2. **The Middle Loop** — a new unnamed category of supervisory engineering work between inner-loop coding and outer-loop delivery. Nobody in industry has named this yet. Strong workshop slide candidate for [`workshop-harnesses.md`](../workshop/workshop-harnesses.md).
3. **TDD as the strongest form of prompt engineering** — not a testing philosophy; a verification strategy for non-deterministic generation. Drops into [`workshop-practices.md`](../workshop/workshop-practices.md) Slide 3.
4. **Risk tiering as the new core engineering discipline** — not "did someone review this code?" but "is our verification proportional to the blast radius?" Major framing shift. Drops into [`workshop-practices.md`](../workshop/workshop-practices.md) and keynote.
5. **Productivity/experience paradox** — productivity and developer experience are decoupling. Organizations can get more output while developers report lower satisfaction. Drops into [`workshop-mental-safety.md`](../workshop/workshop-mental-safety.md).
6. **Cognitive debt** — technical debt is becoming cognitive debt: the gap between system complexity and human understanding. New named concept that resonates with engineers. Drops into keynote and intro.
7. **AI velocity debt** — AI-enabled productivity gains offset by stability losses from large batch sizes (regression to waterfall-like patterns). Rachel Laycock framing. Drops into keynote "what can go wrong" thread.
8. **Juniors more valuable, mid-levels at risk** — counters the "AI replaces juniors" narrative. AI gets juniors past the initial net-negative phase faster. Mid-levels who came up in the hiring boom may lack fundamentals. Drops into [`workshop-intro.md`](../workshop/workshop-intro.md) and [`workshop-mental-safety.md`](../workshop/workshop-mental-safety.md).
9. **Agent topologies + Conway's Law** — Conway's Law didn't retire; it got more complicated. Drops into keynote and [`workshop-harnesses.md`](../workshop/workshop-harnesses.md).
10. **"Agent experience" reframe** — instead of "developer experience," name it "agent experience" — wallets open faster, and the overlap with human-favorable conditions is nearly complete. Cheeky slide for [`workshop-mental-safety.md`](../workshop/workshop-mental-safety.md).

---

## Theme 1: Where does the rigor go?

The most-discussed question of the retreat. Surfaced in nearly every session.

Engineering rigor doesn't disappear when AI writes code — it migrates to five destinations:

**1. Upstream: spec review**  
Teams shifting review from code to the plan that precedes it. "Pre-reviewing the plans and post-reviewing engineering rather than the code itself." Bad specs produce bad code at scale.  
Practical implication: traditional user stories are too vague. Teams rediscovering EARS (Easy Approach to Requirements Syntax), state machines, decision tables — not new, but rediscovered because they give agents enough precision.

**2. Into test suites as first-class artifacts**  
TDD produces dramatically better results from AI agents. The mechanism: TDD prevents agents writing tests that verify broken behavior. When tests exist before code, agents cannot cheat.  
*"I've gotten better results from TDD and agent coding than I've ever gotten anywhere else, because it stops a particular mental error where the agent writes a test that verifies the broken behavior."*  
Reframes TDD as a form of prompt engineering. Tests become deterministic validation for non-deterministic generation.

**3. Into type systems and constraints**  
Strong interest in using language features to constrain AI-generated code. Make incorrect code *unrepresentable* rather than reviewing it after generation.  
Key separation: **specifications** describe what should change; **constraints** define bounded contexts (what must not be touched). Constraints limit blast radius. When a constraint must be broken, it signals a new system boundary → refactor.

**4. Into risk mapping**  
Not all code carries the same risk. Tier code by business blast radius: internal tools vs. external-facing services vs. safety-critical systems.  
The new core question: *"What is the blast radius if this code is wrong, and is our verification proportional to that risk?"*  
Moves engineering from craft model (every line hand-reviewed) to risk management model (verification investment matches exposure).

**5. Into continuous comprehension**  
Code review has served as mentorship, shared understanding, codebase familiarity — not just a quality gate. Losing that channel without replacing it creates a comprehension gap that compounds.  
Alternatives discussed: weekly architecture retrospectives, ensemble programming, AI-assisted comprehension tools.  
*"Paired programming solves all of this. If it's important to understand the system, then do it all the time."*

---

## Theme 2: The Middle Loop

**The strongest first-mover concept from the retreat. Nobody in industry has named this yet.**

Two traditional loops:
- **Inner loop** — developer's personal cycle: write, test, debug
- **Outer loop** — broader delivery: CI/CD, deployment, operations

A **third loop** is forming: supervisory engineering work between them. Directing, evaluating, and fixing agent output. Requires:
- Decomposing problems into agent-sized work packages
- Calibrating trust in agent output
- Recognizing plausible-looking but incorrect results
- Maintaining architectural coherence across parallel agent streams

Skills of practitioners excelling in the middle loop:
- Think in terms of *delegation and orchestration*, not direct implementation
- Strong mental models of system architecture
- Can rapidly assess output quality without reading every line

**Career impact:** Creates an identity crisis for developers who fell in love with programming. Many were hired to translate tickets into code. That work is disappearing.

Historical parallel: 1992 — engineers hand-coded polygon rendering. 1994 — pushed to hardware, the job became animation and lighting. Today — custom physics and game worlds. Each time the abstraction rose, those who insisted they were "hired to render polygons" were left behind.

**Product management side:** If developers now think more about what to build and why, they're doing PM work. One large tech company is researching whether the PM role needs a new name. Others are training all PMs to work in Markdown inside developer tools.

---

## Theme 3: Agent Topologies + Conway's Law

*"We optimized the software delivery process for humans. Now that it's not just humans, we have to ask what organizing actually means."*

**Agent topologies** = Team Topologies framework extended for AI agents. Agents can be duplicated instantly, deployed across multiple teams without onboarding friction. But:

**The speed mismatch:** AI tools clear backlogs in days → teams then hit walls of cross-team dependencies, architecture reviews, human-speed decision-making. Result: same delivery speed, more frustration, because the bottleneck has moved from engineering to *everything else*.

**Agent drift:** Agents that learn from context diverge over time. The database agent on the e-commerce backend accumulates different patterns than the one on the ERP system. Mirrors human team-specific norms, but on an accelerated timeline.

**Decision fatigue as bottleneck:** If agents produce work faster than leaders can review and approve, the constraint shifts from production to decision-making capacity. Middle managers become approval bottlenecks. Already happening: agents generating job specs, code fixes, feature implementations faster than anyone can say yes.

---

## Theme 4: Self-Healing Systems

**Ambition is real. Prerequisites are far from met.**

Self-healing requires foundations most orgs lack:
- Clear ledger of every change (agent auditability)
- OS for agents with identity controls + permission boundaries
- Strong generic mitigation capabilities (rollback, feature flags) working without code changes
- Fitness functions defining "healthy" in terms agents can evaluate

**The latent knowledge problem:** Senior engineers bring decades of pattern-matching that's almost never documented. To replicate this for agents: build an "agent subconscious" — a knowledge graph from years of post-mortems and incident data.

**The incident commander problem:** Human commanders challenge assumptions and push back on comfortable hypotheses. LLMs tend toward positive reinforcement. Solution proposed: "angry agents" specifically designed to challenge the dominant hypothesis.

**Agent coordination risks:** Multiple agents fixing the same issue can create feedback loops. Real example: agent with a 500-line file limit linter responded by making individual lines longer — technically satisfying the rule while violating the principle.

---

## Theme 5: The Human Side

**Productivity/experience paradox:**  
Developer experience defined by flow state, feedback loops, cognitive load. These are now *decoupling* from productivity. Organizations can achieve more output even while developers report lower satisfaction and more cognitive load.  
Business case for developer experience investment weakens — unless we redefine it.  
**Reframe: call it "agent experience."** Wallets open faster. Overlap with human-favorable conditions is nearly complete.

**Staff engineers:**  
- Use AI tools *less* than juniors but *save more time per week* when they do — broader context makes them more effective supervisors
- New recommended role: **friction killers** — identifying and removing impediments that slow both human and agent work
- Many have learned helplessness from years of being told there's no budget for improvements they recommend

**Junior developers — more valuable, not less:**  
- AI gets juniors past the initial net-negative phase faster → they're profitable sooner
- They're better at AI tools than seniors (no habits to unlearn)
- Real concern: **mid-level engineers** from the decade-long hiring boom who may lack fundamentals. Retraining is genuinely hard. No organization has solved it yet.

**Future of product management:**  
Nobody at the retreat could define what PMs will do. AI is exposing *existing* dysfunctions in the PM-developer relationship, not creating new ones — just making them more expensive to ignore.

---

## Theme 6: Technical Foundations

**Programming languages for agents:**  
Every existing language was designed for humans. Retreat converged on: *what is good for AI is good for humans.* Languages making incorrect code unrepresentable (strong types, restricted computation, formal constraints) help both agents and human verifiers.  
More radical possibility: source code becomes a *transient artifact* — generated on demand, never stored. Retreat was divided. Counter-argument: deterministic validation requires a stable artifact to test against.

**Semantic layers and knowledge graphs:**  
Technologies that failed for decades suddenly relevant as grounding layer for domain-aware agents. A large telecom's entire domain ontology: ~286 concepts. Using LLMs to auto-generate event storming artifacts (commands, events, aggregates, policies) from existing code. Human experts validate and correct — compressing weeks of discovery into days.

**The agentic operating system:**  
What it needs:
- Agent identity + permission management
- Memory + context-window management
- Work ledger: future/current/past work with attributes (required skills, acceptance criteria, SLOs, cost constraints)
- Governance paths through agent capabilities and compliance requirements

Core insight: an agent is more than its persona or current context — it *includes the history of work it has performed*. Models are fungible within an agent (swap one LLM for another), but changing a model fundamentally alters behavior and must be tracked.

---

## Theme 7: Security

**Dangerously behind. The security session had low attendance — reflecting the broader industry pattern of treating security as something to solve after the technology "works."**

Most vivid example: granting an agent email access enables password resets → account takeovers. Full machine access for dev tools = full machine access for anything the agent decides to do.

Three priorities:
1. Security by design — safe behavior easy, unsafe behavior hard (platform engineering responsibility)
2. Cross-industry coalitions for interoperable agent security standards
3. AI-enabled defense mechanisms that match the speed of AI-enabled attacks

---

## Theme 8: Agile Evolution + Agent Swarms

**Agile is evolving, not dying:**  
- Some teams compressing to one-week sprints, using AI to automate end-of-sprint ceremonies
- XP renaissance: pair programming, ensemble development, CI are being rediscovered because they create tight feedback loops that agent-assisted work requires
- **Real threat: governance.** Faster teams hit the same approval gates sooner. Must reform governance alongside development practices

**Batch size regression (critical):**  
AI makes it easy to produce large changesets → teams reverting to waterfall-like patterns: large, infrequent releases. *Direct reversal of a decade of DORA research.* The retreat flagged this as an active regression needing industry attention.  
Rachel Laycock framing: "AI velocity debt accelerator."

**Agent swarms:**  
First barrier is mental, not technical — engineers trained in sequential decomposition struggle to conceptualize parallel agent work.  
Key insight: perfect accuracy from individual agents matters less than *collective convergence toward a goal*.  
Most common enterprise pattern is NOT swarming — it's "patrol workers on loops": agents running ETL transforms, data quality checks, business process monitors on continuous cycles. The unsexy work. Organizations with strong, well-designed APIs are significantly better positioned for both patterns.

---

## Quote bank

```
"We kept asking the same question in every room: if AI handles the code, where does 
 the engineering actually go? Nobody had the same answer. But everybody agreed the 
 question is urgent."
  — Retreat participant (Chatham House Rule)

"I've gotten better results from TDD and agent coding than I've ever gotten anywhere
 else, because it stops a particular mental error where the agent writes a test that 
 verifies the broken behavior."
  — Retreat participant

"Paired programming solves all of this. If it's important to understand the system,
 then do it all the time. You don't do it in little phases where you have your code 
 review. Constantly trying to understand what this code is doing."
  — Retreat participant

"We optimized the software delivery process for humans. Now that it's not just 
 humans, we have to ask what organizing actually means."
  — Retreat participant

"The retreat didn't produce a roadmap. It produced a shared understanding that the 
 map is being redrawn and that the people best [positioned are those engaging with 
 the hard questions now]."
  — Thoughtworks closing summary
```

---

## Per-section reuse mapping

| Workshop file | Slide | Thoughtworks insight | Why it works |
|---|---|---|---|
| [`workshop-intro.md`](../workshop/workshop-intro.md) | Opening frame | "Where does the rigor go?" as the central question of the moment | Immediately credible — senior practitioners, not hype-cycle sources |
| [`workshop-intro.md`](../workshop/workshop-intro.md) | Junior/mid/senior split | Juniors more valuable; mid-levels at risk (not the narrative in the room) | Counterintuitive — audience will lean in |
| [`workshop-harnesses.md`](../workshop/workshop-harnesses.md) | New slide | The Middle Loop — naming the new supervisory work | First-mover concept; nobody has named it yet |
| [`workshop-practices.md`](../workshop/workshop-practices.md) | Organizing frame | "Where does the rigor go?" + 5 destinations as section spine | Gives the practices section a coherent narrative arc |
| [`workshop-practices.md`](../workshop/workshop-practices.md) | TDD slide | TDD as the strongest form of prompt engineering | Reframes something the audience already knows as newly important |
| [`workshop-practices.md`](../workshop/workshop-practices.md) | Review slide | Risk tiering: blast radius proportional to verification investment | Moves engineers from craft to risk management model |
| [`workshop-practices.md`](../workshop/workshop-practices.md) | Code review | Code review unbundled — 4 functions (mentorship, consistency, correctness, trust) each need a new home | Concrete deconstruction, not abstract hand-waving |
| [`workshop-mental-safety.md`](../workshop/workshop-mental-safety.md) | New slide | Productivity/experience paradox — decoupling | Names what people in the room will recognize from their own orgs |
| [`workshop-mental-safety.md`](../workshop/workshop-mental-safety.md) | "Agent experience" reframe | Stop calling it developer experience; call it agent experience | Darkly funny but makes a real point |
| [`workshop-mental-safety.md`](../workshop/workshop-mental-safety.md) | Staff engineer identity | Friction killers, learned helplessness, middle-loop identity crisis | Direct relevance to the senior engineers in the room |
| [`vibecode-keynote-v3.md`](../keynote/vibecode-keynote-v3.md) | "What changes" slide | Conway's Law didn't retire — agent topologies | Extends a known mental model engineers already have |
| [`vibecode-keynote-v3.md`](../keynote/vibecode-keynote-v3.md) | Warning beat | Batch size regression: AI makes waterfall attractive again | Concrete danger, DORA framing, surprising |
| [`vibecode-keynote-v3.md`](../keynote/vibecode-keynote-v3.md) | Closing | "Cognitive debt" — new named concept | Lands harder than "technical debt" because it names the human cost |

---

## Open questions

- [ ] "The middle loop" — does this concept need a better name before it goes on a slide? Lean: use their framing ("middle loop") and credit the retreat — it's more credible as a field observation than a coined term.
- [ ] The batch-size regression point (AI → waterfall reversion) is striking but will meet skepticism. Should we present it as an observed risk or a confirmed trend? Lean: observed risk — we don't have data to confirm.
- [ ] "Agent experience" reframe is cheeky but might land wrong with a safety-focused audience. Gauge the room before using it.
- [ ] The "angry agents" concept (challenge-the-hypothesis agents for incident response) is interesting but might be too far out for the 4hr workshop. Better in a keynote as a glimpse of where things go.
- [ ] [VERIFY] Rachel Laycock's "AI velocity debt accelerator" framing — is there a standalone article or only the Fowler bliki reference?
