---
output: 01-intro.pptx
---

::: slide title
title: |-
  From Vibe Coding
  to Agentic Engineering
subtitle: |-
  The engineering practices matter more, not less
notes: |
  OPEN — set the room.

  "Welcome. The goal today isn't to convince you AI will write all your code.
  It's to give you the same operating mental model and muscle memory I use,
  so you can decide for yourselves what's real and what's hype."

  Pause. Look around the room — make eye contact with two or three people.
  Some came in skeptical, some excited, some both. Hold space for that.

  Frame the day in one sentence: "We'll do hands-on, then craft, then more hands-on,
  then we'll talk about the harder questions — your career, review fatigue, what's
  actually working in production. Q&A throughout. Interrupt me anytime."

  Transition: "Before any of that — let me read the room."
:::

::: slide agenda_4
title: Hands up — quick read of the room
items:
  - heading: First time
  - heading: This week
  - heading: Shipped it
  - heading: Got burned
notes: |
  60 seconds total. Don't lecture; just see hands. Read each one out loud:

  1. "Who first used an LLM to help with code before mid-2024?"
     — separates the early adopters; usually a third of the room.
  2. "Who used an agentic harness — Claude Code, Codex, Cursor agent, Aider, opencode —
     in the last 7 days?"
     — real signal of who's currently in the loop.
  3. "Who's shipped something to production this year where an agent wrote
     the majority of the code?"
     — the real bar; usually fewer hands than people expect.
  4. "Who's had an agent silently break something — and wished they'd never started?"
     — invites skeptics to speak. Make this safe to admit.

  Q4 is the most important. Don't rush past it. If hands go up, mentally note one
  or two faces — name those experiences explicitly later in the talk.

  Optional follow-up if the room is quiet:
  "What kind of project — quick task, greenfield, OSS, legacy refactor?"

  Skeptics in the room are the workshop's best signal.

  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ⚡ NEXT: LEAVE THE DECK — RUN THE WIKILINKS LIVE DEMO (~3-4 min)
  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  Switch to the agent terminal. Paste the WikiLinks prompt
  (full text + narration cues are in workshop-intro.md "Slide 1.5").
  When the tool works, click around in it for ~30 seconds.

  Bridge back into the deck:
  "That's where we are in 2026. One prompt, ninety seconds, working tool.
   And that's the EASY half of this story. The hard half is what happens
   when you try to do that on production work — which is what the rest
   of the day is about."

  Then advance to the next slide ("Why we're doing this").
:::

::: slide divider
headline: Why we're doing this
subhead: SWE agents are a tool — but with bigger leverage than any tool that came before
notes: |
  This is the "set the stakes" slide. ~3 minutes here.

  Walk the room through the lineage of tools that changed how engineers work:
  - IDEs / refactoring made code malleable — rename without fear.
  - Testing / TDD turned behavior from a wish into a contract.
  - CI/CD made shipping continuous, not ceremonial.
  - Linters / type systems moved errors left, before runtime.
  - SWE agents: intent → working code in hours, not weeks.

  Each required a mindset shift. This one is bigger because the leverage is bigger.

  Three things genuinely new about this tool:
  - The leverage is order-of-magnitude bigger than any prior tool.
  - The failure mode is also new: confidently wrong, plausibly wrong, fast.
  - The mindset shift is not "learn the tool" — it's "learn to delegate, review, steer."

  Why the ROOM should care: "the engineers who treat this seriously now will be
  the ones writing the playbooks the rest of the industry uses next year. Not because
  of FOMO — because nobody else has the experience yet to do it well."

  Transition: "Let me give you the cleanest articulation of what's actually changed.
  From someone you probably already follow."
:::

::: slide quote
quote: |
  “It’s not about getting work done faster.
  It’s about being able to ship projects
  I wouldn’t have been able to justify spending time on.”

  — Simon Willison, Mar 2025
notes: |
  Source: Simon Willison, "Here's how I use LLMs to help me write code", March 11 2025.

  Why this quote and not something flashier: it names the *real* shift.
  The productivity gain isn't "10× more lines of code per hour" — it's the
  collapse of the cost-of-trying threshold. Projects that weren't worth
  starting are now worth starting.

  Worth saying: Simon was already heading there in 2023.
  - Dec 2022: "Learning Rust with ChatGPT, Copilot and Advent of Code"
  - Mar 2023: "AI-enhanced development makes me more ambitious with my projects"
  - Mar 2025: this quote — the mature articulation
  Two-year arc. Not a hot take. Not a 2025 reaction.

  Personal anecdote slot: pick one project of yours that fits this shape — something
  you wouldn't have started 18 months ago. You'll do this experience yourself
  in Exercise 1 in twenty minutes — that's the WikiLinks demo I'll show.

  Transition: "OK — but the *scale* of this shift is genuinely surprising. Numbers."
:::

::: slide stats_grid_6
title: The agent tsunami
stats:
  - num: "275M"
    lbl: Commits / week
  - num: "14×"
    lbl: Annual growth
  - num: "17M+"
    lbl: AI PRs / month
  - num: "80%"
    lbl: New Neon DBs
  - num: "2.1B"
    lbl: Actions min / wk
  - num: "#1"
    lbl: TypeScript on GH
notes: |
  Don't read every number — pick three and let the rest speak.

  Headline framing: GitHub itself reports the platform is "starting to crack"
  under agent-driven traffic. Servers built for human-scale can't handle
  agent-scale. Outages, performance degradation. April 2026 disclosures.

  The three numbers I'd hit verbally:
  - "275 million commits per week — that's pace for 14 billion this year,
     up from 1 billion all of 2025. Fourteen times in one year."
  - "17 million-plus AI-agent PRs in a single month, up from 4 million in
     September 2025. Four-fold in six months."
  - "80% of new Neon databases — created by agents, not humans. Often one
     per task, per branch, per session."

  Source: quasa.io and GitHub's own April 2026 numbers.

  The TypeScript line is a separate signal worth mentioning:
  August 2025, TypeScript overtook Python AND JavaScript as #1 on GitHub
  — biggest language ranking shift in over a decade. Attributed to AI-assisted
  full-stack work.

  The point I want them to take away: this is no longer a tooling wave —
  it's an infrastructure wave that tooling triggered.

  Transition: "How did we get from Copilot autocomplete to this in three years?
  Four phases. Walk with me."
:::

::: slide divider
headline: Three years, four phases
subhead: From "saving keystrokes" to "engineering with non-human teammates"
notes: |
  Storytelling register — this is the spine of the talk.

  Four slides coming up — one per phase. ~30 seconds each on the slide;
  the stories around them fill the rest of the time.

  Don't be exhaustive. The point is the *arc*, not the details.

  Time budget: ~6-8 minutes total across the four phases + the two
  Karpathy quotes that bracket the year 2025.
:::

::: slide hero_text
eyebrow: PHASE 1 · 2021 – 2024
title: Completion
headline: Saving keystrokes
body: |
  Copilot. Tab. Autocomplete on steroids.
  Engineer in the driver's seat at every line.
notes: |
  Copilot technical preview June 2021, GA June 2022.
  Single-file context. Line-to-block completions.
  Shaved 20–30% off boilerplate.

  Mindset: "smarter IntelliSense" — engineer at every line, AI behind the wheel.

  What broke: subtly wrong completions that compiled but were wrong.
  The hallucinated-import meme. Copyright noise. Subtle bugs the type
  checker didn't catch.

  Quote candidate (Simon ~2023, paraphrase):
  "Copilot is the most useful tool I've adopted in a decade.
   It's also the most likely to lie to me. Both things are true."

  Transition: "Then in February 2025, the vocabulary changed."
:::

::: slide hero_text
eyebrow: PHASE 2 · FEB 2025
title: Vibe coding
headline: "Forget the code"
body: |
  Sonnet 3.5. Cursor. ChatGPT desktop.
  Designers, PMs, scientists shipping working tools without engineers.
notes: |
  Trigger: Sonnet 3.5/3.7 strong enough to one-shot small apps.
  Cursor and Copilot Chat in the IDE. ChatGPT desktop with code execution.

  Mindset: "describe, accept, run." Code becomes throwaway, prompt is the artifact.
  Designers, PMs, scientists shipping working tools without engineers.

  What broke: production. Anything needing maintenance, security, multi-user
  concurrency, compliance, integration with existing systems.

  Important nuance for THIS room: vibe coding is genuinely valuable —
  for prototypes, for learning a new framework, for the first 80% of a
  tool you'll throw away in a week. The mistake is treating it as an SDLC.

  Personal calibration: "I still vibe-code small things. I do not vibe-code
  production systems. The skill is knowing which is which."

  Transition: "And the moment that named the phase — Karpathy on X, four months
  before he himself started walking it back."
:::

::: slide quote
quote: |
  “Give in to the vibes,
  embrace exponentials,
  and forget that the code even exists.”

  — Andrej Karpathy, 2 February 2025
notes: |
  This is the tweet. February 2 2025.

  Within a week, "vibe coding" was on every dev podcast and tech-twitter thread.
  Six months later it was on conference t-shirts.

  Two important things to add verbally:

  First — Karpathy himself retired the term for serious work in early 2026.
  When the inventor walks back the vocabulary, that tells you something.

  Second — vibe coding is GENUINELY VALUABLE. Don't dismiss it. For
  prototypes. For learning a new framework. For the first 80% of a tool
  you'll throw away in a week. The mistake is treating it as an SDLC.

  Transition: "Then six months after this tweet — the model gets a shell."
:::

::: slide hero_text
eyebrow: PHASE 3 · SUMMER – FALL 2025
title: Agent harnesses
headline: The model gets a shell
body: |
  Claude Code, Codex, Cursor agent, Aider, opencode.
  Engineer becomes director. Tasks of a week → an afternoon.
notes: |
  Trigger: models cross the threshold where multi-step tool use becomes reliable.

  The wave: Claude Code (Feb 2025 research preview, GA later), OpenAI Codex
  (relaunch May 2025), Cursor agent mode, opencode, Aider, Cline, Roo.

  What changed: the model now has a filesystem, a shell, and a loop.
  It can read, edit, run, test, iterate — without a human between every step.

  Mindset shift: from "AI helps me write code" to "AI does the work, I review and steer."
  Tasks that took a week now take an afternoon.

  What broke: context windows blew up; token budgets surprised everyone;
  agents went off the rails on long tasks; silent test deletion;
  "ralphing" (re-running with reset) became a standard practice.
  *New craft was needed.*

  Transition: "And in June 2025, Karpathy posted the bracketing tweet —
  the one that sets up Phase 4."
:::

::: slide quote
quote: |
  “Context engineering —
  the delicate art and science of filling the context window
  with just the right information for the next step.”

  — Andrej Karpathy, 18 June 2025
notes: |
  Four months after "vibe coding," Karpathy posted this — and it landed
  almost as widely.

  Why both quotes from the same person matter: they're the two sides of
  the year. February said "forget the code." June said "obsess over what's
  *around* the code."

  Together they describe the journey from prototype-mode to production-mode.
  Vibe coding is fine when you don't care what the model knows.
  Context engineering is what you need when you do.

  This is the bridge into Phase 4 — and into the rest of the workshop.
  Almost everything we'll discuss in the deep dive — AGENTS.md, plan mode,
  hooks, the per-task loop, the cost-of-tokens economics — is *context
  engineering* applied to coding.

  Transition: "Which gets us to where we are right now — late 2025 into 2026."
:::

::: slide hero_text
eyebrow: PHASE 4 · LATE 2025 →
title: Agentic engineering
headline: New teammates, old practices
body: |
  Reasoning models. Spec, tests, AGENTS.md, hooks.
  The practices come back as leverage, not ceremony.
notes: |
  Trigger: Sonnet 4.5 / Opus 4.5 (late 2025), Opus 4.6/4.7 (early 2026)
  — reasoning models that plan, self-correct, hold long arcs.

  What changed: agents are reliable enough that the *practices around them*
  start to matter again. Spec-driven development, TDD, code review,
  architecture, AGENTS.md, hooks. The old practices weren't wrong —
  they were just unreachable when each line cost you keystrokes.
  Now they're reachable AND necessary.

  The realization: good design was never for the machine. It was always
  for humans who had to read, maintain, extend. Now those humans include
  AI teammates that learned the craft from human-written code. The same
  practices serve both audiences.

  This is what the rest of the workshop is about. The deep dive is the
  toolkit. Exercise 2 is where you apply it on real work.

  Transition: "OK — quick aside. WHY is this happening to coding faster
  than to any other knowledge domain?"
:::

::: slide three_col_text
eyebrow: WHY CODING
title: Why this domain runs ahead of every other
heading1: Verifiable
heading2: Tight RL loop
heading3: Ancient tools
body1: Compiles. Tests pass. Or they don't. Ground truth, not vibes.
body2: Generate → run → observe → correct. Densest reward signal of any LLM domain.
body3: Bash, grep, git. Stable for 30 years. Well-represented in training data.
notes: |
  Two minutes here. The point is "this isn't an accident — coding is
  uniquely well-suited."

  Walk the three columns:

  VERIFIABLE — code has a ground truth most domains don't. Did it compile?
  Did the test pass? Type check? Unlike prose, the model can check itself.
  This is why coding capability has improved faster than any other domain
  in the last three years.

  TIGHT RL LOOP — generate, run, observe, correct. Cheap dense training
  signal. Reasoning models were post-trained exactly on this loop shape.
  When we give the agent a test to make pass, we're matching its training
  distribution.

  ANCIENT TOOLS — the shell, grep, git, make. Linux is the lingua franca,
  and it doesn't change much. The model has read every man page and every
  Stack Overflow answer about them. This stability is doing work for us.

  Two more if asked or if time:
  - Clear goals — "tests pass, lint clean, feature works." Most domains don't.
  - Training data IS the artifact — code on GitHub *is* what the model produces.

  Bonus framing: TEST TIME > TRAIN TIME. The model's task-time reasoning
  matters more than what's baked in. That's why context engineering pays off,
  and why the practices we'll discuss matter.

  Transition: "If all of this is real, where does it leave us right now?
  One paraphrase to end the intro."
:::

::: slide quote
quote: |
  “Building is now cheap.
  Knowing whether what you built is correct
  is the expensive part.”

  — after Simon Willison, Lenny’s Newsletter (Apr 2026)
notes: |
  PARAPHRASE — read it as Simon's framing rather than verbatim Simon.
  The *idea* is exactly faithful to his repeated argument on Lenny's
  Newsletter podcast (April 2 2026, "An AI State of the Union") and
  across his recent blog posts. Verification could not find a single
  primary-source utterance with this exact wording, so the slide
  uses "— after Simon Willison" to signal paraphrase rather than
  verbatim attribution.

  If anyone asks, the primary-source line that carries the same
  point verbatim is from his agentic-manual-testing guide (Mar 6 2026):
  "Never assume that code generated by an LLM works until that code
  has been executed."

  This is the bridge sentence — slow down here.

  If building is cheap, then VERIFICATION is the engineering.

  Everything we'll teach you the rest of the day is verification infrastructure:
  - AGENTS.md is "what does correct mean here?"
  - The per-task loop is "verify after every step."
  - Hooks are "verify deterministically — don't trust prompts."
  - Tests are "verify when the agent says it's done."
  - Reviews are "verify before it ships."

  This reframe is the keynote sentence in miniature. We'll come back to it.

  Transition: "Enough talking. Let me show you what 'building is cheap' actually
  looks like — one strong prompt, one working tool. Then your turn."
:::

::: slide divider
headline: What we'll do today
subhead: Hands-on. Craft. More hands-on. The harder conversation. Q&A.
notes: |
  Final transition before Exercise 1. ~30 seconds here.

  Walk the agenda quickly:
  - In a moment: 30-min hands-on. I'll demo a one-shot prompt live (WikiLinks
    — Wikipedia → graph viz). Then your turn to do the same on your own idea.
    *No plan mode, no task breakdown — just one strong prompt and small fixes.*
    This is vibe coding done well.
  - Then break.
  - Then 90 minutes of craft — harnesses, tools, cost, benchmarks, practices,
    own demos. The toolkit for production work.
  - Then break.
  - Then 60-min hands-on on YOUR work — bug, feature, MCP server, unfamiliar
    language. Same toolkit, real stakes. Plan mode, AGENTS.md, the per-task loop.
  - Then the harder conversation: review fatigue, role changes, careers.
  - Then Q&A and resources.

  "Pace yourselves. Take the breaks. I'll be walking the room during exercises —
  flag me down."

  Then go straight into Exercise 1.
:::
