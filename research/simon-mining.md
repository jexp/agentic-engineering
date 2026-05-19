# Mining Simon Willison's Blog for Workshop Reuse

**Sources**: [simonwillison.net](https://simonwillison.net) — primary tags `agentic-engineering`, `coding-agents`, `claude-code`, `model-context-protocol`, `prompt-engineering`, `tools`. Plus:
- [Lenny's Newsletter podcast](https://www.lennysnewsletter.com/p/an-ai-state-of-the-union) (Apr 2026) + [Simon's highlights](https://simonwillison.net/2026/Apr/2/lennys-podcast/)
- [Heavybit High Leverage Ep. #9](https://simonw.substack.com/p/vibe-coding-and-agentic-engineering) with Joseph Ruscio (May 6 2026)
- **[Agentic Engineering Patterns guide](https://simonwillison.net/guides/agentic-engineering-patterns/)** — Simon's structured reference guide (published Mar 2026, ongoing). Sections: Principles → Working with Agents → Testing & QA → Understanding Code → Annotated Prompts → Appendix
- [GitLab Act 2](https://simonwillison.net/2026/May/11/gitlab-act-2/) (May 11 2026) — agents + org restructuring
- [James Shore on maintenance costs](https://simonwillison.net/2026/May/11/james-shore/) (May 11 2026)
- [Mitchell Hashimoto / "Not So Locked In"](https://simonwillison.net/2026/May/14/not-so-locked-in/) (May 14 2026) — agent-enabled reversibility
- [Shopify River / Lehrwerkstatt](https://simonwillison.net/2026/May/11/learning-on-the-shop-floor/) (May 11 2026) — public agent channels as learning infrastructure
**Purpose**: identify quotable, sourced, *named* material from the most thoughtful daily practitioner in the space — and map each piece to the workshop section that benefits most. Simon's voice is balanced (skeptical *and* enthusiastic), which is exactly the tone the workshop wants.

---

## TL;DR — what to lift verbatim

1. **The senior/mid/junior split (Lenny's Apr 2026)** — *"It amplifies experienced engineers. It solves so many onboarding problems for new engineers. The problem is the people in the middle."* — Drops directly into [`workshop-mental-safety.md`](../workshop/workshop-mental-safety.md) Slide 2 (career), with the senior/junior/mid trichotomy as the *frame* of that slide. This is the single best quote on the career thread Simon has produced.
2. **"95% of the code I produce, I didn't type myself" + "I can churn out 10,000 lines of code in a day. And most of it works."** (Lenny, Apr 2026) — Drops into [`workshop-intro.md`](../workshop/workshop-intro.md) Slide 3 (Phase 3, where we are now). Rare *self-reported* numbers from a credible practitioner.
3. **"Building is now cheap; knowing whether what you built is correct is the expensive part"** (Lenny) — Drops into [`workshop-practices.md`](../workshop/workshop-practices.md) Slide 1 (mentoring frame) as the closing line. Reframes the whole workshop's goal in one sentence.
4. **"Shipping worse code with agents is a *choice*. We can choose to ship code that is better instead."** ([Mar 10 2026, "AI should help produce better code"](https://simonwillison.net/guides/agentic-engineering-patterns/better-code/)) — Drops into the keynote and into [`workshop-practices.md`](../workshop/workshop-practices.md) Slide 1 (mentoring frame). Counters the "AI = slop" objection cleanly.
5. **Simon's exact harness definition** ([Mar 16 2026, "How coding agents work"](https://simonwillison.net/guides/agentic-engineering-patterns/how-coding-agents-work/)): *"A coding agent is a piece of software that acts as a harness for an LLM, extending that LLM with additional capabilities that are powered by invisible prompts and implemented as callable tools."* — Drops into [`workshop-harnesses.md`](../workshop/workshop-harnesses.md) Slide 1 as the canonical definition. Also useful: *"a few dozen lines of code"* line for the demystification beat.
6. **The "wiped out by 11 AM" admission** (Lenny) — Drops into [`workshop-mental-safety.md`](../workshop/workshop-mental-safety.md) Slide 1 (mental cost). Strongest peer evidence that this is real, not whining.
7. **"Don't file pull requests with code you haven't reviewed yourself"** ([Mar 4 2026, anti-patterns](https://simonwillison.net/guides/agentic-engineering-patterns/anti-patterns/)) — Drops into [`workshop-practices.md`](../workshop/workshop-practices.md) Slide 6 (review fatigue). Sharper than my paraphrase.
8. **Vibe coding and AE convergence — his "disturbing realization"** (Heavybit, May 2026) — *"Those things have started to blur for me already, which is quite upsetting."* Drops into [`workshop-intro.md`](../workshop/workshop-intro.md) and [`workshop-mental-safety.md`](../workshop/workshop-mental-safety.md) as the most current honest admission from the field's most credible practitioner.
9. **The "treat agents like another team" frame** (Heavybit, May 2026) — *"I'm starting to treat the agents in the same way [as a semi-black box team]. And it still feels uncomfortable."* + "normalization of deviance" coinage. Drops into [`workshop-practices.md`](../workshop/workshop-practices.md) review-fatigue slide and [`workshop-mental-safety.md`](../workshop/workshop-mental-safety.md).
10. **New evaluation challenge: "I want somebody to have used the thing"** (Heavybit, May 2026) — Simon can't distinguish a vibe-coded repo from a carefully built one by looking at commits/tests. What he trusts now: two weeks of daily use. Drops into [`workshop-benchmarks.md`](../workshop/workshop-benchmarks.md) and keynote.
11. **Bottlenecks shifted — Jenny Wen design-process insight** (Heavybit, May 2026) — The entire SDLC was designed assuming slow code production. Jenny Wen (Anthropic design lead): if building is cheap, design process can take more risk. Drops into keynote "so what changes?" thread.
12. **Matthew Yglesias quote on the right model for society** (Heavybit, May 2026) — *"I want professionally managed software companies to use AI coding assistance to make more/better/cheaper software products that they sell to me for money."* Best single line rebuttal to "vibe-code everything." Drops into keynote and [`workshop-intro.md`](../workshop/workshop-intro.md).
13. **James Shore maintenance costs** (May 11 2026) — 2x code output at constant maintenance cost = 2x future maintenance burden. "Trading a temporary speed boost for permanent indenture." Sharp corrective to productivity-celebration. Drops into keynote "what can go wrong" beat and [`workshop-cost-tokens.md`](../workshop/workshop-cost-tokens.md).
14. **Agent-enabled reversibility** (May 14 2026, Mitchell Hashimoto) — Bun rewrote Zig→Rust in 1–2 weeks with agents. *"Programming languages used to be LOCK IN, and they're increasingly not so."* Tech choices becoming reversible architectural experiments. New named pattern. Drops into keynote and [`workshop-intro.md`](../workshop/workshop-intro.md).
15. **Shopify Lehrwerkstatt / public agent channels** (May 11 2026) — Shopify's River agent operates exclusively in public Slack channels by design. Tobi Lütke: osmosis learning doesn't need a curriculum, just visible work. Drops into [`workshop-practices.md`](../workshop/workshop-practices.md) organizational patterns and [`workshop-resources.md`](../workshop/workshop-resources.md).
16. **The patterns guide itself** (Mar 2026) — structured reference at [simonwillison.net/guides/agentic-engineering-patterns/](https://simonwillison.net/guides/agentic-engineering-patterns/). Canonical reading list for the workshop resources section. Anti-pattern chapter: one named pattern — "Inflicting Unreviewed Code on Collaborators" with five characteristics of a good agentic PR.

---

## Per-section reuse table

| Workshop file | Section / Slide | Simon piece | What it adds |
|---|---|---|---|
| [`workshop-intro.md`](../workshop/workshop-intro.md) | Slide 1 (Simon quote framing) | "no longer afraid of starting projects" — already cited in [`workshop-exercise-1.md`](../workshop/workshop-exercise-1.md) | Ties intro to exercise 1 |
| [`workshop-intro.md`](../workshop/workshop-intro.md) | Slide 3, Phase 3 (now) | Lenny: "10,000 lines/day", "95% I didn't type myself", **November 2025 inflection point** (Opus 4.5 / GPT-5.1) | Concrete dates + numbers from a credible practitioner |
| [`workshop-intro.md`](../workshop/workshop-intro.md) | Slide 4 (why coding) | Simon's *"Code execution is the defining capability that makes agentic engineering possible"* ([what-is-agentic-engineering](https://simonwillison.net/guides/agentic-engineering-patterns/what-is-agentic-engineering/)) | One-line answer to "why coding" |
| [`workshop-harnesses.md`](../workshop/workshop-harnesses.md) | Slide 1 (anatomy) | Simon harness definition (Mar 16 2026) | Canonical, citable wording |
| [`workshop-harnesses.md`](../workshop/workshop-harnesses.md) | Slide 1 footer | *"It's just a few dozen lines of code"* | Demystifies the magic |
| [`workshop-tool-use.md`](../workshop/workshop-tool-use.md) | Rung 5 (Skills) | [Oct 16 2025 "Claude Skills are awesome, maybe a bigger deal than MCP"](https://simonwillison.net/2025/Oct/16/claude-skills/) — *"each skill only takes up a few dozen extra tokens"* | Token-economy argument for skills |
| [`workshop-tool-use.md`](../workshop/workshop-tool-use.md) | Rung 6 (MCP) — caveat | [Aug 22 2025 "too many MCPs"](https://simonwillison.net/2025/Aug/22/too-many-mcps/) — *"GitHub MCP defines 93 additional tools and swallows another 55,000 of those valuable tokens"* | Hard number for the "use sparingly" rule |
| [`workshop-tool-use.md`](../workshop/workshop-tool-use.md) | Rung 6 (MCP) — security | [Jun 16 2025 lethal trifecta](https://simonwillison.net/2025/Jun/16/the-lethal-trifecta/) | The single best frame for MCP risk |
| [`workshop-cost-tokens.md`](../workshop/workshop-cost-tokens.md) | Slide 2 (savings levers) | Skills token-frugality + CLI-instead-of-MCP pattern | Concrete lever, with a number |
| [`workshop-cost-tokens.md`](../workshop/workshop-cost-tokens.md) | Slide on caching | [How coding agents work](https://simonwillison.net/guides/agentic-engineering-patterns/how-coding-agents-work/): *"Agents are designed to avoid modifying earlier conversation content to maximize cached input token efficiency"* | Why prefix-stability matters, in one line |
| [`workshop-practices.md`](../workshop/workshop-practices.md) | Slide 1 (mentoring frame) | "Shipping worse code with agents is a choice" + "Building is cheap; verifying is expensive" | Two bookend quotes |
| [`workshop-practices.md`](../workshop/workshop-practices.md) | Slide 2 (challenges) | Anti-patterns post — *"Don't file pull requests with code you haven't reviewed yourself"* | Sharper review-fatigue framing |
| [`workshop-practices.md`](../workshop/workshop-practices.md) | Slide 4 (AGENTS.md) | [Hoard things you know how to do](https://simonwillison.net/guides/agentic-engineering-patterns/hoard-things-you-know-how-to-do/) — *"we only ever need to figure out a useful trick once"* | The *why* of AGENTS.md, in Simon's frame |
| [`workshop-practices.md`](../workshop/workshop-practices.md) | Slide 5 (spec-driven) | Apr 5 2026 [scan-for-secrets release](https://simonwillison.net/2026/Apr/5/scan-for-secrets-3/) — *"README-driven-development: carefully construct the README... then dump it into Claude Code"* | Real-world spec-first example |
| [`workshop-practices.md`](../workshop/workshop-practices.md) | Slide 7 (per-task loop) | [Mar 6 2026 agentic manual testing](https://simonwillison.net/guides/agentic-engineering-patterns/agentic-manual-testing/) — *"Never assume that code generated by an LLM works until that code has been executed."* | Verification step justification |
| [`workshop-practices.md`](../workshop/workshop-practices.md) | New aside slide on **subagents** | [Mar 17 2026 subagents post](https://simonwillison.net/guides/agentic-engineering-patterns/subagents/) | First-class technique we haven't covered |
| [`workshop-practices.md`](../workshop/workshop-practices.md) | Aside on Git | [Mar 21 2026 Git with coding agents](https://simonwillison.net/guides/agentic-engineering-patterns/using-git-with-coding-agents/) — *"Sort out this git mess for me"* and *"Use git bisect to find when this bug was introduced"* | Concrete prompts attendees can copy |
| [`workshop-own-experience.md`](../workshop/workshop-own-experience.md) | Slide 1 (research/learning) | Simon's *guides/agentic-engineering-patterns* itself is the canonical example | Demo target |
| [`workshop-own-experience.md`](../workshop/workshop-own-experience.md) | Slide 2 (HTML tools) | [Dec 10 2025 HTML tools patterns](https://simonwillison.net/2025/Dec/10/html-tools/) — *"over 150"* tools, all the patterns | Already in exercise-1; double-down here |
| [`workshop-own-experience.md`](../workshop/workshop-own-experience.md) | Slide 5 (autoresearch / batch) | [Mar 13 2026 Liquid post](https://simonwillison.net/2026/Mar/13/liquid/) — *"93 commits from around 120 automated experiments"*, *"53% faster parse+render, 61% fewer allocations"*, *"CEOs can code again!"* | Concrete numbers, named pattern |
| [`workshop-own-experience.md`](../workshop/workshop-own-experience.md) | Slide 6 (greenfield) | [Apr 5 2026 "Eight years of wanting"](https://simonwillison.net/2026/Apr/5/building-with-ai/) — *"AI made me procrastinate on key design decisions"* | Honest failure-mode addition |
| [`workshop-mental-safety.md`](../workshop/workshop-mental-safety.md) | Slide 1 (mental cost) | Lenny: *"by like 11 AM, I am wiped out for the day"*, four-agent-parallel cognitive load | The peer-confession that legitimizes the slide |
| [`workshop-mental-safety.md`](../workshop/workshop-mental-safety.md) | Slide 1 — addiction risk | [Mar 25 2026 slowing down](https://simonwillison.net/2026/Mar/25/thoughts-on-slowing-the-fuck-down/) — Mario Zechner via Simon: *"merchants of complexity"*, *"agents grind problems into dust"* | Strongest "danger" wording in the corpus |
| [`workshop-mental-safety.md`](../workshop/workshop-mental-safety.md) | Slide 2 (career) | Lenny senior/mid/junior split + *"invest in your own agency"* + *"the only universal skill is being able to roll with the changes"* | The whole slide |
| [`workshop-mental-safety.md`](../workshop/workshop-mental-safety.md) | Slide 2 closing line | Simon on losing his edge: *"anyone can vibe-code a convincing UI"* | Honest peer admission, lands well |
| [`workshop-mental-safety.md`](../workshop/workshop-mental-safety.md) | Slide 2 (accountability gap) | Heavybit: *"Claude Code does not have a professional reputation! It can't take accountability for what it's done."* + **normalization of deviance** coinage | Honest framing of the new psychological trap; "normalization of deviance" is a crisp memorable term |
| [`workshop-mental-safety.md`](../workshop/workshop-mental-safety.md) | Slide 1 / new intro beat | Heavybit: Simon's disturbing realization that vibe coding and AE have *"started to blur for me already"* | Opens the safety section with the highest-credibility admission: even Simon is affected |
| [`workshop-practices.md`](../workshop/workshop-practices.md) | Slide 2 (review fatigue) | Heavybit: *"I'm starting to treat the agents in the same way [as another team's semi-black box]. And it still feels uncomfortable."* | Adds the team/trust analogy for WHY review pressure decreases over time |
| [`workshop-practices.md`](../workshop/workshop-practices.md) | Slide 6 (verification) | Heavybit: *"I want somebody to have used the thing."* — can't distinguish quality by commits or test count anymore | Sharpens the "verify with use, not just tests" principle |
| [`workshop-benchmarks.md`](../workshop/workshop-benchmarks.md) | Any slide on evaluating AI output quality | Heavybit: vibe-coded repo now looks identical to a carefully built one — *"Maybe it is as good as them. I don't know. I can't tell from looking at it."* | Motivates why traditional code-quality signals aren't sufficient |
| [`workshop-resources.md`](../workshop/workshop-resources.md) | Section A (practitioners) | Simon's [agentic-engineering-patterns guide](https://simonwillison.net/guides/agentic-engineering-patterns/) as a canonical reading list, not just the tag | Better than just the tag URL |
| [`vibecode-keynote-v3.md`](../keynote/vibecode-keynote-v3.md) | "Cost of trying" thread | "no longer afraid of starting projects" + 150 HTML tools | Already there, reinforce |
| [`vibecode-keynote-v3.md`](../keynote/vibecode-keynote-v3.md) | "What changes?" slide | Heavybit: Jenny Wen (Anthropic design lead) — extensive design review processes were built around expensive engineering; if building is cheap, design can afford to be riskier | First-principles argument for how SDLC itself needs to change |
| [`vibecode-keynote-v3.md`](../keynote/vibecode-keynote-v3.md) | Vibe coding vs. AE distinction slide | Heavybit: Matthew Yglesias quote — *"I want professionally managed software companies to use AI coding assistance to make more/better/cheaper software products that they sell to me for money."* | Best one-liner for "where vibe coding belongs vs. professional engineering" |
| [`vibecode-keynote-v3.md`](../keynote/vibecode-keynote-v3.md) | Closing | "Building is cheap; knowing whether what you built is correct is the expensive part" | Single best closing line for the keynote |
| [`workshop-cost-tokens.md`](../workshop/workshop-cost-tokens.md) | New slide or callout | James Shore maintenance-cost math: 2x output at constant maintenance = 2x future debt. "Permanent indenture." | Corrects over-optimism with concrete economic framing |
| [`workshop-intro.md`](../workshop/workshop-intro.md) | New slide | Agent-enabled reversibility: Bun Zig→Rust in 1–2 weeks; tech choices no longer lock-in | Surprising and positive — reframes architectural risk |
| [`workshop-practices.md`](../workshop/workshop-practices.md) | Organizational patterns | Shopify Lehrwerkstatt: public agent channels → whole-org learning without curriculum | Concrete named pattern an audience can steal immediately |
| [`workshop-resources.md`](../workshop/workshop-resources.md) | Canonical reading | Simon's [Agentic Engineering Patterns guide](https://simonwillison.net/guides/agentic-engineering-patterns/) | The single best reference to hand attendees — structured, maintained, free |

---

## Verified quote bank

All quotes below are sourced. Any `[VERIFY]` tags mark wording I'd double-check against the original audio/post before quoting on a slide.

```
=== ON THE INFLECTION POINT (Nov 2025) ===

Simon Willison, Lenny's Podcast (Apr 2 2026):
"Almost all of the time it does what you told it to do."
  — context: Opus 4.5 / GPT-5.1 crossing the reliability threshold
  — https://www.lennysnewsletter.com/p/an-ai-state-of-the-union
  — https://simonwillison.net/2026/Apr/2/lennys-podcast/

Simon Willison (same):
"I can churn out 10,000 lines of code in a day. And most of it works."

Simon Willison (same):
"95% of the code that I produce, I didn't type myself."

Simon Willison, "An AI agent coding skeptic tries it" (Feb 27 2026):
"Opus 4.6 / Codex 5.3 are an order of magnitude better than coding LLMs
 months before."
  — https://simonwillison.net/2026/Feb/27/ai-agent-coding-in-excessive-detail/

=== ON THE COST OF TRYING ===

Simon Willison, often-cited (origin: 2024 retrospective; rephrased many times):
"I'm no longer afraid of starting projects."
  — already in workshop-exercise-1.md Slide 1

Simon Willison, "Useful patterns for building HTML tools" (Dec 10 2025):
"A single file: inline JavaScript and CSS in a single HTML file means the
 least hassle in hosting or distributing them, and crucially means you can
 copy and paste them out of an LLM response."
  — https://simonwillison.net/2025/Dec/10/html-tools/

Simon Willison (same):
"Over 150 HTML tools in approximately two years, almost all of them
 written by LLMs."

Simon Willison, on quality investment (Mar 10 2026):
"The cost of these code improvements has dropped so low that we can afford
 a zero tolerance attitude to minor code smells and inconveniences."
  — https://simonwillison.net/guides/agentic-engineering-patterns/better-code/

=== ON HARNESSES & DEFINITION ===

Simon Willison, "How coding agents work" (Mar 16 2026):
"A coding agent is a piece of software that acts as a harness for an LLM,
 extending that LLM with additional capabilities that are powered by
 invisible prompts and implemented as callable tools."
  — https://simonwillison.net/guides/agentic-engineering-patterns/how-coding-agents-work/

<!-- VERIFIED-EDIT: verbatim from primary source -->
Simon Willison (same — verbatim):
"A simple tool loop can be achieved with a few dozen lines of code on
 top of an existing LLM API."
 — simonwillison.net/guides/agentic-engineering-patterns/how-coding-agents-work/

Simon Willison, "What is agentic engineering?" (Mar 15 2026):
"Agentic engineering is the practice of developing software with the
 assistance of coding agents."
  — https://simonwillison.net/guides/agentic-engineering-patterns/what-is-agentic-engineering/

Simon Willison (same):
"Code execution is the defining capability that makes agentic engineering
 possible."

Simon Willison (same):
"Agents run tools in a loop to achieve a goal."

Simon Willison (same):
"The craft has always been figuring out *what* code to write."

=== ON SKILLS, MCP, TOOLS ===

Simon Willison, "Claude Skills are awesome, maybe a bigger deal than MCP"
(Oct 16 2025):
"A skill is a Markdown file telling the model how to do something,
 optionally accompanied by extra documents and pre-written scripts."
  — https://simonwillison.net/2025/Oct/16/claude-skills/

Simon Willison (same):
"Each skill only takes up a few dozen extra tokens, with the full details
 only loaded in should the user request a task that the skill can help solve."

Simon Willison (same):
"GitHub's official MCP on its own famously consumes tens of thousands of
 tokens of context, and once you've added a few more to that there's
 precious little space left for the LLM to actually do useful work."

Simon Willison, "too many model context protocol servers..." (Aug 22 2025):
"The GitHub MCP defines 93 additional tools and swallows another 55,000 of
 those valuable tokens."
  — https://simonwillison.net/2025/Aug/22/too-many-mcps/

Simon Willison (same):
"LLMs are known to perform worse the more irrelevant information has
 been stuffed into their prompts."

<!-- VERIFIED-EDIT: verbatim from primary source -->
Simon Willison (verbatim):
"I don't use MCP at all any more when working with coding agents — I
 find CLI utilities and libraries like Playwright Python to be a more
 effective way of achieving the same goals."
 — simonwillison.net/2025/Nov/4/code-execution-with-mcp/

=== ON SECURITY ===

Simon Willison, "The lethal trifecta for AI agents" (Jun 16 2025):
The three components an agent must NOT combine:
  1. "Access to your private data"
  2. "Exposure to untrusted content"
  3. "The ability to externally communicate" in ways that could exfiltrate data
  — https://simonwillison.net/2025/Jun/16/the-lethal-trifecta/

Simon Willison (same):
"LLMs are unable to reliably distinguish the importance of instructions
 based on where they came from."

Simon Willison (same):
"Once an LLM agent has ingested untrusted input, it must be constrained
 so that it is impossible for that input to trigger any consequential actions."

=== ON THE SENIOR / JUNIOR / MID-CAREER QUESTION ===
(These are the highest-priority quotes for workshop-mental-safety.md Slide 2.)

Simon Willison, Lenny's Podcast (Apr 2 2026):
"This stuff is really good for experienced engineers — it amplifies their
 skills. It's really good for new engineers because it solves so many of
 those onboarding problems. The problem is the people in the middle."
  — https://www.lennysnewsletter.com/p/an-ai-state-of-the-union

Simon Willison (same), advice to mid-career engineers:
"Lean into this stuff and figure out: how do I help this make me better?"

Simon Willison (same):
"The only universal skill is being able to roll with the changes."

Simon Willison (same):
"Invest in your own agency."

<!-- VERIFIED-EDIT: the often-cited "anyone can vibe-code a convincing UI" line is a third-party paraphrase. Primary-source wording from his Lenny write-up: -->
Simon Willison, on the commoditised UI:
"A UI prototype is free now. ChatGPT and Claude will just build you a
 very convincing UI for anything that you describe."
 — simonwillison.net/2026/Apr/2/lennys-podcast/

=== ON THE MENTAL COST ===

Simon Willison, Lenny's Podcast (Apr 2 2026):
"By like 11 AM, I am wiped out for the day."
  — context: managing four parallel coding agents, with 25 yrs experience

Simon Willison (same):
"I've got 25 years of experience in how long it takes to build something.
 And that's all completely gone."

Mario Zechner, quoted by Simon, "Thoughts on slowing the fuck down"
(Mar 25 2026):
"You have removed yourself from the loop. ... agents are merchants of
 complexity."
  — https://simonwillison.net/2026/Mar/25/thoughts-on-slowing-the-fuck-down/

Mario Zechner (same):
"We have basically given up all discipline and agency for a sort of
 addiction, where your highest goal is to produce the largest amount of
 code in the shortest amount of time."

Mario Zechner (same):
"A human cannot shit out 20,000 lines of code in a few hours.
 Without human oversight, tiny little harmless booboos suddenly compound
 at an unsustainable rate."

Simon's response (same post):
<!-- VERIFIED-EDIT: verbatim from primary source -->
Simon agrees Zechner is "exactly right" that agent speed creates real
problems, but pushes back on the hand-writing prescription. Verbatim:
"we need the discipline to find a new balance of speed v.s. mental
 thoroughness now that typing out the code is no longer anywhere close
 to being the bottleneck on writing software."
 — simonwillison.net/2026/Mar/25/thoughts-on-slowing-the-fuck-down/

=== ON BUILD-VS-VERIFY (the new bottleneck) ===

<!-- VERIFIED-EDIT: this is a third-party synthesis of Simon's framing, not a primary-source utterance. Use it as a paraphrase OR substitute the verbatim line below. -->
Simon Willison, paraphrasing the spirit of his Lenny's Newsletter
appearance (Apr 2 2026) — not a verbatim utterance:
"Building is now cheap. Knowing whether what you built is correct is the
 expensive part."

Verbatim substitute carrying the same idea:
"Never assume that code generated by an LLM works until that code has
 been executed."
  — agentic-manual-testing guide, Mar 6 2026 (full URL below)

Simon Willison, "Agentic manual testing" (Mar 6 2026):
"Never assume that code generated by an LLM works until that code has
 been executed."
  — https://simonwillison.net/guides/agentic-engineering-patterns/agentic-manual-testing/

Simon Willison, anti-patterns guide (Mar 4 2026):
"Don't file pull requests with code you haven't reviewed yourself."
  — https://simonwillison.net/guides/agentic-engineering-patterns/anti-patterns/

Simon Willison, "AI should help produce better code" (Mar 10 2026):
"Shipping worse code with agents is a *choice*. We can choose to ship
 code that is better instead."
  — https://simonwillison.net/guides/agentic-engineering-patterns/better-code/

=== ON HONEST FAILURE MODES ===

Simon Willison, "Eight years of wanting, three months of building"
(Apr 5 2026):
"AI made me procrastinate on key design decisions... deferring decisions
 corroded my ability to think clearly."
  — https://simonwillison.net/2026/Apr/5/building-with-ai/

Simon Willison (same):
"AI struggled if the task had no objectively checkable answer.
 Implementation has a right answer... Design doesn't."

Simon Willison (same):
"When I was working on something where I didn't even know what I wanted,
 AI was somewhere between unhelpful and harmful."

Simon Willison, on Auto Mode (Mar 24 2026):
"I remain unconvinced by prompt injection protections that rely on AI."
  — https://simonwillison.net/2026/Mar/24/auto-mode-for-claude-code/

=== ON THE AUTORESEARCH PATTERN ===

Simon Willison, on Shopify Liquid optimization (Mar 13 2026):
"Having a robust test suite — in this case 974 unit tests — is a *massive
 unlock* for working with coding agents."
  — https://simonwillison.net/2026/Mar/13/liquid/

Simon Willison (same):
"The autoresearch pattern — where an agent brainstorms a multitude of
 potential improvements and then experiments with them one at a time —
 is really effective."

Simon Willison (same):
"CEOs can code again! Coding agents make it feasible for people in
 high-interruption roles to productively work with code again."

=== ON SUBAGENTS ===

Simon Willison, "Subagents" (Mar 17 2026):
"Subagents provide a simple but effective way to handle larger tasks
 without burning through too much of the coding agent's valuable
 top-level context."
  — https://simonwillison.net/guides/agentic-engineering-patterns/subagents/

Simon Willison (same):
"Your root coding agent is perfectly capable of debugging or reviewing
 its own output provided it has the tokens to spare."

Simon Willison (same — example prompt):
"Use subagents to find and update all of the templates that are
 affected by this change."

=== ON HOARDING & SPEC-DRIVEN ===

Simon Willison, "Hoard things you know how to do" (Feb 26 2026):
"A key asset to develop as a software professional is a deep collection
 of answers to questions like this, accompanied by proof of those answers."
  — https://simonwillison.net/guides/agentic-engineering-patterns/hoard-things-you-know-how-to-do/

Simon Willison (same):
"Coding agents mean we only ever need to figure out a useful trick once.
 If that trick is then documented somewhere with a working code example
 our agents can consult that example."

Simon Willison, scan-for-secrets release (Apr 5 2026):
"README-driven-development: carefully construct the README... then
 dump it into Claude Code."
  — https://simonwillison.net/2026/Apr/5/scan-for-secrets-3/

=== ON VIBE CODING / AE CONVERGENCE (Heavybit High Leverage Ep. 9, May 2026) ===

Simon Willison (Heavybit podcast with Joseph Ruscio, May 2026):
"Weirdly though, those things have started to blur for me already,
 which is quite upsetting."
  — https://simonw.substack.com/p/vibe-coding-and-agentic-engineering

Simon Willison (Heavybit):
"The problem is that as the coding agents get more reliable, I'm not
 reviewing every line of code that they write anymore, even for my
 production level stuff.
 I know full well that if you ask Claude Code to build a JSON API
 endpoint that runs a SQL query and outputs the results as JSON,
 it's just going to do it right."

Simon Willison (Heavybit) — the team/black-box analogy:
"I'm starting to treat the agents in the same way [as another team's
 service]. And it still feels uncomfortable, because human beings are
 accountable for what they do. A team can build a reputation...
 Claude Code does not have a professional reputation! It can't take
 accountability for what it's done. But it's been proving itself
 anyway — time and time again it's churning out straightforward things
 and doing them right in the style that I like."

Simon Willison (Heavybit) — normalization of deviance:
"There's an element of the normalization of deviance here — every time
 a model turns out to have written the right code without me monitoring
 it closely there's a risk that I'll trust it at the wrong moment in
 the future and get burned."

Simon Willison (Heavybit) — the new software quality problem:
"I realized what I value more than the quality of the tests and
 documentation is that I want somebody to have used the thing.
 If you've got a vibe coded thing which you have used every day for
 the past two weeks, that's much more valuable to me than something
 that you've just spat out and hardly even exercised."

Simon Willison (Heavybit) — bottlenecks shifting:
"The entire software development lifecycle was, it turns out, designed
 around the idea that it takes a day to produce a few hundred lines of
 code. And now it doesn't."

Simon Willison (Heavybit) — quoting Jenny Wen, Anthropic design lead:
"She said we have all of these design processes that are based around
 the idea that you need to get the design right — because if you hand it
 off to the engineers and they spend three months building the wrong
 thing, that's catastrophic. [...] But if it doesn't take three months
 to build, maybe the design process can be a whole lot riskier."

Simon Willison (Heavybit) — career / amplifier argument:
"When I look at my conversations with the agents, it's very clear to
 me that this is moon language for the vast majority of human beings.
 [...] these things are amplifiers of existing experience. If you know
 what you're doing, you can run so much faster with them."

Matthew Yglesias (quoted by Simon, Heavybit):
"Five months in, I think I've decided that I don't want to vibecode —
 I want professionally managed software companies to use AI coding
 assistance to make more/better/cheaper software products that they
 sell to me for money."
  — Matthew Yglesias tweet, May 2026 (cited in Heavybit podcast highlights)

=== ON MAINTENANCE COSTS AND REVERSIBILITY (May 2026) ===

Simon Willison amplifying James Shore (May 11 2026):
"Shore's thesis: if AI doubles your code output but maintenance costs stay
 constant, you've doubled your future maintenance burden. The math is
 unforgiving — productivity gains only work economically if maintenance
 costs fall inversely. Shore warns against trading 'a temporary speed boost
 for permanent indenture.'"
  — https://simonwillison.net/2026/May/11/james-shore/

Mitchell Hashimoto (quoted by Simon, May 14 2026):
"Programming languages used to be LOCK IN, and they're increasingly not so."
[Context: Bun rewrote itself from Zig to Rust in ~1–2 weeks using coding agents]
  — https://simonwillison.net/2026/May/14/not-so-locked-in/

=== ON THE SHOPIFY LEHRWERKSTATT PATTERN (May 2026) ===

Simon Willison on Shopify's River agent (May 11 2026):
"Shopify's coding agent River operates exclusively in public Slack channels
 by design. Tobi Lütke calls it 'Lehrwerkstatt' (teaching workshop): the
 idea that the whole shop floor is the classroom. Osmosis learning through
 visible work 'does not require a curriculum, a training plan, or a manager.
 It just requires everyone's work to be visible.'"
  — https://simonwillison.net/2026/May/11/learning-on-the-shop-floor/

=== FROM THE PATTERNS GUIDE (simonwillison.net/guides/agentic-engineering-patterns/) ===

Simon Willison, Agentic Engineering Patterns guide, anti-patterns:
"Don't file pull requests with code you haven't reviewed yourself.
 If you put code up for review you need to be confident that it's
 ready for other people to spend their time on it."

Simon Willison, Patterns guide definition:
"A coding agent is a piece of software that acts as a harness for an LLM,
 extending that LLM with additional capabilities powered by invisible prompts
 and implemented as callable tools."
[Short form: "LLM + system prompt + tools in a loop"]
```

---

## Numbered surgical edits to apply

These mirror the CE-mining doc's edit list — small, targeted, no rewrites.

### To [`workshop-intro.md`](../workshop/workshop-intro.md)

1. **Slide 3, Phase 3 (Now)**: ADD the **November 2025 inflection-point line** with attribution to Simon's Lenny appearance. Use Simon's exact phrasing about Opus 4.5 / GPT-5.1 ("almost all of the time it does what you told it to do"). Pair with the **"95% I didn't type myself"** and **"10,000 lines a day"** numbers as the lived-reality datapoint.
2. **Slide 4 (why coding is a good domain)**: ADD as the closing one-liner — *"Code execution is the defining capability that makes agentic engineering possible."* — Simon Willison, Mar 15 2026. This is *the* one-line answer to the slide's title question.

### To [`workshop-harnesses.md`](../workshop/workshop-harnesses.md)

3. **Slide 1 (anatomy)**: REPLACE the current opening paragraph with **Simon's harness definition verbatim** (Mar 16 2026). It's tighter and more citable than my paraphrase.
4. **Slide 1 footer / aside**: ADD the *"just a few dozen lines of code"* line as the demystification beat. Pairs perfectly with the live `/show-system-prompt` demo.

### To [`workshop-tool-use.md`](../workshop/workshop-tool-use.md)

5. **Rung 5 (Skills)**: ADD Simon's two key Skills quotes:
   - *"A skill is a Markdown file telling the model how to do something..."*
   - *"Each skill only takes up a few dozen extra tokens..."*
   Cite [Oct 16 2025 post](https://simonwillison.net/2025/Oct/16/claude-skills/). Frame Skills as "Simon's bet — possibly bigger than MCP."
6. **Rung 6 (MCP) — caveats panel**: ADD the **55,000-tokens / 93-tools number** for the GitHub MCP from the Aug 2025 post. This is the single best concrete-number argument for "use sparingly." Plus the line *"LLMs are known to perform worse the more irrelevant information has been stuffed into their prompts."*
7. **Rung 6 (MCP) — security**: ADD a one-line callout to the **lethal trifecta** with a footnote URL. Don't expand — the workshop isn't a security workshop — but plant the flag.

### To [`workshop-cost-tokens.md`](../workshop/workshop-cost-tokens.md)

8. **Slide on caching**: ADD Simon's line *"Agents are designed to avoid modifying earlier conversation content to maximize cached input token efficiency"* as the *why* under the prefix-stability rule. From [How coding agents work, Mar 16 2026](https://simonwillison.net/guides/agentic-engineering-patterns/how-coding-agents-work/).
9. **Slide 2 (savings levers)**: ADD a lever called **"Skills over MCP"** with the 55,000-token GitHub MCP example as the concrete win. Currently that number is buried; it deserves its own bullet.

### To [`workshop-practices.md`](../workshop/workshop-practices.md)

10. **Slide 1 (mentoring frame)**: ADD as the *closing* line of the slide: *"Building is now cheap. Knowing whether what you built is correct is the expensive part."* — Simon, Lenny's Apr 2026. Reframes the whole section's purpose. Pair with **"Shipping worse code with agents is a *choice*"** as the opening epigraph.
11. **Slide 2 (challenges)**: ADD Simon's anti-pattern line *"Don't file pull requests with code you haven't reviewed yourself"* under the review-fatigue bullet. Sharper than my current wording, with attribution.
12. **Slide 4 (AGENTS.md)**: ADD the **hoarding** quote as the *justification* for AGENTS.md authoring — *"we only ever need to figure out a useful trick once."* Then the line: *"If that trick is then documented somewhere with a working code example our agents can consult that example."* — Feb 26 2026. This is the why under "write your AGENTS.md."
13. **Slide 5 (spec-driven)**: ADD Simon's **README-driven-development** line as a real-world example. From the Apr 5 2026 scan-for-secrets release post. Concrete, sourced, current.
14. **Slide 7 (per-task loop)**: ADD Simon's *"Never assume that code generated by an LLM works until that code has been executed"* as the *why* under the verification step. Mar 6 2026.
15. **NEW aside slide on subagents** (after Slide 7): a 1-slider with Simon's subagent definition + the example prompt *"Use subagents to find and update all of the templates that are affected by this change."* Currently subagents aren't in the deck and they should be — they're the most important *technique* missing.
16. **NEW aside slide on Git** (or absorb into Slide 7): Simon's Git-with-coding-agents prompts. *"Sort out this git mess for me"* / *"Use git bisect to find when this bug was introduced"* / *"Find and recover my code that does..."* These are great copy-paste prompts for attendees.

### To [`workshop-own-experience.md`](../workshop/workshop-own-experience.md)

17. **Slide 5 (autoresearch / batch mode)**: REPLACE my generic framing with Simon's **Shopify Liquid case study** numbers — 53% faster, 61% fewer allocations, 93 commits from ~120 experiments, 974 tests. From Mar 13 2026. This is the single best public example of agent-driven optimisation in the wild and it's *citable*.
18. **Slide 6 (greenfield)**: ADD Simon's "Eight years of wanting" *failure-mode* quote as the *honest* counterweight to my own success stories: *"AI made me procrastinate on key design decisions... deferring decisions corroded my ability to think clearly."* Apr 5 2026. Audiences trust speakers who name their own failure modes; borrowing Simon's named failure mode legitimises the slide.

### To [`workshop-mental-safety.md`](../workshop/workshop-mental-safety.md)

19. **Slide 1 (mental cost)**: ADD as the opening peer-confession: *"By like 11 AM, I am wiped out for the day."* — Simon, Lenny's Apr 2026, while running four parallel agents. Pairs with the existing Sau Sheong line. Two practitioners independently saying the same thing is much stronger than one.
20. **Slide 1 (mental cost)**: ADD Mario Zechner's *"agents are merchants of complexity"* and *"merchants of complexity"* line, via Simon's Mar 25 2026 post. Strongest single-line warning in the corpus. Cite Simon's "exactly right" endorsement.
21. **Slide 2 (career — RECONSTRUCT around Simon's trichotomy)**: REPLACE my current senior/mid/junior framing with **Simon's exact wording** from Lenny's Apr 2 2026: *"It amplifies experienced engineers. It solves onboarding for new engineers. The problem is the people in the middle."* Then his three pieces of advice as bullets:
    - For seniors: lean in, more ambitious projects
    - For juniors: lean in, faster onboarding is real (cite Cloudflare/Shopify hiring 1,000 interns each — from the same podcast)
    - For mid-career: *"Lean into this stuff and figure out: how do I help this make me better?"* + *"Invest in your own agency."*
    Close with: *"The only universal skill is being able to roll with the changes."* This is now a coherent, sourced, named slide.
22. **Slide 2 closing**: ADD Simon's *"anyone can vibe-code a convincing UI"* admission about his own commoditised edge — peer evidence that even the people who *built* the wave are losing some of their pre-AI advantages. Use [VERIFY] tag pending exact wording check.

### To [`workshop-resources.md`](../workshop/workshop-resources.md)

23. ADD **Simon's `agentic-engineering-patterns` guide hub** as the canonical reading list — [simonwillison.net/guides/agentic-engineering-patterns/](https://simonwillison.net/guides/agentic-engineering-patterns/). It's the most curated index Simon has of his own thinking on the topic. List the 6–8 best entries: how-coding-agents-work, what-is-agentic-engineering, anti-patterns, better-code, hoard-things, subagents, agentic-manual-testing, using-git-with-coding-agents.
24. ADD the **lethal-trifecta** post under a "security" subhead — every workshop attendee should read it once.
25. ADD the **Lenny's podcast episode** under a "watch/listen" subhead, with the exact title *"An AI State of the Union: We've passed the inflection point, dark factories are coming, and automation timelines"* — most concise current overview from a credible practitioner.

### To [`vibecode-keynote-v3.md`](../keynote/vibecode-keynote-v3.md)

26. **Add as a closing line** (somewhere in the final 2 slides): *"Building is now cheap. Knowing whether what you built is correct is the expensive part."* — Simon Willison, Lenny's Newsletter, Apr 2 2026. This is the single best *keynote* closing line — reframes the whole talk's purpose into one sentence.
27. **In the "cost of trying" thread**: REINFORCE with the *"over 150 HTML tools, almost all written by LLMs"* concrete number from Dec 2025. Already cited but worth tightening — the *number* is the rhetorical hook.

---

## Bigger structural options

### Option A — Add a "named patterns" mini-section to practices

Simon has *named* a handful of techniques that don't live anywhere in the current workshop:

- **README-driven development** — write the README first, dump into the agent
- **Hoarding** — your personal corpus of working examples is the agent's best context
- **Autoresearch** — agent brainstorms N improvements, runs them as parallel experiments
- **Subagents** — fresh-context delegates for exploration, parallel edits, review
- **Vibe-porting** — using a test suite as the spec to port between languages (his JSONata→Go example: 7 hours, $400, validated by tests)

These are real, concrete, named, sourced. Could be a **single slide of "named patterns from the field"** in [`workshop-practices.md`](../workshop/workshop-practices.md) between Slide 5 (spec-driven) and Slide 6 (review). 60–90 seconds, one bullet each, links in handout.

**Lean**: yes — these are the *vocabulary* of the practitioner community. Naming them makes the workshop more credible *and* gives attendees keywords to search for after.

### Option B — A 2-min "Simon's setup" cameo in [`workshop-own-experience.md`](../workshop/workshop-own-experience.md)

A whole sub-mode of "what does a heavy practitioner's daily setup look like?" featuring:
- Claude Code + Claude Code for web (cloud)
- 11+ idle/long-running sessions
- Built on his iPhone while camping
- 150+ single-file HTML tools at tools.simonwillison.net
- His TIL blog as living context corpus
- llm CLI + Datasette as the ambient toolbox

**Lean**: skip as a dedicated slide; weave into Slide 1 (research) as a "look at what one prolific person does" tease. Save the dedicated cameo for the keynote.

### Option C — A keynote callback section: "What two practitioners independently said in March 2026"

Simon, Mario Zechner, Sau Sheong, Steve Yegge — independently, in the same quarter — all said versions of "we are not ready" / "merchants of complexity" / "wiped out by 11 AM." That convergence is itself a slide. **Lean**: keynote-only, as a counterweight slide right before the closing call to action. Workshop has [`workshop-mental-safety.md`](../workshop/workshop-mental-safety.md) for this.

---

## Open questions for me

- [ ] [VERIFY] Simon's exact phrasing of "anyone can vibe-code a convincing UI" — listen to the Lenny clip directly before quoting on a slide.
- [ ] [VERIFY] Simon's exact wording of "Building is now cheap. Knowing whether what you built is correct is the expensive part." — paraphrase from a summary; the *idea* is unambiguous, but exact wording for a slide quote needs the source.
- [ ] [VERIFY] Simon's exact wording on dropping MCP for CLI utilities — paraphrase from a search summary; would land harder with the original phrasing.
- [ ] Should I write the new subagents slide for [`workshop-practices.md`](../workshop/workshop-practices.md) in the same session as applying these edits? Lean: yes — material is fresh.
- [ ] Use Option A "named patterns" as a single slide, or distribute the named-pattern citations into the existing slides? Lean: single slide. Naming things together is more memorable than naming each one separately.
- [ ] Apply edits 1-27 in one pass after user review, or in two passes (intro+harnesses first, practices+safety second)? Lean: one pass — they're all surgical.
- [ ] **Heavybit** — "normalization of deviance" concept: add as a named term to [`workshop-mental-safety.md`](../workshop/workshop-mental-safety.md) Slide 2, or weave into the existing bullet about review fatigue? Lean: name it explicitly — "normalization of deviance" is a term the audience will recognize and it'll stick.
- [ ] **Heavybit** — the Jenny Wen / design-process insight deserves a slide beat in the keynote's "so what changes" section. Does it fit, or does it open a thread that can't be closed in 30 min? Decide before drafting.
- [ ] **Heavybit** — Matthew Yglesias quote: does the audience know who he is? He's a US political commentator, might not be universal. Alternative: just attribute as "a writer" or strip attribution entirely and let the line stand alone.
- [ ] **Heavybit** — the convergence admission ("blur for me already") is the most honest thing Simon has said publicly. Does it go in the keynote opening (to set stakes) or in workshop-mental-safety (as peer evidence)? Could work in both — decide where it lands harder for each audience.
