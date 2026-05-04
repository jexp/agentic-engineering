# Agentic Engineering — Workshop & Keynote

Materials for a 4-hour workshop and a 30-minute conference keynote on the move *from vibe coding to agentic engineering*.

By **Michael Hunger** ([@jexp](https://github.com/jexp), VP Product Innovation / AI at Neo4j).

---

## What's here

```
.
├── workshop/        # 4-hour workshop, ~16 section docs + outline
│   ├── workshop-outline.md          ← start here for the full running order
│   ├── workshop-intro.md
│   ├── workshop-exercise-1.md
│   ├── workshop-harnesses.md
│   ├── workshop-tool-use.md
│   ├── workshop-cost-tokens.md
│   ├── workshop-benchmarks.md
│   ├── workshop-practices.md
│   ├── workshop-own-experience.md
│   ├── workshop-mental-safety.md
│   ├── workshop-exercise-2.md
│   ├── workshop-resources.md
│   └── agentic-engineering-ideas.md (raw notes)
│
├── keynote/         # 30-min keynote drafts
│   ├── prompt.md        (original brief)
│   ├── vibecode-keynote-v1.md
│   ├── vibecode-keynote-v2.md
│   └── vibecode-keynote-v3.md
│
├── research/        # Source / reference material that fed the workshop
│   ├── coding-agents/                       ← per-tool deep dives + comparison tables
│   ├── context-engineering-mining.md        ← reusable bits from prior CE deck
│   ├── context-engineering-presentation.pdf ← prior CE deck (40 slides)
│   └── agent-hooks.md                       ← hooks comparison across harnesses
│
├── assets/          # Images, QR codes, etc.
│   └── qrcode-github-jexp-agentic-engineering.png
│
├── CLAUDE.md        # Repo memory file for Claude Code / agentic editors
├── progress.md      # Running log of what's been written and what's next
└── README.md        # This file
```

---

## Quick start

- Reading the **workshop**? Open [`workshop/workshop-outline.md`](./workshop/workshop-outline.md) — it's the master running order, points at every other workshop file, and includes timing + slide budgets.
- Reading the **keynote**? Open [`keynote/vibecode-keynote-v3.md`](./keynote/vibecode-keynote-v3.md) — current draft.
- Comparing **agentic coding tools**? Open [`research/coding-agents/README.md`](./research/coding-agents/README.md) — 16 per-tool deep dives + comparison tables for Claude Code, Codex, Cursor, Aider, Cline, Copilot agent mode, Junie, opencode, Goose, Crush, Pi, Gemini CLI, Antigravity, Windsurf, Devin, Kiro.

---

## What this argues

The short version (the long version is the keynote):

1. **Vibe coding (Karpathy, Feb 2025)** is real and useful — for prototypes, learning, throwaway tools.
2. **Agentic engineering** is the next phase for production work — and it brings the strong engineering disciplines back, not as overhead, but as the way agents stay useful.
3. **Good software design was never for the machine.** It was always for other developers who had to read, maintain, and extend the code. Now those developers include AI teammates that learned the craft from human-written code.
4. **The system you build around the model is the moat.** The model gets better every six months. The system is yours.

---

## License

Materials in this repo are released under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Use, adapt, share — please credit.

Code snippets within docs are released under MIT.

---

## Contact

- **Email**: michael@neo4j.com
- **GitHub**: [@jexp](https://github.com/jexp)
- **Talk to me about**: graphs + LLMs, agent memory, MCP, context engineering
