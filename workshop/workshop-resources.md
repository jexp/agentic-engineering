# Workshop — Deep Dive Resources

**Purpose**: closing slide(s) of the deep-dive block + handout. Give attendees a curated, opinionated reading/install list so they can keep going Monday morning.
**Format**: probably 1 slide of QR codes + this doc as a handout (PDF or shared link).
**Time on the slide**: 60–90 seconds, point at the QR, say "everything's here, including this slide as a doc."

---

## Framing line

> "The field moves weekly. These are the sources I actually keep up with. If you read three things from this list before next month, pick one from each section: practitioner, craftsperson, vendor."

---

## A. Practitioners writing weekly (the ones to follow)

The signal-to-noise filter for everything else.

- **Simon Willison** — [simonwillison.net](https://simonwillison.net) — daily blog, the most thoughtful and prolific practitioner. Tag worth bookmarking: [simonwillison.net/tags/agentic-engineering/](https://simonwillison.net/tags/agentic-engineering/). His TIL stream is gold for picking up small techniques.
- **Addy Osmani** (Google) — [addyo.substack.com](https://addyo.substack.com) — sharpest writing on spec-driven development, the "factory model," and why "vibe coding" is a suitcase term for production work.
- **Shrivu Shankar** — [blog.sshh.io](https://blog.sshh.io) — *How I Use Every Claude Code Feature*; clear, advanced, no hype.
- **Steve Yegge** — episodic but excellent on the cognitive-load shift and the "we are not ready" thread.
- **Geoffrey Huntley** — [ghuntley.com](https://ghuntley.com) — coined "ralphing"; opinions on harness design.
- **Gergely Orosz** — *The Pragmatic Engineer* — industry-trend signal, broader than just AI.
- **Ethan Mollick** — *One Useful Thing* (substack) — for the broader AI context, well-calibrated.

## B. Craftspeople with a long pedigree (now writing about AI)

Read these for the *durability* perspective. They've seen this rodeo before.

- **Kent Beck** — Substack. "Augmented coding," tests as superpower, the "unpredictable genie" framing.
- **Kevlin Henney** — talks and essays. Tests as specifications; quality skepticism as engineering discipline. His [97 Things Every Programmer Should Know](https://www.oreilly.com/library/view/97-things-every/9780596809515/) collection is still the best short-form craft anthology.
- **Grady Booch** — interviews and X posts on the "third golden age" + the Amodei pushback.
- **Martin Fowler** — [martinfowler.com](https://martinfowler.com) — slower cadence, very high signal. The [legacy modernization with GenAI](https://martinfowler.com/articles/legacy-modernization-gen-ai.html) piece is essential.
- **Dan North** — [dannorth.net](https://dannorth.net) — Deliberate Discovery, Replaceable Component Architecture. No detailed AI piece yet — opportunity for someone to apply the ideas.
- **Andrej Karpathy** — X / talks. The Feb 2025 vibe-coding tweet; his early-2026 retirement of the term for serious work.

## C. Books worth (re-)reading in this era

Old books, suddenly more relevant. These are the *durable* artifacts; the AI-specific books will date in a year.

- **Kent Beck** — *Test-Driven Development: By Example* — the safety net for everything that follows
- **Martin Fowler** — *Refactoring* (2nd ed.) — the move set for steering an agent's output
- **Kevlin Henney (ed.)** — *97 Things Every Programmer Should Know* — short-form craft wisdom
- **Andy Hunt & Dave Thomas** — *The Pragmatic Programmer* (20th anniversary ed.) — still the best onboarding book
- **Philip G. Armour** — *The Laws of Software Process* — *"software is a knowledge medium"*; the philosophical backbone
- **Christopher Alexander** — *A Pattern Language* / *The Timeless Way of Building* — for taste, not technique
- **Eric Evans** — *Domain-Driven Design* — making the implicit explicit; gold for AGENTS.md and spec work
- **Gerald Weinberg** — *The Psychology of Computer Programming* — for the mentoring frame

## D. Anthropic / Claude Code official

- [Claude Code docs](https://code.claude.com/docs) — keep this open in a tab
- [Claude Code best practices](https://code.claude.com/docs/en/best-practices) — the canonical CLAUDE.md / hooks / sub-agents reference
- [Anthropic engineering blog](https://www.anthropic.com/engineering) — the "Building effective agents" post is essential
- [MCP specification](https://modelcontextprotocol.io) — and the [official server registry](https://github.com/modelcontextprotocol/servers)
- [Anthropic cookbook](https://github.com/anthropics/anthropic-cookbook) — patterns and recipes

## E. Other harnesses

- **Cursor** — [cursor.com/docs](https://cursor.com/docs); blog post on the [Codex-model harness](https://cursor.com/blog/codex-model-harness)
- **Codex CLI** — OpenAI docs + the Agents SDK
- **opencode** — [opencode.ai](https://opencode.ai) — open-source, provider-agnostic, Go
- **Aider** — [aider.chat](https://aider.chat) — git-native, repo-map context strategy
- **Cline / Roo** — VS Code agents (open source)
- **Windsurf** — Cascade agent
- **Goose / Pi / Crush** — niche but worth knowing

## F. Curated directories & comparisons

- [bradAGI/awesome-cli-coding-agents](https://github.com/bradAGI/awesome-cli-coding-agents) — comprehensive directory of CLI harnesses
- [artificialanalysis.ai/agents/coding](https://artificialanalysis.ai/agents/coding) — coding-agent leaderboard, updated regularly
- [thoughts.jock.pl harness comparison (2026)](https://thoughts.jock.pl/p/ai-coding-harness-agents-2026)
- [AkitaOnRails — AI Agents: which is best? (Jan 2026)](https://akitaonrails.com/en/2026/01/24/ai-agents-which-is-best-opencode-crush-claude-code-codex-copilot-cursor-windsurf-antigravity/)
- [claude.md](https://claude.md) — community CLAUDE.md examples

## G. Specific deep-dive references (for the topics in this section)

- [SmartScope — Claude Code advanced practices: hooks, subagents, context (2026)](https://smartscope.blog/en/generative-ai/claude/claude-code-best-practices-advanced-2026/)
- [Plan Mode guide (when & how)](https://www.claudedirectory.org/blog/claude-code-plan-mode-guide)
- [Mustafa Morbel — Taming Claude Code: CLAUDE.md & Hooks](https://medium.com/becoming-for-better/taming-claude-code-a-guide-to-claude-md-and-hooks-ed059879991c)
- [augmentcode.com — How to write good AGENTS.md files](https://www.augmentcode.com/blog/how-to-write-good-agents-dot-md-files)
- [Datacamp — Claude Code best practices tutorial](https://www.datacamp.com/tutorial/claude-code-best-practices)

## H. Talks, podcasts, videos

- **Simon Willison on Lenny's Podcast** — *An AI State of the Union* — the keynote lit a lot of this. [lennysnewsletter.com/p/an-ai-state-of-the-union](https://www.lennysnewsletter.com/p/an-ai-state-of-the-union)
- **Latent Space** podcast (swyx + Alessio) — interviews with most of the harness builders
- **AI Engineer** conference talks (YouTube) — heaviest signal-to-noise of any AI conf
- **The Pragmatic Engineer** podcast on AI tooling — practitioner perspective
- **Boris Cherny on Claude Code** — search for the podcast appearance; design philosophy of CC

## I. MCP servers worth installing first

Pick 3–5; they compound. *(Many require auth — check before tomorrow.)*

- **context7** — live, version-aware library docs in your harness; replaces "go google the docs"
- **neo4j MCP / mcp-neo4j-graphrag / mcp-toolbox** — graph queries, GraphRAG, multi-DB toolbox
- **GitHub MCP** — issues, PRs, reviews, checks
- **Filesystem MCP** — controlled FS access from external tools
- **Browser / Playwright MCP** — for any web interaction
- **Sentry, Linear, Slack, Atlassian MCPs** — depending on stack
- **codebase-memory-mcp** — graph-based agent memory ([deusdata.github.io/codebase-memory-mcp](https://deusdata.github.io/codebase-memory-mcp/))

## J. Communities & places to lurk

- [agentskills.ai](https://agentskills.ai) — skills sharing community
- [Anthropic Discord / forum](https://www.anthropic.com/community)
- r/ClaudeAI, r/LocalLLaMA — for the LLM landscape
- HackerNews — the canonical first-place to see new harnesses
- X — follow the practitioners in section A; resist everyone else

<!-- CE-EDIT #14 (from context-engineering-presentation slide 40): cross-referenced items from the original CE deck resources list -->
## J2. Context engineering canon (added from the existing CE deck)

The body of work that named "context engineering" and is worth knowing as background:

- **[Dex Horthy — 12-Factor Agents](https://github.com/humanlayer/12-factor-agents)** — the original framing that crystallized the term
- **[Lance Martin (LangChain) — Context Engineering presentation + podcast](https://rlancemartin.github.io/2025/06/23/context_engineering/)** — practitioner-grade write-up
- **[LangChain — *Communication is all you need*](https://blog.langchain.com/communication-is-all-you-need/)** — the "agent failures are communication failures" frame
- **[Jeff Huber (Chroma) — *RAG is Dead, Context Engineering is King*](https://www.chroma.research/)** [VERIFY exact URL]
- **[Chroma — Context Rot research](https://research.trychroma.com/context-rot)**
- **[Drew Breunig — *How Long Contexts Fail (and How to Fix Them)*](https://www.dbreunig.com/2025/06/22/how-contexts-fail-and-how-to-fix-them.html)** — the 5 named failure modes used in workshop-practices.md Slide 2
- **[Foundation Capital — *Context Graphs: AI's trillion-dollar opportunity*](https://foundationcapital.com/ideas/context-graphs-ais-trillion-dollar-opportunity/)**
- **[Beyond Prompts: Learning from Human Communication for Enhanced AI Intent Alignment (paper)](https://arxiv.org/)** [VERIFY exact arXiv ID]
- **[The Prompt Pyramid — A Better Way to Structure Complex Tasks for GPT](https://medium.com/)** [VERIFY exact URL]
- **[Jason Liu — Context Engineering Series](https://jxnl.co/)** [VERIFY exact URL]

## K. Research / academic

- [arXiv — agentic coding taxonomy paper (2025)](https://arxiv.org/abs/2502.11371) — vibe / agentic distinction with 20 use cases
- BCG, Forrester, Turing College reports on AI dev productivity (find via search; they're regularly updated)
- The IBM "humans aren't ready for this much software" thread — Sau Sheong's writing is the cleanest source

---

## Suggested QR-slide layout

One slide, four QR codes (or six max — more is unreadable):

| QR | Where it points |
|---|---|
| 1 | **github.com/jexp/agentic-engineering** — canonical repo with all workshop & resource materials. QR ready: `assets/qrcode-github-jexp-agentic-engineering.png` |
| 2 | Anthropic CC best practices |
| 3 | Simon Willison's agentic-engineering tag |
| 4 | bradAGI/awesome-cli-coding-agents |

Optional 5th and 6th:
| 5 | Your own GitHub / hone repo |
| 6 | The workshop's pre-flight checklist (when written) |

Closing line on the slide:
> "Pick one from each section. The field moves weekly; depth on a few sources beats breadth on all of them."

---

## Open questions

- [ ] Which 4 QR codes go on the actual slide? **Lean: this doc + CC best practices + Simon's tag + the awesome-cli-coding-agents directory.**
- [ ] Do I host this resources doc somewhere durable (gist? own site?) before the workshop, so the QR is stable?
- [ ] Add my contact / Mastodon / X handle to the slide? Probably yes — small, bottom of slide.
