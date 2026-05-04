# Workshop — Mental Load, Roles & Career (the conversation we should have)

**Block**: Opens the Q&A session, ~5–7 min before opening the floor
**Position**: Slot at the *start* of Block 11 (Q&A), before my "what will you try Monday?" opener
**Goal**: surface the harder questions the room is carrying — exhaustion, role anxiety, skill atrophy, junior career paths — so they're on the table when Q&A opens, not stuck under it. Three slides, no hand-wringing.

---

## Framing line

> "Before we open Q&A, I want to put three things on the table that the room is probably already thinking about and won't always volunteer: the *cost of all this on us as humans*. None of this has clean answers — but the conversation matters more than the optimization."

---

## Slide 1 — The mental cost is real

The unspoken half of the productivity story.

- **Review fatigue (Jevons paradox).** Tools got 10× faster; demand for human judgment grew to absorb the gain. Reviewing 500 lines of plausible code is harder than writing 200. *Anyone who's spent an afternoon reviewing agent PRs has felt this.*
- **Cognitive load shifts up the stack.** The agent does the typing; you carry the *taste*, the *trust calibration*, the *architecture decisions*. That work is harder, less visible, and not yet measured by any metric your manager has.
- **Always-on collaborator, never tired.** The agent is happy at 3am. You are not. The asymmetry is dangerous if you let it set the pace.
- **Trust calibration is exhausting.** Every output needs a "is this real?" pass. That meta-cognition adds up; it's why a day of agent work can feel heavier than a day of solo coding even though you produced more.
- **The skeptic in the room is right about *something*.** Cognitive exhaustion from always-on AI work is real, documented (BCG, Yegge, multiple practitioner accounts), and not solved by a better tool.

> *"We are not ready for this much software."* — Sau Sheong (Singapore GovTech) — and what he meant is: the *humans* aren't ready, regardless of the tooling.

**What helps**:
- AI-free hours / days. Treat them as you'd treat exercise.
- Pair with humans on hard work; don't let the agent become your only collaborator.
- Pace yourself across weeks, not turns. The agent doesn't care how fast you go.

---

## Slide 2 — The role question (senior · mid · junior)

Different career stages face *very different* situations. Simon Willison made this point well in the Lenny interview — worth quoting and engaging with directly.

### Senior engineers
- **Your judgment is suddenly the bottleneck — and the moat.** Code velocity is up 5×; *the question of what to build* hasn't changed. Your taste, your scar tissue, your sense of "this won't survive next quarter" matter more, not less.
- **You are now a reviewer-first.** Get good at it. Reviewing well is a different skill than writing well; most of us are out of practice.
- **You set the practices.** AGENTS.md, hooks, the spec discipline — these are senior-engineer artifacts. Don't outsource them.

### Mid-level
- **The fastest-evolving role.** You have enough context to direct the agent and enough humility to verify. Right now this is the highest-leverage place to be in the industry.
- **The trap**: skipping the "do it the hard way once" step. Senior engineers can verify because they've done it. Mid-level engineers who only direct agents will plateau.

### Junior engineers (the hardest path)
- **Simon's point**: *the agent can do what a junior can do.* That's a real career-path problem and we shouldn't pretend it isn't. The traditional "learn by doing the boring tasks" path is broken.
- **What still works**: deep domain learning, debugging, architecture, code review, taste. Less of these are automatable.
- **The trap**: accepting agent output you can't yet evaluate. *"You can't tell the agent did it wrong if you couldn't have done it right."* Pair with a senior; do some work without the agent on purpose; build a baseline you can measure against.
- **Mentorship matters more, not less.** This is the part the field hasn't caught up to.

> *"If you've never debugged a production memory leak by hand, you're going to accept the agent's first plausible-looking fix. That's the failure mode no harness solves."*

<!-- CLAIRE-EDIT (verified): Claire Vo's "manager skill" frame — fits here as the answer to "what skill is becoming valuable" -->
### The skill that's quietly becoming valuable: *managing*

Claire Vo on Lenny's Newsletter, on what actually makes her effective with these tools:

> *"I know how to make an employee successful. That is what you need to make these agents work. You don't need the technical skills. We can figure that out. You need role scoping or design, like voice. How do we talk to customers? How do we talk to each other? The rest of it's easy to follow. The rest of it, we can give to ClaudeCode to figure out."*
> — Claire Vo, *[How OpenClaw changed my life](https://www.lennysnewsletter.com/p/how-openclaw-changed-my-life-claire-vo)* (Lenny's, 2026)

**Why this matters across the role question**:

- **For senior engineers**: the *management* lens is now part of the IC job. Onboarding, scoping, feedback loops, trust calibration — these aren't "manager work you escaped from", they're the new core skill.
- **For mid-career**: this is the upskilling path that's *additive*, not in conflict with what you already do. Lean into it. Pair with someone in your org who actually manages people; ask them how they onboard.
- **For juniors**: this is the *opportunity*. Most senior ICs in your company haven't deliberately built management muscle. The juniors who do — through deliberate study, not just exposure — leapfrog.

The skill is "make an employee successful" applied to a non-human teammate. **Many people in this room have *already* built that muscle. The question is whether you point it at agentic engineering.**

---

## Slide 3 — How to stay sharp (and other things worth saying out loud)

### Skill maintenance

- **The "AI sabbath".** Pick something — a side project, a Friday afternoon — where you don't use AI. Not as a moral position, as muscle memory. The goal isn't purity; it's not letting your taste atrophy.
- **Read more code than you generate.** Agents shift the ratio toward generation. Counter-balance deliberately — read PRs, OSS, internal code without prompting an agent first.
- **Code reviews matter more, not less.** This is where calibration happens. Slow them down on purpose.
- **Measure what's *yours*.** What did you understand, choose, and stand behind? That's your work, regardless of who typed it.

### Job & career questions worth being honest about

- **Will this replace engineers?** Probably not in aggregate (Jevons again — demand expands to fill capacity). Specific *roles* will compress. The skills above are durable.
- **Will my comp drop?** For pure-execution roles in commodity domains, possibly. For judgment-heavy roles, the opposite — leverage = pricing power.
- **What about the next generation?** This is the question we don't have a clean answer to yet. *We* — the senior practitioners in this room — are the ones who get to figure it out. Not the platform vendors. Not the model labs. Us.

### Three things you can do this week

1. **Schedule a no-AI block** — half a day, your call.
2. **Pair with a junior on something *they* drive.** Don't bring the agent. Watch how they solve it.
3. **Review one agent PR slowly** — 30 minutes minimum on a 200-line diff. Find one thing the agent did that you'd have done differently. Tell the team.

---

## Hand-off into Q&A proper

> "These three slides aren't questions I'm answering — they're questions I'm putting on the table. I want them in the room before we open the floor, because they're the ones we don't volunteer.
>
> So — what would you do Monday morning? What did you see today that you want to try? What did I get wrong?"

(Then go to the standard Q&A questions in `workshop-outline.md` if hands don't go up.)

---

## Sources & further reading

- [Simon Willison on Lenny's Podcast — *An AI State of the Union*](https://www.lennysnewsletter.com/p/an-ai-state-of-the-union) — *the* interview to point people at; the senior/junior framing is here
- [BCG — AI productivity research (2024–2025)](https://www.bcg.com/) — search "BCG AI developer productivity"
- [Steve Yegge on cognitive exhaustion](https://sourcegraph.com/blog) — episodic but worth following
- [Sau Sheong (Singapore GovTech) — *Humanity is not ready for this much software*](https://sausheong.com/) [VERIFY exact post URL]
- [Kent Beck Substack on "augmented coding"](https://tidyfirst.substack.com/) — pragmatic senior-engineer take
- [Addy Osmani (Google) on the cognitive shift](https://addyo.substack.com/) — frequent posts on "factory model" effects
- [Ethan Mollick — *One Useful Thing*](https://www.oneusefulthing.org/) — on AI's broader impact

---

## Open questions for me to decide before tomorrow

- [ ] Is this the right place — start of Q&A — or earlier (e.g. between deep dive and Exercise 2 break)? **Lean: start of Q&A. The exercise is the hopeful part; this is the honest part; both belong, in this order.**
- [ ] Three slides or compress to one? **Lean: three. The mental-cost slide alone won't land; the role-question slide is what people are actually thinking; the staying-sharp slide gives them an action.**
- [ ] How explicit to be about my *own* cost / fatigue stories? **Lean: one personal sentence per slide max. The room has heard "I'm so tired from AI" takes; offer something specific instead.**
- [ ] Reference Simon's interview by name and URL? **Lean: yes. The Lenny interview is the canonical source; pointing at it lets the room go deeper without me having to over-summarize.**
