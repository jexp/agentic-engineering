# Kiro

**Vendor / origin**: AWS (Amazon). Launched in public preview July 2025 at kiro.dev; presented at AWS re:Invent 2025 (session DVT209). Built on **Code OSS** (the open-source base of VS Code), so it's effectively a VS Code fork in the same lineage as Cursor, Windsurf, and Antigravity. Stack is TypeScript on the IDE side; agent backend runs on AWS [VERIFY]. Note: there are unrelated products called "Kiro" — this entry covers the AWS coding IDE only.
**License / source**: Closed source IDE; some assets and examples open at https://github.com/kirodotdev/Kiro. Code OSS base is MIT.
**Surface**: Desktop IDE (macOS/Linux/Windows) plus a CLI. Marketed as "agentic IDE + CLI" rather than an AWS-branded service.

## Install & access
Download installers from https://kiro.dev/. Sign in with an AWS Builder ID or AWS account. Open VSX is the marketplace, so most VS Code extensions and your settings/themes import directly through the onboarding flow. CLI installs as a separate binary (`kiro` command) [VERIFY package name]. Free tier with 50 credits; Pro $20/mo (1,000 credits); Pro+ $40/mo (2,000); Power $200/mo (10,000). Credit cost varies by model and tool use — Spec mode is cheaper than Vibe mode per task because plans are reused.

## Core architecture
Kiro's central bet is **spec-driven development**: before code is written, the agent produces three artifacts — a `requirements.md` (user stories with acceptance criteria), a `design.md` (system/architecture), and a `tasks.md` (ordered implementation list). The agent loop then implements tasks one at a time against the spec, marking them complete. Underneath, it's a standard tool-using loop (read/edit/run/search) with a frontier model — Claude Sonnet 4.x and 3.7 are the documented backends as of 2026 [VERIFY]. Specs persist in `.kiro/specs/<feature>/` so the artifact set survives across sessions and serves as the agent's long-term memory.

## Extension model
- **Steering files** — `.kiro/steering/*.md` provide global or scoped rules, conventions, and tool preferences. Equivalent to AGENTS.md/CLAUDE.md.
- **Specs** — versioned, editable; the user can amend `requirements.md` mid-flight and the agent re-plans `tasks.md`.
- **Agent Hooks** — event-driven actions tied to file create/save/delete or manual triggers (e.g. "on save of any *.ts file, run typecheck and fix"). Hooks are themselves authored by describing them in natural language; Kiro generates the hook config.
- **MCP servers** — first-class support, configured per project [VERIFY].
- **Open VSX extensions** — VS Code-style plugin compatibility.

## Interaction model
Two primary modes: **Vibe** (free-form chat-driven coding, like Cursor's Composer) and **Spec** (the disciplined three-doc workflow). The IDE shows a familiar VS Code layout with an agent panel; spec docs render as Markdown previews you can edit. Diffs are reviewed inline in the editor. Hooks fire in the background and surface as side activity. Kiro touches files directly with checkpoints; rollback is per-task. The CLI mirrors the Spec workflow for headless use.

## How it works (the actual loop)
1. User describes a feature. 2. Kiro generates `requirements.md` and asks for confirmation. 3. It writes `design.md` (data flows, APIs, components) — user edits. 4. It produces `tasks.md` — an ordered checklist with acceptance criteria. 5. For each task: load relevant files + steering + spec context → call model → parse tool calls → edit/run/test → check off task. 6. Hooks fire on file events between agent turns. The deliberate slowdown in steps 2–4 is the whole point — Kiro markets this as "writes zero lines of code first." Internal claim: feature builds went from two weeks to two days using Kiro to build Kiro.

## What's special / cool
- **Spec-driven by default**: artifacts (requirements/design/tasks) are first-class files in your repo, not hidden agent state. Reviewable in PRs, versionable, durable across sessions.
- **Hooks authored in natural language**: describe a hook ("run security scan on save of any auth/* file") and Kiro writes the config.
- **AWS-native ergonomics** without being locked to AWS — works on any codebase, but AWS service integration is unsurprisingly polished.
- **Code OSS lineage** means most VS Code muscle memory transfers immediately.

## Models supported
Claude Sonnet 4.x (default) and Claude 3.7 Sonnet documented in preview [VERIFY whether GPT/Gemini have been added since]. AWS-hosted; no BYOK in the consumer tier. Enterprise plans likely allow Bedrock model selection [VERIFY].

## Pricing / access
Free 50 credits, Pro $20/1,000, Pro+ $40/2,000, Power $200/10,000. Overage policy and trial rules updated March 2026. The August 2025 pricing change drew sharp criticism (The Register: "wallet-wrecking tragedy") for surprise billing; subsequent revisions added clearer credit accounting and per-mode (Spec vs Vibe) cost transparency.

## Notable & gotchas
- Spec workflow is genuinely heavier — for tiny edits, Vibe mode or another tool is faster. Kiro is best for medium-to-large features where the spec amortizes.
- Pricing has changed at least twice since launch; check kiro.dev/pricing before committing.
- Two-product confusion: don't conflate with the unrelated Kiro identity/security products that share the name.
- Public preview status as of 2026; GA timing not officially announced [VERIFY].

## References
- Kiro homepage and intro blog: https://kiro.dev/ , https://kiro.dev/blog/introducing-kiro/
- Pricing: https://kiro.dev/pricing/
- AWS docs hub: https://aws.amazon.com/documentation-overview/kiro/
- Repo / examples: https://github.com/kirodotdev/Kiro
- InfoQ — "Beyond Vibe Coding: Amazon Introduces Kiro" (Aug 2025): https://www.infoq.com/news/2025/08/aws-kiro-spec-driven-agent/
- The Register on Kiro pricing controversy (Aug 2025): https://www.theregister.com/2025/08/18/aws_updated_kiro_pricing/
