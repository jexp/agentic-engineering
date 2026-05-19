## Agentic Engineering
4hrs total?

Some Q&A to engage
When did you first try using an LLM for coding
Last?
What kinds of projects? (task in , greenfield, oss contribution)
History
Change since Dec
Vibe coding vs. agentic engineering


It is a tool like any other tool

Own experiences

- analyze code (mongot, claude code)
- Sather-K
- neo4j - MCP, MCP Toolbox, multi-db tool, contribution
- inferrs
- tools like openalex
- agentskills.ai

- Simon not afraid anymore of taking on software projects
- where's the skill/experience - ideas - programming language - libraries/idioms - take it to prod
- don't 

Agents.md / claude.md
Agent Skills

APIs / CLIs
MCP - context7, neo4j, toolbox, gh?, gws?
- neon / github growth

collapsing context -> need to guide or reset

Context issues
Ralphing
hone-ai
superpowers?
plan mode

agentic coding harnesses
- podcast on CC (+ newer even creator of CC doesn't code anymore, ukrainian Boris Cherny) - push everything into the model
- model is good at linux tools (they have been aroudn for a long time)
- claude code - treat the code as source of truth and rely
- token efficiency, rtk, headroom, caveman
- memory, dreaming (claude code) - don't store things that are in memory

Treat like a colleague

- Red Green Refactor
- tests as harness
- commit cycle 
- software architecture
- good software design / naming / docs / describe the why (context graph) not the what
- what is in the code
- Implementation Patterns?
- docs

I try to stick only to the anthropic guidelines when the landscape shifts so much. There’s many examples of decreased performance from going to deep in to LLM-whisperer territory and in my experience, if there’s a useful pattern, antrophic folds the best practises into claude code anyway

https://www.augmentcode.com/blog/how-to-write-good-agents-dot-md-files
https://code.claude.com/docs/en/best-practices#write-an-effective-claude-md
https://claude.md/
https://www.datacamp.com/tutorial/claude-code-best-practices

- investigation + questions
- spec
- tasks
- each tasks has the same cycle + quality gates + commit / review

future / frontier
- shipping specs (frontier)
- multi-agent
- pi as core of openclaw
- world models
- memory / team / project / org - transplant memories

Exercises:

- HTML tools / tools (30 mins)
- e.g. a course or a tool
- 1hr - to something real in your product - let's see how far we get
- solve a nasty bug / add a new capability / or building something in a different language that they have not used before (e.g. a go cli for product), build an MCP server
- give it access to your codebase + tests / tools


---

## Max Schoening (Head of Product, Notion) — Lenny's Podcast, May 2026

**Vibe coding vs. agentic engineering:**
- Max's quality concern: "I don't feel like the quality of software has increased all that much in the last 12 months. I think maybe the *amount* of software has, but it's very, very hard to find software that is reliable."
- 3D printing analogy: prototypes have layer lines — it's obvious to everyone they're not production-ready. Software is losing that signal. "Where's the engineering part?" — engineering = making it work for a hundred million people.
- Designers should code not to ship to production but to "think and design in the medium that will actually end up being the real thing." Code is the right material to interrogate, not Figma.
- Key insight on what matters for product people: "I would much rather take the designer or PM that deeply has an affinity for understanding how agent loops work... than someone who can write traditional software and tweak styles."
- Any manual intervention in the agent's code should feel like a bug — good litmus test for how "agent-filled" your process is.
- On superhero framing: auto code review tools roasted your code publicly → demotivating. Claude Code: you publish the work of you + AI and get bragging rights. The tool must make the human feel like a superhero, not expose their weaknesses.

**Role of product / agency:**
- The new differentiator is **agency**, not skills: "Before, it was very easy to always say, 'I will never be able to do this because — insert skill issue.' We're realizing that even if you have the skills at your fingertips, the thing that matters is agency."
- Agency ≠ working around your boss. "Start by making things." Tinkering builds it. Making → confidence → "I can change things."
- "Do you drive Notion like it's stolen?" — personal bar for acting with agency inside a company with existing PMF.
- Taste = "run a virtual machine in your head where, given an idea, you can predict for a certain in-group whether they're going to like it or not." Just reps. Ironically, taste might not be AI-proof: it's basically backpropagation.
- "The first 10% of every project are now free." [...] "the last 10% are still actually 90%."
- "Demos not memos" (GitHub era principle) — now trivially achievable. "Waterfall is sort of, why bother?"
- Quality bar: "Make obviously good stuff." Don't confuse shots-on-goal (more iterations) with feature count. Feature count = as meaningless as lines of code or token spend.
- "Incremental correctness" — iterate fast, but also consolidate branches back to the naked core of the idea. Software quality requires doing the hard reconciliation work.
- Token spend as vanity metric: "same silly metric as lines of code or tokens consumed." ROI reckoning coming in 6–12 months.

**Build vs. buy (maintenance):**
- "I don't think most people actually want to maintain the full stack of software."
- "Software is like a garden, you need to tend to it." — Bret Taylor
- "The thing you pay for as a service is the maintenance and a bunch of specialists thinking really hard about a problem."
- Slack notification decision-flow example: you only get that depth of reliability from real users, real scale, and decades of customer understanding. Vibe-coded alternatives can't replicate that.
- Kubernetes > Heroku: "We're going to make your ops team superheroes. And also, we're not going to lock you into a cloud." Businesses want to feel like superheroes AND avoid lock-in.
- SaaS apocalypse is "greatly exaggerated." Software will move toward general tools (like '90s: WordProcessor, spreadsheet, FileMaker) but still **as a service**. Specialized tools for real problems survive.
- General tools will become more malleable (Notion direction) — not replaced, re-shaped.

**Malleable software:**
- Core idea: "software works closer to the interest of the people that use it than the interest of the corporation that makes it."
- Apartment analogy: you can't rearrange your living room if it was designed by the ivory tower. Apps on phones are like that — every layer is glued together.
- "Do you have ownership over your computing life?" — increasingly, no.
- People are awakening to "I can just make tools." But individual tools aren't enough — needs a communal platform (Ink & Switch / Geoffrey Litt direction).
- Stewart Brand / timeless way of building: the best homes aren't built by architects — they adapt to how you actually live.
- Connection to agency: understanding the world is malleable → willingness to change it.
- "The best homes for you... are the thing that over a long time adapt to exactly how you would love to lead your life."
- All agents now resemble coding agents: "If you look at all the harnesses, whether it's the open source ones or the ones from the model companies, they all resemble a coding agent now." → coding = the substrate of agency in software.
- Playground approach at Notion: created a small, LLM-friendly codebase for prototyping chat UIs. Removed the fear of the terminal. Then gradually moved designers/PMs to production contributions. "Get people on the treadmill."

**Broader observations:**
- "Universal basic income = knowledge work." We already have it; we just come up with new reasons to insert humans into the loop.
- Intelligence saturation: retina display analogy — "after I can't see the pixels, I can't see the pixels." At some point models are good enough and you optimize for speed, cost, local. Labs may be wrong to assume users always want the frontier model.
- "Software is eating the world will just accelerate" — not that AI replaces other roles, but that software-encoding of everything gets cheaper, so every role gains access to building.

References (todo)
- Anthropic
- Willison (articles agentic engineering) 
- Karpathy
- Max Schoening, Lenny's Podcast: https://www.lennysnewsletter.com/p/why-cultivating-agency-matters-more (May 2026)