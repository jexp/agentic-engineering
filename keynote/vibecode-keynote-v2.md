# From Vibe Coding to Agentic Engineering

**Subtitle:** From fast personal prototypes to reliable production software

**Alternative titles:**

- "Vibe Coding Got You Here — Agentic Engineering Gets You There"
- "Beyond the Vibes: What Production Software Actually Needs"
- "Code Is Cheap Now — So What Becomes Expensive?"

---

## Abstract

Vibe coding changed the game. In a matter of minutes, anyone can turn an idea into a working prototype — no deep framework knowledge required. And that's genuinely wonderful: for personal tools, rapid exploration, learning new tech, and democratizing software creation. But the moment your vibe-coded prototype needs to serve real users, integrate into existing systems, or survive its first security audit, the vibes run out.

This keynote maps the journey from vibe coding to what Andrej Karpathy, Simon Willison, Addy Osmani and others have started calling *agentic engineering* — the discipline of building production-grade software with AI coding agents while remaining accountable for every line they produce. Drawing on 25+ years of experience with software design patterns, TDD, domain-specific languages, and software architecture, Michael shows that the practices which matter most in the age of AI aren't new — they're the ones we always knew mattered but were too expensive to do consistently: rigorous testing, clean API design, spec-driven development, security review, and thorough documentation.

The talk introduces a provocative reframe borrowed from Dan North and Philip Armour: software isn't a product — it's captured knowledge. The code is the least important artifact; the learning, the behavioral specifications, and the tested interfaces are what endure. If your components have well-specced, well-tested APIs, their internals become *throwaway* — rewritable anytime with new tech, new models, or simply better understanding. AI agents make this vision practical for the first time.

You'll leave with a clear mental model of the spectrum from vibe coding through agentic engineering, concrete patterns you can adopt Monday morning, and a renewed appreciation for why the craft of software architecture matters more — not less — when an AI can produce ten thousand lines of code before lunch.

---

## Speaker Bio

Michael Hunger is VP of Product Innovation / AI at Neo4j, where he has spent over 16 years working on developer experience, query language design, and applied graph + AI. A long-time contributor to the software patterns community, Michael reviewed several of Martin Fowler's books and has deep roots in TDD, refactoring, domain-specific languages, and the pattern ideas of Christopher Alexander. Today he focuses on making AI and knowledge graphs work together — for code intelligence, agent memory, and production-grade AI applications.

---

## Slide Narrative (30 minutes)

### Act I — The Vibe Coding Revolution (7 min)

**Slide 1 — Opening: "95% of the code I produce, I didn't type myself"** (1 min)
Open with Simon Willison's statement from the Lenny Rachitsky podcast. Set the scene: we're in a world where a 25-year veteran writes most of his code on his phone, walking his dog. This is real. This is now.

**Slide 2 — What Vibe Coding Actually Is** (2 min)
Andrej Karpathy's original definition (Feb 2025): you don't look at the code, you go on vibes. One year later (Feb 2026), Karpathy himself retired the term for professional work, saying his "shower thoughts throwaway tweet" had been stretched beyond recognition. Addy Osmani captured why: "vibe coding" became a suitcase term — people use it to describe everything from a weekend hack to a disciplined agent-driven workflow. These are fundamentally different activities.

Describe the spectrum — from "non-programmer builds a tool for themselves" to "senior engineer prototyping three approaches before committing." Both are valid. Both can be called vibe coding. But conflating them causes real confusion — and real damage.

**Slide 3 — The Gift of Vibe Coding** (2 min)
Celebrate what's genuinely great:

- Democratization — anyone can automate tedious tasks and get a computer to do stuff for them
- Prototyping is almost free — fire off three variants, pick the best (Willison: "any feature I want to design, I'll prototype three different ways")
- Learning new frameworks/languages without the months-long on-ramp (Willison's AppleScript example: "the two to three month initial learning curve has been shaved right down")
- Personal tools with no downside risk — "if the only person who gets hurt by bugs is you, go wild"
- Coming to meetings with a working prototype instead of a slide deck

**Slide 4 — The Inflection Point: November 2025** (2 min)
Brief history: GPT 5.1 and Claude Opus 4.5 crossed a threshold. Previously agents "mostly worked, most of the time." Now they "almost always do what you told them to do" — and that difference changes everything. Engineers came back from the holidays, tried the new models, and realized the game had shifted. All of 2025, both Anthropic and OpenAI had thrown everything at making models better at code — reasoning, reinforcement learning, coding-specific training. The November models were the payoff.

---

### Act II — Where the Vibes Run Out (6 min)

**Slide 5 — "Writing Code Is Cheap Now"** (2 min)
Willison's core insight, now echoed across the industry: code has always been expensive, and all our engineering habits — estimation, planning, feature prioritization — are built around that constraint. Addy Osmani's "Factory Model" essay makes the same point: the history of software engineering is the history of raising abstraction, and we just jumped another level.

When writing code takes 1/100th the time, the bottleneck moves. Willison: "We've taken the writing code bit and we've massively accelerated that. Now the bottlenecks are everywhere else." Where exactly?

**Slide 6 — Software Is Not a Product, It's Knowledge** (2 min)
Philip Armour's reframe from "The Laws of Software Process" (CACM, 2000): software is the fifth knowledge storage medium (after DNA, brains, hardware, books). A working system is proof that you've acquired the knowledge. The code is a by-product of learning. "A functioning system is the by-product of the activity of finding things out."

Connect to Dan North's Deliberate Discovery: the biggest risk on any project is *ignorance* — specifically 2nd Order Ignorance (things you don't know you don't know). The purpose of process isn't to produce code; it's to surface questions. Methodologies give you questions, not answers.

**AI accelerates code production massively. But it doesn't accelerate *learning* unless you deliberately design your process to learn.**

This connects directly to North's "Replaceable Component Architecture": if you have small enough components with well-specced, well-tested APIs for their behavior, the *inside* of those components is throwaway. You can rewrite internals anytime with new tech, new learnings, shedding accumulated cruft. What endures are the learnings about the business process and the behavioral coverage. AI makes this vision practical — rewriting is now cheap. So optimize for the spec and the tests, not the implementation.

**Slide 7 — The Responsibility Boundary** (2 min)
Willison's rule of thumb: vibe code for yourself → go wild. Vibe code for others → stop. The Turing College analysis puts it bluntly: "It demos great, then reality arrives." Amazon ordered a 90-day reset on code deployment controls after incidents in Q3 2025 tied to insufficiently safeguarded AI-generated changes.

The challenge: knowing where that line is requires expertise. Scraping too aggressively, missing security holes, leaking data, breaking APIs — there are many ways to cause damage if you don't know what you're doing. As Osmani wrote: "When you tell a CTO you're 'vibe engineering' their payment system, you can see the concern on their face."

This is the gap that agentic engineering fills.

---

### Act III — Agentic Engineering: The Discipline (12 min)

**Slide 8 — Defining Agentic Engineering** (1.5 min)
Karpathy's Feb 2026 reframe, now widely adopted: "'Agentic' because the new default is that you are not writing the code directly 99% of the time, you are orchestrating agents who do and acting as oversight. 'Engineering' to emphasize that there is an art & science and expertise to it."

Professional software development using coding agents, where the engineer remains accountable for the result. You may not type the code, you may not even read every line — but you are responsible for the system's correctness, security, and maintainability. The key difference from vibe coding: *you care about the code's qualities, not just its behavior.*

Osmani's litmus test: "If you can't explain what a module does, it doesn't go in."

The irony: AI-assisted development actually *rewards* good engineering practices more than traditional coding does. The better your specs, tests, and architecture, the better the agent performs.

**Slide 9 — The Practices That Now Matter More** (1 min)
Overview slide. These aren't new — they're the practices we always said mattered but were often too expensive to do consistently. AI agents change the economics:

1. Spec-driven development & task decomposition
2. API design and software architecture
3. Test-driven development (red/green TDD)
4. Security review and penetration testing
5. Usage simulation and QA
6. Code and feature review
7. Documentation
8. Integration with existing systems

**Slide 10 — Spec-Driven Development & Task Decomposition** (2 min)
Before you let an agent touch code, write the spec. Osmani's advice: "Write a design doc or spec — sometimes with AI assistance. Break the work into well-defined tasks. Decide on the architecture. This is the part vibe coders skip, and it's exactly where projects go off the rails."

Each task gets executed following a consistent model — no exceptions, no "I'll just quickly vibe code this one." The spec is the knowledge artifact that survives; the code is replaceable. Osmani: "Experienced folks often write good documentation first and the model may be able to build the matching implementation from that input alone."

Connect back to North/Armour: the spec captures your 0th Order Ignorance (things you know). Tests capture your behavioral expectations. Together, they're the durable artifacts. The code is the proof, not the product.

**Slide 11 — Red/Green TDD with Agents** (2 min)
Willison's most impactful single pattern. Five words that materially improve agent output: "Use red/green TDD." The agent writes the test first, watches it fail, implements until it passes. Osmani calls testing "the single biggest differentiator between agentic engineering and vibe coding."

Key shift: verbose test suites used to be a code smell (too expensive to maintain). Now the agent maintains them. A hundred tests for a small library? That's fine — code is cheap. Willison: "updating a thousand lines of tests is now the job of the coding agent."

Ladybird browser example: they ported their JavaScript engine from C++ to Rust using agents, producing 25,000 lines of Rust in two weeks. Zero regressions — because they had the test262 conformance suite. "Having an existing conformance testing suite of that quality is a huge unlock for agentic engineering."

**Slide 12 — The Dark Factory and QA Simulation** (2 min)
StrongDM's experiment: nobody writes code, nobody reads code, but the software is security-critical access management. Their answer: swarms of simulated users making requests 24/7, simulated Slack and Jira environments built by agents, continuous behavioral testing at scale ($10K/day in tokens). The factory with the lights off — but it requires *more* engineering discipline, not less.

Osmani calls this the "Factory Model" and notes it's now production reality: "a substantial portion of merged pull requests now originate from agents running autonomously in cloud environments." Cursor's Michael Truell: "The developer's job is becoming building the system that builds the software — the factory, not just the product."

But Sau Sheong (Singapore government tech) offers a sobering complement: "The constraint isn't engineering capacity anymore. Agents can produce work faster than humans can review it, faster than customers can absorb it, faster than organizations can adapt to it." One person he spoke with put it bluntly: "Humanity is not ready for this much software."

**Slide 13 — Security, Pentesting & the Lethal Trifecta** (1.5 min)
Agents are getting good at security penetration testing. Anthropic discovered and responsibly reported ~100 vulnerabilities in Firefox. But the flip side is prompt injection and Willison's lethal trifecta (private data + malicious instructions + exfiltration channel). Production systems need to account for this — your agent is a new attack surface.

Willison's warning: we're experiencing "normalization of deviance" — using these systems in increasingly unsafe ways and getting away with it. His prediction: a Challenger-disaster-scale AI security incident is coming. Whether or not it's imminent, designing for it is the responsible engineering choice.

**Slide 14 — Architecture, Patterns & the Graph of Software** (2 min)
Christopher Alexander's original insight: patterns are not templates — they're solutions to recurring problems in context. That idea transfers directly to how we structure agent-built code. Good architecture — clean boundaries, well-defined interfaces, separation of concerns — matters *more* when code is cheap, because cheap code without structure is just cheap debt.

Software itself is a graph — code, dependencies, call chains, commits, architectures, transformations. ThoughtWorks' CodeConcise (published on martinfowler.com) combines AST parsing with a knowledge graph to let LLMs reason about legacy codebases *structurally*, not just textually — enabling capability mapping, dead code detection, and idiomatic translation at scale. They found that reducing noise through graph traversal (following only relevant call paths rather than reading entire files) dramatically improves LLM focus and context efficiency.

Tools like codebase-memory-mcp take a similar graph-first approach: indexing a repo into a structural graph that agents can query (call chains, architecture overviews, dead code detection) at 120x fewer tokens than file-by-file reading. The graph becomes *agent memory* — persistent, structural context that survives across sessions and lets agents understand your codebase the way a senior engineer does: relationally, not textually.

---

### Act IV — The Human in the Loop (5 min)

**Slide 15 — "Hoarding Things You Know How to Do"** (1.5 min)
Willison's career advice, amplified by AI: build a backlog of things you've tried — frameworks explored, patterns applied, benchmarks run. GitHub repos of little tools (193 and counting), research projects where an agent actually ran the code and plotted the results. Each one is a reusable building block. AI lets you accumulate these faster than ever. "I constantly throw tasks at AI that I don't think it'll be able to do because every now and then it does it."

Connect to Armour's 0th Order Ignorance: these artifacts represent knowledge you've acquired and can display. They're your competitive advantage as an engineer — the things only *you* have tried in combination.

This maps to personal and organizational learning: the most effective teams will be those that systematically capture what they learn, not just what they build.

**Slide 16 — The Exhaustion Problem & Sustainable Pace** (1.5 min)
Willison: "By 11 AM, I am wiped out." Steve Yegge's "AI Vampire" essay went further: "AI has turned us all into Jeff Bezos — automating the easy work and leaving us with all the difficult decisions." He reports that 3-4 hours of agent orchestration per day is a realistic ceiling. HBR published research in March 2026 confirming the pattern: certain patterns of AI use drive cognitive fatigue.

The TinyComputers analysis frames this as Jevons Paradox applied to human attention: AI makes cognitive output cheaper, so demand for it expands — but human judgment doesn't scale. You can't mine more attention. The Quality Forge essay adds the sharpest warning: the expensive mistakes happen in "that last hour when you're still technically working but your judgment has already checked out."

Agentic engineering isn't just about practices for agents — it's about sustainable practices for humans. The discipline includes knowing when to stop.

**Slide 17 — What Stays Human** (2 min)
The things AI can't do (yet):

- **Agency** — deciding what problems to take on. Willison: "I would argue that the one thing AI can never have is agency because it doesn't have human motivations."
- **Deliberate Discovery** — Dan North's insight that the most valuable activity is *reducing ignorance*, and that requires asking questions AI doesn't know to ask. AI accelerates answers to known questions (1st Order Ignorance). Surfacing the unknown unknowns (2nd Order) still requires human judgment, domain expertise, and genuine curiosity.
- **Usability testing with real humans** — Willison: "I don't think you're going to get as good results from ChatGPT pretending to click around on your prototype as from an actual human being."
- **Taste and judgment** — Looking at three AI-generated variants and knowing which one solves the actual business problem. The ability to say "we don't need this" — which, as Osmani notes, becomes more valuable when anyone can generate thousands of lines in minutes.
- **Treating AI as an unreliable source** — Willison's observation that journalists, who deal with untrustworthy sources daily, are naturally well-equipped for AI collaboration. The skill is verification, not generation.

---

### Closing (2 min)

**Slide 18 — The Spectrum, Not the Binary** (1 min)
Visual: a spectrum from "Vibe Coding" on the left to "Agentic Engineering" on the right. Sau Sheong's five-level framework offers a useful ladder: Level 1 (prompt-and-pray) → Level 2 (AI-assisted with human oversight) → Level 3 (autonomous agents, supervisory engineering) → Level 4 (collaborative agent networks) → Level 5 (software factory).

Both ends are valid. The question isn't which one you do — it's knowing *when* you're on which part of the spectrum and whether that's appropriate for what you're building. Prototype for yourself? Vibe away. Shipping to users? Slide right. Different parts of your organization can and should operate at different levels simultaneously.

**Slide 19 — Your Monday Morning Checklist** (0.5 min)

- Start projects with a thin template (one test, your preferred style — agents match existing patterns)
- Write the spec before the code — it's the knowledge artifact that endures
- Tell agents: "Use red/green TDD"
- Run agents in safe environments (cloud, containers, sandboxed)
- Review via PRs, not by watching the agent type
- Hoard your learnings — every prototype is a building block
- Be ambitious — then be disciplined
- Know your cognitive ceiling — 3-4 focused hours, then stop

**Slide 20 — "I don't just want cheap code. I want really good code."** (0.5 min)
Close with Willison's aspiration: "I don't just want to build software that's good. I want us to build software that is *better* than we were building before. If the agents let us move a bit faster, but we're still churning out the same quality of software, that's less interesting to me than if the software we're producing has less bugs, more features, it's higher quality, it's better software because we're harnessing these tools."

That's the promise of agentic engineering. Not faster code. Better software. And the craft to tell the difference.

---

## Key References

**Core voices on agentic engineering:**

- Andrej Karpathy — Feb 2026 X thread retiring "vibe coding" for professional contexts, proposing "agentic engineering"
- Simon Willison — [Agentic Engineering Patterns](https://simonwillison.net/guides/agentic-engineering-patterns/) (ongoing book-on-blog) and [Lenny's Podcast interview](https://www.lennysnewsletter.com/p/an-ai-state-of-the-union)
- Addy Osmani — [Agentic Engineering](https://addyosmani.com/blog/agentic-engineering/), [The Factory Model](https://addyosmani.com/blog/factory-model/), [How to Write a Good Spec for AI Agents](https://addyosmani.com/blog/good-spec/), [The 80% Problem](https://addyo.substack.com/p/the-80-problem-in-agentic-coding)
- Steve Yegge — [The AI Vampire](https://steve-yegge.medium.com/the-ai-vampire-eda6e4f07163) (cognitive burden and sustainable pace)
- Sau Sheong — [From Vibe Coding to Agentic Engineering](https://sausheong.com/from-vibe-coding-to-agentic-engineering-1ca3ca72b5ac) (five-level framework, government tech perspective)

**Software-as-knowledge lineage:**

- Dan North — [Deliberate Discovery](https://dannorth.net/tags/deliberate-discovery/) and "Software That Fits in Your Head" / Replaceable Component Architecture
- Philip G. Armour — [The Five Orders of Ignorance](https://cacm.acm.org/opinion/the-five-orders-of-ignorance/) (CACM, 2000) and *The Laws of Software Process* (Auerbach, 2003)
- Christopher Alexander — *A Pattern Language* / *The Timeless Way of Building*
- Kellan Elliott-McCrea — "Code has always been the easy part" (Feb 2026)

**Graph-powered code intelligence:**

- ThoughtWorks / Fowler — [Legacy Modernization meets GenAI](https://martinfowler.com/articles/legacy-modernization-gen-ai.html) (CodeConcise: AST + knowledge graph for codebase comprehension)
- DeusData — [codebase-memory-mcp](https://deusdata.github.io/codebase-memory-mcp/) (graph-based code intelligence for AI agents, 120x token reduction)

**Case studies and analysis:**

- Ladybird browser — [Adopts Rust with AI assistance](https://ladybird.org/posts/adopting-rust/) (conformance suite as agentic engineering enabler; 25K lines, zero regressions)
- Nicholas Carlini / Anthropic — Claude C Compiler; Chris Lattner's [review](https://www.modular.com/blog/the-claude-c-compiler-what-it-reveals-about-the-future-of-software)
- StrongDM — dark factory / simulated QA experiments
- Turing College — [Agentic Engineering vs. Vibe Coding](https://www.turingcollege.com/blog/agentic-engineering-vs-vibe-coding) (industry analysis including Amazon Q incident)
- TinyComputers — [The AI Vampire Is Jevons Paradox](https://tinycomputers.io/posts/the-ai-vampire-is-jevons-paradox.html)
- The New Stack — [From Vibes to Engineering](https://thenewstack.io/vibe-coding-agentic-engineering/) (Forrester analyst perspectives)
- HBR — [When Using AI Leads to "Brain Fry"](https://hbr.org/2026/03/when-using-ai-leads-to-brain-fry) (BCG research on cognitive fatigue patterns)
- arXiv — [Vibe Coding vs. Agentic Coding](https://arxiv.org/abs/2505.19443) (academic taxonomy, 20 use cases)

---

## Reasoning & Design Notes

### Why this structure

The keynote follows a four-act dramatic arc rather than a flat list of practices:

1. **Excitement** (Act I) — establish that vibe coding is genuinely wonderful. This matters because the audience is at a *VibeCode* conference. If you open by dismissing vibe coding, you lose them. Instead, celebrate it first, then create productive tension.
2. **Tension** (Act II) — introduce the gap between prototype and production. The Armour/North philosophical frame ("software is knowledge") provides the *why* — it's not just that vibe-coded software has bugs, it's that the learning process itself was skipped. This elevates the argument beyond "be more careful" to "fundamentally rethink what the artifact is."
3. **Resolution** (Act III) — the agentic engineering practices. These are concrete and actionable, but grounded in the philosophical frame from Act II. Each practice maps to a knowledge concern: specs capture what you know, tests capture expected behavior, architecture captures structural decisions, security reviews capture threat models.
4. **Reflection** (Act IV) — the human element. This brings it home personally: exhaustion is real, sustainable pace matters, and the things that stay uniquely human (agency, discovery, taste, judgment) are more valuable than ever.

### Why Armour and Dan North as the philosophical backbone

There are many ways to argue "vibe coding isn't enough for production." Most of them boil down to "you need tests and code review." That's true but not inspiring — it sounds like scolding.

Armour and North provide a deeper frame: software development is fundamentally a *knowledge discovery* activity. Code is a by-product, not the product. This reframe is powerful because:

- It explains *why* the practices matter (they capture and preserve knowledge)
- It makes the argument *for* AI, not against it — if code is throwaway and knowledge is what matters, then cheap code via AI is a feature, not a bug
- It connects to North's Replaceable Component Architecture: well-specced, well-tested components with throwaway internals. AI makes "throwaway internals" practical for the first time
- It gives the audience a mental model that lasts beyond the talk

Michael's background with the patterns community, Martin Fowler, and Christopher Alexander makes this frame authentic — it's not borrowed wisdom, it's lived experience.

### Why the broader community voices

The initial draft drew primarily from Simon Willison. While Willison is the most detailed and practitioner-grounded voice, the argument is much stronger with convergent perspectives:

- **Karpathy** retiring his own term gives the vocabulary shift legitimacy at the highest level
- **Addy Osmani** (Google) brings the enterprise/team perspective and the sharpest articulations of spec-driven development and the factory model
- **Steve Yegge** (40 years, ex-Amazon/Google) brings the human cost dimension — the "AI Vampire" and sustainable pace, now confirmed by HBR/BCG research. This is important for an experienced-engineer audience who *feels* this exhaustion.
- **Sau Sheong** (Singapore government) brings the organizational absorption problem: "Humanity is not ready for this much software." This is the most provocative line in the talk and lands perfectly after the factory discussion.
- **The New Stack / Forrester** bring analyst credibility for the skeptics in the room
- **Ladybird / Claude C Compiler** bring concrete case studies that prove agentic engineering works at scale when you have the right infrastructure (conformance suites, trusted reference implementations)

Together, these voices create a sense of industry consensus rather than one person's opinion.

### Why the cognitive exhaustion thread (Act IV)

An inspiring keynote for experienced engineers can't ignore the elephant in the room: this stuff is mentally brutal. Willison says he's wiped by 11 AM. Yegge says 3-4 hours is the ceiling. The TinyComputers analysis frames it as Jevons Paradox — efficiency gains get consumed by demand expansion, and the input that can't scale is human judgment.

Including this honestly (rather than pretending agentic engineering is pure upside) builds trust with the audience and makes the "Monday morning checklist" more credible — especially the last item: "Know your cognitive ceiling."

### Why the Neo4j / graph touch is light

Michael asked for a light mention, and the keynote positions it naturally in Slide 14 under "Architecture, Patterns & the Graph of Software." The argument is genuine, not promotional: software structure *is* a graph (code, dependencies, call chains, commits), and reasoning about it structurally rather than textually is demonstrably more efficient for both humans and agents. CodeConcise (ThoughtWorks, published on martinfowler.com) and codebase-memory-mcp are third-party validations of this approach, not Neo4j marketing. The 120x token reduction stat from codebase-memory-mcp is concrete and memorable.

### What's intentionally left out

- **Detailed tool comparisons** (Claude Code vs. Codex vs. Jules vs. Gemini CLI) — this dates fast and distracts from the craft argument
- **Pricing / business model discussion** — not the right venue
- **AI doomerism** — the tone is "inspiring & encouraging," not alarmist. The Challenger disaster warning is included but positioned as motivation for discipline, not despair
- **Live demo** — not planned, but Slides 11 (TDD) and 14 (graph intelligence) could anchor a demo if Michael wants one. Worth discussing.
- **The "middle career" squeeze** — Willison and ThoughtWorks both discuss how mid-career engineers are most at risk. This is fascinating but potentially demoralizing for the audience and tangential to the practice-focused arc. Could be added to Q&A talking points.

### Timing budget

| Section | Minutes |
|---------|---------|
| Act I — The Vibe Coding Revolution | 7 |
| Act II — Where the Vibes Run Out | 6 |
| Act III — Agentic Engineering Practices | 12 |
| Act IV — The Human in the Loop | 5 |
| **Total** | **30** |

This leaves zero buffer, so in practice Michael should identify 1-2 slides to compress if audience energy or Q&A setup requires it. Slides 12 (Dark Factory) and 13 (Security) are the most compressible — each could lose 30 seconds without losing the arc.
