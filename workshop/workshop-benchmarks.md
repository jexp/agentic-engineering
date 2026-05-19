# Workshop — SWE Benchmarks: What They Measure, What They Miss

**Block**: Deep dive — sub-section, ~5–7 min, slot near the end of the harness landscape (after Slide 2) or as a callout in the practices section
**Position**: Goes between the harness landscape and the craft levers — context for "which is best?" questions before they get asked
**Goal**: give the room a literate take on benchmarks. Not "tool X scores Y, therefore use it" — but "here's what the numbers mean, where they're trustworthy, and where to be skeptical."

---

## Framing line

> "Benchmarks tell you the *direction* the field is moving. They don't tell you which tool is best for *your* codebase. Use them like a weather report — informative, directional, not a substitute for going outside."

---

## Slide 1 — The benchmark landscape (one slide, dense)

Five families of benchmark, in roughly increasing realism:

### 1. Function-level coding (mostly saturated by 2026)
- **HumanEval** (OpenAI, 2021) — 164 simple Python functions; saturated, pass rates >95% mean little. Historical reference only.
- **MBPP** — similar, slightly broader. Saturated.
- **MultiPL-E** — HumanEval translated into 18+ languages; useful for multi-language signal.
- **BigCodeBench** — 1,140 tasks with real library calls and complex instructions. Less saturated; closer to what people actually write.

### 2. Competitive / contest-style
- **LiveCodeBench** — *continuously updated* competitive programming problems, key feature is freshness (resists training contamination by adding new problems monthly). Carnegie Mellon.
- **APPS / CodeContests** — older contest-style benchmarks.

### 3. Repo-level issue resolution
- **SWE-bench** (Princeton, 2023) — real GitHub issues from 12 popular Python repos (Django, sympy, scikit-learn, etc.). Model gets the issue + repo, must produce a patch that passes the repo's own tests. ~2,300 issues original; **SWE-bench Verified** is the 500-issue OpenAI-curated subset confirmed solvable.
- **SWE-bench Lite** — 300-issue fast-eval subset.
- **SWE-bench Multilingual / Multimodal** — extended scope; multimodal includes screenshots / UI work.
- **RepoBench** — earlier repo-scale code completion benchmark.

### 4. Terminal / agentic loop
- **Terminal-Bench** (Stanford, 2025) — multi-step real terminal tasks: install, debug, build, deploy. Closer to what an agent actually does.
- **Terminal-Bench 2.0** (2026) — harder, expanded; current state-of-the-art lives here.
- **Cybench** — security/CTF tasks.

### 5. Real-work / human-correlated
- **SWE-Lancer** (OpenAI) — ~$1M of *real* Upwork freelance tasks; ground truth is whether the work would have been paid out.
- **METR uplift studies** — measured productivity of *real* engineers with/without AI tools on *real* tasks. Closest thing to a randomized control trial in the field.
- **ARC-AGI** (Chollet) — not coding-specific, but cited everywhere as the "abstract reasoning" counter-signal when SWE numbers spike.

> The realism axis: HumanEval (synthetic, isolated function) → SWE-bench (one repo, one bug) → Terminal-Bench (many tools, multi-step) → SWE-Lancer (someone would have paid real money for this).

---

## Slide 2 — Where the leading tools currently sit (with caveats)

Not a leaderboard; a snapshot. **Numbers move monthly.** Verify before quoting.

| Benchmark | Top score (≈) | Tool / config | Notes |
|---|---|---|---|
<!-- VERIFIED-EDIT (April 2026): SWE-bench Verified top-of-leaderboard is now ~88%. Specifics: GPT-5.5 88.7%, Opus 4.7 87.6%, Opus 4.5 80.9%. -->
| SWE-bench Verified | ~88% top-of-leaderboard (April 2026) — GPT-5.5 88.7%, Opus 4.7 87.6%, Opus 4.5 80.9% | Multiple frontier models in agent harnesses | The number to watch; also the most contamination-sensitive |
| SWE-bench Verified | 76.2% | **Antigravity** (Gemini 3 Pro), at launch Nov 2025 | First-party-reported |
| Terminal-Bench 2.0 | 92.1% | **Claude Code** "Mythos" config | Claude Code's reference number |
| Terminal-Bench 2.0 | 77.3% | **Codex CLI** w/ GPT-5.5 | Closed gap fast; #1 on standard Terminal-Bench in April 2026 |
| LiveCodeBench | continuous | All major frontier models tracked | Best signal against contamination |
| Aider polyglot | varies | Per-model leaderboard at aider.chat | Useful for comparing edit-format reliability |
<!-- VERIFIED-EDIT: METR's actual figure is +19% SLOWDOWN, not +25% uplift. The slide originally had the wrong sign — re-quoting wrong here would be reputation-killing for a senior-engineer audience. -->
| METR uplift | **+19% slowdown** in early-2025 RCT (CI: +2% to +39%); gap narrowing in 2026 follow-up | Real engineers, real tasks | The number that matters most for procurement *— and has flipped sign since the study landed* |

**Critical caveat**: scores are produced by *(model × harness × scaffolding)*. A Claude model in a poorly-tuned harness will underperform a worse model in a great harness. The "92.1% Terminal-Bench" is a *Claude Code* number, not a *Claude* number. Apples-to-apples comparisons are hard, and vendors know it.

---

## Slide 3 — Pros and cons (the slide that earns trust)

### What benchmarks do well

- **Directionality**: the curve is real. SWE-bench Verified went from ~2% (GPT-4, 2023) to ~80% in three years. That's not noise.
- **Comparability across model versions**: same benchmark, same harness, different model → genuine signal about model capability.
- **Forcing function on capability**: vendors target the benchmarks; the work to *target* SWE-bench actually does improve real coding ability — incidentally, which is the point.
- **Reproducibility**: open eval scripts, public test sets (mostly), public submissions.

### What benchmarks miss / where they mislead

- **Contamination**: SWE-bench, Terminal-Bench, and HumanEval problems are *publicly available*. Frontier models are trained on the open web. The line between "the model learned to solve it" and "the model has seen the answer" is not zero. **LiveCodeBench's monthly refresh is a deliberate response.**
- **RL training loops**: when a model is RL-trained on a coding-agent harness, the *exact tasks used in training* can leak into evaluation domains. Vendors don't publish their RL data.
- **Single-repo, single-bug tasks**: SWE-bench measures fixing *isolated* issues in mature repos. Real work is multi-feature, ambiguous-spec, long-arc. The benchmark's *shape* doesn't match the *shape* of most engineering work.
- **No domain transfer test**: a model great at fixing Django bugs may be mediocre at your bespoke financial-services codebase. Benchmarks don't measure this.
- **Scaffolding asymmetry**: the gap between Codex's 77.3% and Claude's 92.1% on Terminal-Bench 2.0 is *partly* harness craft (apply_patch format, sandboxing, hook integration) — not raw model capability. Same model in a different harness scores differently.
- **Pass@k inflation**: "pass@5" or "best-of-N" results are quoted alongside pass@1 without always being labeled. A 90% pass@5 may be 65% pass@1.
- **Test-set tuning**: vendors who *care about leaderboard placement* will optimize for benchmark idiosyncrasies. Real engineers don't get those optimizations on their codebase.
- **Cost-blind**: a 92% score using $10 of inference per task is not the same product as a 78% score for $0.50. Most leaderboards don't normalize for cost.
- **Latency-blind**: same problem in reverse for interactive use.
- **No measure of what makes agents fail in production**: confident hallucination, silent test deletion, scope creep, plausibly-wrong architectural suggestions. None of this is benchmarked.

---

## Slide 4 — How to read benchmarks like a senior engineer

A practical rubric — use this whenever you see a number quoted in a vendor blog post or a Twitter thread.

1. **Date-check it.** Numbers older than 90 days are stale.
2. **Tool *and* model.** "GPT-5.5 hits X" is meaningless without "in *which harness*."
3. **pass@1 or pass@N?** If unstated, assume the most flattering reading was chosen.
4. **Public vs. private eval?** Hidden eval sets (e.g. SWE-Lancer's held-out set) resist contamination better than fully public ones.
5. **Cost & latency footnote?** No? Treat the number as upper-bound theoretical.
6. **Direction of the curve, not the absolute.** The interesting question is "is this getting better?" not "is X > Y."
7. **Real-work proxy?** SWE-Lancer, METR studies, Aider polyglot, or your own internal eval beat HumanEval every time.
8. **Triangulate with three benchmarks.** Different benchmarks have different biases. A tool that wins on three is more likely a real win than one that wins on one.
9. **Run your own.** Pick 5 representative tasks from your codebase; run each tool on them once a quarter. Internal eval beats external benchmarks for procurement decisions, full stop.

---

## Slide 5 — The honest take (closing line of the section)

> "The acceleration is real. The numbers are directionally trustworthy. But the absolute leaderboard position of harness X over harness Y is a worse signal than running both on three of your own tickets for an afternoon. Ten engineers' worth of internal eval beats all the public benchmarks combined."

What to do Monday morning:
- Pick **3 representative tasks** from your last sprint (one easy, one medium, one nasty)
- Run them through your two leading harness candidates
- Score *yourself* on review burden, not just task completion
- Re-run quarterly — that's *your* benchmark, and it's the one that matters

---

## Where this slide goes in the deck

Two reasonable placements:

- **Inside the harness landscape** — right after the comparison table (Slide 2). Makes "why these numbers don't mean what you think" land while the comparison is fresh.
- **As an aside in the practices section** — between "challenges" and "collapsing the latent space." Useful if the room is benchmarks-skeptical and you want to acknowledge it before the practices argument.

**Lean**: include in the harness section. Skeptics will raise this exact issue if you don't.

---

## Sources & references

- [SWE-bench](https://www.swebench.com/) — original benchmark + Verified subset + leaderboards
- [Terminal-Bench](https://www.tbench.ai/) — Stanford's terminal-task benchmark [VERIFY domain]
- [LiveCodeBench](https://livecodebench.github.io/) — continuously-updated competitive coding benchmark
- [BigCodeBench](https://bigcode-bench.github.io/) — complex-instruction coding benchmark
- [Aider leaderboards](https://aider.chat/docs/leaderboards/) — edit-format-aware multi-language comparison
- [METR — *Early-2025 AI experienced OS dev study*](https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/) (the +19% slowdown finding) and the [2026 follow-up](https://metr.org/blog/2026-02-24-uplift-update/) showing the gap narrowing
- [SWE-Lancer (OpenAI)](https://openai.com/index/swe-lancer/) — real freelance work as eval
- [ARC-AGI](https://arcprize.org/) — Chollet's abstract reasoning counter-benchmark
- [On contamination of code benchmarks (multiple arXiv 2024–2026)](https://arxiv.org/) — search for "code benchmark contamination" + year
- [artificialanalysis.ai/agents/coding](https://artificialanalysis.ai/agents/coding) — third-party leaderboard, updated regularly

---

## Open questions for me to decide before tomorrow

- [ ] Verify the headline numbers against current leaderboards. Especially: Antigravity 76.2% SWE-bench Verified at launch, CC "Mythos" 92.1% Terminal-Bench 2.0, Codex CLI 77.3% TB2.0. These move.
- [ ] Single slide or two? **Lean: condense into one slide of "what they measure, what they miss" + one closing line. Skip if running tight on time.**
- [ ] Show one specific contamination example (e.g. a SWE-bench issue whose code was likely in training data)? **Lean: skip — too much detail, slows the room. One sentence on contamination is enough.**
- [ ] Do I include METR uplift number explicitly? **Lean: yes — it's the most respectable real-work number and the room will appreciate it.**
- [ ] Do I name any harnesses' numbers explicitly, or keep the slide vendor-neutral? **Lean: name a few — anonymity reads as evasion to engineers. Be specific, label "directionally."**
