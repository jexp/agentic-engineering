# From Vibe Coding to Agentic Engineering

**Subtitle:** From fast personal prototypes to reliable production software

**Alternative titles:**

- "Vibe Coding Got You Here — Agentic Engineering Gets You There"
- "Beyond the Vibes: What Production Software Actually Needs"
- "Code Is Cheap Now — So What Becomes Expensive?"

---

## Abstract

Vibe coding changed the game. In a matter of minutes, anyone can turn an idea into a working prototype — no deep framework knowledge required. And that's genuinely wonderful: for personal tools, rapid exploration, learning new tech, and democratizing software creation. But the moment your vibe-coded prototype needs to serve real users, integrate into existing systems, or survive its first security audit, the vibes run out.

This keynote maps the journey from vibe coding to what Simon Willison and others have started calling *agentic engineering* — the discipline of building production-grade software with AI coding agents while remaining accountable for every line they produce. Drawing on 25+ years of experience with software design patterns, TDD, domain-specific languages, and software architecture, Michael shows that the practices which matter most in the age of AI aren't new — they're the ones we always knew mattered but were too expensive to do consistently: rigorous testing, clean API design, spec-driven development, security review, and thorough documentation.

The talk introduces a provocative reframe borrowed from Dan North and Philip Armour: software isn't a product — it's captured knowledge. The code is the least important artifact; the learning, the behavioral specifications, and the tested interfaces are what endure. If your components have well-specced, well-tested APIs, their internals become *throwaway* — rewritable anytime with new tech, new models, or simply better understanding. AI agents make this vision practical for the first time.

You'll leave with a clear mental model of the spectrum from vibe coding through agentic engineering, concrete patterns you can adopt Monday morning, and a renewed appreciation for why the craft of software architecture matters more — not less — when an AI can produce ten thousand lines of code before lunch.

---

## Speaker Bio

Michael Hunger is VP of Product Innovation / AI at Neo4j, where he has spent over 16 years working on developer experience, query language design, and applied graph + AI. A long-time contributor to the software patterns community, Michael reviewed several of Martin Fowler's books and has deep roots in TDD, refactoring, domain-specific languages, and the pattern ideas of Christopher Alexander. Today he focuses on making AI and knowledge graphs work together — for code intelligence, agent memory, and production-grade AI applications.

---

## Slide Narrative (30 minutes)

### Act I — The Vibe Coding Revolution (7 min)

**Slide 1 — Opening: "95% of the code I produce, I didn't type myself"** (1 min)
Open with Simon Willison's quote from the Lenny Rachitsky podcast. Set the scene: we're in a world where a 25-year veteran writes most of his code on his phone, walking his dog. This is real. This is now.

**Slide 2 — What Vibe Coding Actually Is** (2 min)
Andrej Karpathy's original definition: you don't look at the code, you go on vibes. Describe the spectrum — from "non-programmer builds a tool for themselves" to "senior engineer prototyping three approaches before committing." Both are valid. Both are vibe coding.

**Slide 3 — The Gift of Vibe Coding** (2 min)
Celebrate what's genuinely great:

- Democratization — anyone can automate tedious tasks
- Prototyping is almost free — fire off three variants, pick the best
- Learning new frameworks/languages without the months-long on-ramp (Willison's AppleScript example)
- Personal tools with no downside risk — "if the only person who gets hurt by bugs is you, go wild"

**Slide 4 — The Inflection Point: November 2025** (2 min)
Brief history: GPT 5.1 and Claude Opus 4.5 crossed a threshold. Previously agents "mostly worked, most of the time." Now they "almost always do what you told them to do" — and that difference changes everything. Engineers came back from the holidays, tried the new models, and realized the game had shifted.

---

### Act II — Where the Vibes Run Out (6 min)

**Slide 5 — "Writing Code Is Cheap Now"** (2 min)
Willison's core insight: code has always been expensive, and all our engineering habits — estimation, planning, feature prioritization — are built around that constraint. When writing code takes 1/100th the time, the bottleneck moves. Where does it move *to*?

**Slide 6 — Software Is Not a Product, It's Knowledge** (2 min)
Philip Armour's reframe from "The Laws of Software Process": software is the fifth knowledge storage medium (after DNA, brains, hardware, books). A working system is proof that you've acquired the knowledge. The code is a by-product of learning.

Connect to Dan North's Deliberate Discovery: the biggest risk on any project is *ignorance* — things you don't know you don't know (2nd Order Ignorance). The purpose of process isn't to produce code; it's to surface questions.

**AI accelerates code production massively. But it doesn't accelerate *learning* unless you deliberately design your process to learn.**

**Slide 7 — The Responsibility Boundary** (2 min)
Willison's rule of thumb: vibe code for yourself → go wild. Vibe code for others → stop. The challenge: knowing where that line is requires expertise. Scraping too aggressively, missing security holes, leaking data, breaking APIs — there are many ways to cause damage if you don't know what you're doing. This is the gap that agentic engineering fills.

---

### Act III — Agentic Engineering: The Discipline (12 min)

**Slide 8 — Defining Agentic Engineering** (1 min)
Professional software development using coding agents, where the engineer remains accountable for the result. You may not type the code, you may not even read every line — but you are responsible for the system's correctness, security, and maintainability. The key difference from vibe coding: *you care about the code's qualities, not just its behavior.*

**Slide 9 — The Practices That Now Matter More** (1 min)
Overview slide listing the disciplines. These aren't new — they're the practices we always said mattered but were often too expensive to do consistently. AI agents change the economics:

1. Spec-driven development
2. Task decomposition and controlled execution
3. API design and software architecture
4. Test-driven development (red/green TDD)
5. Security review and penetration testing
6. Usage simulation and QA
7. Code and feature review
8. Documentation
9. Integration with existing systems

**Slide 10 — Spec-Driven Development & Task Decomposition** (2 min)
Before you let an agent touch code, write the spec. Break the work into small, well-defined tasks. Each task gets executed following a consistent model — no exceptions, no "I'll just quickly vibe code this one." The spec is the knowledge artifact that survives; the code is replaceable.

Connect to Dan North's insight: if components have well-specced, well-tested APIs for their behavior, the *inside* is throwaway. You can rewrite internals anytime with new tech, better understanding, or simply to shed accumulated cruft. AI makes rewriting cheap — so optimize for the spec and the tests, not the implementation.

**Slide 11 — Red/Green TDD with Agents** (2 min)
Willison's most impactful single pattern. Five words that materially improve agent output: "Use red/green TDD." The agent writes the test first, watches it fail, implements until it passes. Agents are phenomenally good at sticking to this discipline (even though many human engineers resist it). Tests accumulate into a safety net that lets you confidently tell agents to build new features without breaking old ones.

Key shift: verbose test suites used to be a code smell (too expensive to maintain). Now the agent maintains them. A hundred tests for a small library? That's fine — code is cheap.

**Slide 12 — The Dark Factory and QA Simulation** (2 min)
StrongDM's experiment: nobody writes code, nobody reads code, but the software is security-critical. Their answer: swarms of simulated users making requests 24/7, simulated Slack and Jira environments built by agents, continuous behavioral testing at scale. This is the factory with the lights off — but it requires *more* engineering discipline, not less.

Parallel to Willison's point: the Claude C Compiler project (Nicholas Carlini / Anthropic) succeeded because it had a conformance test suite (test262) and could compare output byte-for-byte with the existing C++ implementation. *Having an existing trusted implementation to test against is a huge unlock for agentic engineering.*

**Slide 13 — Security, Pentesting & the Lethal Trifecta** (2 min)
Agents are getting good at security penetration testing. Anthropic discovered and responsibly reported ~100 vulnerabilities in Firefox. But the flip side is prompt injection and the lethal trifecta (private data + malicious instructions + exfiltration). Production systems need to account for this — your agent is a new attack surface.

**Slide 14 — Architecture, Patterns & the Graph of Software** (2 min)
Christopher Alexander's original insight: patterns are not templates — they're solutions to recurring problems in context. That idea transfers directly to how we structure agent-built code. Good architecture — clean boundaries, well-defined interfaces, separation of concerns — matters *more* when code is cheap, because cheap code without structure is just cheap debt.

Light Neo4j touch: software itself is a graph — code, dependencies, call chains, commits, architectures. ThoughtWorks' CodeConcise (published on martinfowler.com) combines AST parsing with a knowledge graph to let LLMs reason about legacy codebases structurally, not just textually — enabling capability mapping, dead code detection, and idiomatic translation at scale. Tools like codebase-memory-mcp take a similar approach: indexing a repo into a graph that agents can query structurally (call chains, architecture overviews) at 120x fewer tokens than file-by-file reading. The graph becomes *agent memory* — persistent, structural context that survives across sessions.

---

### Act IV — The Human in the Loop (5 min)

**Slide 15 — "Hoarding Things You Know How to Do"** (2 min)
Willison's career advice, amplified by AI: build a backlog of things you've tried — frameworks explored, patterns applied, benchmarks run. GitHub repos of little tools (193 and counting), research projects where an agent actually ran the code and plotted the results. Each one is a reusable building block. AI lets you accumulate these faster than ever.

Connect to Armour's 0th Order Ignorance: these artifacts represent knowledge you've acquired and can display. They're your competitive advantage as an engineer — the things only you have tried in combination.

**Slide 16 — The Exhaustion Problem** (1.5 min)
Willison: "By 11 AM, I am wiped out." Steve Yegge: "AI has turned us all into Jeff Bezos — automating the easy work and leaving us with all the difficult decisions." Running four parallel agents is cognitively brutal. The bottleneck has moved from typing to thinking. The craft of agentic engineering includes knowing your own limits, not burning out, and resisting the "my agents could be running" anxiety.

**Slide 17 — What Stays Human** (1.5 min)
The things AI can't do (yet): agency — deciding what problems to take on. Usability testing with real humans. The judgment call of "this prototype *feels* right." The ability to look at three AI-generated variants and know which one solves the actual business problem. The ability to treat AI as an unreliable source (journalists are naturally good at this). The learning itself — which is the real product, not the code.

---

### Closing (2 min)

**Slide 18 — The Spectrum, Not the Binary** (1 min)
Visual: a spectrum from "Vibe Coding" on the left to "Agentic Engineering" on the right. Both are valid. The question isn't which one you do — it's knowing when you're on which part of the spectrum and whether that's appropriate for what you're building. Prototype for yourself? Vibe away. Shipping to users? Slide right.

**Slide 19 — Your Monday Morning Checklist** (0.5 min)

- Start projects with a thin template (one test, your preferred style)
- Write the spec before the code
- Tell agents: "Use red/green TDD"
- Run agents in safe environments (cloud, containers)
- Review via PRs, not by watching the agent type
- Hoard your learnings — every prototype is a building block
- Be ambitious — then be disciplined

**Slide 20 — "I don't just want cheap code. I want really good code."** (0.5 min)
Close with Willison's aspiration: the goal isn't to move faster and produce the same quality. The goal is to produce *better* software — fewer bugs, more features, higher quality — because we're harnessing these tools with the craft they deserve.

---

## Key References

- Simon Willison — [Agentic Engineering Patterns](https://simonwillison.net/guides/agentic-engineering-patterns/) (ongoing book-on-blog)
- Simon Willison on Lenny's Podcast — [An AI State of the Union](https://www.lennysnewsletter.com/p/an-ai-state-of-the-union)
- Dan North — [Deliberate Discovery](https://dannorth.net/tags/deliberate-discovery/) and "Software That Fits in Your Head" (Replaceable Component Architecture)
- Philip G. Armour — [The Five Orders of Ignorance](https://cacm.acm.org/opinion/the-five-orders-of-ignorance/) (CACM, 2000) and *The Laws of Software Process* (Auerbach, 2003)
- Christopher Alexander — *A Pattern Language* / *The Timeless Way of Building*
- ThoughtWorks / Fowler — [Legacy Modernization meets GenAI](https://martinfowler.com/articles/legacy-modernization-gen-ai.html) (CodeConcise + knowledge graph approach)
- DeusData — [codebase-memory-mcp](https://deusdata.github.io/codebase-memory-mcp/) (graph-based code intelligence for AI agents)
- Kellan Elliott-McCrea — "Code has always been the easy part"
- Steve Yegge — "The AI Vampire" (on agent fatigue and cognitive burden)
- StrongDM — dark factory / simulated QA experiments
- Ladybird browser — [Adopts Rust with AI assistance](https://ladybird.org/posts/adopting-rust/) (conformance suite as agentic engineering enabler)
- Nicholas Carlini / Anthropic — Claude C Compiler; Chris Lattner's review
