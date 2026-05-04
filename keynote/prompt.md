### Original Prompt

I need an abstract and flow for my keynote for the vibecode conference

*This is the task:* Create an markdown artifact with the keynote title and abstract and also lay out a possible slide narrative for a 30 minute keynote.
Ask me any clarifying questions before you start.

*Title idea* (add more options) From VibeCoding to Agentic Engineering
*Subtitle:* From fast personal prototypes to reliable production software.

I had already a number of ideas in this direction but Simon Willison put it quite well
In Lenny's podcast, he's also writing a book about it (see linked articles)
https://simonwillison.net/tags/agentic-engineering/

I attached the transcript of the podcast - do extract the nuggets for only this topic (not the side topics like pelicans on a bicycle)
https://www.lennysnewsletter.com/p/an-ai-state-of-the-union


I want to show how to get form one to the other, but don't dismiss vibe coding (it has still  a lot of value for personal projects, prototyping, democratization of software development, getting started in new frameworks and languages) but for production grade software there are more requirements that need to be met and be reflected in the sw development process (even SWE agent based ones where the human doesn't write a line of code - e.g. spec driven development (with break-down to tasks and task execution following a sound model without exceptions), good API design, good software architecture, TDD, tests (unit, component, integration), security and pentesting, usage simulation, code / feature review, good documentation, integration into existing systems) 

I also want to integrate some thougts from Dan North on deliberate learning and deliberate discovery (i.e. the learning is the important part of software, not the coding also  discussed in the "laws of software process" by philip G armour) 
Dan discussed if you have small enough components with a well specced and tested API for the behavior, the inside of these components is throwaway (can be rewritten any time with new tech, new learnings, and leaving off the accumulated cruft), what is important are the learnings about the (business) process and the coverage for behavior.

in my past I gathered a lot of expertise with software design patterns, refactoring, domain specific languages, software architecture and design, TDD and more so this ties also to my experience. I contributed to several of Martin Fowlers books as reviewer and was closely engaged with the software pattern community and love the pattern ideas from Christoffer Alexander.

Create an markdown artifact with the keynote title and abstract and also lay out a possible slide narrative for a 30 minute keynote.

Here were my previous notes/ideas on the topic:

#### Thoughts on GenAI Agents \-\> Software Development

* what are GenAI agents  
  * tools and functions that give the LLM access to the outer world of information, data, actions and interactions  
  * kind of how the human brain makes use of many sensors and actuators to learn and affect the real world  
* examples of agents  
  *   
* many agentic approaches could be handled better by just regular software development  
  * those are just loops and if conditions  
  * as soon as the decision making rules and data is clear, regular programming paradigms can be used to execute the action  
* moving the control up one layer of the stack  
* implications \- latency, cost, correctness, probabilistic behavior  
* what's the benefit of using an LLM? \- which is focused on generation  
* too expensive and slow  
* regular code for extraction  
* specialized models for extraction, retrieval, reasoning


### Questions from Claude

Q: What's the audience for the VibeCode conference — mostly vibe coders / beginners, experienced engineers, or a mixed audience?
A: Experienced engineers / team leads

Q: Do you want the keynote to reference Neo4j / knowledge graphs at all, or keep it purely about the software craft journey?
A: light mention when it comes to software structure and representation of many aspects of software as a graph (code, dependencies, commits, architectures, code transformation and modernization - thoughtworks - https://martinfowler.com/articles/legacy-modernization-gen-ai.html) and then also for agent-memory, can mention the example of https://deusdata.github.io/codebase-memory-mcp/

Q: What tone should the keynote strike?
A: Inspiring & encouraging

Output was @vibecode-keynote v1.md

### Output from Claude on v1

Let me grab that ThoughtWorks/Fowler article on legacy modernization with AI and the codebase memory MCP page for context.Searched the webSearched the webNow let me quickly search for Dan North's deliberate discovery ideas to make sure I reference them accurately.Searched the webSearched the webNow let me search for Philip Armour's "Laws of Software Process" to get the key framing right.Searched the webSearched the webExcellent — I now have everything I need. Let me build the keynote artifact.VibeCode Conference Keynote — From Vibe Coding to Agentic EngineeringDocument # From Vibe Coding to Agentic Engineering

**Subtitle:** From fast personal prototypes to reliable production software

**Alternative titles:**

- "Vibe Coding Got You Here — Agentic Engineering Gets You There"
- "Beyond the Vibes: What Production SoHere's your keynote draft. A few notes on the choices I made:
Structure: Four acts that mirror a natural audience journey — excitement (vibe coding is amazing) → tension (but it breaks down) → resolution (agentic engineering practices) → reflection (the human element). This keeps it from feeling like a lecture and instead tells a story.
The philosophical backbone comes from Armour and Dan North, not as a detour but as the reason the practices matter: if software is knowledge, then the spec, the tests, and the behavioral contracts are the durable artifacts — the code is throwaway. AI makes that vision practical for the first time, which is your fresh angle.
Neo4j touch is in Slide 14 — it lands naturally when discussing how software structure is itself a graph, with CodeConcise and codebase-memory-mcp as concrete examples of graph-powered agent intelligence. Not a sales pitch, just a genuine "this is where graphs fit."
Your personal expertise (patterns community, Fowler books, Alexander, TDD) is woven through rather than called out in one slide — it gives you authority throughout rather than a single "here's my resume" moment.
Timing is budgeted conservatively at ~28 min of content, leaving 2 min of buffer for audience reactions and transitions. Want me to adjust any section, add a live demo slot, or shift the emphasis?


### My feedback on @vibecode-keynote v1.md

Good first draft.
Add your thinking and resasoning to the artifact too at the end.

If you need to do further research how others in the field see this, in this area please do so to widen and strengthen the perspective.


### Output from Claude on V2

Claude responded: Let me research some additional perspectives to strengthen the keynote before updating.
Let me research some additional perspectives to strengthen the keynote before updating.


Searched the web
Searched the web
This is excellent material. Now let me search for one more angle — the cognitive debt / exhaustion dimension and the "humanity is not ready for this much software" perspective.


Searched the web
Searched the web
Excellent — I now have a rich set of additional perspectives from Addy Osmani, Steve Yegge, Sau Sheong, Karpathy's reframing, the Turing College analysis, IBM, and more. Let me update the artifact with strengthened content and the reasoning section.


VibeCode Conference Keynote — From Vibe Coding to Agentic Engineering
Document ∙ Version 2 
Here's the significantly strengthened version. The key additions from the research:

New voices woven in:

Karpathy's own retirement of "vibe coding" for professional work (Feb 2026) — gives the vocabulary shift authority from its creator
Addy Osmani (Google) — the sharpest practitioner writing on spec-driven development, the factory model, and why "vibe" carries too much baggage for a CTO conversation. His "suitcase term" framing is perfect for your Slide 2.
Sau Sheong (Singapore gov tech) — the sobering "humanity is not ready for this much software" quote, plus a five-level maturity framework that works beautifully for your closing spectrum slide
Steve Yegge / TinyComputers / HBR — the cognitive exhaustion thread is now grounded in Jevons Paradox (efficiency gains consumed by demand expansion for human judgment) and confirmed by BCG research. Makes the "know your ceiling" advice land with authority.
Turing College / Forrester analysts — industry analysis including the Amazon Q deployment incident, which gives the "responsibility boundary" real teeth
arXiv paper — academic taxonomy validating the vibe/agentic distinction with 20 use cases
Structural changes:

Slide 2 now includes Karpathy's self-retirement and Osmani's "suitcase term" critique
Slide 6 (Software Is Knowledge) now integrates North's Replaceable Component Architecture directly — the "throwaway internals" argument is made concrete
Slide 12 (Dark Factory) now includes both the Cursor/Osmani "factory" framing and Sau Sheong's counterpoint about absorption capacity
Slide 18 (closing) uses Sau Sheong's five-level framework as a concrete visual
Want me to adjust emphasis, add a demo slot, or develop any section further?


### My Feedback on @vibecode-keynote v2.md

I think the new abstract is too literal and boring, and not inspiring, thought evoking enough.  Ala "you thought everything would be new, shiny, different with AI SWE - but the core principles still hold". One aspect that I would love to get across in the Keynote is - good software design was never for the machine it was always for other humans that had to understand and maintain and extend the code/system - now the SWE agents are another kind of team mate that also relies on language (both natural and code) for communication, reasoning, learning, and production.  And as LLMs are trained on human communications they have integrated the ways of how humans exchange information as their main way of communication/reasoning - in this case how we describe, discuss and explain software.

You should also research the work from Kent Beck and Kevlin Henney in this area.

Not sure what Ward Cunningham, Erich Gamma and Grady Booch have to say here.

And Dan North and a few other SWE luminaries are AI sceptics so would be good to also integrate their perspectives.

Final output of far  @vibecode-keynote v3.md


### Response from Claude

Let me research Kent Beck, Kevlin Henney, and the other luminaries' perspectives on AI and software engineering.Searched the webSearched the webNow I have everything I need. Let me rewrite the artifact with the new abstract, the "design was always for humans, now agents are another kind of teammate" thread, and all the new voices integrated.VibeCode Conference Keynote — From Vibe Coding to Agentic EngineeringDocument ∙ Version 3 # From Vibe Coding to Agentic Engineering

**Subtitle:** From fast personal prototypes to reliable production software

**Alternative titles:**

- "Vibe Coding Got You Here — Agentic Engineering Gets You There"
- "Code Is Cheap Now — So What Becomes Here's the significantly reworked keynote. The three biggest changes:
1. The abstract is now provocative, not descriptive. It leads with the surprise ("you thought everything would be new — turns out the old practices are what matter") and immediately introduces the core insight about design-as-communication and agents-as-teammates.
2. The "design was never for the machine" thread runs through the entire talk as the unifying argument. Slide 6 is now the conceptual heart — explaining why good practices work with agents (because agents are built from human communication about code). This connects naturally to Henney's "tests as specifications," Beck's context-seeding, Alexander's quality-without-a-name, and your own patterns background.
3. The luminaries are woven in as a chorus, not just cited:

Kent Beck: "unpredictable genie," TDD as superpower, agents deleting tests, augmented coding as the middle term
Grady Booch: third golden age, "your tools change but your problems don't," architecture measured by cost of change, the Amodei pushback
Kevlin Henney: tests as specifications, 10x defect rate data, quality skepticism as engineering discipline
Dan North: Deliberate Discovery applied to the AI context, replaceable components (your original framing), his skepticism lending credibility
The Deer Valley declaration (Beck/Tacho/Yegge at Fowler's retreat): "We remain skeptical and we remain human"

I also noted in the reasoning section what I couldn't find: Ward Cunningham and Erich Gamma don't have public AI positions I could locate, and North hasn't written a detailed AI piece — which actually creates an opportunity for you to be the one who applies his ideas to the agent era.
Want me to develop any section further, or start working on the actual CFP submission text?