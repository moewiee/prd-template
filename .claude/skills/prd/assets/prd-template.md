# PRD Template

How to use this template:
- **Core sections** (§1–§14) are the default spine. Drop a section only when a reviewer would agree it's pointless for this product, and scale each section's depth to the stakes.
- **Optional sections** (bottom of this file): add the ones whose concerns came up in the interview, in whatever position reads best. If a real concern has no section here, add your own.
- Remove all guidance text in *italics* and [brackets] from the final PRD.
- IDs (`UJ-`, `FR-`, `NFR-`, `SM-`, `R-`, `OQ-`) are global, contiguous, and never reused, even when you reorder features.

---

```markdown
---
title: {Product / Feature Name}
slug: {slug}
status: draft            # draft | in-review | final
stakes: {hobby | internal | launch | enterprise}
owner: {stakeholder name}
author: Claude (PRD interview) with {stakeholder name}
created: {YYYY-MM-DD}
updated: {YYYY-MM-DD}
---

# PRD: {Product / Feature Name}

## 1. Summary
**TL;DR:** [Two or three sentences a busy executive can read alone: what we're building, for whom, and the outcome we expect.]

**Vision:** [One or two paragraphs. What this is and why it matters to the user. It should be specific enough that it couldn't be pasted into a competitor's PRD unchanged.]

**Thesis:** [The bet in one sentence: "We believe {users} will {behavior} because {insight}, which we'll know when {metric moves}."]

## 2. Problem and motivation
### 2.1 Problem
[The problem from the user's point of view. What happens today, and what it costs them in time, money, errors, or frustration.]

### 2.2 Current workarounds
[How people cope today. Workarounds point straight at requirements.]

### 2.3 Evidence
[Data, quotes, tickets, lost deals, observations. Say so if the evidence is thin; that's an open question, not a gap to hide.]

### 2.4 Why now *(include when timing matters)*
[A deadline, market shift, customer commitment, or new capability.]

## 3. Users
### 3.1 Target users
*One line per user type, with their job-to-be-done. Avoid persona theater: include a persona only if it drives at least one decision in this PRD.*
- **{User type}:** {who they are, context}. *Job:* {what they're trying to get done}.

### 3.2 Not for (v1) *(include when the boundary isn't obvious)*
- {Who this is explicitly not for, and why}

### 3.3 Key user journeys
*Named protagonist, real context. FRs reference these by ID ("realizes UJ-2").*

- **UJ-1. {Name} {does the thing}.**
  - **Context:** {who they are and why they're here}
  - **Entry:** {where they come from; signed in or not; which device or surface}
  - **Path:** {3–5 concrete steps}
  - **Value moment:** {when and how they know it worked}
  - **Edge case:** {one realistic failure and what happens next}

## 4. Features and functional requirements
*Group FRs by feature. Describe behavior first, then the FRs. Priorities use MoSCoW: Must / Should / Could. "Won't" items go in §5 or §6.*

### 4.1 {Feature name}
**Description:** [How the feature behaves from the user's side, including rules and states. Realizes UJ-X. Tag inferences inline as `[ASSUMPTION: …]`.]

| ID | Requirement | Priority | Realizes |
|----|-------------|----------|----------|
| FR-1 | {Actor} can {capability} {under conditions}. | Must | UJ-1 |
| FR-2 | … | Should | UJ-1 |

**Acceptance criteria**
- **FR-1**
  - Given {state}, when {action}, then {observable result}.
  - {Another testable condition, including the error or edge case.}
- **FR-2**
  - …

**Out of scope for this feature:** {bounds, if any}
**Notes / open items:** {feature-specific questions → link to §13}

### 4.2 {Feature name}
…

## 5. Non-goals
*What this product will not be or do. This prevents "while we're at it" scope creep downstream.*
- {We are not building X, because …}

## 6. MVP scope
### 6.1 In scope (v1)
- {Feature / FR range}

### 6.2 Later (v2+)
- {Item}: {one-line reason it's deferred}

## 7. Non-functional requirements
*Numbers, not adjectives. Include only what's real for this product.*

| ID | Category | Requirement | How measured |
|----|----------|-------------|--------------|
| NFR-1 | Performance | {e.g. p95 page load < 2 s on 4G} | {RUM / load test} |
| NFR-2 | Availability | {e.g. 99.9% monthly} | {uptime monitor} |
| NFR-3 | Security / privacy | {e.g. PII encrypted at rest; role-based access} | {review / pen test} |
| NFR-4 | Accessibility | {e.g. WCAG 2.1 AA} | {audit} |
| NFR-5 | Platforms | {browsers / OS / devices} | {test matrix} |

## 8. Constraints, dependencies, and assumptions
### 8.1 Constraints
- {Budget, deadline, team, mandated technology, legal}

### 8.2 Dependencies
- {Team / vendor / API / data / approval}: {what we need, and by when}

### 8.3 Key assumptions
- {Assumption that, if false, changes the plan}: {how and when we'll validate it}

## 9. Success metrics
*Each metric validates specific FRs. Counter-metrics guard against optimizing the wrong thing.*

| ID | Metric | Baseline | Target | When | Validates |
|----|--------|----------|--------|------|-----------|
| SM-1 | {primary metric} | {now} | {goal} | {30/90 days} | FR-1, FR-3 |
| SM-2 | {secondary} | | | | |
| SM-C1 | **Counter:** {must not get worse} | {now} | {limit} | | balances SM-1 |

*For hobby stakes, one sentence can be enough: "Success = I use it weekly for 3 months."*

## 10. Risks and mitigations
| ID | Risk | Likelihood | Impact | Mitigation |
|----|------|------------|--------|------------|
| R-1 | {risk} | Low/Med/High | Low/Med/High | {plan} |

## 11. Rollout, stakeholders, and timeline
- **Rollout:** {big bang / beta / feature flag / phased}, {who first}
- **Milestones:** {milestone}: {date or relative timing}, {fixed or flexible}
- **Stakeholders:** {name/role}: {decides / approves / consulted / informed}

## 12. Glossary
*Every domain term, defined once. Use these terms exactly throughout, with no synonyms.*
- **{Term}:** {definition}

## 13. Open questions
| ID | Question | Owner | Needed by | Blocking? |
|----|----------|-------|-----------|-----------|
| OQ-1 | {question} | {who} | {date / milestone} | Yes/No |

## 14. Assumptions index
*Every inline `[ASSUMPTION: …]`, collected here for confirmation.*
- §{x.y}: {assumption}

---

## Appendix
### A. Technical notes
[Implementation ideas the stakeholder volunteered, technology preferences, and rejected alternatives with reasons. Kept out of the main body so the PRD stays about *what* and *why*.]

### B. Interview record
Decisions and their reasoning are logged in `session.md` in this folder.

## Changelog
| Date | Change | Reason |
|------|--------|--------|
| {YYYY-MM-DD} | Initial draft | PRD interview |
```

---

## Optional sections (add when the concern applies)

**Product and experience**
- **Experience and tone:** look and feel, reference and anti-reference products, voice for in-product text.
- **Information architecture:** top-level screens and navigation; a Mermaid or ASCII sketch helps.
- **Onboarding:** first-run flow, time to first value.
- **Monetization:** pricing model, plans, what's gated.

**Business and enterprise**
- **Business case / ROI:** expected benefit, cost, payback.
- **Roles and permissions:** a matrix of role × capability.
- **Integrations:** systems, direction of data flow, owner of each.
- **Operational requirements:** SLAs, RTO/RPO, support tier, on-call.
- **Data governance:** residency, classification, retention, deletion.
- **Rollout and change management:** training, comms, migration of existing users.

**Regulated**
- **Compliance:** each applicable regime → the concrete obligations → the FR/NFR that satisfies it.
- **Audit trail:** what gets logged, who can read it, how long it's retained.

**Developer products**
- **API surface:** resources and operations, auth, rate limits, error model.
- **Versioning and deprecation policy.**
- **Performance budgets:** latency, throughput, payload size.

**AI / ML**
- **Quality bar:** examples of good and bad output, evaluation method, acceptance threshold.
- **Failure handling:** human review, fallback, user feedback loop.
- **Cost and latency budget.**
- **Data policy:** what may be sent to model providers, retention.

**Mobile / hardware**
- **Offline and sync:** what works offline, conflict resolution.
- **Device constraints:** permissions, battery, memory, connectivity.
- **Update mechanism.**

**Small scope (1–3 stories)**
- Collapse §4 into a short **Stories** list: "As a {user}, I can {action} so that {outcome}. Acceptance: {criteria}." Keep §1, §5, and §6 brief. The whole PRD fits on one page.
