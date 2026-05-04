# Workshop — Exercise 1: Build the Tool You Wished Existed

**Block**: Hands-on Exercise 1
**Duration**: 30 min hard cap (5 min frame · 22 min build · 3 min rapid show-and-tell)
**Position**: After the intro section, before the deep dive
**Goal**: experience the modern agentic loop on a tiny task. Feel the *cost-of-trying* collapse Simon Willison talks about. Ship something working before lunch.

---

## Slide 1 — The frame

Open with the Simon quote that motivated the keynote in the first place:

> "I'm no longer afraid of starting projects."
> — Simon Willison

Why this matters for what we're about to do:

- The thing that used to take you a Saturday now takes you the **30 minutes** we're about to spend
- It doesn't have to be impressive, public, or maintainable — it has to **exist** and **work for you**
- Unix philosophy: **one tool, one job, done well**
- Simon's practical demonstration: **150+ single-file HTML tools**, almost all LLM-generated, all useful to him personally — [tools.simonwillison.net](https://tools.simonwillison.net/)
- His Dec 2025 writeup: [*Useful patterns for building HTML tools*](https://simonwillison.net/2025/Dec/10/html-tools/) — single file, CDN deps, no React, localStorage for state, Pyodide/WASM if you need real compute

> "Make the tool you wish existed." — the rallying cry

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

## Slide 3 — How to do it well in 30 minutes

A condensed version of the per-task loop from the practices section, time-boxed to fit:

```
0:00–0:02   Decide. One sentence: "I want a tool that ___."
0:02–0:05   Open agent. Plan mode. State the goal + constraints.
            Ask the agent to ask you any clarifying questions.
            Resolve them now.
0:05–0:08   Confirm the plan. ≤8 steps. Real symbols/APIs only.
0:08–0:25   Implement. Let the agent drive. Run it. Fix what's broken.
            One pass of "this isn't quite right" is fine.
            More than two? You're rabbit-holing — narrow the scope.
0:25–0:28   Use it. For real. The thing you wanted to do, do it.
            Note one improvement you'd make if you had another hour.
0:28–0:30   Save it somewhere you'll find it. Be ready to show.
```

### Tactical tips (worth saying out loud)

- **HTML tool path**: ask the agent to write a *single self-contained file* with no build step. CDN imports are fine. localStorage for persistence. No npm.
- **Skill path**: a skill is a Markdown file with frontmatter and a clear procedure. Ask the agent to write the skill, then *use it on a real input* before declaring done.
- **CLI path**: pick a language you have *already installed and authenticated*. Not the time to fight `cargo install`.
- **Use `/clear` if you wander.** It's free.
- **Do not start in your work repo.** Fresh folder. No AGENTS.md collisions.

### Escape hatches (if you get stuck)

- **Stuck on the idea?** Pick the *most boring* of the suggestions above. The point is the experience, not the artifact.
- **Stuck mid-build?** Ralph: `/clear`, restate the goal, paste the failing piece, restart.
- **Agent making it too fancy?** Tell it: "Strip it down. Single file. No frameworks. Smallest thing that works."
- **No good ideas at all?** Build a tool that helps you think of small tools. Yes, really.

---

## Show-and-tell (3 min at the end)

Round-robin, 20 seconds each:
- What did you build?
- Did the agent surprise you (good or bad)?
- One thing you learned

If the room is shy, ask **three volunteers** instead — quality over completeness. We have a 60-min exercise later for the deeper version.

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

## Open questions for me to decide before tomorrow

- [ ] Pre-pick **3 starter ideas** I personally know are achievable in 25 min, in case the room freezes. **Suggest**: regex tester w/ explanation, JSON-to-Cypher converter (Neo4j-flavoured), markdown TOC generator.
- [ ] Have one of *Simon's* tools open in a browser as the room arrives, as ambient inspiration.
- [ ] Decide hard-stop policy: do I cut people off at 25 min for show-and-tell, or let it slide? **Lean: hard stop. The point is shipping under constraint.**
- [ ] Should I build one *live* in front of the room as a 5-min preamble before they start? Risky if it fails on stage; effective if it works. **Lean: only if I've already built it once and know it works in <4 min.**
- [ ] Skill examples — pre-write 1–2 minimal skill examples to show as "this is what a skill looks like" if anyone asks.
