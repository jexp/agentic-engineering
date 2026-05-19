---
output: agentic-engineering-workshop.pptx
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

  Pause. Eye contact with two or three people. Some came in skeptical, some
  excited, some both. Hold space for that.

  Frame the day in one sentence: hands-on, then craft, then more hands-on,
  then the harder questions, then Q&A. Interrupt me anytime.

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
  60 seconds total. Don't lecture; just see hands. Read each one out loud.

  Question 4 is the most important. Don't rush past it. If hands go up,
  mentally note one or two faces — name those experiences explicitly later.

  Skeptics in the room are the workshop's best signal.

  Transition: "Now — let me show you what we're actually talking about."
:::

::: slide hero_text
eyebrow: LIVE DEMO · 3 MIN
title: WikiLinks
headline: One prompt. Ninety seconds. Working tool.
body: |
  Wikipedia → graph viz. Single HTML file, vanilla JS, d3.
  Watch the prompt — six things specific. Watch what it produces.
notes: |
  COLD-OPEN MOMENT — earn trust before any abstract argument.

  THE PROMPT (paste verbatim into the agent):

  Create a simple simple html tool "WikiLinks" (no react, ts, just base JS)
  for a wikipedia to graph viz conversion. Single input field for the
  wikipedia page URL (check valid wikipedia page link), just use d3.
  Pull the first 5 links of a wikipedia page to other wikipedia pages,
  follow them, render them as nodes, and pull the next first 5 links
  from those as well, to render as connections and target nodes (so at
  most 25 nodes in total visible). Clicking on a node sets this new
  page as center, and re-runs the fetch/render action for this page
  now, and fetches non-fetched pages. Just store the pages and target
  links in memory. Render page title on node, and keep page link to
  be used in the action. Light mode only.

  WHAT TO NARRATE WHILE IT BUILDS:

  - Specificity over cleverness. Six things this prompt nails:
    tech stack (no React, no TS, base JS, d3), named tool, algorithm
    bounds (5+5, max 25), edge case (URL validation), interaction model
    (click recenters, lazy fetch), UX bounds (light mode only — no
    "should I add dark mode" question).

  - Model-progression line they need to FEEL:
    "Three years ago this prompt would have failed. 18 months ago partial.
     Today it's first-try, ~90 seconds, no follow-ups."

  - If a snag hits (CORS, d3 version), narrate the fix as a small follow-up
    — not a re-prompt. "This is what one fix looks like."

  - When it works, CLICK AROUND. Let the room watch the graph reshape.

  BRIDGE INTO NEXT SLIDE:
  "That's where we are in 2026. One prompt, ninety seconds, working tool.
   And that's the EASY half of this story. The hard half is what happens
   when you try to do that on production work — which is what the rest
   of the day is about."

  PRE-FLIGHT (do tonight): Run the prompt twice on a fresh CC session.
  Backup screenshots in case it fails on stage. Pre-position browser windows.
  Fallback: at 90s if going sideways, switch to backup and narrate.
:::

::: slide two_col_text
eyebrow: WHY WE'RE DOING THIS
title: A new tool — bigger leverage than any before it
heading1: The lineage we know
heading2: What's genuinely new
body1: |
  IDE / refactoring → code became malleable.
  Testing / TDD → behavior became a contract.
  CI/CD → shipping became continuous.
  Linters / type systems → errors moved left.
body2: |
  Leverage order-of-magnitude bigger than any prior tool.
  Failure mode is new: confidently wrong, plausibly wrong, fast.
  Mindset shift is "delegate, review, steer" — not "learn the tool."
  The skill is judgment, not typing.
notes: |
  Set the stakes. ~2-3 minutes here.

  Walk the lineage on the left. Each tool required a mindset shift, and
  each one paid off massively for engineers who adopted it early.
  SWE agents are the same shape — just bigger.

  Three things genuinely new on the right are what makes this not just
  another IDE upgrade.

  WHY THIS ROOM SHOULD CARE: "the engineers who treat this seriously now
  will be the ones writing the playbooks the rest of the industry uses
  next year. Not FOMO — nobody else has the experience yet to do it well."

  Transition: "Cleanest articulation of the shift — from someone you
  probably already follow."
:::

::: slide quote
quote: |
  “It’s not about getting work done faster.
  It’s about being able to ship projects
  I wouldn’t have been able to justify spending time on.”

  — Simon Willison, Mar 2025
notes: |
  Source: Simon Willison, "Here's how I use LLMs to help me write code", Mar 11 2025.

  Why this quote: it names the REAL shift. Not "10× more lines per hour"
  — the collapse of the cost-of-trying threshold. Projects that weren't
  worth starting are now worth starting.

  Two-year arc: Dec 2022 (Rust + ChatGPT), Mar 2023 (AI-enhanced ambitious),
  Mar 2025 (this quote). Not a hot take.

  Personal anecdote slot: pick one project of yours that fits — something
  you wouldn't have started 18 months ago. They just felt this in the
  WikiLinks demo.

  Transition: "But the SCALE of this shift is genuinely surprising. Numbers."
:::

::: slide stats_grid_6
title: The agent tsunami (April 2026)
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

  Headline: GitHub itself reports the platform is "starting to crack"
  under agent traffic. Servers built for human-scale can't handle
  agent-scale. April 2026 disclosures.

  The three to hit verbally:
  - "275 million commits per week — pace for 14 billion this year, up
     from 1 billion in all of 2025. Fourteen times in one year."
  - "17 million-plus AI-agent PRs in a single month, up from 4M in
     September 2025. Four-fold in six months."
  - "80% of new Neon databases — created by agents, often one per task,
     per branch, per session."

  TypeScript line worth mentioning separately: August 2025, TS overtook
  Python AND JavaScript as #1 on GitHub. Biggest ranking shift in over
  a decade. Attributed to AI-assisted full-stack work.

  Takeaway: this is no longer a tooling wave — it's an INFRASTRUCTURE
  WAVE that tooling triggered.

  Transition: "How did we get from Copilot autocomplete to this in three
  years? Four phases."
:::

::: slide divider
headline: Three years, four phases
subhead: From "saving keystrokes" to "engineering with non-human teammates"
notes: |
  Storytelling register — the spine of the talk.
  Four slides, one per phase, ~30s each. Stories around them fill the time.

  Time budget: ~6-8 minutes total across the four phases + the two
  Karpathy quotes that bracket 2025.
:::

::: slide hero_text
eyebrow: PHASE 1 · 2021 – 2024
title: Completion
headline: Saving keystrokes
body: |
  Copilot. Tab. Single-file context. Line-to-block completions.
  Shaved 20–30% off boilerplate. Engineer in the driver's seat at every line.
  What broke: subtly wrong completions that compiled. The hallucinated import.
notes: |
  Copilot technical preview June 2021, GA June 2022.

  Mindset: smarter IntelliSense — engineer at every line, AI behind the wheel.

  What broke beyond the slide: copyright noise, subtle bugs the type
  checker didn't catch, the meme that "Copilot is the most useful tool
  I've adopted in a decade and the most likely to lie to me."

  Transition: "Then in February 2025, the vocabulary changed."
:::

::: slide hero_text
eyebrow: PHASE 2 · FEB 2025
title: Vibe coding
headline: "Forget the code"
body: |
  Sonnet 3.5/3.7. Cursor. ChatGPT desktop with code execution.
  Designers, PMs, scientists shipping working tools without engineers.
  Mindset: "describe, accept, run." Code becomes throwaway, prompt is the artifact.
notes: |
  Trigger: Sonnet 3.5/3.7 strong enough to one-shot small apps. Cursor
  and Copilot Chat in the IDE. ChatGPT desktop with code execution.

  What broke: production. Anything needing maintenance, security, multi-user
  concurrency, compliance, integration with existing systems.

  Important nuance for THIS room: vibe coding is genuinely valuable — for
  prototypes, learning a new framework, the first 80% of a tool you'll
  throw away in a week. The mistake is treating it as an SDLC.

  Personal calibration: "I still vibe-code small things. I do not vibe-code
  production systems. The skill is knowing which is which."

  Transition: "And the moment that named the phase."
:::

::: slide quote
quote: |
  “Give in to the vibes,
  embrace exponentials,
  and forget that the code even exists.”

  — Andrej Karpathy, 2 February 2025
notes: |
  This is the tweet. Within a week, "vibe coding" was on every dev podcast.
  Six months later it was on conference t-shirts.

  Two things to add:
  - Karpathy himself retired the term for serious work in early 2026.
    When the inventor walks back the vocabulary, that tells you something.
  - Vibe coding is GENUINELY VALUABLE. Don't dismiss it. Just don't ship it.

  Transition: "Then six months after this tweet — the model gets a shell."
:::

::: slide hero_text
eyebrow: PHASE 3 · SUMMER – FALL 2025
title: Agent harnesses
headline: The model gets a shell
body: |
  Claude Code, Codex, Cursor agent, Aider, opencode, Cline.
  Filesystem + shell + loop. Read, edit, run, test, iterate without a human in between.
  Engineer becomes director, not typist. Tasks of a week → an afternoon.
notes: |
  Trigger: models cross the threshold where multi-step tool use becomes
  reliable.

  The wave: Claude Code (Feb 2025 preview), OpenAI Codex (relaunch May 2025),
  Cursor agent mode, opencode, Aider, Cline, Roo.

  What changed: the model now has a filesystem, a shell, and a loop. It can
  read, edit, run, test, iterate without a human between every step.

  Mindset shift: from "AI helps me write code" to "AI does the work, I
  review and steer."

  What broke: context windows blew up; agents went off the rails on long
  tasks; silent test deletion; "ralphing" (re-running with reset) became
  standard practice. New craft was needed.

  Transition: "And in June 2025, Karpathy posted the bracketing tweet."
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

  Two sides of the year, same person:
  - February: "forget the code."
  - June: "obsess over what's AROUND the code."

  Vibe coding is fine when you don't care what the model knows. Context
  engineering is what you need when you do.

  This is the bridge into Phase 4 — and into the rest of the workshop.
  AGENTS.md, plan mode, hooks, the per-task loop, the cost-of-tokens
  economics — all of it is *context engineering* applied to coding.

  Transition: "Which gets us to where we are right now — late 2025 into 2026."
:::

::: slide hero_text
eyebrow: PHASE 4 · LATE 2025 →
title: Agentic engineering
headline: New teammates, old practices
body: |
  Reasoning models — Sonnet 4.5, Opus 4.5/4.6/4.7. Plan, self-correct, hold long arcs.
  Spec-driven dev. TDD. AGENTS.md. Hooks. Code review.
  Old practices come back as leverage, not ceremony.
notes: |
  Trigger: Sonnet 4.5 / Opus 4.5 (late 2025), Opus 4.6/4.7 (early 2026)
  — reasoning models that plan, self-correct, hold long arcs.

  What changed: agents are reliable enough that the practices around them
  start to matter again. Spec-driven, TDD, code review, AGENTS.md, hooks.
  The old practices weren't wrong — they were unreachable when each line
  cost you keystrokes. Now they're reachable AND necessary.

  The realization: good design was never for the machine. It was always
  for humans who had to read, maintain, extend. Now those humans include
  AI teammates that learned the craft from human-written code. Same
  practices serve both audiences.

  This is what the rest of the workshop is about. The deep dive is the
  toolkit. Exercise 2 is where you apply it on real work.

  Transition: "Quick aside — WHY is this happening to coding faster than
  to any other knowledge domain?"
:::

::: slide three_col_text
eyebrow: WHY CODING
title: Why this domain runs ahead of every other
heading1: Verifiable
heading2: Tight RL loop
heading3: Ancient tools
body1: |
  Compiles. Tests pass. Or they don't.
  Code has a ground truth most domains lack —
  the model can check itself.
body2: |
  Generate → run → observe → correct.
  Densest reward signal in any LLM domain.
  Reasoning models trained on this exact loop shape.
body3: |
  Bash, grep, git, make. Stable for 30 years.
  Linux is the lingua franca, well-represented in training data.
  This stability is doing work for us.
notes: |
  Two minutes here.

  Two more reasons not on the slide if asked: clear goals (tests pass)
  most domains don't have; training data IS the artifact (code on GitHub
  is what the model produces).

  Bonus framing: TEST TIME > TRAIN TIME. Task-time reasoning matters more
  than baked-in knowledge. That's why context engineering pays off.

  Transition: "If all of this is real, where does it leave us right now?"
:::

::: slide quote
quote: |
  “Building is now cheap.
  Knowing whether what you built is correct
  is the expensive part.”

  — after Simon Willison, Lenny’s Newsletter (Apr 2026)
notes: |
  PARAPHRASE — read it as Simon's framing rather than verbatim Simon.
  The slide uses "— after Simon Willison" to signal paraphrase.

  Verbatim substitute (same idea, primary-sourced):
  "Never assume that code generated by an LLM works until that code
   has been executed." — Agentic Manual Testing guide, Mar 2026.

  This is the BRIDGE sentence. Slow down here.

  If building is cheap, then VERIFICATION is the engineering.
  Everything we'll teach is verification infrastructure:
  - AGENTS.md = "what does correct mean here?"
  - The per-task loop = "verify after every step"
  - Hooks = "verify deterministically — don't trust prompts"
  - Tests = "verify when the agent says it's done"
  - Reviews = "verify before it ships"

  Transition: "Enough talking. Your turn."
:::

::: slide divider
headline: What we'll do today
subhead: Hands-on. Craft. More hands-on. The harder conversation. Q&A.
notes: |
  Walk the agenda quickly:
  - Now: 30-min hands-on. Same shape as WikiLinks but YOUR idea.
    Vibe coding done well — one strong prompt + small fixes.
  - Break.
  - 90 minutes of craft: harnesses, tools, cost, benchmarks, practices, my demos.
  - Break.
  - 60-min hands-on on YOUR work. Plan mode, AGENTS.md, the per-task loop.
  - The harder conversation: review fatigue, role changes, careers.
  - Q&A and resources.

  "Take the breaks. Flag me down during exercises."
:::

::: slide divider
headline: Exercise 1 · 30 minutes
subhead: Build the tool you wished existed
notes: |
  Reset the energy. The room just saw the WikiLinks demo, so they have
  the model in their head. Now they do the same on their own idea.

  "Laptops out. The next 30 minutes are yours. I'll walk the room."
:::

::: slide three_col_text
eyebrow: VIBE CODING DONE WELL
title: Three rules — make 30 minutes feasible
heading1: Personal use only
heading2: One task
heading3: Single artifact
body1: |
  No tests for edge cases you'll never hit.
  No accessibility audit. No README.
  Works for YOU — you're the only user.
body2: |
  One feature, Unix philosophy.
  If you're adding a second, that's a v2.
  Narrower scope = better prompt = faster build.
body3: |
  One HTML file, OR one skill, OR one CLI script.
  No monorepo, no build step, no scaffolding.
  Reach for npm or cargo init = exited the exercise.
notes: |
  Plus two more constraints worth saying:
  - GREENFIELD — fresh folder, not your work repo, no AGENTS.md collisions
  - BOUNDED SCOPE — if your prompt makes the agent want 3 clarifying questions,
    your scope is too vague. Tighten it.

  Transition: "Don't agonize on the idea. Six categories on the next slide."
:::

::: slide four_col_text
eyebrow: SIX CATEGORIES — PICK ONE, DON'T AGONIZE
title: What to build
heading1: Format converter
heading2: Data viewer
heading3: Decision aid
heading4: Content generator
body1: |
  CSV ↔ JSON. Time zones. Units.
  Regex tester. A weekly thing
  you do by hand right now.
body2: |
  Drop in a file → see something useful.
  Strava export. Markdown folder.
  Screenshots, your podcast feed.
body3: |
  Checklist. Scorer. Sliders.
  "Should I do X?" tools with
  constraints and weights.
body4: |
  Names. Passwords. ASCII art.
  Diagram scaffolder. Anything where
  "give me ten of X" is the use case.
notes: |
  Three categories shown on the slide; three more I'll mention verbally:

  - CONTENT GENERATOR — name generator, password generator, ASCII art,
    diagram scaffolder. "Give me ten of X."
  - RESEARCH / LOOKUP — fetch + format from an API you actually use.
    OpenAlex, GitHub, Wikipedia, your company's internal API.
  - A SKILL — captures something you know that the agent doesn't do well.
    "Review my Cypher for performance", "draft a release note",
    "audit this AGENTS.md".

  If room freezes, three I personally know are achievable in 25 min:
  - Regex tester with explanations
  - JSON-to-Cypher converter
  - Markdown TOC generator

  Transition: "Now — the prompt itself. Five things every strong one-shot prompt names."
:::

::: slide ordered_list_3
title: What every strong prompt names
items:
  - heading: Tech stack
    subline: "“single HTML file, vanilla JS, no build step”"
  - heading: Inputs and outputs
    subline: "“text area takes JSON, button copies output to clipboard”"
  - heading: Algorithm or rule
    subline: "“parse with X, group by Y, sort descending”"
notes: |
  Three on layout. Two more verbally:

  4. STORAGE — "in memory only" or "localStorage" or "none."

  5. WHAT NOT TO ADD — "no settings page, no dark mode, no auth."
     Most under-used. The agent fills in blanks. Fill them yourself.

  Reference back: WikiLinks nailed all five.
  - Tech: "no react, ts, just base JS, d3"
  - I/O: "single input field for the wikipedia page URL"
  - Algorithm: "first 5 links, then first 5 of those, max 25 nodes"
  - Storage: "in memory"
  - Don't add: "light mode only" (no dark mode), no settings, no save

  If your prompt hits all five, the model has nothing to ask back.
  That's the threshold for one-shot success.

  Transition: "Twenty-two minutes. Here's the rhythm."
:::

::: slide hero_text
eyebrow: 22 MINUTES, ONE PROMPT, ONE TOOL
title: The rhythm
headline: One prompt → run → at most two fixes → use it
body: |
  0:05  decide and write the prompt (specific, all five things)
  0:20  run, fix, use it. Targeted follow-ups, two-fix limit.
  0:30  save it, ready to show. No plan mode. No task breakdown.
notes: |
  Methodology slide. Walk it crisply:

  0:00–0:05  Decide. Write the prompt. Be specific (the five things).
  0:05–0:20  Run. If broken: ONE targeted follow-up. At most TWO before
             you stop and re-think. Follow-up #3 = open new chat.
  0:20–0:25  USE IT for real. Catch one bug or missing feature.
  0:25–0:30  Save it. Be ready to show.

  Rule: TARGETED FOLLOW-UP BEATS RE-PROMPT. Two-fix limit beats infinite
  tweaking. Don't expand scope mid-fix.

  Discipline DELIBERATELY excluded: no plan mode, no task breakdown, no
  AGENTS.md. All of that comes in Exercise 2.

  Transition: "I'll walk the room. Flag me down. Go."
:::

::: slide divider
headline: Show and tell
subhead: 30 seconds each — what you built, did one prompt do it, what surprised you
notes: |
  Final 3 minutes of the exercise.

  Round-robin if engaged; 3 volunteers if shy. Three questions, 30 sec each:
  1. What did you build?
  2. Did one prompt do it, or did you need fixes?
  3. One thing the agent did better — or worse — than you expected.

  Listen for the model-progression moment. Someone WILL say "that surprised
  me; I didn't expect it to work first try." Name it: "Hold onto that.
  Now we look at what production work needs ON TOP of that capability."

  Bridge into the break:
  "Take 10 minutes. When we come back: how the harness ACTUALLY works,
  and where the cost-of-trying gain comes from."
:::

::: slide divider
headline: Break · 10 minutes
subhead: Coffee. Stretch. Back at <time>.
notes: |
  Use this slide for the visible "back at" time.
  Update the time on the slide before the workshop starts.

  When the room comes back: deep dive. Different energy — analytical,
  toolkit-focused. Slow down a notch from the exercise's hands-on energy.
:::

::: slide divider
headline: Harnesses & tool use
subhead: How the body works — and where the levers are
notes: |
  Block 4 of the day. ~20 minutes.

  Goal: vendor-neutral mental model of harnesses; the 6-rung tool-use ladder;
  calibrate the room on what each rung costs.

  Frame: "The model is the brain. The harness is the body. Most of the
  productivity difference between engineers using these tools comes from
  how well they understand the body, not how clever the brain is."
:::

::: slide three_col_text
eyebrow: ANATOMY OF ANY HARNESS
title: Six boxes every harness has
heading1: System prompt + Loop
heading2: Tools + Context
heading3: Permissions + State
body1: |
  System prompt — behavior, safety, persona.
  The loop — read user → call model → parse tool calls → execute → repeat.
body2: |
  Tools — Bash, file ops, grep, web fetch, LSP, MCP, planning.
  Context mgmt — caching, compaction, deferred tool loading.
body3: |
  Permissions — modes, risk classifier, protected paths, hooks.
  State / memory — session, transcript, AGENTS.md, persistent memory.
notes: |
  Six boxes. Strip away the branding and they all share this anatomy:

  1. SYSTEM PROMPT — behavior, safety, tool-use protocol, persona
  2. THE LOOP — read user → call model → parse tool calls → execute → repeat
  3. TOOLS — Bash, file ops, grep, web fetch, LSP, MCP, planning, …
  4. CONTEXT MANAGEMENT — caching, compaction, deferred tool loading
  5. PERMISSIONS — modes, risk classifier, protected paths, hooks
  6. STATE / MEMORY — session, transcript, AGENTS.md, persistent memory

  Why it matters: every "tip" or "best practice" you read about CC,
  Cursor, Codex, Aider — it's a tweak to ONE of these six boxes. With
  this anatomy, you can read any new tool's docs in 10 minutes.

  Transition: "Two main families — CLI and IDE. Different ergonomics, same anatomy."
:::

::: slide two_col_text
eyebrow: TWO FAMILIES
title: CLI vs IDE — same anatomy, different ergonomics
heading1: CLI-first
heading2: IDE-first
body1: |
  Claude Code, Codex CLI, Aider, opencode, Goose, Crush, Pi, Gemini CLI.
  Long autonomous runs. Hooks. Sub-agents. Scripting. CI integration.
  Parallel worktrees.
body2: |
  Cursor, Cline, Windsurf, Copilot agent, Junie, Antigravity.
  Live diff review. Inline edits. Parallel agent tabs (Cursor 3, Windsurf).
  Onboarding for non-CLI engineers.
notes: |
  Quick orientation across the field.

  CLI wins for: long autonomous runs, background/cron, sub-agents,
  scripting, CI integration, parallel worktrees.

  IDE wins for: live code review, inline diffs, parallel agent tabs,
  onboarding for engineers who haven't lived in a terminal.

  Take for the room: pick ONE CLI harness and ONE IDE harness, learn both
  deeply. The mental model transfers.

  Feb 2026 multi-agent convergence: every major tool shipped parallel
  sessions in the same two-week window. Grok Build (8), Windsurf (5),
  CC Agent Teams, Codex Agents SDK, Devin parallel. The race is over
  the orchestration layer now, not the model.

  Transition: "Three architectural choices recur across all of them.
  Worth naming because each is a deliberate bet."
:::

::: slide three_col_text
eyebrow: ARCHITECTURAL BETS
title: Three context strategies in the wild
heading1: Repo-map
heading2: Vector RAG
heading3: Whole-context
body1: |
  Aider's signature.
  PageRank-over-symbols, AST-derived.
  Token-efficient on million-line repos.
heading2: Vector RAG
body2: |
  Cursor's approach.
  Chunked embedding lookups.
  Flexible, opaque about what got retrieved.
body3: |
  Gemini CLI's bet.
  1M-token window often replaces RAG entirely.
  Simple, expensive at scale.
notes: |
  Three different bets on how to give the model what it needs.

  Many teams use more than one. None is universally right.

  Three more architectural patterns worth naming if time:
  - EDIT FORMAT: Codex apply_patch DSL (RL-trained custom diff format)
    vs CC structured edits vs Cline whole-file rewrites (Roo's apply_diff
    fork ships ~30% cheaper edits).
  - TOOL ARCHITECTURE: MCP-everything (Goose — every capability is an MCP
    subprocess) vs built-in + MCP (most others) vs Cline can GENERATE
    MCP servers on demand.
  - CODE INTELLIGENCE: LSP-first (Crush, Junie spawn language servers
    per project for type-aware navigation) vs grep heuristics (most others).

  Transition: "Now — every harness has a sliding scale of HOW it lets
  the model use tools. Six rungs."
:::

::: slide ordered_list_3_staggered
title: The tool-use ladder — six rungs
items:
  - heading: 1 · Built-in
    subline: Read · Edit · Bash · Grep · WebFetch — zero effort, lowest cost
  - heading: 2 · Linux CLI
    subline: jq · sed · awk · ripgrep · git — free leverage, model is fluent
  - heading: 3 · Code snippets
    subline: python -c · node -e · awk one-liners — throwaway
notes: |
  Three on screen. Three more verbally:

  4. REST APIs — curl + jq + auth. Anything HTTP-shaped. Watch the
     token-fat JSON responses; pipe through jq before the prompt sees it.

  5. SKILLS — captured procedures, slash-commands + prompt bundles.
     "Skill the third repetition." First time: just do it. Second: note it.
     Third: skill it.

  6. MCP servers — full external platforms (Snowflake, GitHub, Sentry,
     Linear, Atlassian, Neo4j, browsers). Biggest capability AND biggest
     cost / fragility jump.

  RULES OF THUMB:
  - Bash is the universal escape hatch. Every other tool is a wrapper.
  - jq + ripgrep are force multipliers. Install everywhere your agents run.
  - Don't reach for MCP when curl would do. Curl|jq ships in 2 minutes;
    equivalent MCP server takes a day.
  - MCP for PLATFORMS, skills for PROCEDURES. Complementary, not alternatives.

  Transition: "Same anatomy, same ladder — but where productivity comes
  from is HOW you steer it. Five craft levers."
:::

::: slide three_col_text
eyebrow: FIVE CRAFT LEVERS
title: Where productivity actually comes from
heading1: Sessions + Plan mode
heading2: Context + Models
heading3: Tools, hooks, skills, MCP
body1: |
  Start fresh per task. One topic per session.
  Plan mode for ~80% of tasks (CC creator's number).
  Plan-mode is a gate, not magic.
body2: |
  Cache boundary. /clear, /compact at 70%.
  Deferred tool loading.
  Haiku for glue, Sonnet for bulk, Opus for hard.
body3: |
  ~10 core tools in the prompt; rest deferred.
  Hooks = deterministic shell at lifecycle events.
  Skills bundle expertise. MCP for external platforms.
notes: |
  Five levers grouped into three columns.

  PLAN MODE is the lever I most want them to internalize. CC's creator
  reportedly uses it for ~80% of tasks. Pattern: plan mode → review →
  flip to auto-accept for execution → flip back. PLAN MODE IS A GATE,
  NOT MAGIC.

  HOOKS are the production differentiator: deterministic shell commands
  that ALWAYS run on lifecycle events (PreToolUse, PostToolUse, Stop,
  SessionStart). The right place for things that MUST happen every time
  — formatting, linting, security checks. Block at submit, not at write.

  PUSH (RAG) vs PULL (tool calling): two ways context arrives. Push is
  cheaper but speculative. Pull is precise but slower. API design
  principles apply to tool design — clear names, stable signatures,
  terse responses.

  Transition: "Every lever I just listed maps to a token cost decision.
  Where the tokens actually go — next."
:::

::: slide divider
headline: Cost & token economics
subhead: New top skill in 2026 — same model, same task, 10× cost difference
notes: |
  Block 5. ~10 minutes.

  Goal: cost-literate. Every craft lever from the last section costs
  (or saves) tokens. The discipline shows up in ccusage.

  Frame: "In 2026 the new top skill is token economy. Same model, same task,
  same outcome — 10× cost difference between someone who knows the levers
  and someone who doesn't."
:::

::: slide hero_text
eyebrow: THE MENTAL MODEL
title: Every session is a long invoice
headline: Productive tokens are the residual
body: |
  CLAUDE.md, hooks, skills, MCP schemas, conversation history, cache miss —
  all pre-charged before your prompt.
  90-day audit (430 hours, $1,340): only 27% of tokens were productive.
  73% was overhead. The bloat is in context, not model choice.
notes: |
  This is the conceptual heart of the section. Anchor it.

  Source: @mnilax 90-day instrumented Claude Code audit, April 2026.
  430 hours, 6M input tokens, $1,340 spend. Categorized every token.
  Productive: 27%. Overhead: 73%.

  Critically: cheaper-model-on-bloated-context still costs MORE than
  expensive-model-on-lean-context. The bloat is in the context, not the model.

  CONTEXT PYRAMID (Lance Martin's framing):
  - PERSISTENT BASE (cached): system prompt, role, AGENTS.md, core facts
  - DYNAMIC MIDDLE (partially cached): examples, memory, tool list
  - EPHEMERAL TOP (never cached): tool outputs, current reasoning, user message

  Caching applies most strongly at the BASE. Stable layers compound discounts;
  churn at the bottom invalidates everything above.

  Transition: "Here's where the 73% actually goes — nine invisible patterns."
:::

::: slide stats_grid_6
title: 9 invisible patterns of waste
stats:
  - num: "14%"
    lbl: CLAUDE.md bloat
  - num: "13%"
    lbl: History re-reads
  - num: "11%"
    lbl: Hook injection
  - num: "10%"
    lbl: Cache miss on resume
  - num: "7%"
    lbl: Skill auto-loading
  - num: "6%"
    lbl: MCP tool schemas
notes: |
  Six on screen. Three more not shown:
  - 5% extended thinking on simple questions
  - 4% wrong-direction generation (model goes off track, you let it finish)
  - 3% plugin / SessionStart noise

  Source: @mnilax 90-day Claude Code audit, April 2026.

  Headline result of fixing all 9: avg input tokens / prompt 18,400 → 6,100
  (-67%); productive token share 27% → ~65%; days until weekly limit
  4.2 → 7+; ~$130/month saved on the same workload.

  Counter-intuitive finding: switching to Haiku for "simple" tasks saved
  only 3%. Aggressive /clear lost context that cost more in re-prompting.
  The bloat is in the patterns above, not in model choice.

  30-second audit (Monday morning):
  - wc -w ~/.claude/CLAUDE.md (target < 1500 tokens)
  - cat .claude/settings.json | jq '.hooks.UserPromptSubmit'
  - jq '.mcpServers // {} | keys' (target ~3 always-on)

  Transition: "Three moves you can make. Frame from context engineering."
:::

::: slide three_col_text
eyebrow: THREE MOVES
title: Offload · Consolidate · Retrieve
heading1: Offload
heading2: Consolidate
heading3: Retrieve
body1: |
  Get info OUT of the prompt.
  /clear (free). Filesystem notes.
  Vector DB. Graph for structural.
body2: |
  Reduce what's already in context.
  /compact at ~70%.
  Sub-agent fork → digest.
body3: |
  Bring exactly what's needed.
  Prompt caching (10× discount).
  Deferred tool loading. RAG.
notes: |
  Every saving lever is one of three moves.

  PROMPT CACHING is the single biggest lever — 10× discount on cached input
  across all major vendors. Cache reads at $0.30/Mtok vs $3 input on Sonnet.

  Three rules of thumb:
  1. Cache hit rate IS the metric. If you don't know yours, find out tomorrow.
  2. Don't churn the system prompt. Every AGENTS.md edit invalidates the cache.
  3. Use the cheapest model that works. 80% of tasks don't need Opus.

  Transition: "Five tools that make this practical."
:::

::: slide three_col_text
eyebrow: FIVE TOOLS WORTH KNOWING
title: Token measurement and reduction
heading1: Measure
heading2: Reduce input
heading3: Reduce output
body1: |
  ccusage — reads ~/.claude JSONL.
  Tokens by model, type, day.
  De facto standard. Install first.
body2: |
  RTK — proxy. 60-90% on git/grep/test.
  headroom — context interceptor.
  SmartCrusher, reversible. ~50%.
body3: |
  caveman — output rewriter, 65-75%.
  Built-in: caching, /clear, /compact,
  token-efficient tools (Claude 4.x).
notes: |
  MEASUREMENT first — you can't fix what you can't see.
  - ccusage: github.com/ryoppippi/ccusage. `npx ccusage` reads local JSONL,
    produces reports. Install tomorrow if you don't have it.
  - Most modern harnesses now show running token cost in the TUI.

  ACTIVE REDUCTION on the input side:
  - RTK (Rust Token Killer): Rust CLI proxy, intercepts git/ls/grep/etc,
    rewrites to token-efficient equivalents. 60-90% on dev operations.
  - headroom (chopratejas): context-compression interceptor (library, proxy,
    middleware, or MCP). SmartCrusher strips redundant tool outputs / logs /
    files, reversible retrieval if model needs the original. ~50% savings.

  ACTIVE REDUCTION on the output side:
  - caveman: Claude Code skill that rewrites the agent's output style for
    65-75% output-token savings. Bundled caveman-shrink MCP also compresses
    input ~46%.

  Built-in protocol-level: prompt caching (Anthropic, OpenAI, Google all
  support); token-efficient-tools default in Claude 4.x; Aider's architect
  mode (cheap editor, expensive reasoner).

  Transition: "What does this cost in actual dollars in 2026?"
:::

::: slide stats_grid_6
title: 2026 model pricing (per Mtok)
stats:
  - num: "$1"
    lbl: Haiku 4.5 in
  - num: "$3"
    lbl: Sonnet 4.x in
  - num: "$5"
    lbl: Opus 4.5 in
  - num: "$5"
    lbl: GPT-5.5 in
  - num: "$1.25"
    lbl: GPT-5 in
  - num: "$2"
    lbl: Gemini 3 Pro in
notes: |
  Verified May 2026. Pricing moves monthly — re-verify before slides go up.

  Output prices (each ~5× input):
  - Haiku 4.5: $5 out
  - Sonnet 4.x: $15 out
  - Opus 4.5: $25 out (Fast tier: $30 / $150 — 6× standard)
  - GPT-5: $10 out
  - GPT-5.5: $30 out (verified — was $25 in stale draft)
  - Gemini 3 Pro: $12 out (≤200K), $18 above

  Cache reads are ~10× cheaper than fresh input across all vendors.
  This is why caching matters: 90% discount on 90% of your bytes.

  Real-task cost snapshots (rough, my own runs):
  - Small bug fix (~10 turns): $0.05 disciplined / $0.50 sloppy
  - Medium feature (~50 turns): $0.50 / $5
  - Big refactor (~200 turns): $3-5 / $30-60
  Same model, same outcome. The 10× gap is entirely discipline.

  Transition: "OK — but how do we KNOW any tool is good? Benchmarks."
:::

::: slide divider
headline: Benchmarks
subhead: Direction yes. Absolute no. Run your own.
notes: |
  Block 6. Compress to ~5 minutes. Skeptics will raise this if I don't.

  Frame: "Benchmarks tell you the DIRECTION the field is moving. They
  don't tell you which tool is best for your codebase. Use them like a
  weather report — informative, directional, not a substitute for
  going outside."
:::

::: slide three_col_text
eyebrow: 5 FAMILIES — LEAST → MOST REALISTIC
title: The benchmark landscape
heading1: Function-level
heading2: Repo-issue
heading3: Real-work
body1: |
  HumanEval, MBPP, MultiPL-E.
  Saturated >95% — historical only.
  BigCodeBench is less saturated.
body2: |
  SWE-bench Verified — top ~88%.
  Terminal-Bench 2.0 — CC 92%, Codex 77%.
  Single-repo, contamination-sensitive.
body3: |
  METR — +19% SLOWDOWN in 2025 RCT.
  SWE-Lancer — $1M real Upwork tasks.
  Your own 3-task eval beats them all.
notes: |
  Three on screen. Two more in the middle:

  - CONTEST-STYLE — LiveCodeBench (continuously updated, contamination-resistant)
  - TERMINAL / AGENTIC — Terminal-Bench, Cybench. Multi-step, real loop.

  CRITICAL caveat: scores are produced by (model × harness × scaffolding).
  The 92.1% is a Claude Code number, not a Claude number. Apples-to-apples
  comparisons are hard.

  METR REAL-WORK NUMBER deserves emphasis: 2025 RCT measured +19% SLOWDOWN
  (not uplift) with AI tools. The procurement-relevant signal — and it
  has FLIPPED SIGN since the study landed. The 2026 follow-up shows the
  gap narrowing.

  Transition: "How to read benchmarks like a senior engineer."
:::

::: slide hero_text
eyebrow: THE HONEST TAKE
title: Run your own three-task eval
headline: Internal eval beats public leaderboards
body: |
  Pick 3 tasks from your last sprint (easy, medium, nasty).
  Run each tool on them — once a quarter.
  Score yourself on review burden, not just task completion.
  That's the only number that matters for procurement.
notes: |
  9-point rubric for reading benchmarks (use as needed):

  1. DATE-CHECK IT. >90 days = stale.
  2. TOOL AND MODEL. "GPT-5.5 hits X" is meaningless without "in WHICH harness."
  3. pass@1 or pass@N? If unstated, assume the most flattering reading.
  4. PUBLIC vs PRIVATE eval? Hidden eval sets resist contamination better.
  5. COST and LATENCY footnote? No? Treat as upper-bound theoretical.
  6. DIRECTION not absolute. "Is it getting better?" beats "is X > Y."
  7. REAL-WORK PROXY? METR, SWE-Lancer, Aider polyglot, your own eval.
  8. TRIANGULATE three benchmarks. Different biases.
  9. RUN YOUR OWN. The only number that matters for procurement.

  Closing line: "The acceleration is real. The numbers are directionally
  trustworthy. But the absolute leaderboard position of harness X over
  harness Y is a worse signal than running both on three of your own
  tickets for an afternoon. Ten engineers' worth of internal eval beats
  all the public benchmarks combined."

  Transition: "OK — anatomy, ladder, cost, benchmarks. Now the practices
  that turn this into a working method."
:::

::: slide divider
headline: Practices
subhead: AGENTS.md · plan mode · ralphing · spec-driven · the per-task loop
notes: |
  Block 7 — the conceptual heart of the day. ~20 minutes.

  Goal: turn anatomy + cost knowledge into a working method.

  Frame: "Treat the agent like the most patient, deepest-diving junior
  engineer you've ever worked with — who has read every line of public
  code, knows nothing about YOUR code, and has no ego, no fatigue, no
  fear of being wrong. Everything that follows is good onboarding for
  that teammate."
:::

::: slide two_col_text
eyebrow: THE MENTORING FRAME
title: Strengths and gaps of your new teammate
heading1: What it has (better than humans)
heading2: What it lacks (yours to bring)
body1: |
  Infinite patience. No ego, accepts correction.
  Endurance — hour 8 same as hour 1, 3am same as 9am.
  Deep dives — reads the whole RFC, every linked spec.
  Consistent rule-following.
  Massive surface area — every framework, every API.
body2: |
  No project memory — yesterday's PR is news every morning.
  No production scars in YOUR codebase.
  No taste calibrated to your team's trade-offs.
  Can't read between the lines of a Slack thread.
  No causal reasoning about WHY past decisions were made.
notes: |
  Same things you'd do for a sharp new hire — good README, clear style
  guide, paired-up planning, code review, written-down conventions, a
  test suite that catches obvious mistakes — are EXACTLY what turns an
  agent from a liability into a teammate.

  The leverage of doing them well is much higher with an agent than with
  a human, because the agent ingests them perfectly and applies them tirelessly.

  KEY REFRAME: "Good software design was never for the machine. It was
  always for the humans who had to read, maintain, and extend it. Now
  those humans include AI teammates that learned the craft from
  human-written code."

  Transition: "Lance Martin says it cleanest."
:::

::: slide quote
quote: |
  “Most of the time when an agent is not performing reliably,
  the underlying cause is not that the model is not intelligent enough,
  but rather that context and instructions
  have not been communicated properly to the model.”

  — LangChain, “Communication is all you need”
notes: |
  This is THE quote for the design-as-communication thread.

  Frame the implication: most agent failures are communication failures.
  The model is rarely the bottleneck — the prompt, the AGENTS.md, the
  spec is.

  Add Claire Vo's manager-skill take if there's room: "I know how to make
  an employee successful. That is what you need to make these agents work.
  You don't need the technical skills. You need role scoping, design,
  voice. The rest of it we can give to ClaudeCode to figure out."
  — Claire Vo, Lenny's Newsletter, 2026.

  This is a manager's skill, not just an IC's. Many seasoned engineers
  have the muscle from leading teams; just need to point it at a new target.

  Transition: "The agent will fail in five named ways. Drew Breunig
  catalogued them in June 2025."
:::

::: slide three_col_text
eyebrow: 5 NAMED FAILURE MODES
title: How context fails (Drew Breunig, June 2025)
heading1: Rot · Poisoning
heading2: Confusion · Distraction
heading3: Clash
body1: |
  ROT — long sessions accumulate stale assumptions, lose focus.
  Silent degradation before visible failure.

  POISONING — hallucinated content gets re-used.
  Gemini playing Pokémon hallucinated an item, tried to use it later.
body2: |
  CONFUSION — more tools = worse, not better.
  Especially when tools overlap or have similar names.

  DISTRACTION — at >100k tokens, Gemini favoured repeating prior
  actions over new plans. The agent stops thinking; it pattern-matches.
body3: |
  CLASH — back-to-back tool calls
  that contradict tank performance.
  Model can't reconcile the conflict.

  Plus: PLAUSIBLY WRONG. COGNITIVE LOAD.
notes: |
  Source: Drew Breunig, "How Long Contexts Fail and How to Fix Them",
  dbreunig.com, June 22 2025.

  Naming these gives engineers vocabulary for failure modes they've
  experienced but couldn't articulate.

  Two more failure modes worth mentioning:
  - PLAUSIBLY WRONG: confidently wrong code that compiles, lints,
    eyeballs fine — and breaks production.
  - COGNITIVE LOAD: reviewing 500 lines of plausible code is harder
    than writing 200. Jevons paradox: efficiency gains absorbed by
    demand for human judgment. Real and unsolved.

  Transition: "Why does writing things down help? Because it COLLAPSES
  the distribution of possible answers."
:::

::: slide hero_text
eyebrow: THE CONCEPTUAL HEART
title: Every constraint collapses the latent space
headline: TDD and spec-driven dev are sudden killers
body: |
  AGENTS.md → spec → plan → tests → existing code.
  Each constraint narrows the model's distribution toward what you want.
  TDD: tests are verifiable rewards — exactly what RL trained on.
  Spec: collapses the latent space BEFORE the agent hallucinates.
notes: |
  This is THE big idea slide. Slow down here. ~3 minutes.

  A model holds an enormous distribution over possible continuations.
  "Write a function that fetches a user" has millions of plausible answers.
  Every constraint conditions the output distribution toward what you want.

  This isn't a metaphor — it's how the model actually works.

  WHY TDD IS SUDDENLY THE KILLER TECHNIQUE:
  - Tests are VERIFIABLE REWARDS. Model was post-trained on this signal.
  - A failing test is a precise, machine-readable specification.
  - "All tests green" is an unambiguous stopping condition.

  WHY SPEC-DRIVEN IS WORTH THE CEREMONY:
  - Spec collapses the latent space BEFORE the agent starts hallucinating.
  - Moves human-judgment work upstream, where it's cheap.
  - Makes review a check-against-spec, not a check-against-vibes.

  Dan North's Replaceable Component Architecture suddenly very practical:
  "Code is throwaway. Specs and tests are the durable artifacts."

  Transition: "AGENTS.md is the project's MVC — Minimum Viable Context."
:::

::: slide two_col_text
eyebrow: AGENTS.MD = MINIMUM VIABLE CONTEXT
title: The team handbook for your AI teammate
heading1: What goes in (50–100 lines)
heading2: What does NOT
body1: |
  3-line orientation — system, stack, entry points.
  Exact commands — pnpm test, lint, typecheck.
  Conventions not obvious from code.
  Guardrails — never edit .env, migrations.
  Pointers (links) to ADRs, API spec.
  Reiterate the essence at the END.
body2: |
  Patterns derivable from the code itself.
  Long history (rots, bloats every prompt).
  Things better expressed as a hook.
  Anything that belongs in a test.
  Generic AI advice the model knows.
notes: |
  AGENTS.md is the project's MINIMUM VIABLE CONTEXT — smallest set of
  facts and rules that lets the agent do good work without overwhelming
  the prompt. High signal-to-noise.

  STRUCTURE RULES (often missed):
  - Group related info; label with headers + XML tags
  - Build hierarchy: short summary at top, detail below
  - REITERATE THE ESSENCE AT THE END — attention weights are higher at
    the end of the prompt. Close AGENTS.md with one line restating the
    most important rule.

  LAYERING:
  - ~/.claude/CLAUDE.md — personal global
  - <project>/AGENTS.md — project root, team-shared, in git
  - <project>/<area>/AGENTS.md — optional per-area overrides
  - .claude/skills/ — slash-commands and skill definitions

  OPERATING:
  - Keep it 50-100 lines at root. Long files = cache-bloat + signal dilution.
  - Don't churn mid-session. Every edit invalidates prompt cache.
  - Treat it like a PR-reviewed artifact. Bad rules propagate silently.

  Transition: "And when the session is going sideways — ralph."
:::

::: slide hero_text
eyebrow: WHEN STUCK
title: Ralphing — context reset, re-seeded
headline: If you've corrected twice, the third try isn't the charm
body: |
  Capture goal · /clear · re-seed with goal + spec + key files · restart in plan mode.
  KEEP: goal, spec, failing test, 1-2 key file refs.
  DROP: diagnostic detours, wrong-path commits, "let me try once more" energy.
notes: |
  Named after Geoff "Ralph" Huntley's 2025 pattern. Now standard practice
  across CC, Cursor, opencode, Pi (Pi has it as a UI primitive — branchable
  session tree).

  WHEN TO RALPH:
  - You've corrected twice on the same point
  - Agent is "fixing" things you didn't ask it to touch
  - Long plan-mode investigation has bloated context past 60-70%
  - You feel the urge to write a long corrective prompt — that's the signal

  HOW (the loop):
  1. Capture state — git status, screenshot the plan, note goal in 3 lines
  2. /clear — drop the session
  3. Re-seed — fresh prompt with goal, current state, ONLY the files that
     matter, the constraints from earlier
  4. Restart in plan mode — let it re-orient cleanly

  COUSIN TECHNIQUES:
  - /compact at ~70% — softer reset, summarizes session into smaller replacement
  - Plan-mode reset — exit plan, /clear, re-enter with plan as the seed
  - Worktree split — for parallel tracks, give each its own worktree
  - Sub-agent fork — for research detour, spawn a sub-agent so main context stays clean

  Quote to land: "If you find yourself writing a long corrective prompt,
  that's the signal to ralph instead."

  Transition: "Ralphing handles broken sessions. The bigger question is
  how to NOT have broken sessions — spec-driven development."
:::

::: slide three_col_text
eyebrow: SPEC-DRIVEN DEVELOPMENT
title: Three task sizes, three patterns
heading1: Small
heading2: Medium (the 80% case)
heading3: Large
body1: |
  ≤30 min, single file, clear.
  One-shot prompt with strong AGENTS.md context.
  Skip the ceremony. Like Exercise 1.
body2: |
  Multi-file, well-understood.
  Plan mode → review → execute.
  CC's creator: ~80% of tasks fit here.
body3: |
  Multi-day, ambiguous, cross-cutting.
  Full spec flow: spec doc → task breakdown → per-task loop.
  Like Exercise 2 in 60 minutes.
notes: |
  Decisions are cheap when made before code is written. Plan mode and
  specs are how you front-load the judgment.

  THE 6-STEP SPEC FLOW (for large tasks):
  1. Scope & orient — what problem, whose, boundaries
  2. Gather context — read code, ADRs, similar past work (plan mode)
  3. Surface questions — agent asks, human decides; resolve before code
  4. Write the spec — goals, non-goals, API shape, data shape, invariants
  5. Break into tasks — each scope, acceptance criteria, dependencies
  6. Per-task loop (next slide)

  WHY PLAN MODE WORKS FOR REASONING MODELS:
  - Produces structured intermediate state the model was trained to consume
  - Per-task scoping matches the agentic loop the model was RL-trained on
  - Clean per-task context = fresh prompt-cache prefix → fast AND accurate

  PLAN MODE TACTICS:
  - Always plan-mode first for medium+ tasks. ~80% per CC creator.
  - Read the plan critically. "I'll figure out X during implementation"
    will rabbit-hole. Push back; resolve X now.
  - Distill before exiting. 40-step plan = too big, split.

  Transition: "And the loop you run for each task."
:::

::: slide three_col_text
eyebrow: PER-TASK LOOP — 11 STEPS, 3 PHASES
title: Same loop, every task, every time
heading1: Reason / Plan
heading2: Act / Execute
heading3: Verify / Observe
body1: |
  1. Determine scope — what's "done"?
  2. Verify prerequisites — env, deps.
  3. Gather local context — neighbouring code only.
  4. Resolve questions — most undervalued step.
  5. Plan execution — 5-10 steps, real symbols.
body2: |
  6. Establish safety net — TDD where possible.
  7. Implement — smallest change that works.
  No drive-by refactors.
  No scope expansion.
body3: |
  8. Run tests — relevant test, not whole suite.
  9. Run quality gates — as hooks not prompts.
  10. Show diff + commit message.
  11. Feedback — refine or commit.
notes: |
  THE 11-STEP LOOP, mapped to 3 phases.

  REASON / PLAN (1-5): What to do?
  Goals, role, task breakdown, memory, metadata, tool selection.

  ACT / EXECUTE (6-7): How?
  Parameter conversion, multi-tool execution, error handling.

  VERIFY / OBSERVE (8-11): Integrate results.
  Extract & integrate, judging/eval, compress, update memory, decide next loop.

  WHAT THE LOOP BUYS YOU:
  - DETERMINISM in an indeterministic system. Model is probabilistic; loop isn't.
  - RECOVERABILITY at any step.
  - REVIEWABLE UNITS — one task = one diff = one reasoning trail.
  - CACHE-FRIENDLY — each task = clean prefix → high cache hit rate.
  - TRAINS YOU — after 30 of these, you know which tasks the agent eats
    whole and which need spec work.

  Transition: "OK — that's the toolkit. Let me show you what it actually
  looks like in my daily work. Six modes."
:::

::: slide divider
headline: How I use this every day
subhead: Six modes. Live demos.
notes: |
  Block 8. ~10 min. ALL LIVE DEMOS — minimal slides.

  Six modes I'll demo briefly:
  1. Research / generating learning content (Sather-K, vibe-haskell)
  2. Content generation (neo4j-skills, agent-integrations)
  3. Codebase research (claude-code analysis, cocoindex)
  4. Simple greenfield (openalex-neo4j, clauditopia)
  5. OSS contributions (inferrs, aura-cli)
  6. Larger greenfield (agent-intelligence, neo4j-skills cypher,
     create-context-graph.dev)

  90 seconds each + intro/outro = ~10 minutes. Cut to 4 if running tight
  (drop 2 + 5).

  Pre-flight: terminals pre-opened, AGENTS.md visible per demo, fresh
  sessions. One failure ready per category — credibility comes from
  showing warts.

  Transition (after the demos):
  "Six modes, same toolbox. The mistakes are real and yours to make.
   Now you're going to make some — that's Exercise 2."
:::

::: slide divider
headline: Break · 10 minutes
subhead: Coffee. Stretch. Back at <time>.
notes: |
  Update the time on the slide before the workshop.

  When the room comes back: Exercise 2. Different energy from Ex1 —
  this one is harder, longer, on real work, with the full discipline.

  While the room is on break, walk-the-room checklist visible:
  catch attendees skipping plan mode at minute 8, not minute 30.
:::

::: slide divider
headline: Exercise 2 · 60 minutes
subhead: Real work. Real discipline.
notes: |
  Block 10. The main event of the workshop.

  Frame: "Pick something non-trivial from your own world. Real ticket-shape
  work, multi-step, you can verify it worked. The agent will go off the
  rails on this one — that's not a bug, that's the lesson. We're going
  to use the discipline (spec → plan → subtasks → loop) to keep it on track."

  Hand out the printed 2-page handout (exercise-2-handout.md).
:::

::: slide quadrant_2x2
title: Pick a task archetype
heading1: |-
  Nasty bug
  Multi-file. Possibly intermittent. Root cause + fix + regression test.
heading2: |-
  New feature
  Small but real. Multi-file. Has a test. Doesn't break what was there.
heading3: |-
  MCP server / extension
  A surface you own. Expose 2-3 useful tools.
heading4: |-
  Cross-language port
  Existing functionality, language you don't normally use.
notes: |
  Four shapes. Pick whichever fits something you've actually got.

  Don't agonize for more than 2 minutes. The discipline matters more than
  the topic.

  Examples per shape:
  - BUG: race condition, memory leak, edge case the tests miss, regression
  - FEATURE: CSV export, new query parameter, admin toggle, rate limit
  - MCP: list_pipelines/get_status/restart for orchestration; run_query/
    list_databases/get_schema for a DB; list_users/get_audit for admin
  - PORT: Go CLI wrapping an HTTP endpoint; Rust port of a hot Python
    utility; TypeScript MCP server when you usually write Java

  Transition: "Sixty minutes. Here's the rhythm — and yes the setup
  feels long. That's the lesson."
:::

::: slide hero_text
eyebrow: 60-MINUTE BREAKDOWN
title: Discipline · Execution · Review
headline: Setup feels long. That's the lesson.
body: |
  0:05 pick · 0:15 AGENTS.md & env · 0:25 plan mode · 0:35 task breakdown
  0:55 execution loop (≤5 subtasks · ≤5 min each) · 1:00 review
  Skip setup → 1-2 messy commits. Disciplined → 5 clean ones.
notes: |
  Time math: 25 min setup discipline + ~5 min × 5 subtasks (25 min) +
  5 min review + slack = 60 min.

  THE BREAKDOWN (visible in their handout the whole hour):

  0:00–0:05  Pick task. Open fresh repo / branch.
  0:05–0:15  SETUP — AGENTS.md, tools, environment
  0:15–0:25  PLAN MODE on the chosen task
  0:25–0:35  TASK BREAKDOWN (agent does, you verify)
             ≤5 subtasks for 60 min total; aim for 5-7
  0:35–0:55  EXECUTION LOOP (~5 min × ≤5 subtasks)
             For each: plan → confirm → implement → tests → diff → commit
             Ralph if stuck twice. Don't reason your way out.
  0:55–1:00  REVIEW

  Time announcements: 0:15, 0:25, 0:35, 0:55. Walk the room during setup
  — most attendees skip AGENTS.md or stuff it with too much. Catch it
  early.

  Transition: "Five rules. Read these out loud once before they start."
:::

::: slide ordered_list_3
title: Five execution rules
items:
  - heading: Plan mode for every subtask
    subline: Even small ones. The 30s you save costs 5 min of cleanup.
  - heading: One subtask = one commit
    subline: Tempted to bundle? Your subtasks were too small. Commit anyway.
  - heading: Agent suggests, you decide
    subline: Especially on architecture and dependencies. Push back on libraries.
notes: |
  Three on screen. Other two:

  4. RALPH AFTER TWO CORRECTIONS. /clear, restate goal cleanly, restart.
     Third correction is rarely the charm. The signal: you're typing a
     long corrective prompt — stop, ralph instead.

  5. TIME-BOX EACH SUBTASK AT 5 MIN. If a subtask is taking 10, either
     it was actually 2 subtasks, or the scope was wrong. Stop, revise
     the breakdown, restart.

  Quote to land: "If you find yourself writing a long corrective prompt,
  that's the signal to ralph instead."

  Transition: "Sixty minutes. I'll walk the room. Go."
:::

::: slide divider
headline: Show and tell
subhead: How many subtasks landed? Where did the discipline break — or save you?
notes: |
  Last 5 minutes of Exercise 2.

  3 questions, 30 seconds each:
  1. What was your task?
  2. How many subtasks landed?
  3. Where did the discipline break down — or save you?

  Three volunteers if shy — quality over completeness.

  Anti-patterns to surface in wrap-up if they appear:
  - "I just told it what to do" — no plan, no breakdown, lots of code
  - "It kept fighting me on X" — didn't ralph
  - "My AGENTS.md was 200 lines" — over-engineered upfront
  - "I let it run and it did way more than I asked" — no scope discipline
  - "I didn't commit and now I can't roll back" — broke one-task-one-commit

  Bridge into mental-safety:
  "We've talked the whole time about technique. Before we open Q&A, I
  want to put three things on the table that are probably already in
  the room — the COST of all this on us as humans."
:::

::: slide divider
headline: Mental load · roles · career
subhead: The harder conversation
notes: |
  Block 11a. ~5-7 minutes before opening the floor.

  Frame: "These are questions I'm putting on the table, not answering.
  None of this has clean answers. The conversation matters more than
  the optimization."
:::

::: slide three_col_text
eyebrow: THE COST IS REAL
title: The mental load nobody volunteers
heading1: Review fatigue (Jevons)
heading2: Cognitive load shift
heading3: Always-on collaborator
body1: |
  Reviewing 500 lines of plausible code is harder than writing 200.
  Tools got 10× faster; demand for human judgment grew to absorb the gain.
body2: |
  Agent does the typing. You carry taste, trust calibration, architecture.
  Trust calibration is exhausting — every output needs an "is this real?" pass.
body3: |
  Agent at 3am, hour 8, last task of the day — same quality.
  You aren't. Asymmetry is dangerous if you let it set the pace.
notes: |
  The unspoken half of the productivity story.

  THE SKEPTIC IS RIGHT ABOUT SOMETHING. Cognitive exhaustion from
  always-on AI work is real, documented (BCG, Yegge, Sau Sheong),
  and not solved by a better tool.

  Sau Sheong (Singapore GovTech): "Humanity is not ready for this much
  software." The HUMANS aren't ready, regardless of tooling.

  WHAT HELPS:
  - AI-free hours / days. Treat them like exercise.
  - Pair with humans on hard work. Don't let the agent be your only collaborator.
  - Pace across weeks, not turns. The agent doesn't care how fast you go.

  Transition: "Different career stages face very different situations.
  Simon's framing is the cleanest."
:::

::: slide three_col_text
eyebrow: THE ROLE QUESTION (SIMON ON LENNY, APR 2026)
title: Senior · mid-career · junior
heading1: Senior
heading2: Mid-career
heading3: Junior
body1: |
  Judgment is the bottleneck — and the moat.
  Reviewer-first now. Get good at it.
  You set the practices: AGENTS.md, hooks, spec discipline.
body2: |
  Fastest-evolving role.
  Enough context to direct, enough humility to verify.
  Highest-leverage place in the industry right now.
body3: |
  The hardest path. "Agent can do what I can do."
  Trap: accepting output you can't yet evaluate.
  Mentorship matters MORE, not less.
notes: |
  SENIOR — your judgment is more valuable than ever, but you're now
  reviewer-first. Reviewing well is a different skill than writing well;
  most of us are out of practice.

  MID-CAREER — fastest-evolving role. TRAP: skipping the "do it the hard
  way once" step. Senior engineers can verify because they've done it.

  JUNIOR — Simon's point: the agent can do what a junior can do. Real
  career problem, don't pretend it isn't. The traditional "learn by
  doing the boring tasks" path is broken.
  TRAP: "You can't tell the agent did it wrong if you couldn't have done it right."

  CLAIRE VO ON LENNY: "I know how to make an employee successful. That
  is what you need to make these agents work. You don't need the
  technical skills. You need role scoping, design, voice. The rest of
  it we can give to ClaudeCode to figure out."

  Manager skill is the missing frame. Many seasoned engineers have the
  muscle from leading teams; just need to point it at a new target.

  Transition: "How to stay sharp — three things you can do this week."
:::

::: slide three_col_text
eyebrow: STAY SHARP
title: Three things you can do this week
heading1: AI sabbath
heading2: Pair with juniors
heading3: Slow down on review
body1: |
  Half a day, a side project, a Friday afternoon — no AI.
  Not a moral position. Muscle memory.
  Don't let your taste atrophy.
body2: |
  Pair with a junior on something THEY drive.
  Don't bring the agent. Watch how they actually solve.
  Mentorship matters more, not less.
body3: |
  30 min minimum on a 200-line agent diff.
  Find one thing you'd do differently.
  Tell the team. Calibration happens here.
notes: |
  Skill maintenance:
  - Read more code than you generate. Agents shift the ratio.
  - Code reviews matter more, not less. Slow them down on purpose.
  - Measure what's YOURS — what did you understand, choose, stand behind?

  Career questions worth being honest about:
  - Will this replace engineers? Probably not in aggregate (Jevons).
    Specific roles will compress. Judgment-heavy roles benefit.
  - The next generation? We don't have a clean answer yet. WE — the
    senior practitioners in this room — are the ones who get to figure
    it out. Not the platform vendors. Not the model labs. Us.

  Transition: "These three slides aren't questions I'm answering — they're
  questions I'm putting on the table. So — what would you do Monday morning?"
:::

::: slide divider
headline: Q&A
subhead: What did you see today that you want to try Monday morning?
notes: |
  Open the floor. ~18-20 minutes.

  My OPENING question (always ask, even if hands are up):
  "Before I take questions — let me ask one back. What's the thing you
  saw or did today that you want to try Monday morning? Just shout it out."

  This buys 30 seconds of genuine engagement, surfaces what landed,
  signals conversation not lecture. Tells me what to emphasize in closing.

  HAND-RAISER QUESTIONS if room stalls (use sparingly):

  Easy on-ramps:
  - "Who's about to switch their primary harness based on something today? To what?"
  - "What's something the agent has done well that genuinely surprised you?"
  - "What's the failure mode that bites you most? What did you change?"

  Mid-depth:
  - "Where in your stack do you NOT use AI today? Why?"
  - "Skeptics — what would convince you to try this on production work?"
  - "Team leads: how would you onboard a new team member to agentic workflows?"
  - "How are you handling reviewing agent-authored PRs at scale?"
  - "What do you actually MEASURE to know your AI tooling is helping?"

  Deeper:
  - "Has the agent ever proposed an architecture that was technically right
    but wrong for your team / product? How did you handle it?"
  - "What capability do you most want from these tools in the next 12 months
    that doesn't exist yet?"
  - "How is YOUR JOB different than a year ago? Better, worse, both?"

  Closing redirect: "If you take exactly ONE thing from today and apply it
  next week, what is it?"
:::

::: slide three_col_text
eyebrow: THREE THINGS TO TAKE WITH YOU
title: Closing
heading1: Practices that work
heading2: The system is the moat
heading3: All three are real
body1: |
  The practices that work with agents
  are the practices that always worked with humans.
  Spec, test, review, commit small.
  We just couldn't afford the ceremony before.
body2: |
  The model gets better every six months.
  The system you build around it is yours.
  AGENTS.md, hooks, the per-task loop —
  that's where your leverage lives.
body3: |
  The failure modes are real.
  The discipline is real.
  The leverage is real.
  Don't dismiss any of the three.
notes: |
  Pivot when Q&A winds down (signal: third silence > 5 sec).

  Walk the three:

  ONE — the practices that work with agents are the practices that always
  worked with humans. Spec, test, review, commit small. We just couldn't
  afford the ceremony before.

  TWO — the system you build around the model is the moat. The model gets
  better every six months. The system is yours.

  THREE — the failure modes are real, the discipline is real, and the
  leverage is real. Don't dismiss any of the three.

  Transition: "Resources are in the QR — take a picture before you stand
  up. Thank you."
:::

::: slide closing
headline: Thank you
contact: github.com/jexp/agentic-engineering
notes: |
  Final slide. Hold for ~30 seconds while people scan the QR / picture
  the slide. Don't rush it.

  The QR code (assets/qrcode-github-jexp-agentic-engineering.png) points
  to the public repo with all materials. Add it to this slide in the
  PowerPoint editor (the closing template has a space for it).

  The repo includes:
  - workshop-resources.md (full reading list, MCP server starters,
    practitioners and craftspeople to follow)
  - All section docs
  - Coding-agents/ — 16 per-tool deep dives
  - Mining docs from the CE deck and Simon's blog

  After the workshop is over: stick around for hallway conversations.
  The questions people bring up after the talk are usually the most
  interesting ones.
:::
