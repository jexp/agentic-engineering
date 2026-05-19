# Antigravity

**Vendor / origin**: Google. Announced November 18, 2025 alongside Gemini 3. Positioned as Google's "agent-first" successor experience to Gemini Code Assist [VERIFY direct lineage from Code Assist].
**License / source**: Closed source, free public preview. Built on a fork of Visual Studio Code (so the editor shell is OSS).
**Surface**: Desktop IDE (macOS / Windows / Linux), with cloud-backed agent orchestration. Not a CLI.

## Install & access
- Download installer from https://antigravity.google/.
- Sign in with a Google account; free during public preview, with "generous rate limits" on Gemini 3 Pro.
- No paid tier announced at launch [VERIFY as of mid-2026].

## Core architecture
Two coordinated surfaces: the Editor View (a VS Code-fork IDE with inline agent) and the Manager Surface (a dashboard for spawning, observing, and orchestrating multiple long-running agents in parallel across workspaces). Agents have direct permissions on the file system, terminal, and a controlled browser instance. The agent loop is plan-act-verify with artifacts (diffs, screenshots, test runs) surfaced as reviewable evidence rather than raw chat. Reports 76.2% on SWE-bench Verified at launch.

## Extension model
- VS Code extension compatibility via the fork [VERIFY scope].
- MCP support for external tools.
- Browser tool is a built-in first-class agent capability (DOM interaction, screenshots) — not a plugin.
<!-- VERIFIED-EDIT: Antigravity reads both AGENTS.md (cross-tool standard) and GEMINI.md (Antigravity-specific override, higher priority) since v1.20.3 (March 5 2026). -->
- Rules: **AGENTS.md** (cross-tool standard) plus **GEMINI.md** (Antigravity-specific override, higher priority). Both honored since v1.20.3 (March 5 2026). Source: [antigravity.google/docs/rules-workflows](https://antigravity.google/docs/rules-workflows).

## Interaction model
Two main modes: Editor (hands-on, IDE-style with inline agent chat and diff review) and Manager (asynchronous, multi-agent — fire off tasks, monitor, review when they finish). Diff review with accept/reject per file. Multiple agents run in parallel across workspaces from a single Manager view.

## How it works (the actual loop)
1. User states a goal in Editor or Manager.
2. Agent plans, then executes via terminal/file/browser tools, producing "artifacts" (commits, screenshots, run logs).
3. User reviews artifacts and diffs in the Manager surface; can chat back, accept, or branch.
Distinctive: parallel async agents are a first-class UI primitive, and the browser tool is built in (closing the loop on web app verification).

## What's special / cool
- Manager Surface for orchestrating many concurrent agents — closer to Devin/Jules than to Cursor.
- Native browser-control agent for verifying UI work end-to-end.
- Multi-model: Gemini 3 Pro, Claude Sonnet 4.5, and GPT-OSS supported on day one.

## Models supported
Gemini 3 Pro (default), Anthropic Claude Sonnet 4.5, OpenAI GPT-OSS. No local model story announced [VERIFY].

## Pricing / access
Free public preview. Rate limits on Gemini 3 Pro are generous but undefined publicly. Pricing tier post-preview not yet announced [VERIFY].

## Notable & gotchas
- Public preview: API surface, rate limits, and even product naming may shift before GA.
- It's a separate IDE app, not a VS Code extension — adopting it means switching editors, not adding a plugin.

## References
- https://antigravity.google/
- https://developers.googleblog.com/build-with-google-antigravity-our-new-agentic-development-platform/
- https://en.wikipedia.org/wiki/Google_Antigravity
- https://www.kdnuggets.com/google-antigravity-ai-first-development-with-this-new-ide
