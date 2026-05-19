# Keynote v4 — Critical Review
_Generated 2026-05-18 · Apply before converting to slides_

---

## 0 — First decision (blocks everything else)

**The current deck is a 50-minute talk, not a 40-minute one.**

At 35s/slide average: 48 non-demo slides × 35s + 12 min demo = **39.5 min**. But most slides need 45–90s, not 35s. Act III alone has ~12 slides in 6 min. Realistic current runtime: **50–55 min**.

**Decision required before any edits:**
- [ ] Is the slot fixed at 40 min? → cuts below are non-negotiable
- [ ] Can slot expand to 50 min? → merges and compressions only, cuts optional

---

## 1 — Cut candidates 

| Slide | Why |
|---|---|
| **14** — Why coding runs ahead | Implicit from demo; audience doesn't need it explained |
| **27** — Good-design insight | Redundant with Slide 18 opener (same claim, slightly different words) |
| **31** — The loop restated | Recap slide after demo; fold bullets into Slide 30 close |
| **43** — Productivity / experience paradox | Subtle point that needs unpacking you don't have time for; move to Slide 41 speaker notes |

---

## 2 — Merge candidates (3 pairs → save 3 slides)

| Merge | Action |
|---|---|
| **Slide 26 + 26b** | The "knowledge loop" reframe (26b) is sharper than Destination 5's documentation framing. Make 26b the canonical slide; add "documentation" as a one-liner sub-point in Slide 19's five destinations. Drop the redundant 26. |
| **Slide 41 + 42** — exhaustion + addiction | Same person, same source, same theme. Stack both quotes on one slide. |
| **Slide 18 + 19** — Act III opener + five destinations | The opener ("the maintainer is an agent") is the punchline before the agenda. Combine: opener claim at top, five destinations as the agenda beneath. One slide, one beat. |

---

## 3 — Compress (6 slides carrying too much)

**Slide 5b — The gatekeeper**
- Screen content is too heavy; speaker notes are very long
- Compress to: one claim at top ("Cost of building did two jobs. We're only celebrating one."), two columns (bad gatekeeper / good gatekeeper), drop Marty Cagan by name or make it a speaking note only
- The engineering-practices-as-cost-reduction insight moves better to Slide 18 (Act III opener)

**Slide 28b — Task boundaries / C4**
- C4 in 30s is a stretch; two arXiv citations belong in a paper not a keynote
- Cut to: start = brief the agent (4 bullets), end = commit message
- C4 → one line in speaker notes ("Simon Brown's C4 gives you the architectural vocabulary")
- Kill arXiv references entirely from screen

**Slide 36 — Reversibility**
- Three examples is one too many: pick **Bun** OR **Ladybird**, not both
A: use Bun
- The punchline ("it's not the AI, it's the tests") needs more prominence — make it the last bullet, not buried in speaker notes

**Slide 37 — chardet / OSS relicensing**
- JPlag 1.29% similarity stat is a footnote, not a bullet
- Compress to: "chardet: LGPL → MIT in 5 days with Claude Code. The economic assumption underlying copyleft is gone. No court ruling yet."

**Slide 39 — GitLab Act 2**
- 5 numerical claims overloads the screen
- Keep: 3 layers + per-seat → usage-based (most striking)
- Drop to speaker notes: country presence %, team count doubling

**Slide 49 — Monday morning checklist**
- 9 bullets is too many for a slide
- Cut to 5: (1) spec before code, (2) failing test first, (3) navigate don't drive, (4) ralph when correcting the same mistake twice, (5) build the system

---

## 4 — Missing pieces (add or commit to leaving out)

**4a — Hooks: define or remove**
Slide 31 says "hooks are quality gates that always run." This is the first time hooks appear and they're not defined. Either:
- Add one sentence on first mention: "Hooks: shell commands that run on every agent event — on file save, on task complete, on tool use — regardless of what the agent decides to do"
- Or remove "hooks" from Slide 31 and fold into "constraints / CI" language

**4b — Middle loop: give it its moment**
"The middle loop" is the most original framing in the talk — named by the TW retreat as the unnamed gap. Currently it appears as a passing reference in Slide 29 and Slide 33 without definition. Either:
- Give it a proper definition in one of those two slides (30 seconds: inner loop = agent, outer loop = CI/CD, middle loop = supervisory engineering — direct, evaluate, fix, decompose)
- Or stop calling it "the middle loop" and just describe what it is

**4c — Generic AE workflow (not just hone)**
Slide 30 demos the hone pattern (PRD → tasks → implement → review → commit) but doesn't extract the tool-agnostic takeaway. Add one line either in the screen or speaker notes: "This pattern isn't hone-specific — any agent harness can do it. The structure is the point, not the tool."

**4d — Ralphing: commit or cut**
Currently deferred to Monday checklist only. The open question flags this. Options:
- **Add**: one slide between Acts III and IV, 30 seconds. "Context rot is the problem. Ralphing is the outer-loop fix. Geoffrey Huntley named it after Ralph Wiggum — 'I'm not smart, but I never give up.' While loop. Context wiped. Filesystem persists. Resume." Then move on.
- **Cut**: remove from Monday checklist entirely — "ralph" as unexplained jargon in a checklist is worse than not mentioning it.

**4e — PRD / spec / task vocabulary**
You use "PRD" on Slide 30, "spec" on Slide 20, "task" everywhere. Add a 5-second clarifier on Slide 20: "PRD = the goal. Tasks = the bounded changes. Both are specs at different grain."

---

## 5 — Structural issues

**Act V is misnamed.** Currently "The Future" — but contains mostly current observations (middle loop, Conway's Law, reversibility, GitLab, security). Only roles + cognitive debt are genuinely forward-looking.
→ Rename to: **"Where It's Already Going"** or **"The Patterns Surfacing Now"**

**Act II is front-loaded.** 16 slides for "the moment we're in." The 4-phase history (Slides 7–12) is 6 slides for roughly 2 minutes. Consider:
- Merge Phase 1 and Phase 2 into one slide (both are setup for the Karpathy pivot)
- This saves one slide and tightens the history before Act III

**Quote density.** After cuts above: 12 quote slides ≈ 6 min ≈ 15% of the talk. Defensible. Don't add more.

**The back third is heavy.** Acts V + VI cover 12 major themes in 9 minutes. Audience attention is depleted. The cuts from section 1 help. After cuts, verify Acts V+VI still have enough breathing room — each idea needs at least one sentence of unpacking, not just a bullet.

---

## 6 — Verification pass (complete before slide-build)

| Item | Status | Action |
|---|---|---|
| Claire Vo exact wording (Slide 44) | [VERIFY] | Check lennysnewsletter.com/p/how-openclaw-changed-my-life-claire-vo |
| Bill Staples GitLab quote (Slide 39) | [VERIFY] | Check about.gitlab.com/blog/gitlab-act-2/ |
| Matthew Yglesias source URL (Slide 46) | [VERIFY] | Find exact Substack/Twitter post |
| 275M commits/week data (Slide 13) | [VERIFY] | Source not yet cited — find GitHub blog post or investor deck |
| "Discipline of a good commit message…" (Slide 28b) | Unattributed | Either attribute (it's yours) or strip the blockquote formatting |
| arXiv 2603.15021 and 2510.22787 (Slide 28b) | [VERIFY] | Confirm paper IDs exist and title matches |
| Slide numbering (5b, 26b, 28b) | Pending | Final integer renumber after content locked |

---

## 7 — What's working — do not touch

| Slide | Why it works |
|---|---|
| **Slide 3 + 51** | O'Reilly cover demo open → real book reveal close. Strongest narrative spine. |
| **Slides 15 → 16 → 17** | Simon's "blurring" → "10K lines/day" → section card. Cleanest pivot in the talk. |
| **Slide 25** — James Shore | The maintenance math quote earns its place. Economics frame is fresh. |
| **Slide 26b** — The knowledge loop | "Knowledge captured once, applied every session" is the strongest original framing. |
| **Slide 4** — Thesis card | "Practices we've been ignoring for decades because we finally can't afford not to." The through-line. Keep it, use it at every act break. |
| **Slide 28** — Navigator/driver | Kent Beck anchor. The TDD-as-pacing-mechanism is concise and true. |
| **Slide 48** — The spectrum | Clean close-of-argument: vibe / augmented / agentic — all valid, know which one you're doing. |

---

## 8 — Recommended order of operations

1. **Confirm time slot** — 40 or 50 min (determines whether all cuts are required)
2. **Apply cuts** (section 1 — 9 slides)
3. **Apply merges** (section 2 — 3 pairs)
4. **Apply compressions** (section 3 — 6 slides)
5. **Add missing pieces** (section 4 — decide on each: add or commit to cut)
6. **Fix structural issues** (section 5 — rename Act V, consider Phase 1+2 merge)
7. **Renumber slides** — strip letter suffixes, assign clean integers
8. **Verification pass** (section 6 — before converting to slides, not after)
9. **Read aloud with stopwatch** — the only timing that matters
