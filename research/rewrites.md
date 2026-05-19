# Notable AI-Assisted Rewrites + OSS Relicensing Concern
_Researched 2026-05-18_

## AI-Assisted Rewrites

### Bun: Zig → Rust (May 2026)

After Anthropic acquired Bun (December 2025), the team rewrote the codebase from Zig to Rust in ~1–2 weeks using Claude Code. The PR merged ~1M lines.

**Mitchell Hashimoto's quote (via Simon Willison, May 14 2026):**
> "Programming languages used to be LOCK IN, and they're increasingly not so. Bun has shown they can be in probably any language they want in roughly a week or two. Rust is expendable. Its useful until its not then it can be thrown out."
[VERIFIED — simonwillison.net/2026/May/14/mitchell-hashimoto/]

**Sources:**
- https://simonwillison.net/2026/May/14/not-so-locked-in/ (summary)
- https://weeklyrust.substack.com/p/the-great-zig-to-rust-experiment

---

### Ladybird Browser: C++ → Rust (JavaScript Engine, February 2026)

Independent browser project rewrote its JavaScript engine (LibJS) from C++ to Rust in two weeks using Claude Code and Codex.

**Key facts:**
- ~25,000 lines of Rust produced
- "Human-directed, not autonomous" — developer made all architectural decisions, agents handled translation
- Test suite was critical: every AST produced is identical to C++ version, all bytecode output identical, zero regressions
- Passed 52,898 ECMAScript test262 tests and 12,461 Ladybird regression tests — no new bugs

**The enabling insight:** The JavaScript engine was chosen FIRST precisely because it had excellent test coverage. The test suite was what made the rewrite verifiable, not just the AI capability.

**Sources:**
- https://ladybird.org/posts/adopting-rust/
- https://www.theregister.com/2026/02/23/ladybird_goes_rusty/
- https://news.ycombinator.com/item?id=47120899

---

### iOS + Android → React Native (Simon Willison, May 2026)

Simon Willison described a conversation with engineers at a mid-sized company who had just agent-driven a complete rewrite of both native iOS and Android apps to React Native. Willison's key point: the cost was now so low that reversibility became a real option.

> "how cheap it can be to port native mobile apps to React Native using coding agents... and then port them back again later if it turns out not to work out."

Source: https://x.com/simonw/status/2055060328048885788 (secondhand, not a public case study)

---

### Common Pattern: Tests Enable Rewrites

All three cases point to the same enabling factor: **test suites, not just AI capability**.

- Ladybird chose the JS engine first because it had the best test coverage (ECMAScript test262)
- Bun relied on its own test suite to verify correctness across 1M lines
- Without tests, "rewriting" just means generating plausible-looking code you can't verify

**The reversibility insight:** Technology choices are becoming experiments, not commitments. Architectural risk drops. You can choose the right tool now and change later — IF you have tests that prove equivalence.

---

## OSS Relicensing Concern — "License Washing"

### The chardet Controversy (March 2026)

**What happened:** chardet (Python character encoding library, used by `requests` and millions of projects) was rewritten by maintainer Dan Blanchard using Claude Code over five days. He released chardet 7.0.0 under MIT, relicensed from LGPL.

**JPlag plagiarism detection:** only 1.29% similarity to prior versions.

**Blanchard's defense:** "I started in an empty repository... explicitly instructed Claude not to base anything on LGPL/GPL-licensed code."

**Mark Pilgrim's objection:** Blanchard's decade of intimate knowledge of the codebase defeats any "clean room" claim. Claude itself may have been trained on chardet code. Claude referenced existing chardet files during development. The package retained the same PyPI name and same functionality.

**Legal status:** Entirely unresolved. No court ruling. The question — is AI-generated output trained on/prompted with GPL code a derivative work? — has no settled answer.

### Why This Is Structurally New

> "The GPL family of licenses has always depended on one practical assumption: rewriting a large codebase from scratch is so expensive that nobody bothers. But the line gets blurry when you use AI to systematically rewrite an entire project you did not author, especially one with copyleft obligations."  
> — [OSnews analysis paraphrase]

> "'AI' is the single-greatest coordinated attack on open source in history, and the open source world would do well to realise that."  
> — OSnews

**The economic assumption underlying copyleft is gone:** What took a team months now takes one developer days.

**Sources:**
- https://simonwillison.net/2026/Mar/5/chardet/ (analysis + links)
- https://www.phoronix.com/news/Chardet-LLM-Rewrite-Relicense
- https://www.theregister.com/2026/03/06/ai_kills_software_licensing/
- https://www.osnews.com/story/144547/the-great-license-washing-has-begun/

---

## Slide-Ready Formulations

**Reversibility slide:**
"Test suites are the new lock-in deterrent. Ladybird rewrote 25K lines of C++ to Rust in two weeks — zero regressions — because ECMAScript test262 could verify every line. Bun migrated 1M lines from Zig to Rust at the speed of AI. Mitchell Hashimoto: 'Programming languages used to be LOCK IN, and they're increasingly not so.' What makes rewrites safe is not the AI. It's the tests."

**OSS concern slide:**
"Copyleft's economic assumption was always: reimplementation is too expensive to bother. AI just killed that assumption. chardet was rewritten from LGPL to MIT in five days using Claude Code. The original author called it an LGPL violation. Courts haven't ruled yet. If they don't, the entire copyleft model has a hole big enough to drive every corporate fork through."
