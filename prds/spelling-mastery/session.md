---
slug: spelling-mastery
status: final     # interviewing | drafting | in-review | final
stakes: hobby
mode: thorough
shape: Consumer edtech web app, family use (child learner, parent, content admin)
concerns: [children's personal data / parental consent, audio pronunciation, adaptive spaced review, admin content publishing, curriculum content licensing, handwriting result capture]
created: 2026-10-11
updated: 2026-10-11
---

# Interview session: Spelling Mastery

## Inputs
- verbal brain dump (/prd args, 2026-10-11): personalized English vocabulary + spelling web app for children who understand words but can't write them accurately. Curriculum references: Global Success, Cambridge, Oxford. Daily 15-min session cycle: listen → understand word patterns → spell from memory → targeted correction → spaced review. Adapts to each child's mistakes and retention; prioritizes independent recall over recognition or copying. Ongoing journey, not a fixed course. Expandable word library: admins add/organize/publish words and collections without code changes. Parents track lasting progress, see recurring difficulties, record handwriting results. Balances new words vs. review to keep daily load manageable.

## Coverage
| Area | Status |
|------|--------|
| A. Problem and motivation | ☑ settled |
| B. Users and journeys | ☑ settled (admin journey covered by content decisions) |
| C. Scope and non-goals | ☑ settled |
| D. Capabilities (FRs) | ☑ settled (audio source pending in E) |
| E. Quality and constraints | ☑ settled |
| F. Success metrics | ☑ settled |
| G. Risks, dependencies, and rollout | ☑ settled (engagement mitigation proposed in playback) |
| Consumer / branded product (monetization, onboarding, tone) | ☑ settled |
| Regulated domain (children's data, consent) | ☑ settled |
| Content / curriculum library (admin CMS, licensing) | ☑ settled |
| Learning engine (spaced review, error diagnosis, daily load) | ☑ settled |

*Status values: ☐ open · ◐ partial · ☑ settled · ⏸ parked*

## Open frontier
PRD is final. Open items carried in prd.md §13 (none block design or engineering):
- OQ-1 starter list location (blocks Minh's start, not the build), OQ-2 Speech API provider (blocks audio integration), OQ-3 diagnostic pool compilation (blocks Minh's start), OQ-4 AI provider (non-blocking), OQ-5 threshold review (non-blocking, tunable via FR-81), OQ-6 meaning-check images (non-blocking).
Resume with `/prd spelling-mastery` to update.

## Log
*Append-only. One line per entry. Types: DECISION, ASSUMPTION, OPEN, CHANGE, NOTE.*

### Round 0: Intake, 2026-10-11
- NOTE: Workspace created from brain dump; slug `spelling-mastery`.
- ASSUMPTION: Vietnam is the primary market, since Global Success is the Vietnamese MOET English textbook series. *Confirm by:* Round 1.
- ASSUMPTION: Interview and PRD in English (stakeholder wrote in English). *Confirm by:* Round 1.

### Calibration, 2026-10-11
- DECISION: Stakes = personal / hobby. *Why:* stakeholder choice. Target PRD length is about 2 pages; regulatory depth scales down unless strangers' children will use it.
- DECISION: Interview mode = thorough. *Why:* stakeholder choice.

### Round 1: Problem and users, 2026-10-11
- DECISION: Initial learner is the stakeholder's 8-year-old son, Grade 2 (Vietnam), Global Success at school, Cambridge A2 Flyers level. *Why:* the product's origin.
- NOTE: Core problem is orthographic recall, not vocabulary knowledge: he recognizes and understands words but can't reproduce the exact letter sequence (e.g. friend→freind, beautiful→beautifull). His real mistakes have not been collected or classified yet.
- DECISION: The app classifies error patterns (letter order, vowel patterns, silent letters, double consonants, irregular spelling) and targets interventions to them instead of treating all wrong answers as equal. *Why:* stakeholder's core thesis.
- DECISION: School grade, vocabulary/English proficiency, and spelling ability are separate, independently assessed dimensions. *Why:* a Grade 2 child at Flyers level may still need elementary phonics patterns.
- NOTE: Today there is no systematic spelling practice, only schoolwork. Copying and multiple-choice create a false impression of mastery.
- DECISION: The learning model is active recall + immediate corrective feedback + spaced repetition. On a misspelling: identify the problem segment, explain it, have the child reconstruct the word independently, then retest over the following days. *Why:* stakeholder's "because" example.
- DECISION: Six-month outcomes: fewer recurring mistakes, retention of words learned weeks or months earlier, transfer of patterns to unfamiliar words, more independence and less frustration, a ~15 min/day habit. The parent no longer picks review words manually. *Why:* stakeholder's success picture. The "worth it" moment: he writes a paragraph alone and correctly spells words he used to struggle with.
- DECISION: The product has no end date and supports development over multiple school years. *Why:* stakeholder: "not a 12-week course".
- DECISION: Audience is Vietnamese children aged 6–11 (Grades 1–5).
- DECISION: Child UI in simple English with Vietnamese explanations and translations on demand. Parent UI Vietnamese by default. Admin UI Vietnamese by default with English localization. Natural English audio, with selectable British/American accent preferred. Teaching explanations in simple English supported by Vietnamese. *Why:* English exposure without comprehension barriers.
- DECISION: PRD and technical docs in English. Interview stays in English.
- DECISION: Cambridge, Oxford, and MOET are curriculum references, not boundaries. Any new vocabulary can be added.
- DECISION: Three distinct roles: Admin (content), Parent (child profiles, progress, preferences, priority words from schoolwork), Child (daily session only). The stakeholder holds Admin + Parent for now, but the roles stay separate in the system.
- DECISION: 1–3 child profiles per family in v1.
- DECISION: The child completes the daily session alone: open the app → "Start Learning" → ~15 min → done. The app selects words, adjusts difficulty, corrects, and schedules. Handwriting checks may need a parent.
- DECISION: v1 is for personal family use: no public registration, no multi-tenant admin. Ownership boundaries between users, child profiles, learning records, and content must allow multi-family support later without a rebuild. *Why:* may open to other families later.
- DECISION: Privacy: minimal personal data, no ads, no unnecessary tracking, children's learning records private.
- NOTE: An existing "60-word, 12-week curriculum" is the starter collection, not the whole journey. Not yet provided as an input.
- NOTE: Product philosophy (stakeholder's words): "a scientifically grounded, adaptive spelling tutor that feels effortless to an 8-year-old, provides meaningful visibility to parents, and can grow with the child for years without requiring constant manual intervention."

### Round 2: Daily session and learning engine, 2026-10-11
- DECISION: Placeholder child name "Minh" in the PRD. *Why:* stakeholder prefers not to use the real name.
- DECISION: Core UJ: at home after school/evening on a tablet or laptop. Home screen shows simple progress + one "Start Learning" button, no menus, curriculum choice, or stats. A varied activity mix, each activity tied to a learning objective. Word presented with audio, an example sentence, and Vietnamese meaning on demand. New words are taught first (meaning + spelling structure); review words are tested before showing the spelling.
- DECISION: Correction loop: on an error (e.g. "becaus"), give constructive, specific feedback ("You almost got it! One letter is missing."), show the correct spelling with the faulty segment highlighted, and give a brief explanation. Hide the word, bring it back a few exercises later with no hints. Same-session success does not count as mastery. Repeated struggle with a pattern triggers targeted pattern exercises instead of repeating the full word.
- DECISION: The session ends after ~15 min at the end of the current exercise with a short progress-based summary ("You practised 12 words and improved on 3 tricky spellings"). No scores, grades, or leaderboards. Never punitive, never "falling behind". *Why:* he should leave feeling he accomplished something.
- DECISION: Platforms: tablet landscape is primary; laptop/desktop browser secondary; phone responsive but not primary.
- DECISION: Input: large on-screen full-alphabet QWERTY keyboard + physical keyboard. No autocorrect, prediction, or completion. Large touch targets. No typing outside spelling exercises.
- DECISION: Letter tiles (subset of letters) only in remedial exercises; those results are recorded as scaffolded, not independent. *Why:* a subset turns recall into recognition/arrangement.
- DECISION: Handwriting is a separate mode on paper with parent-recorded results. No OCR/handwriting recognition in v1. *Why:* complexity without learning gain.
- DECISION: The system distinguishes typing slips from spelling-knowledge errors as far as reasonable (e.g. adjacent-key taps). It uses repeated observations and parent-confirmed handwriting to tell them apart.
- DECISION: Mastery (independent spelling) = ≥3 independent correct attempts, on ≥3 separate days, spanning ≥14 days, ≥7 days between the final two qualifying checks, no hints or scaffolding in qualifying attempts. Mastered words get maintenance reviews. A genuine later error returns the word to learning/remediation; a single apparent slip does not necessarily remove mastery.
- DECISION: Three separate per-word indicators: independent spelling mastery, correct usage in context, parent-verified handwriting mastery. Typing mastery does not imply the other two.
- DECISION: Workload is time-budget driven: default ~15 min/day, 5 days/week. Priority: (1) due reviews, (2) recurring-error words, (3) recently introduced patterns, (4) new words if time remains, (5) contextual spelling when appropriate.
- DECISION: New words: initial target 5 per WEEK (not per day), adapted to performance (faster if strong, slower if struggling). New introductions pause when the backlog is large. Overdue backlog after missed days is spread across future sessions, never dumped at once. Missed days never count as incorrect answers.
- DECISION: Open-ended journey with no "program complete". The 12-week/60-word set is only a starter collection.
- DECISION: Error diagnosis is deterministic and rule-based in v1, no LLM in the learning loop. Sequence alignment of attempt vs. target classifies omission, insertion, substitution, transposition, doubling, vowel-pattern confusion, and morphological-structure errors.
- DECISION: Admin-defined word metadata: phonemes/graphemes where relevant, syllable boundaries, spelling patterns, irregular segments, common misspellings, morphological structure. Explanations must be linguistically accurate (e.g. not every final e is a "silent-e" pattern).
- DECISION: Separate the observed error from the inferred learning difficulty. A difficulty is inferred only from repeated errors across related words, aggregated over time. *Why:* one freind→friend doesn't prove a vowel-team problem.
- DECISION: AI is not a v1 dependency. Later AI-assisted authoring (tag suggestions, sentences, explanations) is allowed, but all AI content requires admin review before publication. No LLM-generated content in child sessions. *Why:* fast, predictable, cheap, reliable; no unverified rules.
- DECISION: The starter 60 words come from an earlier PRD discussion and have no verified CSV. Treat them as sample content until source mappings and annotations are reviewed. Extract, validate, and convert them to a seed dataset.
- DECISION: An initial diagnostic assessment establishes the baseline using words he already understands, captures exact attempts, and identifies recurring errors. This drives the personal plan.
- DECISION: Content expansion is core (v1 Must): add single words, bulk CSV import, organize into collections (topic, curriculum, difficulty, pattern), edit annotations/teaching content, publish/unpublish collections, assign collections or words to a child, all without redeploy. A word can be in many collections with one learning history per child. New library content never auto-increases the daily workload.
- NOTE: Engine guiding principle (stakeholder): every exercise either teaches something unknown, strengthens something emerging, or verifies retention. Optimize for long-term independent spelling, not completion, streaks, or short-term accuracy.
- OPEN: Location of the earlier PRD containing the 60-word list. Not found in this repo (searched 2026-10-11). *Owner:* stakeholder.

### Round 3: Diagnosis, activities, content effort, 2026-10-11
- DECISION: Initial diagnostic: adaptive, low-pressure, 2–3 sessions of ~10 min in week 1. Pool of ~40 words from Cambridge Starters/Movers/Flyers + relevant Global Success, covering vowel teams, consonant clusters, silent letters, doubling, suffixes, irregulars.
- DECISION: The diagnostic checks meaning before spelling. Unknown-meaning words are excluded from the spelling diagnostic and classified as vocabulary to teach. *Why:* separate vocabulary from spelling.
- DECISION: Known words are tested by pure dictation (word + context sentence, no hints, no corrective feedback). No aggressive early stopping: a pattern is labelled "Insufficient evidence" until enough observations exist.
- DECISION: Diagnostic outputs: baseline spelling accuracy; per-pattern profile (Secure / Emerging / Not Yet / Insufficient Evidence); error-type distribution; vocabulary-comprehension vs. spelling-recall comparison; auto-generated initial learning queue. No repeated formal diagnostics afterwards; calibration continues in normal sessions.
- DECISION: v1 activity menu is limited to five types: Teach (instructional, the first success is not mastery evidence), Recall Dictation (primary mastery evidence; no hints, tiles, visible answer length, or prediction; only the first submitted answer counts), Segment Repair (scaffolded, never counts toward mastery), Pattern Family (taught words + ≥1 untaught transfer probe; probes feed the pattern-proficiency model, not word mastery; taught vs. probe words distinguished), Sentence Dictation (target words scored; context measured separately from isolated recall).
- DECISION: Multiple choice, copying, whole-word unscramble, and spot-the-mistake are excluded from the core loop and never count as mastery evidence. Possible future optional scaffolds.
- DECISION: Error confidence has three classes: Confirmed spelling error / Possible input slip / Uncertain. A possible slip gets normal corrective feedback, has reduced weight in remediation, and does not demote a mastered word, but an incorrect first submission never counts as successful recall. Repeats or matching handwriting errors raise spelling-error confidence. *Why:* intent can't be inferred from one attempt.
- DECISION: Free editing while composing; no pre-submit retry; the first submitted answer is the recorded attempt.
- DECISION: Tiered metadata. Required to publish: unique word ID, publication status, canonical spelling, Vietnamese meaning, English audio (UK or US), one age-appropriate example sentence, syllable breakdown, ≥1 reviewed spelling-pattern segment. Optional: full phoneme–grapheme alignment, multiple patterns, irregular segments, morphology, common misspellings, difficulty, curriculum references, related words/families. *Why:* annotation must not bottleneck expansion (accepted the push-back).
- DECISION: Graceful degradation: without enhanced metadata, the engine reports observable alignment differences only. It never invents linguistic explanations or asserts pattern weakness without enough evidence.
- DECISION: CSV bulk import validates required fields, detects duplicates, and flags missing/inconsistent annotations before publication. v1 uses deterministic validation + manual review; future AI suggestions need review.
- DECISION: Handwriting check: Parent Dashboard → Handwriting Check → system picks 5–10 words, prioritizing strong typing recall without handwriting verification → plays word + sentence → child writes on paper → parent marks ✓/✗ and optionally enters the exact misspelling → handwriting progress updated. ~1/week, ~5 min, outside the 15-min budget. Skippable with no effect on regular progression.
- DECISION: Handwriting mastery is independent of typing mastery. A parent-entered misspelling runs through the same alignment rules. ✗ without spelling is recorded as a failed attempt with no invented category.
- DECISION: Evidence model: Instructional performance (cannot establish mastery) / Independent recall (establishes mastery after spaced observations) / Transfer + contextual performance (tracked separately).

### Round 4: Parent experience and child motivation, 2026-10-11
- DECISION: Diagnostic meaning check: hear the word, choose from 3 pictures or Vietnamese meanings, or "I don't know". Correct → eligible for spelling assessment. Wrong/unknown → Vocabulary to Teach queue. The spelling stays hidden throughout (no text in images, no hints, no feedback that reveals it). Distractors plausible but unambiguous. Results stored separately from spelling. Excluded words can be reassessed after instruction. A correct pick = receptive vocabulary evidence only.
- DECISION: Parent Dashboard answers three questions: practising consistently? genuinely improving? struggling with what, and what to do?
- DECISION: Weekly activity (sessions, time, new words, newly verified mastery) is labelled as activity, not as evidence of learning.
- DECISION: Lasting progress shows the state distribution New → Learning → Reviewing → Mastered → Maintained. Headline metric is 30-day retention: denominator = eligible independent recall attempts on words whose relevant learning/review exposure was ≥30 days earlier. Shown as % plus sample size ("87% (26/30)"). "Insufficient data" when the sample is too small. Simple trend: improving / stable / declining.
- DECISION: Recurring difficulties: top 3–5 pattern weaknesses with error count, word count, and evidence level ("ie/ei — 4 errors across 3 words — Moderate evidence"), linked to affected words and exact attempts. No overinterpreting isolated errors.
- DECISION: Three skills tracked and shown separately (typed recall, sentence context, parent-verified handwriting). Never combined into one opaque mastery score.
- DECISION: Recommended Actions section with optional parent actions (e.g. pattern already scheduled for extra practice, school words due, N words mastered by typing but not handwriting-checked). The system handles most interventions automatically.
- DECISION: No sophisticated analytics in v1: simple bars, trends, drill-downs.
- DECISION: School priority words are a scheduling constraint, not a separate system. The parent selects library words, adds new ones, or pastes a list. Unknown words become drafts with guided minimum metadata before publication.
- DECISION: Optional deadline. The engine prioritizes introduction, schedules extra recall before the deadline, gives more time to repeatedly misspelled words, trims lower-priority activities, and respects the 15-min budget. It may exceed the 5-new/week target for priorities. No mastery guarantee. If the workload is unrealistic, it warns the parent ("12 priority words remaining. Approximately 4 may need additional practice beyond the available sessions."), with estimates based on actual practice data.
- DECISION: After the deadline, priority words return to normal spacing. Passing a school test ≠ mastery.
- DECISION: Motivation theme is the Word Garden. It grows with cumulative verified mastery, not activity volume. New word = journey starts, no permanent reward. Verified mastery unlocks a plant/flower. Maintenance successes make it grow. Missed days never kill plants. Mistakes and later remediation never remove earned rewards. The reward system is independent of the visual theme.
- DECISION: End-of-session celebration is brief, specific, and age-appropriate ("You finally spelled 'beautiful' correctly without help!"). No excessive animation, random rewards, or addictive engagement loops.
- DECISION: Visual style: friendly and colourful but not overstimulating, large type, clear interactions, gentle animation, minimal distraction during exercises, consistent garden theme.
- DECISION: Auth: parent email + password with a remembered secure device session. Default landing is the child profile selector (nickname, illustrated avatar, profile card). Tap to enter; no child email/password. 1–3 profiles.
- DECISION: Parent/Admin areas need a parent PIN for everyday access, with a retry limit. Password reauthentication for sensitive account actions. Authorization enforced on the backend, not by hiding UI or checking the PIN client-side.
- DECISION: Child profile data: nickname, optional birth year, school grade, English level, avatar, preferences, progress. No real name, school, photo, or email.
- DECISION: Multi-family-ready: profiles belong to a family account; records isolated per family and child; parents can export or delete children's records; child sessions can't access other profiles; public registration disabled in v1; no ads or third-party behavioural tracking.
- DECISION: Admin (global library, annotations, collections, publication) and Parent (children, priorities, progress, family settings) are separate roles.
- NOTE: Five v1 principles: (1) independent recall over recognition, (2) evidence-based personalization, (3) minimal parental workload, (4) continuous learning via the admin library, (5) healthy motivation. Ideal result: the son willingly uses it 15 min/day while the parent can confidently see spelling improving over months and years, not just exercise completion.

### Round 5: Constraints and scope, 2026-10-11
- NOTE: A team of developers will build it (not solo). Hours, budget ceiling, and target date not given yet.
- DECISION: v1 scope = all proposed Must + Should + Could items. Out of scope (Won't, v1): OCR/handwriting recognition; LLM in the learning loop; public registration / multi-family admin; native apps; teacher/classroom accounts; recognition activities as mastery evidence; leaderboards, streaks, random rewards; payments; fully offline mode. *Why:* stakeholder: "everything except Won't".
- DECISION: Audio uses a high-quality third-party Speech (TTS) API. The stakeholder provides the API key. *Why:* stakeholder choice.
- ASSUMPTION: Audio is pre-generated at save time and stored (UK + US voices), with admin preview/regenerate/upload-recording; no live TTS calls during child sessions; the API key is held server-side only. *Confirm by:* Round 6.
- DECISION: Connectivity: online needed to start a session. On a mid-session drop, finish the current exercise; submitted answers are kept locally and synced on reconnect; no attempt lost. Feedback ≤0.5 s after Submit; audio starts ≤1 s after the replay tap. Full offline mode is Won't. *Why:* accepted suggestion.
- DECISION: Copyright/licensing is not a concern for this PRD. The library may hold content as the admin sees fit. *Why:* stakeholder: "don't worry about copyright". Risk noted for any future multi-family release.

### Round 6: Metrics, risks, quality, 2026-10-11
- DECISION: A single v1 release containing Must + Should + Could. Minh starts learning after v1 is complete; no M1/M2 split. A large developer team. No fixed date given. *Why:* stakeholder choice.
- DECISION: Primary metric: 30-day independent-recall retention ≥80% by month 3, sustained through month 6. Baseline = diagnostic accuracy on meaning-known words. Secondary: confirmed-error recurrence rate −50% from month 1 to 3; transfer-probe accuracy rising per pattern; handwriting accuracy on typing-mastered words ≥75%; ≥4 of 5 planned sessions/week. Counter-metrics: sessions >18 min; abandoned sessions; parent time <20 min/week including handwriting. Reviewed monthly, first real read at day 60. *Why:* accepted suggestion.
- DECISION: Accessibility: child-friendly font with distinct letterforms (single-storey a; distinct b/d/p/q, I/l/1); error highlights by colour + underline/outline, never colour alone; unlimited replay + slow replay; WCAG 2.1 AA contrast; honour reduced-motion. Daily backups of learning records, 30-day retention. *Why:* accepted suggestion.
- DECISION: Full-length PRD (~10–15 pages) with testable acceptance criteria; MoSCoW labels mean build order within v1. *Why:* a dev team builds from it.
- DECISION: (confirms Round 5 assumption) TTS is pre-generated via the stakeholder's Speech API at save time and stored, in UK + US voices; admin can regenerate/replace; no live calls in child sessions; API key server-side only.
- NOTE: Top risk (stakeholder): Minh doesn't like the app. Made worse because he first uses it only after the full v1 is built.

### Playback, 2026-10-11
- DECISION: Playback confirmed in full ("Yes, everything is right"), including the proposed mitigation: 2–3 playtests with Minh on a prototype or early build of the child flow during development, before the full v1 release. *Why:* addresses the top risk (Minh doesn't like the app) without changing v1 scope.
- NOTE: Drafting prd.md. Thresholds the stakeholder didn't specify (evidence levels, spacing intervals, slip window, PIN lockout, etc.) go in as [ASSUMPTION] tags.
- NOTE: prd.md draft written (FR-1..FR-73, NFR-1..13, SM-1..5 + SM-C1..C3, R-1..9, OQ-1..6). Sent to prd-reviewer.

### Review, 2026-10-11
- NOTE: prd-reviewer verdict: ready for design, not engineering. The learning-engine core is underspecified (state transitions, pre-mastery spacing, diagnostic hand-off, eligibility) and some rules conflict. 2 critical, 12 high, 12 medium, 4 low.
- NOTE: Reviewer #11 (AI authoring "later" vs v1) missed the Round 5 decision that put Could items, including AI suggestions, into v1. The real inconsistency is §8.1 (release-blocking) vs OQ-4 (non-blocking).
- DECISION (R1): Pre-mastery spacing: after introduction the first check is at +1 day, then +3 after the 1st qualifying correct recall, +7 after the 2nd, +7 after each further one until Mastered (~18 days). After a Confirmed error, re-check at +1. Due dates on non-planned days roll forward. After an error, earlier correct recalls still count toward the 3-attempt/3-day rules, but the 14-day span and 7-day final gap restart from the error. *Why:* accepted reviewer #1/#2 fix.
- DECISION (R2): A word spelled correctly in the diagnostic skips Teach and enters Reviewing with 1 qualifying recall; next check +3 days. Diagnostic misspellings count toward pattern-weakness evidence, not SM-2.
- DECISION (R3): Eligible for introduction = Published AND assigned to the child (directly or via an assigned collection). Order: priority words → words in Not Yet/Emerging patterns → assigned collection order. With nothing to introduce, sessions run reviews only. With nothing due, the home screen says "All done for today! Come back tomorrow."
- DECISION (R4): Priority words with a deadline ≤7 days away come right after due reviews (slot 1) and are exempt from the backlog freeze. Overdue reviews beyond the spread quota are deferred to make room.
- DECISION (R5): A session can only start online. The next 5 exercises + audio are preloaded. After a drop, finish those, then a calm "Waiting for internet…" screen appears with the timer paused. Un-preloaded re-checks move to the next session.
- DECISION (R6): AI-assisted authoring stays in v1 but doesn't block release. v1 can ship with the suggestion feature switched off if no provider has been chosen.
- DECISION (R7): A published word's spelling is immutable (unpublish + create new). Annotation edits create a new version. Past attempts are re-analysed against the new version for pattern evidence only; mastery state and raw attempts never change. No deletion of published words, only unpublishing.
- DECISION (R8): Playtest 1 = clickable child-flow prototype before the engine is built. Playtest 2 = working child flow with real words before the dashboard is finished. Owner = stakeholder. Pass = finishes ~10 min unaided, doesn't ask to stop, reacts positively to the correction and the garden. Fail → redesign the child UX before engine work continues.
- DECISION (R9): Keep SM-1. Add SM-6 cohort retention (words introduced in month 1 that are Mastered AND correct at their first 30-day check by month 3) and a month-3 re-test of 10 held-out diagnostic words as a like-for-like baseline.
- DECISION: Accepted all proposed fixes for reviewer #4, #6, #7, #8 and all medium/low findings (#15–#30). *Why:* stakeholder: "yes to all".
- NOTE: prd.md revised with all review fixes (FR-74..FR-81 added, SM-6..SM-8 added, status in-review). Re-running prd-reviewer as a verification pass.
- NOTE: Verification review: ready for design, and engineering can start outside the engine/metrics. Previous findings: 25 resolved, 5 partial, 0 unresolved. New: 0 critical, 5 high (#31–#35), 10 medium, 8 low. Asking the stakeholder about #32 (who picks held-out words), #33 (exposure vs maintenance interval), #34 (SM-6 read date).

### Verification fixes and finalize, 2026-10-11
- DECISION (V1): Maintenance intervals are counted from the word's most recent exposure, not the mastery date. *Why:* otherwise handwriting/sentence exposures starve SM-1 of eligible attempts.
- DECISION (V2): SM-6 cohort retention is read at the end of month 4, with pending words reported. *Why:* error-prone month-1 words can't reach their first maintenance review by day 90.
- DECISION: Accepted all verification fixes #31–#53. Diagnostic pool and priority words auto-assigned; "diagnosed: misspelled" has its own introduction tier; Held out state, with the system picking the held-out words; Retire (content error) action; Practice recall evidence type; Context-verified status; re-mastery rules; unified remediation trigger (≥2 Confirmed errors in the same segment within 14 days); due-review cap covers today's + overdue reviews during deadlines; extra pre-deadline recalls advance spacing; per-pattern diagnostic coverage; probe once per word. *Why:* stakeholder: "yes to all".
- CHANGE: SM-1 baseline changed from "diagnostic accuracy on meaning-known words" (Round 6) to "none". SM-7 (held-out re-test) is now the like-for-like baseline. *Why:* the reviewer showed the diagnostic accuracy isn't comparable to 30-day retention.
- NOTE: No open question blocks design or engineering. OQ-1/OQ-3 block Minh's start; OQ-2 blocks only audio integration. prd.md and session.md set to final.
