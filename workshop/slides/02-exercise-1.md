---
output: 02-exercise-1.pptx
---

::: slide divider
headline: Exercise 1 · 30 minutes
subhead: Build the tool you wished existed
notes: |
  Open the exercise. The room just saw the WikiLinks demo, so they have
  the model in their head. Now they do the same — on their own idea.

  Reset the energy: "Laptops out. The next 30 minutes are yours.
  I'll walk the room while you build."
:::

::: slide quote
quote: |
  “It’s not about getting work done faster.
  It’s about being able to ship projects
  I wouldn’t have been able to justify spending time on.”

  — Simon Willison, Mar 2025
notes: |
  Same quote as the intro — back-reference is intentional. Anchors them
  on WHY they're doing this exercise.

  One sentence to add: "You saw what one prompt does. Now do the thing
  YOU haven't been able to justify spending time on. Pick small.
  This is a 30-minute exercise, not a 30-day one."

  Transition: "Three rules, then you pick what to build."
:::

::: slide three_col_text
eyebrow: VIBE CODING DONE WELL
title: This exercise has three rules
heading1: Personal use only
heading2: One task
heading3: Single artifact
body1: No tests for edge cases you'll never hit. No README. Works for you.
body2: One feature. If you find yourself adding a second, that's a v2.
body3: One HTML file, OR one skill, OR one CLI script. Not a monorepo.
notes: |
  These are the constraints that make 30 minutes feasible.

  Why each one matters:
  - PERSONAL USE: kills the "what about accessibility / dark mode / i18n"
    instinct. You're the only user. If it works for you, it ships.
  - ONE TASK: Unix philosophy. The narrower the scope, the better the
    prompt, the faster it builds, the more usable the result.
  - SINGLE ARTIFACT: no monorepo, no build step, no scaffolding. The
    moment you reach for npm or cargo init, you've left the exercise.

  Two more constraints worth saying aloud:
  - GREENFIELD — fresh folder, not your work repo, no AGENTS.md collisions
  - BOUNDED SCOPE — if your prompt makes the agent want to ask 3 clarifying
    questions, your scope is too vague. Tighten it.

  Transition: "Pick something. Don't agonize. Six categories on the next slide."
:::

::: slide three_col_icons
eyebrow: PICK ONE — DON’T AGONIZE
title: What to build
label1: Format converter
label2: Personal data viewer
label3: Decision aid
body1: A thing you do weekly. CSV → JSON, time zones, regex tester, units.
body2: Drop in a file, see something useful. Strava, screenshots, markdown folder.
body3: Checklist, scorer, sliders for "should I do X?"
notes: |
  Three categories on screen, but six exist. The other three:

  - CONTENT GENERATOR — name generator, password generator, ASCII art,
    diagram scaffolder. Anything where "give me ten of X" is the use case.
  - RESEARCH / LOOKUP TOOL — fetch + format from an API you actually use.
    OpenAlex, GitHub, Wikipedia, your company's internal API.
  - A SKILL — captures something you know how to do well that the agent
    doesn't do well by default. "Review my Cypher for performance",
    "draft a release note from this commit range", "audit this AGENTS.md".

  If the room freezes on the idea step, name three I personally know are
  achievable in 25 minutes:
  - Regex tester with explanations
  - JSON-to-Cypher converter
  - Markdown TOC generator

  None of these need to be impressive. The point is the experience.

  Transition: "Now — the prompt. Five things every strong one-shot prompt names."
:::

::: slide ordered_list_3_staggered
title: What every strong prompt names
items:
  - heading: Tech stack
    subline: "“single HTML file, vanilla JS, no build step”"
  - heading: Inputs and outputs
    subline: "“text area takes JSON, button copies output”"
  - heading: One named constraint
    subline: "“in memory, no auth, no dark mode”"
notes: |
  Layout shows 3 — say all 5 verbally. The other two:

  4. ALGORITHM OR RULE — "parse with X, group by Y, sort descending."
     The specific instruction that pre-empts a clarifying question.

  5. WHAT NOT TO ADD — "no settings page, no dark mode, no auth."
     This is the most under-used. The agent will fill in blanks. Fill
     them yourself, or it will.

  Reference back to WikiLinks: the prompt I demoed nailed all five.
  - Tech: "no react, ts, just base JS, d3"
  - I/O: "single input field for the wikipedia page URL"
  - Algorithm: "first 5 links, then first 5 of those, max 25 nodes"
  - Storage: "in memory"
  - Don't add: "light mode only" (no dark mode), no settings, no save

  If their prompt hits all five, the model has nothing to ask back.
  That's the threshold for one-shot success.

  Transition: "Twenty-two minutes. Here's the rhythm."
:::

::: slide hero_text
eyebrow: 22 MINUTES, ONE PROMPT, ONE TOOL
title: The rhythm
headline: One prompt → run → at most two fixes → use it
body: |
  No plan mode. No task breakdown.
  If you're on follow-up #3, your prompt was too vague — restart.
notes: |
  This is the methodology slide. Walk it crisply:

  0:00–0:05  Decide your tool. Write the prompt. Be specific (the five
             things from the previous slide).

  0:05–0:20  Run it. If it works, USE IT. If not:
             - One targeted follow-up: "X is broken because Y; fix Y"
             - At most TWO follow-ups before you stop and re-think
             - Follow-up #3? You're rabbit-holing. Open a new chat,
               rewrite the prompt with what you learned, try once more.

  0:20–0:25  Use it for real. The thing you wanted to do — actually
             do it. Catch one bug or missing feature.

  0:25–0:30  Save it somewhere you'll find it. Be ready to show.

  RULE I want them to internalize: "Targeted follow-up beats re-prompt.
  Two-fix limit beats infinite tweaking. Don't expand scope mid-fix."

  The discipline I'm DELIBERATELY excluding:
  - No plan mode (yet)
  - No task breakdown (yet)
  - No AGENTS.md (yet)
  - No commits per subtask (yet)

  All of that comes in the deep dive and Exercise 2. For now: how good
  is one well-formed prompt against current models?

  Transition: "I'll walk the room. Flag me down if you're stuck. Go."
:::

::: slide divider
headline: Show and tell
subhead: 30 seconds each — what you built, did one prompt do it, and what surprised you
notes: |
  Final 3 minutes of the exercise. Don't let it run long.

  Round-robin if room is engaged; 3 volunteers if shy.
  Three questions, 30 seconds each:
  1. What did you build?
  2. Did one prompt do it, or did you need fixes?
  3. One thing the agent did better — or worse — than you expected.

  Listen for the model-progression moment. Someone WILL say
  "that surprised me; I didn't expect it to work first try."
  Name it: "That's the experience. Hold onto it. Now we look
  at what production work needs ON TOP of that capability."

  Bridge into the break:
  "Take 10 minutes. When we come back, we look at how the harness
  ACTUALLY works — and where the cost-of-trying gain comes from.
  Same toolkit, harder problems coming."
:::
