# Mining the Context-Engineering Deck for Workshop Reuse

**Source**: `context-engineering-presentation.pdf`, slides 1–40 (slides after 40 are research material, ignored).
**Purpose**: identify reusable concepts, slides, and quotes from the existing CE deck and map them to specific workshop sections so I don't reinvent. Strong material — much of it lands more cleanly than what I drafted.

---

## TL;DR — what I'd lift verbatim

1. **The Context Pyramid (Slide 18)** — Inverted pyramid: Persistent base / Dynamic middle / Ephemeral top + caching arrow. **Drops directly into `workshop-cost-tokens.md` Slide 1** as a much better visual than the table I drafted. Caching = stability ladder. Use this.
2. **5 Failure Modes of Context (Slide 12)** — Context Rot, Poisoning, Confusion, Distraction, Clash, with the Gemini-Pokemon and Gemini->100k examples and the dbreunig.com source. **Drops into `workshop-practices.md` Slide 2** (Challenges) — replaces my generic list with named, sourced phenomena.
3. **3-Phase Agent Loop with 3 Context Problem (Slides 22–23)** — Reason/Plan · Act/Execute · Observe/Process, with what each phase needs in context. **Drops into `workshop-practices.md` Slide 7** (per-task loop) as the conceptual frame *above* the 11-step loop.
4. **Context Structure principles (Slide 16)** — group, label (headers + XML), hierarchy, concise, refer back, reiterate at end (attention). **Drops into `workshop-practices.md` Slide 4** (AGENTS.md authoring) — these are the *why* under the format rules I gave.
5. **Karpathy "context engineering" tweet (Slide 5)** — pairs perfectly with the Feb 2025 "vibe coding" tweet already in `workshop-intro.md`. **Add to intro Slide 3** (history) as the moment "context engineering" entered the vocabulary (June 2025).
6. **3 Approaches: Offload / Consolidate / Retrieve (Slide 17)** — drops into the cost-tokens deck as the conceptual frame for *why* the savings levers work (Slide 2 of cost-tokens).

---

## Slide-by-slide mining

### Reuse-grade material (drop in mostly as-is)

| CE slide | Concept | Where it goes |
|---|---|---|
| **5** | Karpathy "context engineering > prompt engineering" (June 2025 tweet) | `workshop-intro.md` Slide 3 — pair with Karpathy Feb 2025 vibe-coding tweet |
| **6** | "Why Context Matters Now" — Right info / Test Time > Train Time / Bigger ≠ better / Structured input → reliability | `workshop-intro.md` Slide 4 framing OR `workshop-practices.md` Slide 3 (latent space collapse) |
| **8** | Lance Martin: "Context engineering is building dynamic systems to provide the right information and tools in the right format such that the LLM can plausibly accomplish the task" | quote bank — fits practices Slide 3 |
| **10** | Venn diagram of CE sources (RAG, Prompt Eng, State/History, Memory, Structured Outputs) — Dex Horthy / 12-Factor Agents | Optional: `workshop-harnesses.md` Slide 1 anatomy as an alternative visual |
| **11** | Sources of Context — Human / Cognitive / Memory / Data Tools (clean four-quadrant) | `workshop-harnesses.md` Slide 1 — or skip; my anatomy box is similar |
| **12** | **5 Failure Modes** — Rot / Poisoning / Confusion / Distraction / Clash with named examples | **`workshop-practices.md` Slide 2 — REPLACE my generic challenges list** |
| **13** | **MVC — Minimum Viable Context** — Clear instructions, Role/Goals/Constraints/Facts, Selected Examples, Minimal Tools, User Request. Aim: high signal-to-noise | **`workshop-practices.md` Slide 4 — frame AGENTS.md as MVC** |
| **14** | Miller "Magical Number 7±2" / chunking | quote bank — fits practices Slide 4 (AGENTS.md) as a why-keep-it-short justification |
| **15** | Memory — STM (current context, compression) vs LTM (episodic, semantic/structural, procedural) | optional: practices section subhead OR harnesses section |
| **16** | **Context Structure** — group, label clearly (headers + XML tags), hierarchy, concise, refer back, **reiterate at end** | **`workshop-practices.md` Slide 4 — AGENTS.md authoring rules** |
| **17** | **Approaches: Offload / Consolidate / Retrieve** — three ways to manage context | **`workshop-cost-tokens.md` Slide 2** — frame for the savings levers |
| **18** | **Context Pyramid** — Persistent base / Dynamic middle / Ephemeral top + caching arrow | **`workshop-cost-tokens.md` Slide 1 — REPLACE my "where the tokens go" graphic** |
| **19** | Lisa Maria Martin: "When we organize information, we change it" | quote bank — practices Slide 4 |
| **21** | **Lance Martin / LangChain — "Communication is all you need"**: "Most of the time when an agent is not performing reliably the underlying cause is not that the model is not intelligent enough, but rather that context and instructions have not been communicated properly to the model" | **Keynote!** This is the *single best quote* I've seen for the design-as-communication thread. Goes into `vibecode-keynote-v3.md` and the workshop's mentoring frame. |
| **22** | **3-Phase Agent Loop** — Guidance / Thought / Action / Observation / Human-Agent | **`workshop-practices.md` Slide 7 — per-task loop frame** |
| **23** | **Dynamic Context for Agents — 3 Context Problem**: Reason/Plan (what to do?) · Act/Execute (how?) · Observe/Process (integrate results) | **`workshop-practices.md` Slide 7** as the *conceptual layer* above the 11-step loop. Each step in the 11-step loop maps to one of these three contexts. |
| **24** | Jason Liu: "Context engineering is designing tool responses and interaction patterns that give agents situational awareness" | quote bank — fits harnesses or practices |
| **25** | Tools & Context — Push (RAG) vs Pull (Tool Calling), Tool Selection (API design), Tool outputs (structure/volume/relevancy/explainability) | `workshop-harnesses.md` Slide 3 (craft levers) — as a Tools subsection |
| **26** | Multi-Agent Systems — Divide & Conquer / Conflicting Decisions / Context Isolation | `workshop-harnesses.md` or `workshop-practices.md` aside on sub-agents |
| **30** | Graphs capture context (with sample graph diagram) | **Keynote** — neo4j touch (Slide 14 of keynote v3); workshop only as a brief tease |
| **31** | Context Graphs Enable Explainable AI — Storing/Visualizing/Analysing | Keynote / workshop tease |
| **32** | **Jaya Gupta**: "Context Graph is a knowledge graph specifically designed to capture decision traces — the full context, reasoning, and causal relationships behind every significant decision in an organization" | quote bank — keynote (Slide 14) |
| **33** | create-context-graph.dev (user's product) | **`workshop-own-experience.md` Slide 6** (larger greenfield) — add as a demo option |
| **36** | **Beyond Prompts paper**: "Communicating with an AI is very much a conversation — not a rigid formula. You need to express your intent clearly, but avoid micromanaging every word; too much control collapses the context." | **Keynote** — wraps up the design-as-communication thread perfectly. Pair with Slide 21 quote. |
| **39** | "What we've learned" 6-point recap | optional model for any closing slide |
| **40** | Resources list with hyperlinks | **`workshop-resources.md`** — cross-reference and merge |

### Material to skip / lower-priority

| CE slide | Why skip |
|---|---|
| 1, 2, 3, 4 | Title/intro slides — context-specific, not reusable |
| 7 | "From prompting to CE" — already covered better in our intro |
| 9 | Section divider |
| 20 | Section divider |
| 27 | Section divider |
| 28 | LLMs + KGs better-together — too high-level for the workshop |
| 29 | RAG → GraphRAG — keynote-only |
| 34, 35 | Graph Intelligence Platform / Agentic architecture — keynote-only or product-pitch |
| 37 | Section transition |
| 38 | Graph Academy promo — could be a slot in workshop-resources.md |

---

## Verified quote bank (with attribution + URL where I have it)

Stronger than the bank I had — these are confirmed wordings from your deck.

```
Andrej Karpathy (June 2025):
"+1 for 'context engineering' over 'prompt engineering'.
 Context engineering is the delicate art and science of filling the context
 window with just the right information for the next step."
 — x.com/karpathy/status/1937902205765607626

Lance Martin (LangChain):
"Context engineering is building dynamic systems to provide the right
 information and tools in the right format such that the LLM can plausibly
 accomplish the task."
 — Context Engineering Presentation by Lance Martin

LangChain — "Communication is all you need":
"Most of the time when an agent is not performing reliably the underlying
 cause is not that the model is not intelligent enough, but rather that
 context and instructions have not been communicated properly to the model."
 — LangChain blog: "Communication is all you need"

Jason Liu (Context Engineering Series):
"Context engineering is designing tool responses and interaction patterns
 that give agents situational awareness to navigate complex information
 spaces effectively."

Jaya Gupta (Foundation Capital — Context Graphs):
"Context Graph is a knowledge graph specifically designed to capture
 decision traces — the full context, reasoning, and causal relationships
 behind every significant decision in an organization."
 — foundationcapital.com/ideas/context-graphs-ais-trillion-dollar-opportunity
 — neo4j.com/blog/agentic-ai/hands-on-with-context-graphs-and-neo4j

Lisa Maria Martin (Everyday Information Architecture):
"When we organize information, we change it. The key is to alter it in a
 way that enhances understanding."

Beyond Prompts: Learning from Human Communication for Enhanced AI Intent
Alignment:
"Communicating with an AI is very much a conversation — not a rigid formula.
 You need to express your intent clearly, but avoid micromanaging every
 word; too much control collapses the context."

George A. Miller (paraphrased — chunking):
"We are limited in what we can hold in short-term memory. But by 'chunking'
 — structuring information into meaningful groups — we improve retention
 and reduce cognitive load."
```

These are all confirmed-wording from the deck, so they can be quoted on slides without [VERIFY] tags.

---

## Specific edits to apply to existing workshop files

Numbered for easy execution. None require rewriting from scratch — they're surgical insertions/replacements.

### To `workshop-intro.md`

1. **Slide 3 — Phase 2 (vibe coding 2025)**: Add the **Karpathy "context engineering" tweet (June 2025)** as a *second* Karpathy moment in the timeline. The Feb 2025 vibe-coding tweet says "forget the code"; the June 2025 CE tweet says "obsess over what's *around* the code." Together they bracket the year.
2. **Slide 4 (Why coding is a good domain)**: Add a 6th property — "Test Time > Train Time" — from CE Slide 6. The model's task-time reasoning matters more than its training; that's why context engineering pays off.

### To `workshop-harnesses.md`

3. **Slide 3 (craft levers)**: In the "Tools, hooks, skills, MCP" subsection, add a sub-bullet on **Push (RAG) vs Pull (Tool Calling)** from CE Slide 25 — clean framing for when to inject context vs let the agent fetch it. Also add the "API design principles apply to tool design" line.

### To `workshop-practices.md`

4. **Slide 2 (challenges)**: **REPLACE** my generic 7-failure-mode list with the **5 named failure modes from CE Slide 12**: Context Rot, Poisoning (Gemini Pokemon), Confusion (more tools = worse), Distraction (Gemini >100k), Clash. Cite dbreunig.com/2025/06/22/how-contexts-fail-and-how-to-fix-them.html. Named, sourced, more credible than mine.
5. **Slide 3 (collapsing latent space)**: Add the **Lance Martin "right info, right format, right tools" quote** as the framing line; keep my "every constraint narrows the distribution" prose.
6. **Slide 4 (AGENTS.md)**: **MERGE** in:
   - **MVC framing (CE Slide 13)** — explicitly call AGENTS.md "the project's MVC."
   - **Context Structure rules (CE Slide 16)** — add as a subsection: group, label with XML/headers, hierarchy, concise, **reiterate essence at end (attention)**. The "attention at the end" rule is *missing from my current draft* and matters.
7. **Slide 7 (per-task loop)**: **WRAP** the 11-step loop in the **3-Phase Agent Loop frame from CE Slide 22** (Guidance · Thought · Action · Observation · Human/Agent) and the **3-Context Problem from CE Slide 23** (Reason/Plan · Act/Execute · Observe/Process). Each of my 11 steps maps to one of these three contexts. The 3-context layer is *the missing conceptual frame* I wanted on that slide.

### To `workshop-cost-tokens.md`

8. **Slide 1 (where the tokens go)**: **REPLACE** my "INPUT/OUTPUT/CACHE-FRIENDLY" ASCII table with the **Context Pyramid visual from CE Slide 18**. Persistent base (system prompt, role, policies, core facts) → Dynamic middle (examples, memory, metadata, tool list) → Ephemeral top (tool outputs, reasoning, user query). Caching arrow upward. Much cleaner — and matches how the API actually charges.
9. **Slide 2 (savings levers)**: **PREFIX** the lever list with the **Offload / Consolidate / Retrieve frame from CE Slide 17**. Each lever is one of the three. (Filesystem & graph storage = Offload; /compact & summarization = Consolidate; caching & RAG = Retrieve.) Gives the slide a story arc instead of a flat list.

### To `vibecode-keynote-v3.md` (the keynote — separate from workshop)

10. **Add the Lance Martin "Communication is all you need" quote** somewhere in the design-as-communication thread (likely Slide 6 conceptual heart). The wording is *exactly* what the keynote argues, with stronger attribution than my paraphrases.
11. **Add the Beyond Prompts quote** — "too much control collapses the context" — as a closing-section pair to the Lance Martin quote.
12. **Slide 14 (Neo4j touch)**: Add the **Jaya Gupta context-graphs quote** + reference to `create-context-graph.dev` and the Foundation Capital "trillion-dollar opportunity" piece. Stronger and more current than what's in v3.

### To `workshop-own-experience.md`

13. **Slide 6 (larger greenfield)**: Add **`create-context-graph.dev`** as one of the demo options. From CE Slide 33 — "AI agents with graph memory, scaffolded in seconds." Fits the "larger greenfield" mode and ties the workshop to the keynote thread.

### To `workshop-resources.md`

14. Cross-reference the CE Slide 40 resource list — there's overlap with what I have, but the CE deck includes some I missed:
    - **Dex Horthy — 12-Factor Agents** (the original "context engineering" coinage)
    - **Lance Martin Context Engineering presentation + podcast**
    - **Jeff Huber (Chroma) — "RAG is Dead, Context Engineering is King"**
    - **The Prompt Pyramid — A Better Way to Structure Complex Tasks for GPT**
    - **Beyond Prompts: Learning from Human Communication for Enhanced AI Intent Alignment** (paper)
    - **Context Rot — Chroma**
    - **Foundation Capital — Context Graphs as AI's trillion-dollar opportunity**

---

## Bigger structural option to consider

The CE deck arguably gives us a **whole new mid-deck section** for the workshop: a 5-min "Context Engineering" mini-section between the harness anatomy and the practices. Argument for adding it:

- The workshop currently jumps from "what's a harness" → "good practices" without the *conceptual layer* of "what's the model actually consuming, and why does the structure matter?"
- The 3-Context Problem (CE 23) and the Context Pyramid (CE 18) together form that missing layer.
- It would reuse 6–8 CE slides directly with minimal rework — fastest path to value.
- 5 minutes; sits perfectly between harnesses and cost/tokens.

**Downside**: adds another section to an already-tight deep-dive block. We're at ~30 minutes of harnesses+cost+benchmarks+practices already.

**Lean**: keep the current structure, but inject the 3 strongest CE pieces (Context Pyramid → cost; 5 Failure Modes → practices; 3-Context frame → per-task loop). That's the 80/20.

---

## Open questions for me to decide before tomorrow

- [ ] Apply edits 1–14 above, or wait for user review of which to take?
- [ ] Add the standalone "Context Engineering" mini-section, or keep the surgical-insertion approach? **Lean: surgical, save the mini-section idea for if we discover a gap during dry-run.**
- [ ] Use the full CE Resources list to expand `workshop-resources.md`, or keep that doc tight? **Lean: add the 7 named items above, skip the rest.**
- [ ] On the keynote: do I push v3 → v4 with the Lance Martin + Beyond Prompts quotes now, or wait until closer to keynote date? **Lean: now while it's fresh.**
