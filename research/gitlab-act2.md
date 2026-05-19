# GitLab Act 2 — Research Notes
_Researched 2026-05-18_

## The Announcement (May 11, 2026)

**Source:** https://about.gitlab.com/blog/gitlab-act-2/  
**CEO:** Bill Staples  
**Simon Willison commentary:** https://simonwillison.net/2026/May/11/gitlab-act-2/

### Framing
Explicitly positioned as "not an AI optimization or cost cutting exercise" — instead a "repositioning for the agentic era of software development."

### Key Quotes

> "The agentic era affords GitLab the largest opportunity in our history as a company, and we're making the structural and strategic decisions to meet it."  
> — Bill Staples

> "Software will be built by machines, directed by people. AI is the substrate on which future software gets built."  
> — Bill Staples [VERIFY exact wording against official blog]

> "In some cases AI can augment and accelerate what team members have been doing, in other places we need to expand certain roles to go faster."

> "The constraint was the cost and time of producing and managing it. That constraint is collapsing. As the cost of producing software collapses, demand for it will expand."  
> — [Simon's summary of GitLab's strategic position, simonwillison.net]

### Specific Numbers

| Change | Detail |
|---|---|
| Employees | ~2,500–2,600 across 65+ countries |
| Country presence | Reduce by up to **30%** (from ~60–65 countries) |
| Management layers | Remove **up to 3 layers** in some functions |
| R&D teams | Reorganize into **~60 smaller, empowered teams** — "nearly doubling the number of independent teams" |
| Timeline | Finalize by **June 1, 2026**; financial impact June 2 earnings call |
| Stock reaction | Fell **8%+** after-hours |
| FY2027 revenue guidance | $1.099–1.118B (15–17% growth, down from 26%) |

### Five Strategic "Architectural Bets"
1. Machine-scale infrastructure (Git redesign for agent workloads)
2. Orchestration across the full software lifecycle
3. Context as competitive advantage (connected data model)
4. Governance built into the core platform
5. One platform, three modes: **human-owned / agent-assisted / agent-autonomous**

### Business Model Shift
Per-seat licensing → usage-based credits ($1/credit). Value metric changes from "human seats" to "workflow throughput."

### New Operating Principles (replacing CREDIT values)
- Speed with Quality
- Ownership Mindset
- Customer Outcomes

### Simon Willison's Caveats
- GitLab has financial incentive to frame this positively — stock declined ~$52→~$26 over the year
- "Vast majority of savings reinvested" is unquantified (headcount number comes June 2 earnings call)
- Worth noting if challenged in Q&A

---

## GitLab Engineering Handbook — AI-Assisted Development Playbook

**Source:** https://handbook.gitlab.com/handbook/engineering/workflow/ai-assisted-development/  
**Last updated:** March 27, 2026

### Five Core Principles (from teams shipping production code with agents)

1. **"Failing test before every feature"** — Never give an agent a task without a failing test. The test defines "done" for the agent.
2. **"Fix the environment, not the prompt"** — When an agent produces bad code, add a lint rule, a test, or a doc. Environment fixes persist across sessions; prompts don't.
3. **"Constraints are multipliers"** — One CI gate catches more bugs than a thousand lines of prompt instructions. Encode rules in CI, not in natural language.
4. **"Repo is the single source of truth"** — Architecture decisions, quality standards, and coding conventions belong in the repo where agents (and humans) can read them.
5. **"Ask the agent to challenge you"** — Agents are agreeable by default. Explicitly instruct them to find flaws in your plan.

### Five Autonomy Levels

| Level | Name | Human does | Agent does |
|---|---|---|---|
| 1 | Baseline | Writes everything | Autocomplete suggestions |
| 2 | Pair | Designs and reviews | Writes code |
| 3 | Conductor | Steers in tight feedback loop | Executes single task end-to-end |
| 4 | Orchestrator | Manages multiple async agents | Runs parallel workstreams |
| 5 | Harness | Sets architecture and quality bar | Everything else |

> "Skipping to level 4 or 5 without the right infrastructure produces unreliable output and amplifies technical debt."

### The Harness — Three Components
1. **Constraints** — enforce in CI, not in prompts. "Prompts are suggestions. CI is a gate."
2. **Context** — three-layer hierarchy: `~/.claude/CLAUDE.md` (global) → `AGENTS.md` at repo root (project) → `AGENTS.md` in subdirectories (module)
3. **Garbage collection** — automated maintenance: stale TODOs, coverage drift, doc freshness, dependency updates — including a "Ralph pattern" (doc convergence agent loop running weekly)

### Maturity Grid
Four dimensions, each rated 0–3: CI and Constraints, Context and Docs, Testing Depth, Review Practice. Must reach Level 2 across all four before moving past Baseline autonomy.

### Internal GitLab Examples
- **Knowledge Graph Orbit** — 135K-line Rust codebase, 95% AI-generated, 4 engineers, 259 MRs, 2 weeks. CI + AGENTS.md + architecture docs in place from day one.
- **IAM project** — Go service: AGENTS.md, golden fixture tests, MR review instructions, test count guard, CODEOWNERS
- **Monolith auth harness** — Ruby monolith: module-level AGENTS.md, domain-scoped MR review instructions, characterization tests

### GitLab Duo Agent Platform
- GA January 2026 (with GitLab 18.8)
- Default model: Claude (Anthropic)
- 7 AI agents across the software lifecycle (Planner, Security Analyst, etc.)
- Custom agents via YAML-defined "Flows"
- Governance framing: "Claude's suggestions flow through the same merge request process, the same approval rules, the same security scanning, and the same audit trail as every other change."

---

## For Keynote Use

**Slide-ready quotes:**
- "Software will be built by machines, directed by people." — Bill Staples [VERIFY]
- "Constraints are multipliers" — GitLab Handbook
- "Prompts are suggestions. CI is a gate." — GitLab Handbook

**Most compelling data:** 3 management layers / 30% country exits / doubling to ~60 teams — concrete, verifiable, dramatic.

**Best keynote angle:** GitLab is the first major DevOps platform to publicly restructure its *org* around the agentic era — not just its product. The handbook is the recipe; Act 2 is the proof they're eating their own cooking.

**Caveat for slide:** Headcount reduction percentage TBD until June 2 earnings call. Use "up to 30% of countries" rather than headcount %.

**Sources:**
- https://about.gitlab.com/blog/gitlab-act-2/
- https://handbook.gitlab.com/handbook/engineering/workflow/ai-assisted-development/
- https://simonwillison.net/2026/May/11/gitlab-act-2/
- https://thenextweb.com/news/gitlab-layoffs-agentic-era-devops-ai
- https://about.gitlab.com/blog/gitlab-and-anthropic-governed-ai-for-enterprise-development/
