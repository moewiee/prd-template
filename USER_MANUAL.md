# User Manual

This repo turns Claude Code into a product manager. **You are the stakeholder.** You describe what you want, Claude interviews you, and the result is a reviewed PRD in `prds/<slug>/prd.md`.

- [Getting started](#getting-started)
- [Commands and phrases](#commands-and-phrases)
- Use cases
  1. [Turn a rough idea into a PRD](#1-turn-a-rough-idea-into-a-prd-thorough-mode)
  2. [Get a draft fast](#2-get-a-draft-fast-fast-mode)
  3. [Start from existing notes or documents](#3-start-from-existing-notes-or-documents)
  4. [Pause and resume an interview](#4-pause-and-resume-an-interview)
  5. [Disagree with a suggestion or push back](#5-disagree-with-a-suggestion-or-push-back)
  6. [Skip questions you can't answer yet](#6-skip-questions-you-cant-answer-yet)
  7. [Go deeper on one topic](#7-go-deeper-on-one-topic)
  8. [Stop early and draft now](#8-stop-early-and-draft-now)
  9. [Update a finished PRD](#9-update-a-finished-prd)
  10. [Review a PRD written elsewhere](#10-review-a-prd-written-elsewhere)
  11. [Small feature, one-page PRD](#11-small-feature-one-page-prd)
  12. [Interview in one language, PRD in another](#12-interview-in-one-language-prd-in-another)
  13. [Use it in other projects](#13-use-it-in-other-projects)
  14. [Customize for your team](#14-customize-for-your-team)
- [What you get](#what-you-get)
- [Tips for good answers](#tips-for-good-answers)
- [Troubleshooting](#troubleshooting)

---

## Getting started

```bash
cd prd-template
claude
```

Then start in any of these ways. They all lead to the same interview.

| How | Example |
|-----|---------|
| Slash command | `/prd a booking tool for small dental clinics` |
| Just describe it | `I want to build a booking tool for small dental clinics` |
| Ask for a PRD | `Help me write a PRD for a clinic booking tool` |
| From the shell | `claude "/prd a booking tool for small dental clinics"` |

> Don't use `claude -p "..."` (print mode). It replies once and exits, so the interview can't happen.

---

## Commands and phrases

| You type | What happens |
|----------|--------------|
| `/prd <idea>` | Start a new PRD interview |
| `/prd <slug>` | Resume an interview, or update a finished PRD |
| `/prd-review <path>` | Critique a PRD without changing it |
| `yes` (to a numbered question) | Accept Claude's suggested answer |
| `Q3: no, …` | Answer or override a specific question |
| `skip` / `park it` | Leave the question open, recorded in Open questions |
| `go deeper on <topic>` | Extra rounds on one area |
| `draft now` | Stop asking and write the PRD from what's known |
| `pause` | Save progress; resume later |

---

## Use cases

### 1. Turn a rough idea into a PRD (Thorough mode)

**When:** you have an idea in your head and want a complete, well-reasoned PRD.

**You:**
```
/prd An app for warehouse leads to assign picking tasks to their team.
Right now they do it on a whiteboard and people pick the wrong orders.
```

**Claude** asks whether there's anything else to read, then asks two setup questions in a picker:

```
Stakes:          ○ Personal/hobby  ○ Internal tool  ● Customer-facing launch  ○ Enterprise/regulated
Interview mode:  ● Thorough (recommended)  ○ Fast
```

Then it checks what it inferred and starts the rounds:

```
Sounds like a mobile-first B2B app for warehouse staff, likely with roles
(lead vs. picker) and an integration with your WMS. Right?

**Round 1: Problem and users**  ·  covered so far: none

**Q1. What goes wrong today?**
Walk me through the last time a picker grabbed the wrong order. What happened,
what did it cost, and how did someone notice?

**Q2. Who uses this?**
Describe one real lead and one real picker: their shift, the device in their
hand, and how comfortable they are with tech.

**Q3. Device**
Pickers use shared Android scanners or their own phones?
→ My suggestion: shared Android scanners, because that's common in warehouses
  and avoids BYOD policy issues.

Answer by number. "yes" on a question accepts my suggestion.
```

**You:**
```
Q1: Last week a picker took order 1042 instead of 1024, the truck left with the
wrong pallet, and we paid for a re-delivery. Happens ~3x a week.
Q2: Linh is a shift lead, 10 years' experience, uses a tablet. Pickers are
mostly temp workers, low tech comfort.
Q3: yes
```

This repeats for about 5–10 rounds. Claude then plays back its understanding, you confirm, it drafts `prds/warehouse-picking/prd.md`, runs the reviewer, and walks you through the serious findings.

---

### 2. Get a draft fast (Fast mode)

**When:** you want something to react to rather than a long interview.

**You:**
```
/prd internal tool to track which laptops are assigned to which employee
```
Pick **Internal tool** and **Fast** in the setup picker.

Claude asks one or two rounds on the biggest gaps, then drafts. Anything it guessed is tagged inline:

```markdown
FR-4: IT admin can mark a laptop as "in repair". [ASSUMPTION: no approval step needed]
```

Read the draft and correct it in plain words:
```
FR-4 needs manager approval. Also we have ~400 laptops, not 100.
```

---

### 3. Start from existing notes or documents

**When:** you already have meeting notes, a brief, customer interviews, screenshots, or an old PRD.

**You:**
```
/prd docs/notes/clinic-booking-brainstorm.md
```
or
```
I want a PRD for clinic booking. Read these first:
- ~/Downloads/customer-interviews.md
- ~/Downloads/competitor-screens.png
- https://example.com/our-current-booking-page
```

Claude reads everything (handing large files to a subagent), lists each source under **Inputs** in `session.md`, and **skips questions the material already answers**. The interview is shorter and focuses on the gaps. To keep a copy with the PRD, ask: *"copy these into the inputs folder."*

---

### 4. Pause and resume an interview

**When:** the interview spans more than one sitting.

**You:** `pause`

Claude makes sure `prds/clinic-booking/session.md` is up to date (every decision, assumption, and the next questions to ask), then tells you how to resume.

**Later, in a new session:**
```
/prd clinic-booking
```
or just
```
let's continue the clinic booking PRD
```

Claude reads `session.md`, summarizes what's settled and what's open in a few lines, and picks up at the next unanswered question.

---

### 5. Disagree with a suggestion or push back

**When:** Claude's suggested answer is wrong, or you want to explain why.

```
**Q2. Sign-up**
Require patients to create an account before booking?
→ My suggestion: no. Guest booking with phone verification reduces drop-off.
```

**You:**
```
Q2: No, we need accounts. Clinics want patient history across visits.
```

Claude logs it as `DECISION: accounts required. Why: clinics need visit history` and adjusts later questions. If your answer conflicts with an earlier one or carries a real risk, Claude says so **once**, with the trade-off. You still decide.

---

### 6. Skip questions you can't answer yet

**When:** a question needs someone else (legal, finance, engineering).

**You:**
```
Q4: skip, need to ask our compliance person
```

The question goes into the PRD's **Open questions** table with an owner:

```markdown
| OQ-3 | Do we need patient consent for SMS reminders? | Compliance (Hoa) | Before beta | Yes |
```

---

### 7. Go deeper on one topic

**When:** an area feels thin, or it's the risky part of the product.

**You:**
```
go deeper on success metrics
go deeper on what happens when two leads assign the same task
go deeper on risks
```

Claude switches to elicitation techniques (pre-mortem, forced ranking, edge cases, example mapping) for that area, then returns to the normal flow.

---

### 8. Stop early and draft now

**When:** you've said enough, or you're out of time.

**You:** `draft now`

Claude plays back what it knows, asks you to confirm, and drafts. Everything not yet covered becomes `[ASSUMPTION]` tags or Open questions, so nothing is silently made up.

---

### 9. Update a finished PRD

**When:** requirements changed after the PRD was marked `final`.

**You:**
```
/prd clinic-booking
We're adding online payment for deposits. Also drop the SMS reminder feature
for v1, since the budget got cut.
```

Claude:
1. Reads the PRD and the interview log.
2. Flags conflicts, e.g. *"SM-2 measures no-show reduction from SMS reminders. Drop or replace it?"*
3. Asks follow-ups on the new scope (payment provider, refunds, and so on).
4. Updates the PRD with new IDs. Old IDs are never reused.
5. Adds a **Changelog** row and logs the change in `session.md`.

---

### 10. Review a PRD written elsewhere

**When:** a teammate wrote a PRD (or you wrote one by hand) and you want an honest critique.

**You:**
```
/prd-review ~/Downloads/checkout-redesign-prd.md
```
or
```
review the PRD in prds/clinic-booking
```

The reviewer subagent checks seven dimensions: problem clarity, decision-readiness, substance over theater, strategic coherence, done-ness, scope honesty, and shape fit. It writes `review.md` and you get a short summary:

```
Verdict: Clear problem and good scope, but not ready for engineering. 4 of 9
Must FRs have no testable acceptance criteria, and there's no counter-metric.

critical 0 · high 3 · medium 5 · low 4

#1 [high] §4.2 FR-6: "checkout should be fast" → set p95 < 1.5 s on 4G
#2 [high] §9: only activity metrics → add conversion-rate target + refund-rate counter-metric
#3 [high] §6: guest checkout neither in nor out of scope → decide explicitly
```

Then pick one: fix them now (Claude interviews you on the gaps) or leave the PRD as is.

---

### 11. Small feature, one-page PRD

**When:** it's a small change, and a 10-page PRD would be overkill.

**You:**
```
/prd add a "copy invoice link" button to the invoice page
```
Pick **Personal/hobby** or **Internal tool** and **Fast**.

Claude asks a few questions and produces a one-page PRD: short summary, a few stories with acceptance criteria, and in/out of scope. Length scales with stakes.

---

### 12. Interview in one language, PRD in another

**When:** you think best in your native language but the PRD is for an English-speaking team.

**You:**
```
/prd Tôi muốn làm app quản lý ca làm việc cho nhân viên quán cà phê.
Phỏng vấn bằng tiếng Việt, nhưng viết PRD bằng tiếng Anh.
```

Claude interviews you in Vietnamese and writes `prd.md` in English. If you don't specify, the PRD uses the interview language.

---

### 13. Use it in other projects

**When:** you want `/prd` available in any repo, for example next to the code.

```bash
cp -r .claude/skills/prd .claude/skills/prd-review ~/.claude/skills/
cp .claude/agents/prd-reviewer.md ~/.claude/agents/
```

Now `/prd` works everywhere. In a code repo, Claude can also look up facts from the codebase (existing features, data models) instead of asking you.

> Outside this repo there's no `CLAUDE.md` rule, so starting from a plain description depends on Claude recognizing the request. Use `/prd` when you want to be sure.

---

### 14. Customize for your team

| You want | Edit |
|----------|------|
| Your company's PRD format or section names | `.claude/skills/prd/assets/prd-template.md` |
| Always ask about analytics events, legal review, pricing… | `.claude/skills/prd/references/question-bank.md` |
| A stricter or looser review | `.claude/skills/prd/references/quality-rubric.md` |
| Different interview behavior (round size, tone, steps) | `.claude/skills/prd/SKILL.md` |

Changes take effect in the next session. No other configuration is needed.

---

## What you get

```
prds/clinic-booking/
├── session.md   # interview log: every decision + why, assumptions, open questions, next questions
├── prd.md       # the PRD
├── review.md    # reviewer findings
└── inputs/      # (optional) material you provided
```

The PRD (`prd.md`) contains:

| § | Section | § | Section |
|---|---------|---|---------|
| 1 | Summary: TL;DR, vision, thesis | 8 | Constraints, dependencies, assumptions |
| 2 | Problem and motivation | 9 | Success metrics, including counter-metrics |
| 3 | Users and user journeys (UJ-n) | 10 | Risks and mitigations |
| 4 | Features and requirements (FR-n), with acceptance criteria | 11 | Rollout, stakeholders, timeline |
| 5 | Non-goals | 12 | Glossary |
| 6 | MVP scope (in / later) | 13 | Open questions (OQ-n) |
| 7 | Non-functional requirements (NFR-n) | 14 | Assumptions index |

It also has optional sections added only when relevant (payments, compliance, API, AI/ML, offline, and so on), plus an appendix and a changelog.

---

## Tips for good answers

- **Tell stories, not opinions.** "Last Tuesday Linh spent 20 minutes reassigning tasks because…" beats "it's slow."
- **Give numbers when you can.** Users, volumes, response times, deadlines, budget. If you don't know, say so; it becomes an open question.
- **Say why.** The reason behind a decision goes into the log, which helps the next person who wonders why.
- **Name what's out.** Saying what you *won't* build is as valuable as what you will.
- **Answer by number** (`Q1: …, Q2: yes, Q3: skip`). It's faster, and nothing gets lost.
- **You can always correct the draft** in plain words. You don't have to get everything right in the interview.

---

## Troubleshooting

| Problem | Fix |
|---------|-----|
| Claude wrote a PRD without interviewing | Say "interview me first", or start with `/prd` |
| Too many questions | Pick Fast mode, say `draft now`, or "ask fewer questions per round" |
| Questions are too generic | Give more context up front, or hand over existing documents (use case 3) |
| Lost track after closing the terminal | `/prd <slug>` resumes from `session.md` |
| Wrong slug or folder name | "rename this PRD to `<new-slug>`" |
| Want to start over | "start a new PRD for this, and ignore the old session" |
