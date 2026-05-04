# Exercise 2 — Real Work, Real Discipline (60 min)

## The challenge

Pick something **non-trivial** from your own world. Three rules:

1. **Real ticket-shape work** — something you'd file as an issue if you weren't doing it now
2. **Multi-step** — at least 3–5 logical subtasks
3. **Verifiable** — there's a test, an output, or a behaviour you can check

The agent will go off the rails on this one. *That's the lesson.* Use the discipline below to keep it on track.

---

## Pick a task archetype (≤2 min — don't agonize)

| | Shape | "Done" looks like |
|---|---|---|
| **A** | **Nasty bug** — subtle, multi-file, possibly intermittent | Root cause identified, fix in, regression test added, all tests green |
| **B** | **New feature** — small but real, on the backlog | Feature works end-to-end, has a test, doesn't break what was there |
| **C** | **MCP server / extension on a surface** — pick a surface you own (orchestration, DB, admin, infra), expose 2–3 useful tools | MCP server runs, agent calls at least one tool successfully, README explains install |
| **D** | **Cross-language port** — re-implement existing functionality in a language you don't normally use | It runs, produces right output for one input, you understand ≥50% of the code |

---

## The 60-minute breakdown

```
0:00 ─ 0:05    Pick task. Open a fresh repo / branch.
0:05 ─ 0:15    SETUP — AGENTS.md, tools, environment
0:15 ─ 0:25    PLAN MODE on the chosen task
                 ┣━ Goal in one sentence
                 ┣━ Let the agent investigate — read code, ask questions
                 ┣━ Resolve clarifying questions BEFORE coding
                 ┗━ Output: a 5–10 step plan with real symbols
0:25 ─ 0:35    TASK BREAKDOWN — agent does it, you verify
                 ┣━ "Break the plan into independent subtasks of ≤5 min each"
                 ┣━ Each subtask: scope · acceptance criteria · files involved
                 ┗━ Aim for 5–7 subtasks for the hour
0:35 ─ 0:55    EXECUTION LOOP (≤5 min × ≤5 subtasks)
                 ┣━ For each subtask:
                 ┃    Plan mode → confirm → implement (smallest change)
                 ┃    → run tests / quality gates → review diff → commit
                 ┗━ Ralph if stuck twice. Don't reason your way out.
0:55 ─ 1:00    REVIEW
                 How many subtasks landed?  Where did the agent rabbit-hole?
                 One thing you'd do differently next time?
```

---

## AGENTS.md starter (paste-ready)

```markdown
# AGENTS.md — <project name>

## What this is
<3 lines: the system, the stack, where the entry points live>

## How to run things
- Test:    <exact command>     ← run before declaring done
- Lint:    <exact command>
- Types:   <exact command>     (if applicable)
- Build:   <exact command>

## Conventions
- Errors: <what shape>
- Commits: conventional, one task per commit
- File layout: <only if non-obvious>

## Guardrails
- Never edit: <list>
- Always ask before: destructive ops, schema changes, anything irreversible

## Tools available
- <CLI tools: rg, jq, gh, project's own CLI>
- <MCP servers configured, if any>

## Today's task
<one-sentence goal>

# Reminder: always run tests, ask before destructive ops.
```

> *Time-saving tip*: ask the agent to draft AGENTS.md from a quick repo read, then *you* edit. 3 min vs 10.

---

## 5 execution rules

1. **Plan mode for every subtask.** Even the small ones. The 30 sec you "save" costs 5 min of cleanup.
2. **One subtask = one commit.** Tempted to bundle? Your subtasks were too small. Commit anyway.
3. **The agent suggests; you decide.** Especially on architecture and dependencies.
4. **Ralph if you've corrected twice on the same point.** `/clear`, restate the goal cleanly, restart. The third correction is rarely the charm.
5. **Time-box each subtask at 5 min.** If a subtask is taking 10, the scope was wrong. Stop, revise the breakdown, restart.

---

## What success looks like at 0:55

| Outcome | What it means |
|---|---|
| **5+ commits, task done** | Best case — full execution under the discipline |
| **5+ commits, not done** | Solid — the discipline worked, the task was just bigger than 60 min |
| **2–4 commits, partial** | Common — the loop kicked in midway |
| **0–1 commits, lots of code** | Discipline didn't stick. Look back: skipped plan mode? Subtasks too big? |

> The real measure: read your `git log --oneline` — each line should make sense to a colleague who walks up cold.

---

## Show-and-tell (last 5 min)

Three questions, 30 sec each:
1. What was your task?
2. How many subtasks landed?
3. Where did the discipline break down — or save you?

---

## Workshop materials & follow-up

**github.com/jexp/agentic-engineering**

![QR — github.com/jexp/agentic-engineering](../assets/qrcode-github-jexp-agentic-engineering.png)

*Scan to access all workshop docs, the AGENTS.md template, the tool-use ladder, the per-task loop reference, and the resources list.*
