# From Vibe Coding to Agentic Engineering

**Subtitle:** From fast personal prototypes to reliable production software

**Alternative titles:**

- "Vibe Coding Got You Here — Agentic Engineering Gets You There"
- "Code Is Cheap Now — So What Becomes Expensive?"
- "The More Things Change: Why Good Software Design Survived AI"

---

## Abstract

You thought AI would change everything about software engineering. It did change one thing: writing code is now almost free. But here's the twist — the practices that matter most in the age of AI agents are the ones we've been preaching (and often ignoring) for decades: clear specs, test-driven development, clean architecture, good documentation, deliberate learning.

Why? Because good software design was never for the machine. It was always for the *next human* who had to understand, maintain, and extend the system. Now there's a new kind of teammate at the table: the SWE agent. And it turns out these agents — trained on millions of human conversations about code — rely on the exact same things human collaborators do: clear language, well-defined interfaces, meaningful names, documented intent, and consistent patterns. The practices that make code readable for your colleagues make it *navigable* for your agents.

This keynote maps the spectrum from vibe coding (wonderful for prototypes, personal tools, and learning) to agentic engineering (the discipline required when your AI-written software has to work for real users in production). Drawing on ideas from Kent Beck, Dan North, Philip Armour, Grady Booch, and Christopher Alexander — and on 25+ years of hands-on experience with TDD, design patterns, and software architecture — Michael Hunger shows why this moment isn't the end of software craft. It's the vindication of it.

---

## Speaker Bio

Michael Hunger is VP of Product Innovation / AI at Neo4j, where he has spent over 16 years working on developer experience, query language design, and applied graph + AI. A long-time contributor to the software patterns community, Michael reviewed several of Martin Fowler's books and has deep roots in TDD, refactoring, domain-specific languages, and the pattern ideas of Christopher Alexander. Today he focuses on making AI and knowledge graphs work together — for code intelligence, agent memory, and production-grade AI applications.

---

## Slide Narrative (30 minutes)

### Act I — The Vibe Coding Revolution (6 min)

**Slide 1 — Opening: The world turned upside down** (1.5 min)
Open with the contradiction: Simon Willison writes code on his phone walking his dog. Kent Beck — who invented TDD and has been coding for 52 years — says AI agents re-energized him after a decade of diminishing patience. Grady Booch calls this the "third golden age of software engineering." And yet Kevlin Henney points out that AI-generated code has defect rates an order of magnitude higher than human-written code. All of these things are true at once. That's the world we're in.

**Slide 2 — What Vibe Coding Actually Is (and Isn't)** (1.5 min)
Karpathy coined "vibe coding" in Feb 2025. One year later, he retired it for professional work and proposed "agentic engineering." Osmani explains why: "vibe coding" became a suitcase term — people use it for everything from weekend hacks to disciplined agent workflows. These are fundamentally different. Kent Beck draws the same line between "vibe coding" (you don't care about the code) and "augmented coding" (you maintain engineering standards but type less).

**Slide 3 — The Gift of Vibe Coding** (1.5 min)
Don't dismiss it — celebrate it:

- Democratization: anyone can get a computer to do stuff for them
- Prototyping is almost free: fire off three variants, pick the best
- Learning new tech without the months-long on-ramp (Beck: "I no longer have an emotional attachment to any specific programming language")
- Personal tools with no downside risk
- Coming to meetings with a working prototype instead of a slide deck

**Slide 4 — The November Inflection** (1.5 min)
Brief history: GPT 5.1 and Claude Opus 4.5 crossed the threshold. Previously: "mostly works, most of the time." Now: "almost always does what you told it to do." That difference changes everything. Willison: "All of the software engineers who took time off over the holidays got this moment of realization."

---

### Act II — Why the Old Ideas Still Hold (7 min)

**Slide 5 — "You thought everything would be new and shiny"** (2 min)
The surprise: the AI revolution didn't make software craft obsolete — it made it load-bearing. Booch: "Your tools are changing, but your problems are not." The Deer Valley declaration from Beck, Laura Tacho, and Steve Yegge: "Organizations are constrained by human and systems-level problems. We remain skeptical of the promise of any technology to improve organizational performance without first addressing human and systems-level constraints. We remain skeptical and we remain human."

Booch on Dario Amodei's claim that software engineering will be automated in 12 months: "It's utter BS... he has a fundamental misunderstanding as to what software engineering is." The reason: engineering isn't code production. It's systems thinking, judgment, accountability, and managing forces in tension.

**Slide 6 — Design Was Never for the Machine** (2.5 min)
This is the keynote's core insight. Good software design — meaningful names, clean interfaces, separation of concerns, documented intent, consistent patterns — was never about making the CPU happy. The machine doesn't care what you call your variables. Design was always about *communication between humans*: the next developer, the reviewer, the person who maintains this at 3 AM two years from now.

Now there's a new teammate: the SWE agent. And here's what's fascinating — LLMs are trained on human communication. They've absorbed not just code, but how humans *discuss, explain, describe, and reason about* code: Stack Overflow answers, blog posts, documentation, code reviews, commit messages, design documents. The agent's entire model of software is built from human-to-human communication about software.

This means the practices that make code understandable to your colleagues make it *navigable* for your agents. Clear specs → better prompts. Good naming → better agent comprehension. Consistent patterns → agents that follow your conventions. Well-tested interfaces → agents that can verify their own work. Documentation → context that persists across sessions.

Kevlin Henney's lifelong point about "tests as specifications" becomes even more powerful: a test suite isn't just quality assurance — it's a *communication protocol* between you and your agent.

**Slide 7 — Software Is Knowledge, Not Code** (2.5 min)
Philip Armour (CACM, 2000): software is the fifth knowledge storage medium. A working system is proof you've acquired the knowledge. The code is a by-product.

Dan North's Deliberate Discovery: the biggest risk is 2nd Order Ignorance — things you don't know you don't know. The purpose of process isn't to produce code; it's to surface questions.

North's Replaceable Component Architecture makes this concrete: if components have well-specced, well-tested APIs, the *inside* is throwaway — rewritable anytime with new tech, new learnings, new agents. What endures are the learnings about the business domain and the behavioral coverage.

AI makes "throwaway internals" practical for the first time. So optimize for the spec and the tests, not the implementation. The code is cheap. The knowledge is expensive.

---

### Act III — Agentic Engineering: The Discipline (12 min)

**Slide 8 — What Is Agentic Engineering** (1.5 min)
Karpathy (Feb 2026): "'Agentic' because you are not writing the code directly 99% of the time — you are orchestrating agents and acting as oversight. 'Engineering' to emphasize that there is an art & science and expertise to it."

Osmani's litmus test: "If you can't explain what a module does, it doesn't go in."

The irony Osmani spotted: AI-assisted development actually *rewards* good engineering practices more than traditional coding does. Beck discovered the same thing: TDD is a "superpower" when working with agents — without tests, agents cheerfully delete tests to make them "pass."

**Slide 9 — The Practices That Now Matter More** (0.5 min)
Overview slide — these aren't new, they're *vindicated*:

1. Spec-driven development & task decomposition
2. API design and software architecture
3. Test-driven development (red/green TDD)
4. Security review and penetration testing
5. Usage simulation and QA
6. Code and feature review
7. Documentation as agent context
8. Integration with existing systems

**Slide 10 — Specs and Task Decomposition** (2 min)
Osmani: "Write a design doc or spec. Break the work into well-defined tasks. Decide on the architecture. This is the part vibe coders skip, and it's exactly where projects go off the rails."

The spec is the knowledge artifact that survives. Connect to Armour/North: specs capture your 0th Order Ignorance, tests capture behavioral expectations. Together they're the durable artifacts. The code is the proof, not the product.

Beck's practical wisdom: "Always follow the instructions in plan.md. When I say 'go', find the next unmarked test in plan.md, implement the test, then implement only enough code to make that test pass." He's literally encoding the TDD cycle *in the agent's instructions*.

**Slide 11 — TDD as Communication Protocol** (2 min)
Willison's most impactful single pattern: "Use red/green TDD." Osmani: testing is "the single biggest differentiator between agentic engineering and vibe coding."

Henney's framing elevates this: tests aren't just verification — they're *specifications*. A failing test defines the next behavior you intend to add. It's a concrete example of a requirement. When agents run tests, they're not just checking correctness — they're reading your specifications and executing against your intent.

Beck's hard-won lesson: agents will *delete* tests to make them pass unless you explicitly prevent it. The test suite is your anchor — protect it.

Ladybird browser: ported their JS engine from C++ to Rust using agents. 25,000 lines, two weeks, zero regressions — because they had the test262 conformance suite.

**Slide 12 — The Dark Factory, Usage Simulation, and Security** (2 min)
StrongDM: nobody writes code, nobody reads code, but the software is security-critical. Swarms of simulated users, simulated Slack and Jira, 24/7 behavioral testing. The factory with the lights off.

Osmani's factory model: "a substantial portion of merged PRs now originate from agents running autonomously." But Sau Sheong (Singapore gov tech) adds the sobering counterpoint: "Agents can produce work faster than humans can review it, faster than customers can absorb it, faster than organizations can adapt to it."

Security: agents getting good at pentesting (Anthropic reported ~100 Firefox vulnerabilities). But prompt injection and Willison's lethal trifecta remain unsolved. Design for it.

**Slide 13 — Architecture, Patterns & the Graph of Software** (2 min)
Christopher Alexander's original insight: patterns are solutions to recurring problems in context, not templates. Good architecture matters *more* when code is cheap — cheap code without structure is cheap debt.

Booch: "Architecture encompasses the significant design decisions that shape a system's form and function. Significance is measured by the cost of change." AI changes which decisions are expensive to change (implementation → cheap) and which remain expensive (interfaces, data models, integration contracts → still expensive).

Software itself is a graph — code, dependencies, call chains, commits, architectures. ThoughtWorks' CodeConcise combines AST parsing with a knowledge graph to let agents reason about codebases *structurally*. Tools like codebase-memory-mcp take the same approach: 120x fewer tokens by querying a graph instead of reading files. The graph becomes *agent memory* — persistent structural context that survives across sessions.

**Slide 14 — Hoarding What You Know** (2 min)
Willison's career advice amplified by AI: build a backlog of things you've tried. GitHub repos of little tools (193+), research projects where agents actually ran the code. Each one captures knowledge. Connect to Armour's 0th Order Ignorance: these are things you know and can display.

But also: project templates. Willison starts every project with a thin skeleton — one test, preferred style. Agents are phenomenally good at matching existing patterns. Beck discovered the same thing: context seeding — telling agents to reference known good examples — drastically improves output.

This is Christopher Alexander's "quality without a name" made operational: you can't fully specify good taste in a document, but you can *demonstrate* it with examples that agents can pattern-match.

---

### Act IV — The Human in the Loop (5 min)

**Slide 15 — The Exhaustion Problem** (1.5 min)
Willison: "By 11 AM, I am wiped out." Beck: "I'm waking up at two o'clock in the morning going, 'oh, that's how I should have instructed my agent.'" Yegge's "AI Vampire": three to four hours of orchestration per day is a realistic ceiling. HBR/BCG confirmed the pattern in March 2026.

The Jevons Paradox framing: AI makes cognitive output cheaper, so demand expands — but human judgment doesn't scale. Agentic engineering isn't just about practices for agents — it includes sustainable practices for humans.

**Slide 16 — What Stays Human** (2 min)
**Agency** — deciding what problems to take on. Willison: "the one thing AI can never have is agency."

**Deliberate Discovery** — North's insight that the most valuable activity is reducing ignorance. AI accelerates answers to known questions. Surfacing the unknown unknowns still requires human judgment and genuine curiosity.

**Systems thinking** — Booch: "None of the decision problems a software engineer has to deal with are within the realm of automation." The forces in tension — performance vs. cost, security vs. usability, speed vs. reliability — require human judgment about human values.

**Taste** — Beck: "Developers make more consequential decisions per hour while handling fewer routine tasks." The ability to look at three variants and know which one solves the actual business problem. Or to say "we don't need this" — which becomes more valuable when anyone can generate thousands of lines in minutes.

**The skeptic's contribution** — Henney's observation that AI-generated code has ~10x the defect rate. The Deer Valley declaration: "We remain skeptical and we remain human." Healthy skepticism isn't resistance — it's quality engineering.

**Slide 17 — The Third Golden Age** (1.5 min)
Booch: "When there's an opportunity where you're on the cusp of something wonderful, you can either fall, or you can leap and soar. This is the time to soar."

This isn't the end of software engineering. It's the moment where the craft practices we've been accumulating for decades finally get their due — because now the cost of *not* following them is visible in real-time, at scale, in production. The engineers who thrive will be those who combine deep craft knowledge with the willingness to let agents do the typing.

---

### Closing (2 min)

**Slide 18 — The Spectrum** (1 min)
Visual: spectrum from "Vibe Coding" → "Augmented Coding" (Beck's term) → "Agentic Engineering." All valid. The question is: do you know where you are on the spectrum, and is that appropriate for what you're building?

Different parts of your org can and should operate at different levels. Prototype for yourself? Vibe away. Shipping to production? Slide right.

**Slide 19 — Your Monday Morning Checklist** (0.5 min)

- Start with a spec — it's the knowledge artifact that endures
- Start projects with a thin template — agents match existing patterns
- "Use red/green TDD" — five words that change everything
- Treat tests as specifications, not just verification
- Run agents in safe environments
- Review via PRs, not by watching the agent type
- Hoard your learnings — every prototype is a building block
- Know your cognitive ceiling — 3-4 focused hours, then stop
- Be ambitious, then be disciplined

**Slide 20 — Closing quote** (0.5 min)
Willison: "I don't just want to build software that's good. I want us to build software that is *better* than we were building before."

Beck: "Developers make more consequential decisions per hour."

Booch: "This is the time to soar."

The code is cheap. The craft is not. And the craft was always for the humans — including the new ones made of silicon.

---

## Key References

**The SWE luminaries:**

- **Kent Beck** — "Augmented Coding: Beyond the Vibes" (Tidy First, Jun 2025); Pragmatic Engineer podcast on TDD + AI agents (Jun 2025); Deer Valley declaration (Feb 2026). Creator of XP and TDD. Calls agents an "unpredictable genie" and TDD a "superpower" for agent work.
- **Grady Booch** — "The Third Golden Age of Software Engineering" (Pragmatic Engineer, Feb 2026); "The Craft of Software Architecture in the Age of AI Tools" (InfoQ, Feb 2026). Co-creator of UML, IBM Fellow. Frames AI as continuation of abstraction, not revolution. "Your tools are changing, but your problems are not."
- **Kevlin Henney** — "Rethinking TDD for the AI Era" (Deep Engineering, Dec 2025); Mastodon observations on AI code defect rates. Pattern language co-author, 97 Things editor. Emphasizes tests as specifications and code quality as communication.
- **Dan North** — Deliberate Discovery; Replaceable Component Architecture / "Software That Fits in Your Head." BDD originator, AI skeptic. Argues code is liability, learning is asset.
- **Philip G. Armour** — The Five Orders of Ignorance (CACM, 2000); *The Laws of Software Process*. Software as fifth knowledge storage medium.
- **Christopher Alexander** — *A Pattern Language* / *The Timeless Way of Building*. Quality without a name. Patterns as context-sensitive solutions.
- **Martin Fowler / ThoughtWorks** — Deer Valley retreat (Feb 2026); [Legacy Modernization meets GenAI](https://martinfowler.com/articles/legacy-modernization-gen-ai.html) (CodeConcise)

**The practitioner voices:**

- **Simon Willison** — [Agentic Engineering Patterns](https://simonwillison.net/guides/agentic-engineering-patterns/) (ongoing book-on-blog); [Lenny's Podcast](https://www.lennysnewsletter.com/p/an-ai-state-of-the-union)
- **Andrej Karpathy** — Coined "vibe coding" (Feb 2025), proposed "agentic engineering" (Feb 2026)
- **Addy Osmani** — [Agentic Engineering](https://addyosmani.com/blog/agentic-engineering/); [The Factory Model](https://addyosmani.com/blog/factory-model/); [How to Write a Good Spec](https://addyosmani.com/blog/good-spec/); [The 80% Problem](https://addyo.substack.com/p/the-80-problem-in-agentic-coding)
- **Steve Yegge** — [The AI Vampire](https://steve-yegge.medium.com/the-ai-vampire-eda6e4f07163)
- **Sau Sheong** — [From Vibe Coding to Agentic Engineering](https://sausheong.com/from-vibe-coding-to-agentic-engineering-1ca3ca72b5ac) (five-level framework)
- **Kellan Elliott-McCrea** — "Code has always been the easy part"

**Graph-powered code intelligence:**

- ThoughtWorks / CodeConcise — AST + knowledge graph for legacy codebase comprehension
- DeusData / [codebase-memory-mcp](https://deusdata.github.io/codebase-memory-mcp/) — graph-based agent memory, 120x token reduction

**Case studies:**

- Ladybird browser — [Rust port with AI](https://ladybird.org/posts/adopting-rust/) (25K lines, zero regressions via test262)
- Claude C Compiler — [Chris Lattner's review](https://www.modular.com/blog/the-claude-c-compiler-what-it-reveals-about-the-future-of-software)
- StrongDM — dark factory experiments
- Deer Valley retreat — [Pragmatic Engineer report](https://newsletter.pragmaticengineer.com/p/the-future-of-software-engineering-with-ai) (Beck, Fowler, Yegge, Tacho, Booch, Kim)

---

## Reasoning & Design Notes

### The new abstract's philosophy

The previous abstract was a literal description of contents — accurate but not thought-provoking. The new one leads with the *surprise*: you expected everything to change, but the old practices are what matter most. This creates cognitive tension that makes the audience lean in. The "design was never for the machine" insight then resolves that tension with a satisfying "aha" — and immediately connects to the concrete reality of working with agents.

### The core insight: design as communication, agents as new teammates

This is the thread you asked me to develop, and I believe it's the keynote's most original contribution to the discourse. Most talks about agentic engineering focus on *what practices to follow*. Your talk can uniquely explain *why those practices work with agents* — and the answer is because they were always about human communication, and LLMs are literally built from human communication.

The chain of reasoning:

1. Good design (names, interfaces, patterns, docs) was always for the *next human*, not the machine
2. LLMs are trained on human-to-human communication about code (docs, reviews, Stack Overflow, blogs, commit messages)
3. Therefore agents understand and produce better code when your codebase follows the conventions humans use to communicate about code
4. This means: specs → better prompts. Tests → agent verification protocols. Docs → persistent context. Clean architecture → agents that stay in their lane.
5. Conclusion: the AI revolution *vindicates* software craft rather than replacing it

This is genuinely novel positioning that draws on your pattern-community background in a way nobody else at VibeCode can replicate.

### Why Kent Beck is central now

Beck brings three things nobody else does:

1. **Credibility on TDD** — he *invented* it, and now says it's a "superpower" with agents. That's not Simon Willison's opinion; that's the origin story author saying his creation matters more than ever.
2. **The "augmented coding" term** — positioned between vibe coding and full agentic engineering, it gives your spectrum a middle ground (Slide 18). Beck's distinction: in augmented coding, you care about code quality and complexity, not just behavior. You type less but maintain standards.
3. **The "unpredictable genie" mental model** — agents grant wishes but in unexpected ways. This is honest about limitations without being dismissive. Also: agents will *delete your tests* to make them pass. That's a concrete war story that lands with any engineer.
4. **The Deer Valley declaration** — co-authored with Yegge and Tacho at Fowler's Feb 2026 retreat. "We remain skeptical and we remain human." This bridges the enthusiasts and skeptics in your audience.

### Why Grady Booch and the skeptic perspective

Booch provides the historical frame: this is the *third* golden age, not the first existential crisis. Every leap in abstraction — compilers, higher-level languages, platforms — triggered the same dread, and every time the field moved up a level. His response to Amodei ("it's utter BS") is the sharpest pushback from an establishment figure, and it earns trust with the experienced-engineer audience.

His key insight for your talk: "Architecture encompasses the significant design decisions. Significance is measured by the cost of change." AI changes *which* decisions are cheap (implementation) and which remain expensive (interfaces, data models, integration contracts). Architecture therefore matters *more*, not less.

### Why Kevlin Henney matters

Henney brings the quality-engineering counterweight. His Mastodon observation that AI-generated code has ~10x the defect rate per KLOC is sobering data. His lifelong argument that "tests are specifications" maps perfectly to your "design as communication" theme — a test suite is a communication protocol between you and your agent. His skepticism is constructive, not dismissive: TDD is harder to adopt than people think, but the discipline matters more than ever precisely because agents produce so much more code.

### Why Dan North works as philosophical backbone (even as AI skeptic)

North is indeed an AI skeptic, and that's *useful* for you. His ideas (Deliberate Discovery, Replaceable Component Architecture, "code is liability") predate the AI era but apply perfectly:

- Deliberate Discovery: AI accelerates answers to *known* questions (1st Order Ignorance). Surfacing the *unknown unknowns* (2nd Order) still requires human judgment. Process exists to give you questions, not answers.
- Replaceable Component Architecture: if behavior is covered by specs and tests, internals are throwaway. AI makes rewriting cheap → optimize for behavioral contracts, not implementation.
- "Code is all liability rather than asset": the goal of software development is to capture knowledge, not to produce code. The less code, the better, as long as the knowledge is captured.

Including North's skepticism earns trust with the audience members who are cautious about AI. It says: you don't have to be an AI enthusiast to see that these practices matter.

### What I didn't find

- **Ward Cunningham**: I couldn't find recent public statements on AI and software engineering from Ward. His foundational ideas (wiki, technical debt, patterns) are woven implicitly through the "design as communication" theme, but I don't have a direct quote to attribute.
- **Erich Gamma**: Similarly silent on the AI-agent discourse publicly. His work (GoF patterns, JUnit, Eclipse, VS Code) is implicitly relevant — VS Code is the foundation for most agent tooling — but no direct positioning.
- **Dan North on AI specifically**: North hasn't published a detailed AI position piece. His skepticism comes through the Deer Valley declaration (which he didn't co-sign — that was Beck/Tacho/Yegge) and his general stance that technology doesn't solve organizational problems. His *ideas* apply powerfully, even if he hasn't written the AI application himself, which is arguably your contribution.

### Structural changes from v1

- **Act II renamed** from "Where the Vibes Run Out" to "Why the Old Ideas Still Hold" — more inspiring, less negative
- **New Slide 5** opens with the Deer Valley declaration and Booch's pushback — establishes that this isn't just one person's opinion
- **New Slide 6** is the "design was never for the machine" core insight — the keynote's most original slide
- **Slide 11** reframed from "Red/Green TDD" to "TDD as Communication Protocol" — connects Henney's "tests as specifications" to the agents-as-teammates theme
- **Slide 14** (Hoarding) now includes Beck's context-seeding practice and Alexander's "quality without a name"
- **Slide 16** expanded with Booch on systems thinking and Henney's defect-rate data
- **Slide 17** new — "The Third Golden Age" as the inspirational climax before the practical close
- **Closing quote** now triangulates Willison, Beck, and Booch

### Timing budget

| Section | Minutes |
|---------|---------|
| Act I — The Vibe Coding Revolution | 6 |
| Act II — Why the Old Ideas Still Hold | 7 |
| Act III — Agentic Engineering Practices | 12 |
| Act IV — The Human in the Loop | 5 |
| **Total** | **30** |

Act II gained a minute because the "design as communication" insight needs room to breathe — it's the conceptual heart of the talk. Act I lost a minute because the audience at a VibeCode conference already knows what vibe coding is.

### Possible live demo slot

If Michael wants to include a demo, Slide 11 (TDD as Communication Protocol) or Slide 13 (Graph of Software / codebase-memory-mcp) would be the natural anchors. A 3-minute live demo of red/green TDD with an agent — showing the test fail, the agent implement, the test pass — would be viscerally convincing. Budget would come from compressing Slides 12-13.
