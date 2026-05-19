# Workshop — Exercise 1: Build the Tool You Wished Existed

**Block**: Hands-on Exercise 1
**Duration**: 30 min hard cap (3 min frame · 24 min build · 3 min rapid show-and-tell)
**Position**: After the intro section, before the deep dive
**Goal**: feel what *one strong prompt* gets you in 2026. This is **vibe coding done well** — a single specific prompt, then small fixes if needed. No plan mode, no task breakdown, no AGENTS.md ceremony. That comes in Exercise 2.

**Why this framing**: by the time attendees hit this exercise, they've already seen the WikiLinks demo I run in the *opening of the workshop* (intro block) — so they know what one strong prompt produces in 2026. This is their turn to feel it themselves on their own idea. Hold onto the feeling — when we layer the discipline on top of it in the deep dive, it'll be obvious why we need it for production work and why vibe coding still wins for prototypes.

---

## Slide 1 — The frame

Open with the Simon quote that motivated the talk in the first place:

<!-- SIMON-EDIT (verified): swapped often-cited paraphrase for the verified Mar 2025 wording -->
> *"It's about being able to ship projects that I wouldn't have been able to justify spending time on."*
> — Simon Willison, *[Here's how I use LLMs to help me write code](https://simonwillison.net/2025/Mar/11/using-llms-for-code/)* (Mar 11 2025)

Why this matters for what we're about to do:

- The thing that used to take you a Saturday now takes you the **30 minutes** we're about to spend
- It doesn't have to be impressive, public, or maintainable — it has to **exist** and **work for you**
- Unix philosophy: **one tool, one job, done well**
- Simon's practical demonstration: **150+ single-file HTML tools**, almost all LLM-generated, all useful to him personally — [tools.simonwillison.net](https://tools.simonwillison.net/)
- His Dec 2025 writeup: [*Useful patterns for building HTML tools*](https://simonwillison.net/2025/Dec/10/html-tools/) — single file, CDN deps, no React, localStorage for state, Pyodide/WASM if you need real compute

> "Make the tool you wish existed." — the rallying cry

**This exercise is vibe coding done well.** One specific prompt → one working tool → small fixes if needed. *No plan mode. No task breakdown. No AGENTS.md ceremony.* That's all coming in Exercise 2 — for now, just feel what one strong prompt produces in 2026.

**Why this matters**: the same prompt would have failed three years ago, partially worked 18 months ago, and works first-try today. *That's the model progression you're about to feel.* Hold onto that experience — when we layer the discipline on top in the deep dive, it'll be obvious why we need it for production work and why vibe coding still wins for prototypes.

**Two valid shapes for this exercise:**

1. **A single-file HTML tool** — opens in a browser, works offline, solves one specific itch
2. **A Claude skill / slash-command / AGENTS.md skill** — automates a thing you do repeatedly, ships expertise as instructions instead of code

Why skills count: **shipping expert knowledge is a new product category.** If you've ever explained something to a junior engineer three times, that's a skill waiting to be written down. Skills are durable, copy-pasteable, run on anyone's machine, and don't need a CI/CD pipeline.

---

## Slide 2 — The exercise

**Build something small, greenfield, single-purpose, that solves your own itch.**

### Constraints (these matter — they make it doable in 30 min)

- **Personal use only.** No tests for edge cases you'll never hit. No accessibility audit. No README. Just *works for you*.
- **One task.** If you find yourself adding a second feature, stop — that's a v2.
- **Single artifact.** One HTML file, OR one skill, OR one CLI script. Not a monorepo.
- **Greenfield.** No existing project to integrate into. New folder, fresh start.
- **Bounded scope.** If the agent needs to ask 3 clarifying questions to start, your scope is too vague — narrow it.

### What to build (pick one, don't agonize)

- A **format converter** for a thing you do weekly (CSV → JSON, time zones, units, regex tester)
- A **personal data viewer** — drop in a file, see something useful (your Strava export, a markdown folder, your screenshots)
- A **decision aid** — checklist, scorer, "should I do X?" tool with sliders
- A **content generator** — name generator, password generator, ASCII art, Excalidraw scaffolder
- A **research/lookup tool** — fetch + format from an API you use
- A **skill** that captures something *you* know how to do well that the agent doesn't do well by default
  - Example: "review my Cypher query for performance"
  - Example: "draft a release note from this commit range"
  - Example: "audit this AGENTS.md against best practices"

### What good looks like at the end of 30 min

- It opens / runs
- It does its one job
- *You* would actually use it tomorrow
- Code/skill is in a folder you can find again

### What "good enough" looks like

- It's ugly
- It hardcodes some things
- The error handling is a `try/catch` that prints to console
- It's exactly what you needed and nothing more

---

## Slide 3 — Your turn: 24 minutes

You've already seen what one strong prompt produces — the WikiLinks demo at the start of the workshop. Now do it on your own idea.

Pick one tool from your list (Slide 2). Open your harness. Write **one specific prompt**, with the same shape as the WikiLinks one. Run it. If something's broken or missing, fix it with a follow-up. Repeat until you'd actually use the thing.

Pick one tool from your list (Slide 2). Open your harness. Write **one specific prompt**, with the same shape as my WikiLinks demo. Run it. If something's broken or missing, fix it with a follow-up. Repeat until you'd actually use the thing.

```
0:00–0:02   Decide your tool. One sentence: "I want X that does Y."
0:02–0:05   Write the prompt. Be specific:
              • tech stack (HTML+vanilla JS, or skill format, or Go CLI)
              • named functions / inputs / outputs
              • named constraints (no DB, no auth, in-memory, light mode only)
              • the *one* interaction loop
              • what NOT to add
0:05–0:20   Run it. If it works, use it.
            If it doesn't:
              → one targeted follow-up: "X is broken because Y; fix Y"
              → at most TWO follow-ups before you stop and re-think
              → if you're on follow-up #3, your prompt was too vague
                — open a fresh chat, rewrite the prompt, try once more
0:20–0:25   Use it for real. The thing you wanted to do, actually do it.
            Catch one bug or missing feature.
0:25–0:30   Save it somewhere you'll find it. Be ready to show.
```

### What "specific enough" looks like in your prompt

Five things every strong one-shot prompt names — same shape as my WikiLinks prompt:

1. **Tech stack** — `single HTML file, vanilla JS, no build step` (or equivalent for a skill / CLI)
2. **Inputs / outputs** — `text area takes JSON, button copies output to clipboard`
3. **Algorithm or rule** — `parse with X, group by Y, sort descending`
4. **Storage** — `in memory only` or `localStorage` or `none`
5. **What NOT to add** — `no auth, no dark mode, no settings page`

If your prompt doesn't name all five, the agent will fill in the blanks — and you'll spend follow-ups trimming what you didn't want.

### Tactical tips

- **HTML tool path**: ask for a *single self-contained file* with CDN imports. No npm, no build, no React.
- **Skill path**: ask for a Markdown file with frontmatter + a procedure section. Test it on one real input before declaring done.
- **CLI path**: pick a language you already have installed. Not the time to fight `cargo install` or `pip install`.
- **Do NOT start in your work repo.** Fresh folder. The exercise is one prompt → one folder → one file.
- **Resist the urge to plan.** This exercise is deliberately *not* the agentic-engineering loop. We layer that on in the deep dive. Right now: how good is one well-formed prompt?

### When it doesn't work the first time

This is *expected*. The lesson is in how you respond:

- **Targeted follow-up** beats re-prompt: *"the recenter button doesn't actually re-fetch; fix the click handler"* is better than rewriting the whole prompt.
- **Two-fix limit**: if you're on follow-up #3 you're over-investing. Open a new chat, rewrite the original prompt with what you learned, try once more.
- **Don't expand scope mid-fix**: *"oh and add dark mode"* turns a 5-min fix into a 20-min rabbit hole. Note the missing feature, decide later.
- **The agent making it too fancy?** *"Strip it down. Single file. No frameworks. Smallest thing that works."*

---

## Show-and-tell (3 min at the end)

Round-robin, 20 seconds each:
- What did you build?
- Did one prompt do it, or did you need fixes?
- One thing the agent did better — or worse — than you expected

If the room is shy, ask **three volunteers** — quality over completeness. We have a 60-min exercise later for the disciplined version, where everything you skipped here (plan mode, task breakdown, AGENTS.md) becomes the point.

---

## Pre-flight checklist (in the prereqs email, separate doc)

- Claude Code (or your harness of choice) installed and logged in
- Anthropic API key with credit (or Claude Pro/Max)
- A browser, a terminal, a folder you can write to
- Optional: Python or Node installed if you might go beyond pure HTML

---

## Sources & references

- [Simon Willison — *Useful patterns for building HTML tools* (Dec 10 2025)](https://simonwillison.net/2025/Dec/10/html-tools/)
- [tools.simonwillison.net](https://tools.simonwillison.net/) — 150+ examples to spark ideas
- [simonw/tools on GitHub](https://github.com/simonw/tools) — the source repo
- [tools.simonwillison.net/colophon](https://tools.simonwillison.net/colophon) — every tool with its build transcript; great for showing the *how*
- [Brian Gershon — *Make the Tool You Wish Existed (with Your LLM)*](https://www.briangershon.com/blog/make-tool-you-wish-existed-with-llm)
- Simon's [agentic-engineering tag](https://simonwillison.net/tags/agentic-engineering/)
- [Anthropic — Claude skills docs](https://code.claude.com/docs) (look up skills section)

---

## Decisions locked

- ✅ **No live demo inside this exercise** — the WikiLinks demo runs at the *start of the workshop* (intro block) so the room already has the model-progression experience in their head by the time they hit Ex1.
- ✅ **Single-prompt + small fixes** is the methodology — no plan mode, no task breakdown for this exercise. (That's Ex2.)
- ✅ **Two-fix limit** before re-prompting — surface this rule explicitly.
- ✅ **Hard 25-min cap** before show-and-tell. The point is shipping under constraint.

## Still to do before tomorrow

- [ ] Pre-pick **3 starter ideas** for attendees who freeze: regex tester w/ explanation, JSON-to-Cypher converter (Neo4j-flavoured), markdown TOC generator.
- [ ] Have one of Simon's HTML tools open in a browser tab as ambient inspiration during arrival.
- [ ] Pre-write 1–2 minimal skill examples to show as "this is what a skill looks like" if anyone asks during the build.
- [ ] *(WikiLinks demo prep is in `workshop-intro.md` open questions — not this exercise.)*
