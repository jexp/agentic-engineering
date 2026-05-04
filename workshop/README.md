# Workshop — From Vibe Coding to Agentic Engineering

A 4-hour, hands-on workshop for **experienced engineers and team leads** who want to move from vibe coding to agentic engineering — not as hype, but as practice.

## What this workshop is for

The audience already knows how to code. Many have tried Copilot, Cursor, Claude Code, or similar — some with skepticism, most with mixed results. The workshop is designed to:

1. **Calibrate the room** on how the field actually got here (timeline, what's real, what isn't)
2. **Give a vendor-neutral mental model** of how agent harnesses work, what they cost, where they break
3. **Teach a working method** — AGENTS.md, plan mode, ralphing, the per-task loop, the tool-use ladder
4. **Run two hands-on exercises** so the practices land in muscle memory, not just on slides
5. **Open the harder conversation** — review fatigue, role changes, career questions — and leave room for Q&A

By the end, attendees should have shipped at least one personal tool, made real progress on a non-trivial task in their own codebase under the discipline, and have a Monday-morning action they want to try.

---

## Start here

📌 **[`workshop-outline.md`](./workshop-outline.md)** — the master running order. Every section, every block of timing, every hand-off line, and the slide budget per section live here. Read this first; everything else is detail.

🖨️ **[`exercise-2-handout.md`](./exercise-2-handout.md)** — 2-page printable handout with the 60-min schedule, AGENTS.md template, execution rules, success tiers, and the repo QR. Distribute one per attendee at the start of Exercise 2.

---

## The full agenda (~4 hours)

| Block | Doc | Time |
|---|---|---|
| 0. Welcome & hand-raisers | [`workshop-intro.md`](./workshop-intro.md) | 5 min |
| 1. Intro — From Vibe Coding to Agentic Engineering | [`workshop-intro.md`](./workshop-intro.md) | 30 min |
| 2. **Exercise 1** — Build the tool you wished existed | [`workshop-exercise-1.md`](./workshop-exercise-1.md) | 30 min |
| *Break* | — | 10 min |
| 3. Deep dive — Harnesses & tool use | [`workshop-harnesses.md`](./workshop-harnesses.md) + [`workshop-tool-use.md`](./workshop-tool-use.md) | 20 min |
| 4. Deep dive — Cost & token economics | [`workshop-cost-tokens.md`](./workshop-cost-tokens.md) | 10 min |
| 5. Deep dive — SWE benchmarks | [`workshop-benchmarks.md`](./workshop-benchmarks.md) | 5 min |
| 6. Deep dive — Practices | [`workshop-practices.md`](./workshop-practices.md) | 20 min |
| 7. Deep dive — Own-experience demos (live) | [`workshop-own-experience.md`](./workshop-own-experience.md) | 10 min |
| *Break* | — | 10 min |
| 8. **Exercise 2** — Real work, real discipline | [`workshop-exercise-2.md`](./workshop-exercise-2.md) | 60 min |
| 9. Mental load, roles & career (Q&A starter) | [`workshop-mental-safety.md`](./workshop-mental-safety.md) | 5–7 min |
| 10. Q&A + closing reflection | [`workshop-outline.md`](./workshop-outline.md) § Q&A | 18–20 min |
| 11. Resources / closing QR | [`workshop-resources.md`](./workshop-resources.md) | 5 min |

---


## Conventions used inside the section docs

- Each `workshop-<topic>.md` follows the same shape: **framing line → numbered slides with talking points → sources & references → open questions for the speaker**.
- Quotes tagged `[VERIFY]` need wording confirmation before they go on a slide.
- Edits pulled from prior decks are marked inline with `<!-- CE-EDIT #N -->` (from `../research/context-engineering-mining.md`) or `<!-- SIMON-EDIT #N -->` (from `../research/simon-mining.md`).

---

## Source / reference material

- **[`../research/coding-agents/`](../research/coding-agents/)** — 16 per-tool deep dives + comparison tables (Claude Code, Codex, Cursor, Aider, Cline, Copilot agent mode, Junie, opencode, Goose, Crush, Pi, Gemini CLI, Antigravity, Windsurf, Devin, Kiro). Cited from [`workshop-harnesses.md`](./workshop-harnesses.md).
- **[`../research/context-engineering-mining.md`](../research/context-engineering-mining.md)** — reusable bits from a prior context-engineering deck.
- **[`../research/simon-mining.md`](../research/simon-mining.md)** — Simon Willison's writing on agentic engineering, mapped to workshop sections.
- **[`../research/agent-hooks.md`](../research/agent-hooks.md)** — hooks comparison across harnesses.

---

## License

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — use, adapt, share, please credit.
