# Verification report — [VERIFY] tag sweep

Generated 2026-05-04. Covers 39 tag occurrences across 8 files
(workshop-intro.md, workshop-outline.md, workshop-mental-safety.md,
workshop-README.md, workshop-resources.md, workshop-benchmarks.md,
workshop-cost-tokens.md, keynote/README.md, research/coding-agents/README.md,
research/simon-mining.md).

Several tags are meta (process notes telling future-me to verify quotes
before going on slide) rather than concrete claims; those are listed under
"meta tags" and not counted against the verification totals. Concrete claims
to verify: **27**.

## Summary
- Confirmed: **15**
- Corrected (different wording / number / URL found): **9**
- Could not verify: **3**
- Meta / process-only tags (no claim): **12**

---

## Confirmed

| File:line | Claim | Primary source |
|---|---|---|
| simon-mining.md:106 | Quote: "A coding agent is a piece of software that acts as a harness for an LLM..." | https://simonwillison.net/guides/agentic-engineering-patterns/how-coding-agents-work/ |
| simon-mining.md:182 | Lenny's Podcast quote: senior/junior/mid-career framing | https://www.lennysnewsletter.com/p/an-ai-state-of-the-union and https://simonwillison.net/2026/Apr/2/lennys-podcast/ |
| simon-mining.md:165 | Lethal-trifecta three components | https://simonwillison.net/2025/Jun/16/the-lethal-trifecta/ |
| simon-mining.md:147 | "GitHub MCP defines 93 additional tools and swallows another 55,000 of those valuable tokens." | https://simonwillison.net/2025/Aug/22/too-many-mcps/ |
| simon-mining.md:133 | Skills: "A skill is a Markdown file telling the model how to do something..." | https://simonwillison.net/2025/Oct/16/claude-skills/ |
| simon-mining.md:210 | Mario Zechner "merchants of complexity" + "agents shit out 20,000 lines" | https://simonwillison.net/2026/Mar/25/thoughts-on-slowing-the-fuck-down/ and https://mariozechner.at/posts/2026-03-25-thoughts-on-slowing-the-fuck-down/ |
| workshop-benchmarks.md:55 | SWE-bench Verified top score ~80% | https://www.swebench.com/ — Claude Opus 4.5 80.9%, GPT-5.5 88.7%, Opus 4.7 87.6% (April 2026); ~80% remains a fair shorthand for "Claude class", but top-of-leaderboard is now ~88% |
| workshop-benchmarks.md:133 | Terminal-Bench domain `tbench.ai` | https://www.tbench.ai/ — domain confirmed; jointly Stanford + Laude Institute |
| workshop-resources.md:121 | Jeff Huber "RAG is Dead, Context Engineering is King" | https://www.latent.space/p/chroma — confirmed primary URL (Latent Space podcast, Aug 2025) |
| workshop-resources.md:125 | "Beyond Prompts: Learning from Human Communication for Enhanced AI Intent Alignment" arXiv ID | https://arxiv.org/abs/2405.05678 (Kim et al., May 2024) |
| workshop-resources.md:127 | Jason Liu Context Engineering series | https://jxnl.co/writing/2025/08/28/context-engineering-index/ — series index page |
| coding-agents/README.md:84 | Pi license MIT | https://github.com/badlogic/pi-mono and https://www.npmjs.com/package/@mariozechner/pi-coding-agent — MIT confirmed |
| coding-agents/README.md:103 | Junie supports MCP | https://www.jetbrains.com/help/junie/model-context-protocol-mcp.html and https://junie.jetbrains.com/docs/junie-cli-mcp-configuration.html — confirmed |
| coding-agents/README.md:111 | Devin supports MCP | https://cognition.ai/blog/mcp-marketplace and https://docs.devin.ai/release-notes/overview — confirmed (since mid-2025, expanded 2026) |
| coding-agents/README.md:112 | Kiro supports MCP and uses `.kiro/steering/` | https://kiro.dev/docs/mcp/ and https://repost.aws/articles/ARuX8rkojgSx-TYCc65JyAOw/getting-started-with-kiro-and-mcp-servers-connect-your-ai-ide-to-real-world-tools — both confirmed |

---

## Corrected (different wording / number / URL found)

### simon-mining.md:110 — "few dozen lines of code"
- **Claimed**: "The core mechanic — LLM + system prompt + tools in a loop — is just a few dozen lines of code."
- **Actual wording on Simon's blog**: "A simple tool loop can be achieved with a few dozen lines of code on top of an existing LLM API."
- **Source**: https://simonwillison.net/guides/agentic-engineering-patterns/how-coding-agents-work/
- **Suggested replacement**: Use the verbatim quote *"A simple tool loop can be achieved with a few dozen lines of code on top of an existing LLM API."*

### simon-mining.md:156 — Simon dropping MCP for CLI utilities
- **Claimed (paraphrase)**: "I don't really use MCP anymore when working with coding agents... CLI utilities and libraries like Playwright Python are a more effective way of achieving the same goals."
- **Actual wording**: "I don't use MCP at all any more when working with coding agents — I find CLI utilities and libraries like Playwright Python to be a more effective way of achieving the same goals."
- **Source**: https://simonwillison.net/2025/Nov/4/code-execution-with-mcp/
- **Suggested replacement**: Use the verbatim "I don't use MCP at all any more when working with coding agents — I find CLI utilities and libraries like Playwright Python to be a more effective way of achieving the same goals."

### simon-mining.md:194 — "Anyone can vibe-code a convincing UI"
- **Claimed**: "Anyone can vibe-code a convincing UI."
- **Actual wording from Simon's own write-up of the Lenny episode**: "A UI prototype is free now. ChatGPT and Claude will just build you a very convincing UI for anything that you describe."
- **Source**: https://simonwillison.net/2026/Apr/2/lennys-podcast/
- **Note**: The "anyone can vibe-code a convincing UI" version appears in third-party summaries but I could not locate it verbatim in either Simon's blog write-up or transcript snippets. Use the *primary-source* phrasing on the slide.
- **Suggested replacement**: *"A UI prototype is free now. ChatGPT and Claude will just build you a very convincing UI for anything that you describe."* — Simon Willison, Lenny's Podcast (Apr 2 2026), as reposted on simonwillison.net.

### simon-mining.md:226 — Simon's response to Zechner
- **Claimed (paraphrase)**: "discipline to find a new balance of speed versus mental thoroughness"
- **Actual wording**: "we need the discipline to find a new balance of speed v.s. mental thoroughness now that typing out the code is no longer anywhere close to being the bottleneck on writing software."
- **Source**: https://simonwillison.net/2026/Mar/25/thoughts-on-slowing-the-fuck-down/
- **Suggested replacement**: Use the verbatim quote above.

### simon-mining.md:232 — "Building is now cheap..."
- **Claimed**: "Building is now cheap. Knowing whether what you built is correct is the expensive part."
- **Status**: The *idea* is faithful to Simon's repeated framing on Lenny's podcast and elsewhere, but I could not find a single primary-source utterance with this exact wording. Closest documented version is the "UI prototype is free now... thing I care most about is I want them to have used it for months" framing in the Lenny blog post.
- **Source**: https://simonwillison.net/2026/Apr/2/lennys-podcast/ (closest primary source — paraphrased framing only; the slide-quote sentence is third-party synthesis)
- **Suggested replacement**: Either (a) attribute to "the spirit of Simon's Lenny appearance, paraphrase," or (b) replace with a verbatim Simon line — e.g. *"Never assume that code generated by an LLM works until that code has been executed."* (https://simonwillison.net/guides/agentic-engineering-patterns/agentic-manual-testing/)

### workshop-benchmarks.md:61 — METR uplift "+25% completion time"
- **Claimed**: "METR uplift: ~+25% completion time"
- **Actual numbers**: METR's early-2025 RCT measured **+19% (slowdown)** completion time when AI tools were used (CI: +2% to +39%). The 2026 follow-up shows the gap narrowing/inverting in some subgroups. There is no published "+25%" figure.
- **Source**: https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/ and https://metr.org/blog/2026-02-24-uplift-update/
- **Suggested replacement**: "+19% completion time (i.e. AI made tasks slower) in METR's early-2025 RCT, with the gap narrowing in their 2026 follow-up." Source date matters because the procurement story has changed.

### workshop-cost-tokens.md:203–205 — GPT-5/5.5/Gemini 3 Pro pricing
- **Claimed**: GPT-5 ~$3 / $0.30 / $15; GPT-5.5 ~$5 / $0.50 / $25; Gemini 3 Pro ~$2.50 / $0.25 / $12.50.
- **Actual (May 2026)**:
  - **GPT-5**: $1.25 input / $10.00 output per Mtok (released Aug 2025). Cached read tier exists but published flat rate, not 10× discount-style.
  - **GPT-5.5**: **$5.00 input / $30.00 output** per Mtok (released April 23 2026; doubled vs prior tier). The slide's $25 output is low.
  - **Gemini 3 Pro / 3.1 Pro**: $2.00 input / $12.00 output per Mtok up to 200K context; $4 / $18 above 200K.
- **Sources**:
  - https://openai.com/api/pricing/
  - https://apidog.com/blog/gpt-5-5-pricing/
  - https://ai.google.dev/gemini-api/docs/pricing
  - https://pricepertoken.com/pricing-page/model/google-gemini-3.1-pro-preview
- **Suggested replacement** (per row):
  - GPT-5 — $1.25 / ~$0.13 / $10
  - GPT-5.5 — $5 / ~$0.50 / $30
  - Gemini 3 Pro — $2 / ~$0.20 / $12 (≤200K) / tier-up above

### workshop-cost-tokens.md:275 — Anthropic token-efficient-tools docs page
- **Claimed**: link to release-notes page; flagged "VERIFY exact docs page"
- **Actual canonical doc**: https://docs.claude.com/en/docs/agents-and-tools/tool-use/token-efficient-tool-use (also mirrored at https://docs.anthropic.com/en/docs/build-with-claude/tool-use/token-efficient-tool-use)
- **Important caveat**: The `token-efficient-tools-2025-02-19` beta header **only works with Claude 3.7 Sonnet**; Claude 4 / 4.5 / 4.6 / 4.7 have built-in token-efficient tool use and *should not* set the beta header. The slide's "`token-efficient-tools-2026-03-28` beta header" appears to be a typo / fabricated date — **no such header exists** in Anthropic's published list.
- **Suggested replacement**: Drop the fabricated date; describe as "token-efficient tool use, on by default in Claude 4.x". Link the canonical docs page above.

### workshop-resources.md:111 (mental-safety.md:111) — Sau Sheong post URL
- **Claimed**: "Humanity is not ready for this much software" at https://sausheong.com/
- **Actual**: post is at https://sausheong.com/from-vibe-coding-to-agentic-engineering-1ca3ca72b5ac and is titled *"From vibe coding to agentic engineering"*. The "humanity is not ready..." line is the **opening sentence** of that post.
- **Source**: https://sausheong.com/from-vibe-coding-to-agentic-engineering-1ca3ca72b5ac
- **Suggested replacement**: Use that direct URL with the post title.

---

## Could not verify

### workshop-resources.md:126 — "The Prompt Pyramid" Medium URL
- **Claim**: existence of Medium article "The Prompt Pyramid — A Better Way to Structure Complex Tasks for GPT"
- **What I tried**: Web search for exact title.
- **Found**: Pranav Prakash, "The Prompt Pyramid: A Better Way to Structure Complex Tasks for GPT", https://medium.com/@pranavprakash4777/the-prompt-pyramid-a-better-way-to-structure-complex-tasks-for-gpt-4ebd71dfe49d (Jun 3 2025)
- **Status**: Source exists but **the author is not a recognized authority** on the topic — it's a personal Medium post with limited circulation, not a primary contribution that named the pattern. Recommendation: drop from resources list, or include with explicit note that it's an illustrative example rather than a canonical source.

### workshop-cost-tokens.md:160 — caveman exact mechanism
- **Claim**: caveman is "likely a system-prompt-stripping or context-compaction proxy"
- **Actual**: Caveman is a **Claude Code skill/plugin** (https://github.com/JuliusBrussee/caveman) that *rewrites the model's output style to terse "caveman speak"* — reducing **output tokens** by ~65–75% in measured evals. It is not a context-compaction proxy. It does also bundle a `caveman-shrink` MCP proxy for input-side compression (~46% reported savings).
- **Suggested replacement**: "Claude Code skill that rewrites the agent's output style for ~65–75% output-token savings; bundled `caveman-shrink` MCP additionally compresses input ~46%." Link https://github.com/JuliusBrussee/caveman.
- **Status**: Mechanism now known — strictly speaking this is "verified", but I'm leaving it under Could-not-verify because the user asked to confirm the one-line summary themselves before slide use. Recommendation: confirm phrasing with the user.

### workshop-cost-tokens.md:162 — headroom one-liner
- **Claim**: "automatic compression/elision of stale tool output, surfacing a hash for retrieval if needed"
- **Actual**: Two distinct projects called "headroom" exist:
  1. https://github.com/chopratejas/headroom — context optimization layer / proxy. Claims ~50% savings, runs locally. Marketed at https://extraheadroom.com/.
  2. https://github.com/gglucass/headroom-desktop — menu-bar app for Claude Code, "unlock 2x more usage", same ~50% framing.
  Neither documents a "hash-for-retrieval" mechanism in their public READMEs. The user's own CLAUDE.md may refer to a different in-house tool with that name.
- **Status**: Cannot verify the specific mechanism described. Recommendation: ask the user which "headroom" they mean and confirm the one-liner before slide use.

---

## Meta / process-only tags (no claim to verify)

These tags are reminders for the workshop authors, not concrete claims:

- workshop-intro.md:152 — "VERIFY numbers before quoting verbatim"
- workshop-intro.md:201 — "Mark each as [VERIFY] before using on a slide"
- workshop-outline.md:347 — checklist item "Final sanity check on all `[VERIFY]` quotes and numbers"
- workshop-mental-safety.md (line note inside Open Questions section)
- workshop/README.md:52 — process note in README
- keynote/README.md:23 — process note in README
- coding-agents/README.md:157 — section-intro line "individual files mark every uncertain claim with [VERIFY]"
- simon-mining.md:57 — opening note about VERIFY usage in this doc
- simon-mining.md:228 — `=== ON BUILD-VS-VERIFY` (header text, not a tag)
- simon-mining.md:372 — workshop-edit note ("Use [VERIFY] tag pending exact wording check.")
- simon-mining.md:423–425 — open-questions checklist (the same three concrete-quote claims already addressed above)

---

## Observations and recommendations

1. **Pricing tables age fast.** The GPT-5/5.5/Gemini-3 row in `workshop-cost-tokens.md` is already wrong by May 2026 (GPT-5.5 is double what's on the slide; Gemini 3 Pro tiering isn't captured). Recommend a "valid as of <date>" footnote on the table, plus a slide note to re-verify weekly.

2. **The "token-efficient-tools-2026-03-28" beta header in workshop-cost-tokens.md is fabricated.** No such header exists. Anthropic's only public token-efficient-tools beta is `token-efficient-tools-2025-02-19`, which only applies to Claude 3.7. Remove or correct before slide use.

3. **METR's "+25% completion time"** is a misremembering — the actual figure is **+19% slowdown** (the *opposite* sign too if the slide intended "+25% productivity"). This is the procurement-relevant number; getting it wrong on a workshop slide will cost credibility immediately. Recommend rewriting that row with the +19% figure and the 2026 follow-up nuance.

4. **The "anyone can vibe-code a convincing UI" line** is widely *attributed* to Simon but I could not find it verbatim in primary sources. The closest primary-source phrasing is "A UI prototype is free now. ChatGPT and Claude will just build you a very convincing UI for anything that you describe." Use the primary phrasing.

5. **The "Building is now cheap..." quote** likewise is the spirit of Simon's argument but not a primary-source verbatim. Either paraphrase explicitly or substitute a verbatim line from his blog (the agentic-manual-testing piece has the cleanest substitute).

6. **Continue.dev "cost-aware routing"** is real but not branded as "cost-aware routing" — Continue calls it **model roles** (per-feature model assignment in `config.yaml`). Update the term on the slide.

7. **Sau Sheong attribution**: the "humanity is not ready..." opening line *is* his — it's the first line of his Mar 29 2026 post "From vibe coding to agentic engineering" (https://sausheong.com/from-vibe-coding-to-agentic-engineering-1ca3ca72b5ac). Use that direct URL.

8. **Antigravity AGENTS.md**: the rules file is **AGENTS.md** (cross-tool standard) plus **GEMINI.md** (Antigravity-specific override, higher priority). Both are read since v1.20.3 (March 5 2026). Source: https://antigravity.google/docs/rules-workflows.

9. **Aider MCP support**: as of May 2026, **Aider does not have first-party MCP support**. The current ❌ in the comparison table is correct. Workarounds (`mcpm-aider`, `aider-mcp-client`) are community projects.

10. **Junie CLI npm package**: I did not find a public npm package name for Junie CLI itself in the search; the JetBrains docs install it via the IDE plugin or a JetBrains-provided installer, not via `npm install @jetbrains/junie-cli`. Recommend confirming the install path with the JetBrains docs (https://blog.jetbrains.com/junie/2026/03/junie-cli-the-llm-agnostic-coding-agent-is-now-in-beta/) before publishing the install command on a slide.
