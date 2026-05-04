# Workshop — How Harnesses Actually Use Tools (the ladder)

**Block**: Deep dive — slot inside the harness/architecture section, ~5–7 min, 3 slides
**Position**: After harness anatomy (Slide 1) and before craft levers (Slide 3) — or as Slide 3a if room
**Goal**: give the room a *layered* mental model of the agent's hands. From "Read this file" to "talk to my Snowflake warehouse via MCP" is a 6-rung ladder, and each rung has a different cost/capability/fragility tradeoff. Most teams overshoot.

---

## Framing line

> "The model has a Swiss-army knife of *built-in* tools, a 50-year-old toolbox of *Linux* tools, and a universe of *external* tools through MCP. Picking the right rung of that ladder is half of being good at agentic engineering — and most people overshoot."

---

## Slide 1 — The tool-use ladder

Six rungs, from cheapest/most-built-in to most-external/most-capable.

```
                                           Capability ↑
                                           Cost & Friction ↑
       ┌─────────────────────────────────┐
   6   │  MCP servers / Plugins           │  Snowflake, GitHub, Sentry, Linear, Neo4j…
       ├─────────────────────────────────┤
   5   │  Skills / Slash commands         │  /pr-review, /audit-agents-md, /draft-release-note
       ├─────────────────────────────────┤
   4   │  REST APIs via curl              │  curl -s api.openalex.org/works?…
       ├─────────────────────────────────┤
   3   │  Code snippets (python -c, node) │  python -c "import json,sys;…"
       ├─────────────────────────────────┤
   2   │  Linux CLI                       │  ls, find, grep, sed, awk, jq, git, head, sort, uniq
       ├─────────────────────────────────┤
   1   │  Built-in tools                  │  Read · Edit · Write · Grep · Glob · Bash · WebFetch · WebSearch
       └─────────────────────────────────┘
                                           ↓ Reusability  ↓
                                           ↓ Latency      ↓
```

The model picks rungs *constantly*. Your job is to make the cheap rungs comfortable and only push capability outward when the cheap rungs run out.

---

## Slide 2 — What each rung is for (and what it costs)

| Rung | What it is | Capability | Effort to add | Token cost | Latency | Fragility |
|---|---|---|---|---|---|---|
| **1. Built-in** | Read, Edit, Write, Grep, Glob, Bash, WebFetch, WebSearch | Files, search, shell, web | Zero — ships with the harness | Lowest (schemas cached) | <100ms (local) | None — vendor maintains |
| **2. Linux CLI** | `ls find grep sed awk jq git head/tail sort uniq xargs tree wc` | The full UNIX algebra: filter, transform, navigate, glue | Zero — install once | Low (run via Bash) | <100ms (local) | Stable — these tools haven't changed in 30 years |
| **3. Code snippets** | `python -c "..."`, `node -e "..."`, awk/perl one-liners, throwaway scripts | Anything programmable: parse, classify, transform, restructure | Negligible — model writes them inline | Modest (model has to *generate* the snippet) | <500ms | Snippet has a bug? Model retries; usually self-heals |
| **4. REST APIs** | `curl -s -H 'Authorization: …' https://api…` | Anything with an HTTP API and a key | Find docs, set env var, write the curl | Modest input; verbose JSON output → token-hungry | 100ms – seconds (network) | Auth expires, rate limits, schema changes |
| **5. Skills** | Slash command + prompt bundle + (optional) helper scripts | Captured *expertise* and procedures | Author once: `~/.claude/skills/foo/SKILL.md` + scripts | Low marginal — replaces a paragraph with a one-line invocation | Local | Stable if you maintain them |
| **6. MCP servers / plugins** | External servers exposing typed tools + resources | Whole platforms: Snowflake, GitHub, Sentry, Linear, Atlassian, Neo4j, browsers, computer use | Install + auth + config | Tool schemas can be heavy (deferred loading helps); responses can balloon | Network-dependent; local stdio MCP is fast | Most fragile — auth, server crashes, schema changes, dependency hell |

### Key implication: each step up the ladder buys capability and *spends* something else.

- **Rung 1→2**: nothing lost. Linux CLI is free leverage; the model is fluent in it.
- **Rung 2→3**: spending generation tokens to make a tool. Worth it for one-offs.
- **Rung 3→4**: spending *output token volume* (JSON responses) and adding network latency + auth fragility.
- **Rung 4→5**: spending *authoring time* but recovering it 10× through reuse.
- **Rung 5→6**: biggest jump in capability + biggest jump in cost, latency, and ops surface.

---

## Slide 3 — When to climb the ladder

The practical heuristic the room can take home.

**Start at rung 1. Climb only when the current rung doesn't reach.**

```
  Question                              Answer        →  Rung
  ─────────────────────────────────────────────────────────────
  Read/find/edit a file?                yes           →  1 — built-in
  Filter, transform, glue strings?      yes           →  2 — Linux CLI
  Parse JSON, do non-trivial logic?     yes           →  3 — python -c / node -e
  Talk to an HTTP API once?             yes           →  4 — curl
  Doing the same prompt 3+ times?       yes           →  5 — skill
  Crossing platform / needs auth?       yes           →  6 — MCP
  External system used by whole team?   yes           →  6 — MCP (shared)
```

### Rules of thumb worth saying out loud

1. **Bash is the universal escape hatch.** Every other tool is a wrapper or convenience. If you can't decide, Bash.
2. **`jq` and `rg` (ripgrep) are force multipliers.** Make sure they're installed everywhere your agents run.
3. **Don't reach for MCP when Bash would do.** A `curl | jq` pipeline ships in 2 minutes; the equivalent MCP server takes a day. For one-off lookups, the pipeline wins.
4. **Skill the third repetition.** First time: just do it. Second time: note it. Third time: skill it.
5. **MCP for *platforms*, skills for *procedures*.** A Snowflake MCP server lets the agent *talk to* Snowflake; a skill captures *how your team uses* Snowflake. They're complementary, not alternatives.
6. **Code snippets are throwaway.** Don't ask the agent to write a "utility script" you'll keep. Ask it to write a one-liner — or skill it if it'll repeat.
7. **Watch the token cost of verbose APIs.** REST responses are JSON-fat. Pipe through `jq` to extract only what's needed *before* it lands in the model's context.

---

## Slide 4 — Anti-patterns to call out

Five common mistakes engineers make at each rung.

| Anti-pattern | What's actually happening | Fix |
|---|---|---|
| **MCP-everything** | Reaching for MCP when `curl` would do | Use the cheapest rung that works |
| **One-off scripts that should be skills** | Generating "a helpful utility" inline that's secretly a recurring need | Promote to a skill the second time it appears |
| **Skill bloat** | 50-line slash commands for things that should be hooks (deterministic) | Hooks for "must always run"; skills for "expertise the model invokes" |
| **Re-implementing UNIX** | Asking the model to write a Python sort/dedupe/group-by | `sort -u`, `uniq -c`, `awk` — the model knows them; nudge it |
| **Reading whole files when grep would do** | "Read this 5000-line file then summarize" | `rg "needle" file.py` then read the matching range |
| **Ignoring tool output volume** | A `curl` returns 2MB of JSON; the model has to read all of it | Pipe through `jq -r '.results[] | {id, title}'` first |

---

## Slide 5 (optional) — Worked example: same task across the ladder

If time, show this concretely. **"Find which PRs touched our auth code in the last week."**

| Rung | How you'd do it |
|---|---|
| **1 — Built-in** | `Bash: git log --since=1.week.ago --grep=auth --name-only` |
| **2 — Linux CLI** | `git log … | grep -A5 'auth' | sort -u | head -20` |
| **3 — Snippet** | `python -c "import subprocess,json; … ; print(json.dumps(…))"` for grouping |
| **4 — REST API** | `curl -H 'Authorization: …' "api.github.com/repos/.../pulls?since=…" | jq '.[] | select(.title | test("auth"))'` |
| **5 — Skill** | `/auth-touch-week` — wraps the above with the right repo, defaults, output format |
| **6 — MCP** | GitHub MCP — agent calls `list_pull_requests(repo, since)` typed; results come back structured |

**The lesson**: the *same task* gets cheaper to invoke and harder to maintain as you climb. Pick the rung that matches *how often you'll do this* and *who else needs it*.

---

## Where this section goes in the deck

**Lean: insert as Slide 2a inside `workshop-harnesses.md`**, between the landscape (Slide 2) and craft levers (Slide 3). Sets up the "tools, hooks, skills, MCP" subsection on craft-levers Slide 3 with a much more concrete frame.

Alternative: collapse to 1 slide (the ladder + the heuristic) and reference this doc as a handout. The full 5 slides only if the room engages with the ladder visual on Slide 1.

---

## Sources & references

- [Anthropic — Claude Code best practices: tool usage](https://code.claude.com/docs/en/best-practices)
- [Anthropic — Building effective agents](https://www.anthropic.com/engineering/building-effective-agents) — the canonical "start simple, climb when needed" essay
- [MCP specification](https://modelcontextprotocol.io)
- [bradAGI/awesome-cli-coding-agents](https://github.com/bradAGI/awesome-cli-coding-agents) — see how each harness exposes tools
- *Internal*: `~/d/llm/claude-code/tools.md` — full CC tool inventory with deferred-loading semantics
- *Internal*: user's RTK + headroom for token-efficient versions of common Linux tools

---

## Open questions for me to decide before tomorrow

- [ ] Slides 1–4 or just Slides 1+3 (ladder + heuristic)? **Lean: 1+3, with 2 (cost matrix) as a handout. Slide 4 is good if time, Slide 5 (worked example) is the demo move.**
- [ ] Demo Slide 5 live with my own terminal? **Lean: yes — running the same query 3 ways across 60 seconds is the "this is real" moment.**
- [ ] Should the cost matrix (Slide 2) include actual token numbers or stay qualitative? **Lean: qualitative — concrete numbers will be wrong by next month and the relative ordering is what matters.**
- [ ] Mention `rg` / `bfs` / `fd` explicitly? **Lean: yes, in the rules-of-thumb. They're force multipliers most engineers don't have installed.**
