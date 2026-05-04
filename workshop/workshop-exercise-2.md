# Workshop — Exercise 2: Real Work, Real Discipline (60 min)

**Block**: Hands-on Exercise 2 (the main one)
**Duration**: 60 min hard cap (≈25 min discipline-setup + ≈30 min execution + 5 min review)
**Position**: After the deep dive (harnesses + tool-use + cost + practices + own-experience)
**Goal**: take a *real, non-trivial* task — bug, feature, or extension — and run the full agentic-engineering loop end-to-end. Five commits or substantial progress in 60 minutes. The exercise that makes the workshop pay for itself.
**Prerequisite**: each attendee has at least Copilot in VS Code/IntelliJ, or Junie, or their own preferred harness. We assume working setups; we don't assume the discipline yet.

---

## Slide 1 — The challenge

Pick something **non-trivial** from your own world. Not a toy, not a hello-world. Something you've been meaning to do.

Three rules:
1. **Real ticket-shape work** — something you'd file as an issue if you weren't doing it now
2. **Multi-step** — at least 3–5 logical subtasks; can't be a one-shot edit
3. **You can verify it worked** — there's a test, an output, a behavior you can check

The friction is the point. **The agent will go off the rails on this one.** That's not a bug — that's the lesson. We're going to use the discipline (spec → plan → subtasks → loop) to keep it on track.

---

## Slide 2 — Pick a task archetype

Four shapes, pick whichever fits something you've actually got.

### A. Nasty bug
A bug you've been avoiding. Subtle, multi-file, possibly intermittent. The kind that needs *investigation*, not just a fix.
- **Examples**: race condition, memory leak, edge case the tests miss, regression in someone else's module
- **What "done" looks like**: root cause identified, fix in, regression test added, all tests still green

### B. New feature
Small but real. A flag, an endpoint, a UI affordance, a config option that's been on the backlog for weeks.
- **Examples**: add an export-to-CSV option; new query parameter on an API; admin-only toggle; rate-limit middleware
- **What "done" looks like**: feature works end-to-end, has a test, doesn't break what was there

### C. MCP server / extension on a surface
The most ambitious option — add agent-callable capability to a surface of your own software. **Pick a surface you actually own** — an ETL/orchestration layer, a database/graph backend, an admin console, a piece of infra — and expose 2–3 useful tools as an MCP server.
- **Examples**: an MCP server exposing `list_pipelines / get_pipeline_status / restart_pipeline` for an orchestration layer; `run_query / list_databases / get_schema` for a database backend; `list_users / get_audit_log` for an admin surface
- **What "done" looks like**: MCP server runs, agent can call at least one tool successfully, README explains how to install

### D. Cross-language port
Take a piece of existing functionality and re-implement it in a language you *don't* normally use.
- **Examples**: a Go CLI that wraps an HTTP endpoint of yours; a Rust port of a hot Python utility; a TypeScript MCP server when you usually write Java
- **What "done" looks like**: it runs, it produces the right output for one input, you understand at least 50% of the code

> **Don't agonize over the choice for more than 2 minutes.** The discipline matters more than the topic.

---

## Slide 3 — The 60-minute breakdown

This is the slide attendees should keep visible the whole hour.

```
0:00 ─ 0:05    Pick task. Open a fresh repo / branch.
0:05 ─ 0:15    SETUP — AGENTS.md, tools, environment
                ┣━ Project orientation (3-6 lines)
                ┣━ Commands the agent will run (test, lint, build)
                ┣━ Conventions (errors, commits, file layout)
                ┣━ Guardrails (don't touch X; ask before Y)
                ┗━ Tools / MCP servers the agent should know about

0:15 ─ 0:25    PLAN MODE on the chosen task
                ┣━ Goal in one sentence
                ┣━ Let the agent investigate — read code, ask questions
                ┣━ Resolve clarifying questions BEFORE coding
                ┗━ Output: a 5–10 step plan with real symbols

0:25 ─ 0:35    TASK BREAKDOWN (let the agent do it, you verify)
                ┣━ "Break the plan into independent subtasks of ≤5 min each"
                ┣━ Each subtask has: scope, acceptance criteria, files involved
                ┣━ ≤5 subtasks for 60 min total; aim for 5–7
                ┗━ Verify the breakdown — is each one really independent?

0:35 ─ 0:55    EXECUTION LOOP (the per-task loop, ~5 min × ≤5 subtasks)
                ┣━ For each subtask:
                ┃    ┣━ Plan mode → confirm
                ┃    ┣━ Implement (smallest change that works)
                ┃    ┣━ Run tests / quality gates
                ┃    ┣━ Review diff
                ┃    ┗━ Commit (one task = one commit)
                ┗━ Ralph if stuck twice. Don't reason your way out.

0:55 ─ 1:00    REVIEW
                ┣━ How many subtasks landed?
                ┣━ Where did the agent rabbit-hole?
                ┗━ One thing you'd do differently next time
```

**Time math sanity-check**: 25 min of setup discipline + ~5 min × 5 subtasks (25 min) + 5 min review + slack = 60 min. The setup feels long; **that's the lesson**. Engineers who skip setup and dive straight into "code please" finish with 1–2 messy commits and a frustrated agent. Engineers who invest 25 min upfront finish with 5 clean ones and a working feature.

---

## Slide 4 — The 5–10 minute setup checklist

What goes into AGENTS.md (or `.cursorrules` / `.windsurfrules` / `.junie/guidelines.md` / equivalent) before any code:

```markdown
# AGENTS.md — <project name>

## What this is
<3 lines about the system, stack, where things live>

## How to run things
- Test:    <exact command>     ← run before declaring done
- Lint:    <exact command>
- Types:   <exact command>     (if applicable)
- Build:   <exact command>

## Conventions
- Errors: <what shape>
- Commits: <format — one task per commit>
- File layout: <only if non-obvious>

## Guardrails
- Never edit: <list>
- Always ask before: <destructive ops, schema changes, anything irreversible>

## Tools available
- <list of CLI tools, e.g. rg, jq, gh, your project's own CLI>
- <MCP servers configured, if any>

## Today's task
<one-sentence goal — yes, put it in AGENTS.md for this exercise>
```

**Time-saving tip**: ask the agent itself to draft AGENTS.md from a quick read of the repo. Then *you* edit it. 3 minutes vs 10.

**Tools/MCP setup ideas to install before tomorrow** (so attendees aren't blocked):
- `rg` (ripgrep) — for code search
- `gh` — GitHub CLI for issues/PRs
- `context7` MCP — for live library docs
- A test runner that's already configured
- Whatever your harness's "rules file" location is — confirm it loads

---

## Slide 5 — Execution rules (read out loud once before they start)

The five rules that keep the loop working when the agent gets confused.

1. **Plan mode for every subtask.** Yes, even the small ones. The 30 seconds you "save" by skipping costs you 5 minutes of cleanup.
2. **One subtask = one commit.** If you're tempted to bundle, your subtasks were too small. Commit anyway.
3. **The agent suggests; you decide.** Especially on architecture. Especially on dependencies. Don't accept "I'll add a new library" without asking why.
4. **Ralph if you've corrected twice on the same point.** Capture state, `/clear`, restate the goal cleanly, restart. The third correction is rarely the charm.
5. **Time-box each subtask at 5 min.** If a subtask is taking 10, either it was actually 2 subtasks, or the scope was wrong. Stop, revise the breakdown, restart.

> "If you find yourself writing a long corrective prompt, that's the signal to ralph instead."

---

## Slide 6 — What "success" looks like at 0:55

**Aim for 5 subtasks landed, each as a clean commit.** Beyond that:

| Outcome | What it means |
|---|---|
| **5+ commits, task done** | Best case — full execution under the discipline. You've felt what the loop is like at scale. |
| **5+ commits, not done** | Solid — the discipline worked, the task was just bigger than 60 min. The git log tells a clean story. |
| **2–4 commits, partial** | Common — the loop kicked in midway. Note where the friction was. |
| **0–1 commits, lots of code** | The discipline didn't stick. Look back: skipped plan mode? Subtasks too big? Skipped commits? |

**The real measure**: read your `git log --oneline` at the end. Each line should make sense to a colleague who walks up cold. *That's* what the discipline buys you.

---

## Slide 7 — Show-and-tell (5 min)

Round-robin, 30 seconds each — 8–10 attendees, then we wrap.

Three questions:
1. **What was your task?** (one sentence)
2. **How many subtasks landed?**
3. **Where did the discipline break down — or where did it save you?**

If the room is shy, ask **3 volunteers** with the most interesting outcomes — the "5 clean commits" person, the "rabbit-holed at minute 35" person, and the "agent surprised me" person. Quality over completeness.

---

## Pre-flight — tell attendees in the prereqs email

So they show up ready, not setup-shopping for the first 15 minutes:

- [ ] **Harness installed and authenticated**: Claude Code, Copilot agent mode, Cursor, Cline, Windsurf, Junie, or other — your choice
- [ ] **A repo you can write to** — ideally one you actually work on, on a fresh branch
- [ ] **A task in mind** — a real ticket, a known bug, a feature request you've been deferring
- [ ] **`rg`, `jq`, `gh` installed** if you can — they're force multipliers
- [ ] **Test command verified working** — run your tests once before the workshop so we don't debug your test runner during the exercise
- [ ] **Optional**: one MCP server installed (context7 is a good freebie)

If anyone is on a totally fresh setup, fall back to **a public OSS repo with an open issue** — pick one, do that. Same exercise.

---

## Facilitator notes (for me)

- **Walk the room during the setup phase**. Most attendees will skip AGENTS.md or stuff it with too much. Catch it early — 30 seconds of correction at minute 8 is worth 20 minutes saved at minute 40.
- **Watch for the "I'll just dive in" attendees** during plan mode. They'll be the ones with chaos at 0:35. Gently nudge them back to plan mode when you see code being typed before a plan exists.
- **Time announcements at 0:15, 0:25, 0:35, 0:55**. Keep the pacing visible.
- **Have a "stuck" backup task** ready — a small public OSS issue (your favorite repo) — for anyone whose setup falls apart.
- **For the MCP server task (option C)**: have a working scaffold ready as a fallback. MCP server boilerplate from scratch can eat 20 minutes; nobody wants to fail on that vs. on the actual interesting bit.

---

## Anti-patterns to call out during the wrap-up

If show-and-tell reveals these, name them — they're the most common failure modes and worth surfacing:

- **"I just told it what to do and it kind of worked"** → no plan, no subtasks, lots of code, hard to review. *Discipline didn't stick.*
- **"It kept fighting me on X"** → didn't ralph. Should have reset and re-seeded. Two corrections is the limit.
- **"My AGENTS.md was 200 lines"** → over-engineered upfront. Keep it 50 lines. The agent reads it every turn.
- **"I let it run and it did way more than I asked"** → no scope discipline; agent will *expand* if not constrained. Per-task scope rules are the brake.
- **"I didn't commit and now I can't roll back"** → broke the one-task-one-commit rule. Pay for it on the next task.

---

## Sources & references

- [Anthropic — Building effective agents](https://www.anthropic.com/engineering/building-effective-agents)
- [Anthropic — Claude Code best practices: plan mode](https://code.claude.com/docs/en/best-practices)
- [Plan Mode guide (2026)](https://www.claudedirectory.org/blog/claude-code-plan-mode-guide)
- *Internal*: `workshop-practices.md` — the per-task loop in detail (Slide 7)
- *Internal*: `workshop-tool-use.md` — the tool-use ladder (decide which rung per subtask)

---

## Decisions locked

- ✅ **Print a 2-page handout** with the 0:00–1:00 breakdown for every attendee
- ✅ **Hard-cap the 5-min per subtask rule** — the loop is the lesson, not the finish
- ✅ **Walk the room, take questions** rather than do the exercise myself
- ✅ **Put the AGENTS.md template on the slide** with a QR code linking to the public repo (github.com/jexp/agentic-engineering) for paste-ready access

## Still to do before tomorrow

- [ ] Pre-pick one MCP server scaffold (TypeScript + stdio transport) as a fallback for option C, so nobody fails on boilerplate
- [ ] Print the 2-page handout (one per attendee + ~5 spares)
- [ ] Confirm QR code generated and points to a stable URL on the public repo
