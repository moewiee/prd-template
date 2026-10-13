---
title: Spelling Mastery
slug: spelling-mastery
status: final
stakes: hobby
owner: DatNT (parent, admin)
author: Claude (PRD interview) with DatNT
created: 2026-10-11
updated: 2026-10-11
---

# PRD: Spelling Mastery

> Stakes are personal/family use, but a large development team will build from this document. It is therefore written at full depth, with testable acceptance criteria for every requirement.

## 1. Summary
**TL;DR:** Spelling Mastery is an adaptive English spelling tutor on the web for Vietnamese primary-school children who understand English words but cannot write them accurately from memory. Each day the child does a 15-minute session that teaches words, diagnoses each misspelling, corrects it at the faulty segment and verifies retention over weeks. The parent sees whether spelling ability is genuinely improving, not just whether exercises were completed.

**Vision:** Minh is 8, in Grade 2, and studies Cambridge A2 Flyers. He can read and understand *friend*, *because* and *beautiful*, but he writes *freind*, *becaus* and *beautifull*. His vocabulary is ahead of his spelling, and school practice of copying words and choosing the right spelling from options hides that gap. Spelling Mastery treats spelling as a separate skill. It measures that skill only through **independent recall**: hearing a word and typing it with no hints. It tells a typing slip apart from a misunderstood pattern. It targets the exact segment Minh gets wrong, then checks again days and weeks later until the spelling has stuck. The child sees one button and a growing Word Garden. The engine picks every word, sets the difficulty and schedules every review. The library has no end: the admin keeps adding words and collections, so the product grows with the child across school years.

**Thesis:** We believe a child whose vocabulary is ahead of his spelling will build lasting, independent spelling ability through short daily sessions. The sessions use only independent recall as mastery evidence, diagnose errors down to the segment, and verify retention at spaced intervals. We'll know it works when his 30-day retention is ≥80% (SM-1) and his recurring confirmed errors fall by half (SM-2) by month 3, and most words introduced in his first month are Mastered and still correct at their first maintenance review by month 4 (SM-6).

## 2. Problem and motivation
### 2.1 Problem
Children like Minh recognise and understand many English words but cannot reproduce the exact letter sequence. They drop letters (*becaus*), reverse vowel pairs (*freind*) or double a letter that shouldn't be doubled (*beautifull*). The result is frustration in writing tasks, constant requests for help, and words that look "learned" at school but aren't retained. The parent has no reliable way to know which words or patterns are weak, and today has to choose review words and re-test them by hand.

### 2.2 Current workarounds
- Ordinary schoolwork: learning vocabulary lists, reviewing them, writing words in exercises.
- Copying words repeatedly, and choosing the correct spelling from several options. Both create an **illusion of mastery**, because the child can recognise or reproduce a word that is in front of him without being able to recall it.
- No systematic spelling intervention exists today. That gap is why this product is being built.

### 2.3 Evidence
- The parent observes that Minh recognises words instantly when reading but often can't write them unaided.
- The evidence is thin: Minh's actual misspellings have **not** been collected or classified. *freind* and *beautifull* illustrate the expected error types and are not recorded data. The initial diagnostic (§4.4) exists partly to produce this evidence.

### 2.4 Why now
Minh is at the start of primary school with years of English ahead. Spelling patterns he fixes now make learning new words easier later.

## 3. Users
### 3.1 Target users
- **Child (primary user):** a Vietnamese child aged 6–11 (Grades 1–5). The initial user is Minh: 8, Grade 2, Global Success at school, Cambridge A2 Flyers level. School grade, English vocabulary level and spelling ability are **independent dimensions**; for example, a Flyers-level child may still need elementary phonics patterns. *Job:* practise alone for about 15 minutes a day and come away feeling successful.
- **Parent:** manages 1–3 child profiles, monitors progress, adds school priority words and runs handwriting checks. *Job:* know whether the child's spelling is genuinely improving and what to do about it, without designing practice by hand.
- **Admin:** manages the global word library, spelling annotations, collections, publication and engine parameters. *Job:* keep expanding the curriculum without code changes.

In v1 one person (the product owner) holds both Parent and Admin. The two roles are still separate in the system (§4.1, Roles and permissions).

### 3.2 Not for (v1)
- Other families and the general public: public registration is disabled.
- Teachers, classrooms and schools: there are no teacher or class accounts.
- Children who don't yet understand the words. The product teaches meaning only as a step towards spelling; it is not a general vocabulary course.

### 3.3 Key user journeys
- **UJ-1. Minh does his daily session.**
  - **Context:** after school or in the evening at home, on the family tablet (landscape) or a laptop.
  - **Entry:** the device is already signed in. The profile picker shows, and he taps his avatar.
  - **Path:**
    1. The home screen shows his Word Garden and one **Start Learning** button.
    2. The first exercise starts immediately. For *because* (a review word), the app plays the word and "I stayed home because it was raining." A Vietnamese meaning is one tap away.
    3. He types *becaus* on the on-screen keyboard and taps Submit. The app says "You almost got it! One letter is missing," shows *because* with the missing final *e* highlighted, and gives a one-line explanation.
    4. The word disappears. A few exercises later *because* returns with no hints and he spells it correctly. It isn't mastered yet; it comes back on later days.
    5. At about 15 minutes the current exercise finishes and a summary appears: "You practised 12 words and improved on 3 tricky spellings."
  - **Value moment:** the summary names a specific win ("You finally spelled 'beautiful' correctly without help!") and the garden shows a new plant for a newly Mastered word.
  - **Edge case:** Wi-Fi drops mid-session. He carries on with the exercises already loaded; then a calm "Waiting for internet…" screen appears and the timer pauses. His answers sync when the connection returns, so nothing is lost.

- **UJ-2. Minh's first week: the diagnostic.**
  - **Context:** a new profile has no history.
  - **Entry:** Start Learning on a new profile.
  - **Path:**
    1. Two or three sessions of about 10 minutes run across the first week.
    2. For each word he first hears it and picks its meaning from 3 pictures or Vietnamese meanings, or taps "I don't know." He never sees the spelling.
    3. Words he knows go to pure dictation. Words he doesn't know go to "Vocabulary to Teach."
    4. There is no corrective feedback, just "Thanks, next one."
  - **Value moment:** the parent opens the diagnostic report. It shows a baseline accuracy, a pattern profile (Secure / Emerging / Not Yet / Insufficient Evidence), the error types observed, and how far spelling trails vocabulary. The first learning queue has already been generated.
  - **Edge case:** Minh completes only 2 sessions that week. The diagnostic closes with the evidence available, and patterns without enough observations are labelled Insufficient Evidence instead of being guessed.

- **UJ-3. The parent's weekly check-in and handwriting check.**
  - **Context:** a Sunday evening, about 10 minutes.
  - **Entry:** from the profile picker, the parent opens the Parent area and enters the PIN.
  - **Path:**
    1. The dashboard shows sessions done, retention ("30-day retention: 87% (26/30)", trend: improving) and the recurring difficulties ("ie/ei spelling — 4 errors across 3 words — Moderate evidence").
    2. Recommended Actions says 8 words are Mastered by typing but not yet checked in handwriting.
    3. The parent starts a Handwriting Check. The app plays 8 words with sentences, and Minh writes them on paper.
    4. The parent marks each ✓ or ✗ and types *beutiful* for the one he got wrong.
  - **Value moment:** the parent can see, with evidence, whether spelling is improving and that weaknesses are already being handled automatically.
  - **Edge case:** the parent skips the handwriting check for two weeks. Regular learning continues unaffected and the reminder simply stays in Recommended Actions.

- **UJ-4. The parent adds school words before Friday's test.**
  - **Context:** Minh brings home 12 words for a spelling test on Friday.
  - **Entry:** Parent area, then Priority words.
  - **Path:**
    1. The parent pastes the 12 words and sets the deadline to Friday.
    2. Nine are already in the library. Three are new and become drafts that the parent fills in with spelling, meaning and a sentence.
    3. The drafts are then completed and published in the Admin area.
    4. The engine moves these words to just after due reviews, even if a review backlog exists, and adds recall opportunities before Friday, staying within 15 minutes a day.
  - **Value moment:** the parent sees an honest plan: "12 priority words remaining. Approximately 4 may need additional practice beyond the available sessions."
  - **Edge case:** after Friday the words return to normal spacing. Passing the school test does not mark them Mastered.

- **UJ-5. The admin publishes a new collection.**
  - **Context:** the admin wants to add a "Global Success G2 Unit 6" collection.
  - **Entry:** Admin area, then Import CSV.
  - **Path:**
    1. The admin uploads a CSV of 20 words.
    2. The validation report flags 2 duplicates and 1 word whose segments don't add up to the spelling.
    3. The admin fixes them, previews the generated audio, publishes the collection, and assigns it to Minh.
  - **Value moment:** the words become eligible for Minh without a redeploy, and his daily workload doesn't jump.
  - **Edge case:** a generated pronunciation sounds wrong. The admin regenerates it or uploads a recording before publishing.

## 4. Features and functional requirements
Priorities use MoSCoW as **build order within v1**. Every Must, Should and Could item ships in v1 (§6).

### 4.0 Learning evidence model (applies to all features)
Every attempt is recorded with an **evidence type**, and only independent recall can establish mastery:

| Evidence type | Produced by | Purpose | Can establish mastery? |
|---|---|---|---|
| Instructional | Teach, Segment Repair (scaffolded) | Check the child understands and can practise a pattern | No |
| Diagnostic recall | Diagnostic dictation (FR-22) | Set the baseline and the starting state | A correct answer counts as 1 qualifying recall (FR-75) |
| Independent recall | Recall Dictation (first submission only) | Check the child can retrieve the spelling unaided | Yes, after enough spaced observations (FR-45) |
| Practice recall | Same-session re-checks (FR-35); taught words in a Pattern Family (FR-31) | Strengthen and observe within a session | No. Never counts as a qualifying recall or triggers a state transition. Feeds the pattern profile (FR-77) and counts as an exposure (FR-57) [ASSUMPTION] |
| Transfer | Pattern Family probe words | Check the pattern generalises to untaught words | No. Feeds the pattern profile only (FR-77) |
| Contextual | Sentence Dictation | Check spelling holds up in sentence writing | Tracked as the context track |
| Handwriting | Handwriting Check (parent-recorded) | Check spelling on paper | Tracked as the handwriting track |
| Receptive vocabulary | Meaning check | Check the child knows the meaning | No. It is vocabulary evidence, not spelling evidence |

### 4.1 Accounts, profiles and access
**Description:** In v1 there is one family account; public sign-up is disabled. The parent signs in once per device, and the device then opens to the child profile picker. A child taps his card and goes straight into learning. The Parent and Admin areas sit behind a parent PIN. Sensitive actions also require the account password. Every child profile, learning record and preference belongs to a family account, so multi-family support can be added later without restructuring data. Realizes UJ-1, UJ-3.

**Roles and permissions**

| Capability | Child session | Parent | Admin |
|---|---|---|---|
| Do daily session / diagnostic for own profile | ✓ | — | — |
| View own garden and session summary | ✓ | ✓ (that child) | — |
| View dashboard, attempts and reports for own family's children | — | ✓ | — |
| Manage child profiles, preferences, priority words; run handwriting check | — | ✓ | — |
| Create draft words with spelling, meaning and sentence (from priority-word entry) | — | ✓ | ✓ |
| Create, edit, annotate, import, publish and unpublish library words and collections | — | — | ✓ |
| Change engine parameters (FR-81) | — | — | ✓ |
| Assign collections or words to a child | — | ✓ (own children) [ASSUMPTION] | ✓ |
| Export or delete a child's records | — | ✓ (with password) | — |

| ID | Requirement | Priority | Realizes |
|----|-------------|----------|----------|
| FR-1 | A parent can sign in with email and password, and the device stays signed in through a secure session that persists until sign-out or expiry [ASSUMPTION: 30-day expiry, renewed on use]. | Must | UJ-1, UJ-3 |
| FR-2 | Public registration is unavailable. Family accounts are created only by the operator (FR-80). | Must | — |
| FR-3 | On a signed-in device the default screen is the child profile picker (nickname, illustrated avatar, profile card). Tapping a card opens that child's home screen with no further credentials. | Must | UJ-1 |
| FR-4 | A parent can create, edit and archive [ASSUMPTION: archiving rather than only deleting] 1–3 child profiles. Each holds only: nickname (required), avatar (required), school grade, English proficiency level, optional birth year, and learning preferences. | Must | UJ-3 |
| FR-5 | The Parent and Admin areas require a parent PIN [ASSUMPTION: 4–6 digits]. After repeated wrong PINs, entry is locked [ASSUMPTION: 5 failures lock it for 15 minutes]. Changing the PIN or password, exporting data and deleting data also require the account password. | Must | UJ-3 |
| FR-6 | All authorization (role, PIN-unlocked state, family and child ownership) is enforced on the server for every request. A child session can read and write only its own profile's learning data. | Must | — |
| FR-80 | **Setup and recovery:** the operator creates a family account and its first parent user with a server-side setup procedure, and can grant the Admin role [ASSUMPTION: no UI needed]. On first sign-in the parent must create a PIN. A forgotten PIN can be reset after password re-authentication. A forgotten password can be reset through an emailed link [ASSUMPTION: valid for 1 hour, single use]. | Must | UJ-3 |

**Acceptance criteria**
- **FR-1**
  - Given valid credentials, when the parent signs in, then the profile picker appears. Closing and reopening the browser within the session lifetime shows the picker with no sign-in.
  - Given a wrong password, when the parent submits, then sign-in fails with a generic message that doesn't reveal whether the email exists.
- **FR-2**
  - There is no sign-up link or endpoint. A sign-up request to the API is rejected.
- **FR-3**
  - Given 2 profiles exist, when the device opens, then both cards show. Tapping one shows that child's home screen within NFR-3.
  - Given no profiles exist, then the picker prompts the parent to create one, behind the PIN.
- **FR-4**
  - Creating a 4th active profile is blocked with an explanation.
  - The profile form has no fields for real name, school name, photo or child email.
  - Archiving a profile hides it from the picker and keeps its learning records until they are deleted (FR-72).
- **FR-5**
  - Given the wrong PIN 5 times, then PIN entry is disabled for 15 minutes and the attempts are logged.
  - Given the PIN is unlocked, when the app returns to the profile picker or has been idle in the Parent area [ASSUMPTION: 10 minutes], then the PIN is required again.
- **FR-6**
  - Given a child session token, when it calls any parent or admin endpoint, then the server returns 403.
  - Given a child session for profile A, when it requests profile B's attempts, then the server returns 403 or 404, even within the same family.
  - Automated tests show every learning record query is scoped by family and child.
- **FR-80**
  - Given a newly created parent signs in for the first time, then a PIN must be created before any screen other than PIN creation is reachable.
  - Given a forgotten PIN, when the parent re-enters the account password, then a new PIN can be set and the old one stops working.
  - Given a password-reset link older than 1 hour, or one already used, then it is rejected.

**Out of scope:** multi-family administration, SSO, child passwords.

### 4.2 Word library and content administration
**Description:** The library is global and has no end. Starters, Movers, Flyers, Oxford and Global Success are **reference tags, not boundaries**: any word can be added. Each word has **required** metadata, without which it can't be published, and **optional enhanced** metadata that improves diagnosis. A word can belong to many collections, but each child has one learning history per word. Publishing alone makes nothing reach a child. A word becomes **eligible** for a child only when it is Published **and** assigned to that child (FR-11, FR-76), and the engine still decides when it fits the time budget (FR-47). Realizes UJ-5.

| ID | Requirement | Priority | Realizes |
|----|-------------|----------|----------|
| FR-7 | The admin can create and edit a word. **Required for publication:** unique word ID (system-generated), publication status (Draft / Published / Unpublished), canonical English spelling, Vietnamese meaning, English audio for the word in the default variety, one example sentence with its audio, syllable breakdown, and at least one **reviewed** pattern segment. The example sentence uses only vocabulary at or below the word's level, and at most 12 words [ASSUMPTION]. **Optional:** accepted variant spelling (UK/US), "capital letter required" flag (e.g. *Monday*, *English*), homophones (links to other library words that sound the same), phoneme–grapheme alignment, more pattern segments, irregular-segment flags, morphological structure (e.g. *beauty + ful*), common misspellings, difficulty level, curriculum references, related words and word families, an image for the meaning check, and per-word distractor overrides. | Must | UJ-5 |
| FR-8 | The admin can annotate a word by splitting its spelling into ordered segments. Each segment can be linked to a pattern from the pattern library (FR-16) and given a short explanation in English plus Vietnamese, and each is marked Reviewed or Unreviewed. | Must | UJ-1, UJ-5 |
| FR-9 | The admin can bulk-import words from CSV (columns in Appendix A.3). Imported words land as Drafts. A validation report lists each row's problems: missing required fields, duplicates (against the library and within the file), segments that don't join into the spelling, syllables that don't join into the spelling, pattern references that don't exist, and homophone references that don't exist. | Must | UJ-5 |
| FR-10 | The admin can create collections, add and remove words (a word may be in several), tag a collection by type (topic, curriculum, difficulty, spelling pattern, starter/sample), set the word order within it, and publish or unpublish it. | Must | UJ-5 |
| FR-11 | A parent or admin can assign published collections or individual published words to a child. Assignment makes words eligible for introduction (FR-76) and doesn't change the child's session length or weekly new-word rate. | Must | UJ-5 |
| FR-12 | All library changes (create, edit, import, publish, unpublish, assign) take effect for children without a deployment. Plain unpublishing stops a word being introduced as new; a child who has already started it keeps their history and keeps reviewing it [ASSUMPTION]. Retiring a word for a content error (FR-78) stops all reviews as well. | Must | UJ-5 |
| FR-13 | A child's learning record for a word is kept per word, whatever its collection membership. Moving a word between collections never resets or duplicates progress. | Must | UJ-1 |
| FR-14 | The starter collection (~60 words, from earlier planning) is loaded as a Draft collection tagged "Sample". It is published only after the admin has reviewed its curriculum references and spelling annotations. | Must | — |
| FR-15 | The admin UI shows in Vietnamese by default, and the admin can switch it to English. | Could | — |
| FR-16 | The admin can manage a pattern library. Each pattern (e.g. "ie", "igh", "double consonant before suffix", "-ful suffix", "irregular high-frequency word") has a name, a pattern family (vowel pattern, consonant cluster, silent letter, doubling, suffix/morphology, irregular), and a child-friendly explanation in English and Vietnamese. | Must | UJ-1 |
| FR-78 | **Content versioning:** a published word's canonical spelling can't be changed. To correct a wrong spelling, the admin uses **Retire (content error)**. This immediately stops all introduction and reviews of that word for every child, keeps its attempts in the history (marked "retired"), and leaves them out of all metrics. The admin then creates the corrected word, which starts as Unseen. Edits to segments, patterns, explanations, homophones or morphology create a new word version. Every attempt records the version it was made against. When a new version is published, past attempts are re-analysed against it for pattern evidence (FR-41, FR-77) only. Raw attempts, learning states and mastery never change. Published words can be unpublished but not deleted. | Must | UJ-5 |

**Acceptance criteria**
- **FR-7**
  - Given a Draft word missing any required field, when the admin clicks Publish, then publication is blocked and the missing fields are listed.
  - Given every required field is present and at least one segment is Reviewed, when the admin publishes, then the status becomes Published.
  - A word can be saved as Draft with only its spelling filled in.
- **FR-8**
  - Given *because* split into *be* + *cause*, with the final *e* in *cause* linked to an admin-written explanation, then that explanation is the only text shown when the child omits that *e* (FR-34).
  - Segments that don't join exactly into the spelling cannot be saved.
  - The system never auto-applies a pattern label (e.g. "silent-e") to a segment. Labels come only from the admin.
- **FR-9**
  - Given a 20-row CSV with 2 duplicate rows and 1 bad segmentation, when it is imported, then 17 rows become valid Drafts and 3 are listed with row number and reason. Nothing is published automatically.
  - Given a malformed file (wrong encoding or missing header), then nothing is imported and the reason is shown.
  - Imports of at least 1,000 rows complete within 60 s [ASSUMPTION].
- **FR-10**
  - Given *light* in both "igh pattern" and "Flyers: Time", when either collection is unpublished, then *light* stays available through the other.
- **FR-11**
  - Given a child has 0 due reviews and a 5-per-week new-word rate, when a 40-word collection is assigned, then the next session introduces no more new words than it otherwise would.
  - Given a collection is published but not assigned to Minh, then none of its words are introduced to him.
- **FR-12**
  - Given the admin publishes and assigns a collection at 19:00, when the child starts a session at 19:05, then its words are eligible, with no deployment or restart.
- **FR-13**
  - Given Minh mastered *night* through collection A, when *night* is added to collection B and B is assigned, then *night* stays Mastered and isn't re-introduced.
- **FR-14**
  - The Sample collection can't be assigned while it is Draft.
- **FR-15**
  - Switching the language changes every admin UI label without a reload [ASSUMPTION]. Content fields are unaffected.
- **FR-16**
  - Deleting a pattern that segments still use is blocked, and the dependent words are listed.
- **FR-78**
  - Editing the spelling field of a Published word is disabled, with the hint "Retire it and create a corrected word."
  - Given *freind* was published by mistake as a canonical spelling and Minh has it in Reviewing, when the admin retires it, then it never appears in his sessions again, its attempts disappear from his metrics, and the corrected *friend* can be introduced as a new word.
  - Given *friend* v1 is segmented *fr|ie|nd* with only *fr* linked to a pattern, and Minh's *freind* is recorded as a Transposition, when v2 links *ie* to the "ie" pattern, then that attempt also counts as "ie" pattern evidence. Its raw text, its original v1 classification and the word's state are unchanged.
  - There is no delete action for Published or Unpublished words. Draft words that have never been published can be deleted.

**Notes:** the earlier list of 60 words hasn't been found (OQ-1).

### 4.3 Audio
**Description:** All audio is produced through a high-quality third-party Speech API, using a key the owner supplies. Audio is generated **when content is saved** and stored. Child sessions play stored files only and never call the Speech API live. The **default variety** is UK English [ASSUMPTION]. Realizes UJ-1, UJ-5.

| ID | Requirement | Priority | Realizes |
|----|-------------|----------|----------|
| FR-17 | When a word or sentence is saved, the system generates its audio in the default variety via the Speech API and stores it. The admin can preview it, regenerate it, or upload a replacement recording. | Must | UJ-5 |
| FR-18 | The system generates and stores both UK and US audio for each word and sentence. A parent can choose a child's accent preference, and the child hears that variety. | Should | UJ-1 |
| FR-19 | In any exercise that plays audio, the child can replay the word and the sentence any number of times, at normal or slow speed [ASSUMPTION: slow = about 0.75×]. | Must | UJ-1 |

**Acceptance criteria**
- **FR-17**
  - Given the Speech API is unavailable when a word is saved, then the word saves as Draft, shows the audio status "Failed", and can be regenerated later. Publication stays blocked until audio exists.
  - Given an uploaded recording, then it replaces the generated audio for that variety and is marked "Recorded".
- **FR-18**
  - Given a US preference and a word that has only UK audio, then the UK audio plays and the word is flagged in the admin "missing variety" list.
- **FR-19**
  - Replay never adds to the attempt count and never reveals the spelling.

### 4.4 Initial diagnostic
**Description:** A new profile starts with an adaptive, low-pressure diagnostic spread across 2–3 sessions of about 10 minutes in the first week. It measures spelling **independently of vocabulary**, seeds the pattern profile (FR-77), sets each word's starting state, and builds the first learning queue. There are no further formal tests after it, apart from the month-3 re-test of held-out words (FR-79). Calibration continues through normal sessions. Realizes UJ-2.

| ID | Requirement | Priority | Realizes |
|----|-------------|----------|----------|
| FR-20 | A new child profile begins in Diagnostic mode, drawing from a pool of about 40 admin-designated diagnostic words (Starters, Movers, Flyers and relevant Global Success). The pool covers each pattern family (FR-16). It runs over 2–3 sessions of about 10 minutes each. | Must | UJ-2 |
| FR-21 | Before each word is spelled, the child does a **meaning check**: he hears the word and picks from 3 options (pictures or Vietnamese meanings) or taps "I don't know." Correct makes the word eligible for spelling. Wrong or "I don't know" flags it **Vocabulary to Teach**. | Must | UJ-2 |
| FR-22 | Eligible words are tested by pure dictation: the word and its sentence play and the child types the spelling. There are no hints, no visible answer length and no corrective feedback, only a neutral acknowledgement. Results are Diagnostic recall evidence. | Must | UJ-2 |
| FR-23 | **Selection and completion rule:** words are chosen so that every **pattern** represented in the pool first gets 3 dictated observations, cycling across pattern families so that no family is skipped. Remaining words then go to patterns with mixed results (some correct and some incorrect). The diagnostic doesn't stop early on a pattern. It ends when every pattern has ≥3 observations or no unused pool words remain for it, or 3 sessions are done, or 7 days pass, whichever comes first [ASSUMPTION]. A pattern with fewer than 3 observations is labelled "Insufficient Evidence". While the diagnostic is running, no normal sessions run. | Must | UJ-2 |
| FR-24 | When the diagnostic finishes, the system produces a report and the initial learning queue. The report shows: (a) baseline spelling accuracy on meaning-known words; (b) the initial pattern profile (FR-77); (c) the distribution of error types; (d) words known by meaning vs. words spelled correctly. | Must | UJ-2 |
| FR-25 | Words flagged Vocabulary to Teach are introduced through Teach like any other new word (FR-76). After that they follow the normal state model. | Should | UJ-2 |
| FR-75 | **Diagnostic hand-off:** when the diagnostic ends, the system first picks the held-out words (FR-79). It then assigns every other diagnostic pool word to the child automatically, so they become eligible (FR-76) without any collection being assigned. Each word's starting state is set as follows. A correct dictation puts the word in **Reviewing** with 1 qualifying recall, next check 3 days after the dictation day (FR-74); if that date has already passed, the check is due at the first normal session. An incorrect dictation leaves it **Unseen**, marked "diagnosed: misspelled" [ASSUMPTION: Unseen rather than Learning, because it has never been taught] and ranked in its own tier for introduction (FR-76). A Vocabulary to Teach word stays Unseen. Held-out words get the state **Held out**. Diagnostic misspellings count as pattern evidence (FR-41, FR-77) but not towards SM-2. | Must | UJ-2 |
| FR-79 | **Held-out re-test:** when the diagnostic ends, the system picks 10 diagnostic words to hold out [ASSUMPTION: meaning-known, spread across pattern families, mixing correct and incorrect diagnostic results]. Held-out words are never introduced, reviewed, taught or used as probes. About 90 days after the diagnostic ends they are dictated once as Recall Dictation inside normal sessions. Their accuracy is compared with their diagnostic accuracy (SM-7). If correct, the re-test attempt counts as the word's FR-75 qualifying recall and the word enters Reviewing. If incorrect, the word becomes Unseen, marked "diagnosed: misspelled". Re-test attempts never count towards SM-1 or SM-6. If a parent adds a held-out word as a priority word, it is released from the hold and removed from SM-7, and the parent is told. | Should | — |

**Acceptance criteria**
- **FR-20**
  - Given a new profile, when the child taps Start Learning, then the diagnostic starts, not a normal session.
  - Each diagnostic session ends within about 10 minutes of active time, at the end of the current word.
  - Given the diagnostic pool lacks words for a pattern family, then the admin sees a warning before the diagnostic can be published [ASSUMPTION].
- **FR-21**
  - At no point during the meaning check does the target spelling appear: not in options, image text, feedback or the page title.
  - Distractors are other published words' meanings or images from the same topic, unless the admin has set per-word overrides (FR-7) [ASSUMPTION: auto-selected by default].
  - Given a word has no image, then the options use Vietnamese meanings.
  - Meaning-check results are stored as receptive vocabulary evidence and never change spelling evidence.
- **FR-22**
  - Given the child submits *freind*, then the screen shows only a neutral acknowledgement and moves on. The correct spelling isn't revealed during the diagnostic.
- **FR-23**
  - Given 2 correct answers in a pattern, then the pattern stays "Insufficient Evidence" and no Secure label is assigned.
  - Given the "ie" pattern has had 3 words with 2 correct, then later diagnostic words come from "ie" before patterns that are all-correct or all-incorrect.
  - Given the pool has only 2 words for the "kn" pattern, then the diagnostic can end with "kn" labelled Insufficient Evidence once both have been dictated.
  - Given the child completes only 2 sessions by day 7, then the diagnostic closes on day 7 with the available evidence.
  - Given the diagnostic is still running on day 5, then Start Learning opens a diagnostic session, never a normal session.
- **FR-24**
  - The initial queue ranks Unseen words in Not Yet and Emerging patterns ahead of others, and includes the Vocabulary to Teach words.
  - Leaving mid-session keeps all submitted answers. The next session resumes where it stopped.
- **FR-25**
  - Given *suitcase* is flagged Vocabulary to Teach, when it is introduced, then the Teach activity shows its meaning before its spelling structure.
- **FR-75**
  - Given *night* is dictated correctly on Tuesday (day 2) and the diagnostic ends on Thursday, then *night* is Reviewing with 1 qualifying recall, due Friday (Tuesday + 3 days).
  - Given *night* is dictated correctly on day 2 and the diagnostic ends on day 7, then *night* is due at the first normal session.
  - Given *friend* is dictated as *freind*, then *friend* is Unseen, marked "diagnosed: misspelled", and the error counts towards the "ie" pattern evidence.
  - Given no collections are assigned to Minh, when the diagnostic ends, then the misspelled and Vocabulary to Teach words are eligible for introduction.
- **FR-79**
  - Held-out words are never introduced, reviewed, taught or used as probes before the re-test. That includes held-out words that were spelled correctly.
  - Given a held-out word is correct at the re-test, then it is Reviewing with 1 qualifying recall, and the attempt is absent from SM-1 and SM-6.
  - Given the parent adds held-out *believe* as a priority word, then *believe* becomes eligible, SM-7 is computed over the remaining 9 words, and the parent sees "*believe* was being saved for the 3-month check; it will now be taught."

### 4.5 Daily session and activities
**Description:** The child sees a calm home screen with his garden and one **Start Learning** button. There are no menus, curriculum choices or statistics. The engine (§4.7) builds the session from five activity types. Each activity's purpose is to teach something unknown, strengthen something emerging, or verify retention. No other activity types exist in v1. Realizes UJ-1.

**Child experience principles** (from the stakeholder):
- Friendly and colourful, but not overstimulating.
- Large type and clear interactions.
- Gentle animation.
- Minimal distraction during spelling exercises.
- A consistent garden theme across the child experience.
- No typing outside spelling exercises.
- Never punitive and never "falling behind": he should finish feeling he accomplished something, even after mistakes.

| ID | Requirement | Priority | Realizes |
|----|-------------|----------|----------|
| FR-26 | The child home screen shows the Word Garden (or the mastered-word collection, FR-68) and one Start Learning button. It shows no scores, statistics, curriculum menus or other profiles' data. | Must | UJ-1 |
| FR-27 | Tapping Start Learning starts the first exercise right away. Once the time budget is reached (default 15 minutes of **active time**) [ASSUMPTION: the timer pauses after 60 s with no interaction], the session finishes the current exercise, starts no new one, and shows the session summary (FR-70). There is one session per day [ASSUMPTION]. | Must | UJ-1 |
| FR-28 | **Teach (instructional):** a new word is presented with audio, a sentence, its meaning (English, with Vietnamese on demand) and a breakdown of syllables and segments with the tricky segment highlighted. Then the spelling is hidden and the child reconstructs it from memory. The result is Instructional evidence. | Must | UJ-1 |
| FR-29 | **Recall Dictation (verification):** the word and sentence play and the child types the word. There are no hints, letter tiles, visible answer length or predictive help. Only the first submitted answer is recorded, as Independent recall evidence. | Must | UJ-1 |
| FR-30 | **Segment Repair (strengthen, scaffolded):** the word is shown with its problem segment blanked (e.g. *fr__nd*) and the child supplies the segment, optionally from letter tiles. The result is Instructional evidence and never counts towards mastery. | Must | UJ-1 |
| FR-31 | **Pattern Family (strengthen and transfer):** a set of 3–4 words sharing one pattern (e.g. *light, night, right, bright*), dictated one at a time. At least one is a **transfer probe**, an Unseen eligible word the child has never been taught. Taught words and probes are recorded separately. Probe results are Transfer evidence and update the pattern profile (FR-77) only. A wrong probe gets normal feedback (FR-34). The probe word stays Unseen and doesn't count towards the weekly new-word rate (FR-48). Each word is used as a probe at most once per child, because the feedback shows its spelling. Taught words in a Pattern Family are Practice recall (§4.0). | Must | UJ-1 |
| FR-32 | **Sentence Dictation (context):** a short sentence plays and the child types it. Only the target word(s) are scored, and the result is Contextual evidence. Capitalisation and punctuation are not scored [ASSUMPTION]. | Must | UJ-1 |
| FR-33 | Spelling input uses a large on-screen QWERTY keyboard with all 26 letters, apostrophe, hyphen and space, and also accepts a physical keyboard. Submit is disabled while the answer is empty. The child can edit freely before tapping Submit. Browser autocorrect, autocomplete, spellcheck and predictive text are disabled. The keyboard is never limited to the target word's letters, except for letter tiles in Segment Repair. Answers are compared case-insensitively. For words flagged "capital letter required", a lower-case answer counts as correct and gets a gentle reminder ("Remember: *Monday* starts with a capital letter") [ASSUMPTION]. | Must | UJ-1 |
| FR-34 | After a wrong answer, feedback (1) gives a child-friendly message chosen by the message map below, (2) shows the correct spelling with the faulty segment(s) marked, and (3) shows the admin-written explanation for each faulty segment that has one. Feedback is encouraging and never shows a red-cross-only response, a score or a penalty. | Must | UJ-1 |
| FR-35 | A word missed in a session comes back later in the same session as a no-hint Recall Dictation, after other exercises in between [ASSUMPTION: 3–6 exercises later]. The re-check is Practice recall (§4.0): it **does not** count as a qualifying recall and doesn't change the word's state, whether it is right or wrong. | Must | UJ-1 |
| FR-36 | In every activity the child can tap to see the word's Vietnamese meaning, and the sentence's Vietnamese translation where one exists. Doing so doesn't change how the attempt is classified. | Must | UJ-1 |
| FR-37 | A session can only start while online. At the start and after each exercise, the app preloads the next 5 exercises with their audio. If the network drops, the child can finish the preloaded exercises, and his submitted attempts are queued on the device. Then a calm "Waiting for internet…" screen appears and active time pauses. Queued attempts sync in order on reconnection. Same-session re-checks that weren't preloaded move to the next session. If the app is closed mid-session, restarting the same day continues with the remaining time budget [ASSUMPTION]. | Must | UJ-1 |

**FR-34 message map.** The rows are checked in this order, and the first match wins: Homophone, then no meaningful match, then 3+ differences, then 2 differences, then the 1-difference rows by primary error type (FR-38).

| Situation | Child message (English; Vietnamese available) | Display |
|---|---|---|
| Homophone | "That's a real word that sounds the same! Here we need this one." | Both words shown with meanings |
| No meaningful match (edit distance > half the target length) [ASSUMPTION], or 3+ differences | "Let's look at this one together." | Full word with its syllable and segment breakdown; no error type named |
| 2 differences | "Nearly there! Two small fixes." | Both positions highlighted |
| 1 difference, Morphological-boundary | "Look at the ending *-ful*." (the admin explanation for that morpheme) | Morpheme highlighted |
| 1 difference, Vowel-pattern confusion | "Check the vowel letters here." | Vowel segment highlighted |
| 1 difference, Doubling (extra letter) | "This word has just one *l* here." (with the actual letter) | Segment highlighted |
| 1 difference, Doubling (missing letter) | "Look at the double letter here." | Double letters highlighted |
| 1 difference, Transposition | "Nearly! Two letters are swapped." | Swapped letters highlighted |
| 1 difference, Omission | "You almost got it! One letter is missing." | Correct word, missing letter highlighted |
| 1 difference, Insertion | "Nearly! There's one extra letter." | Extra letter's position marked |
| 1 difference, Substitution | "So close! One letter is different." | Differing letter highlighted |

**Acceptance criteria**
- **FR-26**
  - The child home screen has exactly one primary action, plus a small "Switch profile" control that returns to the profile picker without a PIN [ASSUMPTION]. The Parent and Admin areas are reachable only from the picker, through the PIN.
- **FR-27**
  - Given 15 minutes of active time pass during an exercise, then that exercise completes and the summary follows. No exercise begins after the budget is reached.
  - The child never sees a countdown timer.
  - Given today's session is complete, when the child opens his home screen again that day, then it shows "Today's practice is done! Come back tomorrow." in place of Start Learning.
  - Given nothing is due and nothing is eligible to introduce, then the home screen shows "All done for today! Come back tomorrow."
- **FR-28**
  - The child's first reconstruction attempt in Teach is stored as Instructional evidence and doesn't count towards FR-45.
- **FR-29**
  - The input field doesn't reveal the number of letters (no slots or underscores).
  - Given the child submits *becaus* and then sees the correction, then only *becaus* is stored as the recall attempt.
- **FR-30**
  - An attempt that used tiles is flagged "scaffolded: tiles" in the attempt history.
- **FR-31**
  - Given a Pattern Family for "igh", then at least one word is an Unseen eligible word with no prior Teach for that child, and the attempt history marks it "transfer probe".
  - A probe, correct or not, leaves the word Unseen and doesn't use up a new-word slot.
  - Given no Unseen eligible word shares the pattern, then the Pattern Family runs with taught words only and the admin sees "No probe word available for pattern 'igh'".
  - Given *bright* has already been used as a probe for Minh, then it is never used as a probe for him again.
- **FR-32**
  - Given the target *because* and the typed sentence "i stayed home becuse it was raining", then *because* is scored as a misspelling, the other words are ignored, and capitalisation isn't penalised.
  - Given the child leaves the target word out, then it is scored as incorrect with the message "One word is missing" [ASSUMPTION].
  - Given the child types "be cause", then the target is matched to the closest 1–2-word span and scored as an Insertion (extra space).
- **FR-33**
  - Each on-screen key is at least NFR-8's minimum size. Physical-keyboard letters, apostrophe, hyphen, space, Backspace and Enter (as Submit) work.
  - Typing "freind" on a device with OS autocorrect switched on leaves the text unchanged.
  - Given the target *don't*, then *don't* is correct and *dont* is an Omission.
- **FR-34**
  - Given *becaus* for *because*, then the message says one letter is missing, the final *e* is highlighted (colour plus underline, NFR-8), and the admin explanation for that segment appears if there is one.
  - Given no annotation covers the faulty position, then only the observable difference is shown and no linguistic rule is invented.
  - Given *xqz* for *because*, then "Let's look at this one together." appears with the full breakdown.
- **FR-35**
  - Given a missed word, then it reappears at least 3 exercises later in the same session. If the session ends first, it is scheduled for the next session.
  - Given a New word is misspelled again at its re-check, then it stays New. Only its scheduled check the next day (FR-74) can move it to Learning.
- **FR-36**
  - Given the child taps the Vietnamese meaning during Recall Dictation, then the attempt is still Independent recall evidence and the spelling isn't shown.
- **FR-37**
  - Given the device is offline, then Start Learning shows "Connect to the internet to start" and no session begins.
  - With the network turned off after 3 submitted answers, the child can complete up to 5 preloaded exercises. Then "Waiting for internet…" appears and active time stops. On reconnection all answers sync, with no duplicates and none lost.

**Out of scope:** multiple choice, copying, whole-word unscrambling and spot-the-mistake as learning activities (§5).

### 4.6 Error analysis and pattern profile
**Description:** Error analysis is deterministic and rule-based, with no AI. Each attempt is aligned against the target spelling, and each difference is classified. The engine keeps the **observed error** (what happened in this attempt) separate from the **inferred difficulty**. A difficulty is claimed only from repeated evidence across related words, held in one per-pattern **pattern profile**. Realizes UJ-1, UJ-3.

| ID | Requirement | Priority | Realizes |
|----|-------------|----------|----------|
| FR-38 | For every incorrect attempt (typed, or handwriting with the exact spelling entered), the system aligns attempt and target at the character level using an edit distance that allows adjacent transpositions. It records each raw difference (omission, insertion, substitution, transposition). It then gives each difference one **primary error type** using this order of precedence [ASSUMPTION: order chosen so that the most informative annotated cause wins]: **Homophone** (the whole attempt equals a word linked as a homophone of the target; no further classification) > **Morphological-boundary** (the difference falls in or at an annotated morpheme, e.g. *-ful*) > **Vowel-pattern confusion** (the difference falls inside a segment whose pattern belongs to the vowel-pattern family) > **Doubling** (an inserted letter equals its neighbour, or one letter of a double is missing) > Transposition > Omission > Insertion > Substitution. | Must | UJ-1 |
| FR-39 | Each error is attributed to the segment(s) it falls in, and to the pattern(s) those segments are linked to. Where the error falls in a segment with no pattern link, only the raw difference and its position are recorded, with no pattern attribution. | Must | UJ-3 |
| FR-40 | Each incorrect attempt gets an error-confidence class: **Possible input slip**, **Uncertain** or **Confirmed spelling error** (rules in the acceptance criteria). Classes are revised as evidence builds. A revision changes pattern evidence (FR-41) and SM-2 only. It never changes learning state retroactively. | Must | UJ-1 |
| FR-41 | Pattern weakness evidence is aggregated from attributed errors across words and over time, including Diagnostic recall, Independent recall, Transfer, Contextual and Handwriting evidence. Each pattern's weakness has an evidence level of Weak, Moderate or Strong [ASSUMPTION: Weak = 1–2 confirmed errors; Moderate = ≥3 errors across ≥2 words; Strong = ≥5 errors across ≥3 words; counting only errors from the last 60 days; any number of errors on a single word stays Weak until a second word is affected]. Possible input slips count at reduced weight [ASSUMPTION: 0.25]. | Must | UJ-3 |
| FR-42 | When a word has an accepted variant spelling (e.g. *colour* / *color*), either spelling is marked correct, and feedback shows the variant matching the child's accent preference. | Must | UJ-1 |
| FR-77 | **Pattern profile:** for each child and pattern the system keeps one profile with two views. **Proficiency level:** Secure / Emerging / Not Yet / Insufficient Evidence, from first-submission accuracy on words containing an annotated segment of that pattern [ASSUMPTION: Secure ≥80%, Emerging 40–79%, Not Yet <40%, over the last 60 days; Insufficient Evidence with <3 observations]. **Weakness evidence level:** from FR-41. Inputs are Diagnostic recall, Independent recall, Transfer, Contextual and Handwriting attempts, but not Instructional ones. The diagnostic seeds the profile, and it updates after every attempt. It drives new-word order (FR-76) and remediation (FR-47, FR-50), and parents see it on the dashboard (FR-59). | Must | UJ-2, UJ-3 |

**Acceptance criteria**
- **FR-38**
  - *freind* for *friend*: if the *ie* segment is linked to a vowel pattern, it is Vowel-pattern confusion (raw: transposition). If *ie* has no pattern link (e.g. only *fr* is linked), it is a Transposition.
  - *becaus* for *because* (segments *be|cause*, with *cause* linked to an "-ause" pattern of the irregular family) is an Omission of the final *e*.
  - *beautifull* for *beautiful*: with *-ful* annotated as a morpheme it is Morphological-boundary (raw: insertion). Without a morphology annotation it is Doubling.
  - *write* for *right*, where they are linked as homophones, is a Homophone.
  - The same attempt on the same word version always produces the same classification.
- **FR-39**
  - Given *friend* is segmented *fr|ie|nd* and only *fr* is linked to a pattern, then *freind* is recorded as a transposition at positions 3–4 and no "ie pattern" weakness evidence is created.
- **FR-40**
  - **Possible input slip:** exactly one substitution, the substituted letter sits next to the correct one on QWERTY, and either the child made a qualifying recall of this word within the last 14 days [ASSUMPTION: 14-day window] or the word is Mastered or Maintained. Practice recalls don't satisfy this condition.
  - **Uncertain:** exactly one adjacent-key substitution that doesn't meet the slip condition.
  - **Confirmed spelling error:** everything else, or a slip or uncertain error that recurs in the same position on a later attempt, or one matched by a handwriting attempt.
  - Whatever its class, an incorrect first submission never counts as a correct independent recall.
  - A possible slip gets the same corrective feedback (FR-34) as any other error.
  - Given a typed slip is reclassified as Confirmed because of a handwriting attempt, then the word's typed-recall state stays as it is.
- **FR-41**
  - Given a single *freind*, then any "ie/ei" weakness is at most Weak, and it isn't shown in the dashboard's recurring difficulties.
  - Given 4 errors across *friend*, *believe* and *piece* in 30 days, then an "ie/ei" weakness with Moderate evidence exists and links to those attempts.
  - Given 4 confirmed errors, all on *friend*, then the "ie/ei" weakness is Weak.
- **FR-42**
  - Given a US-preference child types *colour*, then it is marked correct and feedback notes "Also spelled *color*."
- **FR-77**
  - Given 5 attempts in the last 60 days on "igh" words (taught and probes), with 4 correct, then "igh" is Secure.
  - Given only 2 observations, then the pattern is Insufficient Evidence whatever their results.
  - Teach and Segment Repair attempts never change a pattern's proficiency level.

### 4.7 Learning states, mastery and scheduling
**Description:** Each child-word pair has three independent **skill tracks**: typed recall, context and handwriting. The typed-recall track moves through learning states according to a defined transition table. The engine fills each session's **time budget** by a fixed priority order and adapts how fast new words are introduced. Missed days are never counted as failures. All calendar days and weeks use the family's local time zone (Asia/Ho_Chi_Minh). Weeks run Monday to Sunday. Realizes UJ-1, UJ-4.

A **qualifying recall** is a correct first submission in a scheduled Recall Dictation with no hints or scaffolding, made on a later calendar day than the word's introduction. Correct diagnostic dictations (FR-75) and correct held-out re-tests (FR-79) also count, and the "later day" clause doesn't apply to them. Practice recalls (§4.0) never count.

**Learning states (typed-recall track)**
- **Held out:** one of the 10 held-out diagnostic words (FR-79). Nothing is scheduled until the re-test.
- **Unseen:** eligible or diagnosed, but not yet introduced through Teach. Probe words and Vocabulary to Teach words stay here until introduced.
- **New:** introduced through Teach; no qualifying recall yet, and no independent recall attempt yet.
- **Learning:** has had an incorrect independent recall, and no qualifying recall since its last Confirmed error (or since introduction).
- **Reviewing:** at least one qualifying recall since its last Confirmed error (or since introduction), but FR-45 not yet met.
- **Mastered:** meets FR-45.
- **Maintained:** Mastered, plus at least one successful maintenance review since mastery.

**Transition table**

The slip and Uncertain rows and the re-mastery rows are [ASSUMPTION]. The rest follow stakeholder decisions R1, R2 and R7.

| From | Trigger | To | Effect on mastery evidence |
|---|---|---|---|
| — | Diagnostic ends and the word is picked for hold-out (FR-79) | Held out | Nothing scheduled |
| Held out | Correct re-test | Reviewing | Counts as qualifying recall #1; next check +3 days |
| Held out | Incorrect re-test, or released by a priority request | Unseen | None |
| Unseen | Teach completed | New | — (first check due +1 day) |
| Unseen | Correct diagnostic dictation (FR-75) | Reviewing | Counts as qualifying recall #1; next check +3 days from the dictation day |
| Unseen | Incorrect diagnostic dictation, Transfer probe, meaning-check failure | Unseen | None |
| New | Qualifying recall | Reviewing | +1 qualifying recall |
| New | Incorrect independent recall (any class) | Learning | None; next check +1 day |
| Learning | Qualifying recall | Reviewing | +1 qualifying recall |
| Learning | Incorrect independent recall | Learning | None; next check +1 day |
| Reviewing | Qualifying recall | Reviewing, or Mastered if FR-45 is met | +1 qualifying recall |
| Reviewing | Possible input slip or Uncertain error | Reviewing | Not counted; next check +1 day; spacing step kept |
| Reviewing | Confirmed spelling error | Learning | Earlier qualifying recalls kept for the count; spacing window restarts at the error date |
| Mastered | Successful maintenance review | Maintained | Maintenance step advances (FR-46) |
| Maintained | Successful maintenance review | Maintained | Maintenance step advances (FR-46) |
| Mastered / Maintained | Possible input slip | unchanged | Correction shown; the step doesn't advance, and the next review repeats the same interval |
| Mastered / Maintained | Uncertain error | unchanged | Early re-check next session; a failed re-check is treated as a Confirmed error, and a passed one counts as a successful maintenance review |
| Mastered / Maintained | Confirmed spelling error | Learning | As for Reviewing; earned garden reward kept (FR-68) |
| Reviewing (after an earlier demotion) | FR-45 met again | Mastered | Maintenance restarts at the first step (30 days); no second garden reward, and the existing plant is unchanged |

| ID | Requirement | Priority | Realizes |
|----|-------------|----------|----------|
| FR-43 | For each child and word the system keeps three separate skill tracks: typed recall (Recall Dictation), context (Sentence Dictation) and handwriting (Handwriting Check). None of them changes another's status. The context track has two statuses, Not verified and **Context-verified** [ASSUMPTION: after 2 correct Sentence Dictations of the word on separate days ≥7 days apart]. The handwriting track's statuses are defined in FR-67. | Must | UJ-3 |
| FR-44 | The typed-recall track moves between Held out, Unseen, New, Learning, Reviewing, Mastered and Maintained exactly as the transition table above specifies. | Must | UJ-1 |
| FR-45 | A word becomes **Mastered** (typed recall) only when all of these hold: (1) ≥3 qualifying recalls in total; (2) on ≥3 different calendar days; (3) the last qualifying recall is ≥14 days after the start of the spacing window (the first qualifying recall, or the most recent Confirmed error if later); (4) the last two qualifying recalls are ≥7 days apart, and both fall after the spacing-window start; (5) none used hints or scaffolding. Qualifying recalls from before a Confirmed error still count towards (1) and (2). | Must | UJ-1 |
| FR-46 | Mastered and Maintained words get maintenance reviews at growing intervals [ASSUMPTION: 30, 60, 120, then every 180 days]. Each interval is counted from the word's **most recent exposure** (FR-57), not from the mastery date. A handwriting check, a Sentence Dictation or a Pattern Family use therefore pushes the next maintenance review back, and every maintenance review is a genuine ≥30-day test. Errors are handled as the transition table specifies. | Must | UJ-1 |
| FR-47 | Each session is filled up to its time budget in this priority order. (1) **Due reviews:** Recall Dictation of words whose check is due today or overdue, up to the backlog-spread quota (FR-49). (2) **Deadline priority words** (deadline ≤7 days away, FR-53): Teach for those not yet introduced, plus extra Recall Dictation. While such words exist, at least 40% of the budget is kept for them [ASSUMPTION], and any reserved time they don't use flows to slots (3) to (6). (3) **Remediation** as defined in FR-50. (4) **Recent-pattern reinforcement:** Pattern Family for patterns whose first word was introduced in the last 14 days [ASSUMPTION]. (5) **New words:** Teach, at the FR-48 rate, in FR-76 order. (6) **Context:** Sentence Dictation using Reviewing-or-later words [ASSUMPTION: 1–2 per session when time allows]. Durations are estimated from the child's own past timings per activity [ASSUMPTION: default estimates until 5 sessions are complete]. | Must | UJ-1, UJ-4 |
| FR-48 | New words are introduced at 5 per week by default. The rate adapts to performance [ASSUMPTION: +1 per week, up to 10, when first-submission review accuracy over the last 2 weeks is ≥85% and there is no backlog; −1 per week, down to 2, when it is <60%]. Deadline priority words and transfer probes don't count towards the rate. | Must | UJ-1 |
| FR-49 | When the estimated time for due reviews goes above a threshold [ASSUMPTION: 80% of the budget], no non-priority new words are introduced. Overdue reviews after missed days are spread over later sessions, most overdue first, and never all shown at once [ASSUMPTION: at most 80% of the budget per session goes to due reviews (due today plus overdue); while a deadline priority word exists, the cap is 60%]. Missed days never count as incorrect answers and never change a word's state. | Must | UJ-1 |
| FR-50 | **Remediation:** when a word gets ≥2 Confirmed errors in the same segment within the last 14 days [ASSUMPTION], the engine schedules Segment Repair for it. When a pattern weakness reaches Moderate or Strong evidence, it schedules a Pattern Family for that pattern instead of repeating the same full-word dictation. | Must | UJ-1 |
| FR-51 | A parent can change a child's daily time budget [ASSUMPTION: 5–30 minutes] and planned days per week (1–7). The defaults are 15 minutes and 5 days. | Could | UJ-3 |
| FR-74 | **Pre-mastery spacing:** after Teach, the first check is due +1 day. After the 1st qualifying recall in the spacing window it is +3 days, after the 2nd +7 days, and after each later one +7 days, until FR-45 is met. After any incorrect independent recall the next check is +1 day. A Confirmed error also restarts the step sequence. A due date that falls on a day that isn't a planned practice day rolls forward to the next planned day [ASSUMPTION: Monday–Friday by default]. Extra pre-deadline recalls of priority words (FR-53) are scheduled Recall Dictations. They count as qualifying recalls when correct, they advance the step sequence, and the next due date is computed from the latest one [ASSUMPTION]. | Must | UJ-1 |
| FR-76 | **Eligibility and new-word order:** a word is eligible for introduction only if it is Unseen, Published and assigned to the child. A word is assigned directly, through an assigned Published collection, automatically when the diagnostic ends (FR-75), or automatically when a parent adds it as a priority word (FR-52). Eligible words are introduced in this order: (1) priority words, soonest deadline first, then those with no deadline; (2) "diagnosed: misspelled" words; (3) words whose pattern is Not Yet or Emerging, including Vocabulary to Teach words; (4) the order in which collections were assigned, then each collection's word order. When no eligible word remains, sessions run reviews and remediation only. | Must | UJ-1, UJ-5 |
| FR-81 | **Engine parameters:** the admin can change these engine thresholds without a deployment: pre-mastery spacing steps (FR-74); maintenance intervals (FR-46); mastery span and gap (FR-45); evidence levels and window (FR-41); slip weight and window (FR-40, FR-41); proficiency cut-offs and minimum observations (FR-23, FR-77); remediation trigger and window (FR-50); recent-pattern window (FR-47); new-word rate and adaptation (FR-48); backlog threshold and caps (FR-49); priority reservation and deadline window (FR-47, FR-53); retention sample size and trend threshold (FR-57, FR-58); context- and handwriting-verification rules (FR-43, FR-67). Each change is logged with time and old/new value, and attempts record the parameter version in force. | Should | — |

**Acceptance criteria**
- **FR-43**
  - Given a word that is Mastered in typed recall, its handwriting track still shows "Not verified" until a handwriting check records a result.
  - Given correct Sentence Dictations of *because* on Monday and the following Tuesday, then its context track becomes Context-verified. Its typed-recall state is unaffected.
- **FR-44**
  - Given *because* is introduced through Teach on Monday, then it is New and due Tuesday.
  - Given *because* is New and he types *becaus* on Tuesday (Confirmed), then it is Learning and due Wednesday.
  - Given *because* is Learning and he spells it correctly on Wednesday, then it is Reviewing with 1 qualifying recall, due Monday (+3 days is Saturday, which rolls forward to Monday).
  - Given *night* is Reviewing with 2 qualifying recalls and he types *nihgt* (Confirmed), then it is Learning, keeps 2 qualifying recalls for the count, and its spacing window starts that day.
  - Given a Mastered word with an Uncertain error, then it stays Mastered and is re-checked next session. A failed re-check moves it to Learning.
  - Given a word that was Mastered, demoted and then meets FR-45 again, then it is Mastered, its next maintenance review is 30 days after its most recent exposure, and the garden gains no second plant.
- **FR-45** (day 0 = the introduction day; every day shown is assumed to be a planned day)
  - Given qualifying recalls on days 1, 4, 11 and 18, then the word is Mastered on day 18. On day 11 it isn't, because the window span is only 10 days.
  - Given qualifying recalls on days 1, 3 and 14, then it is not Mastered (13-day span).
  - Given qualifying recalls on days 1, 10 and 15, then it is not Mastered (5-day final gap).
  - Given 2 qualifying recalls, then a Confirmed error on day 12, then qualifying recalls on days 13 and 20, then it isn't Mastered on day 20: the window started on day 12, so the span is only 8 days. A further recall on day 27 or later masters it.
  - Given a correct answer made with tiles, it never counts.
- **FR-46**
  - Given a word Mastered on day 18 and handwriting-checked on days 21 and 28, then its first maintenance review is due on day 58 (day 28 + 30), not day 48.
  - Given a Mastered word and a Possible input slip in a maintenance review, then the word stays Mastered, the child sees the correction, and the next review repeats the same 30-day interval.
  - Given a Mastered word and a Confirmed spelling error, then the word goes back to Learning and its earned garden reward stays (FR-68).
- **FR-47**
  - Given due reviews estimated at 6 minutes and a 15-minute budget, then the session contains all due reviews before any new word.
  - Given 40 overdue reviews plus 5 reviews due today after a missed week, and 12 priority words due in 3 days, then the session spends at most 60% of the budget on due reviews (today's and overdue together) and at least 40% on the priority words.
  - Given the priority words need only 3 of their 6 reserved minutes, then the remaining 3 minutes go to remediation, reinforcement, new words or context, in slot order.
- **FR-48**
  - Given default settings and no backlog, then at most 5 non-priority words are introduced in a calendar week.
- **FR-49**
  - Given 7 missed days and 40 overdue reviews, then the first session back contains no more reviews than its quota and no non-priority new words, and the remaining overdue reviews spread over the following sessions.
  - Given the 7 missed days, then no word changes state because of the absence.
- **FR-50**
  - Given 2 Confirmed errors in the *ie* segment of *friend* within 14 days, then the next session includes a Segment Repair for *friend*.
  - Given 2 errors in that segment 20 days apart, or one Confirmed error and one Possible input slip, then no Segment Repair is triggered.
- **FR-51**
  - Given the parent sets 10 minutes and Monday/Wednesday/Friday, then sessions end at 10 minutes of active time, and due dates falling on other days roll forward to the next of those days.
  - Values outside 5–30 minutes can't be saved.
- **FR-74**
  - Given a Reviewing word with 1 qualifying recall on Monday, then it is due Thursday. After a 2nd on Thursday, it is due the following Thursday.
  - Given priority word *island* is introduced Monday, a Friday deadline is set, and he spells it correctly on Tuesday (scheduled) and Wednesday (extra recall), then after Wednesday it has 2 qualifying recalls and its next scheduled check is the following Wednesday (+7 days), after the deadline. It isn't Mastered.
- **FR-76**
  - Given Minh has an unassigned published collection, then none of its words are introduced.
  - Given *friend* is "diagnosed: misspelled" and its pattern "ie" is Insufficient Evidence, then *friend* is still introduced before any tier-(3) or tier-(4) word.
  - Given eligible words in "ie" (Not Yet) and "short a" (Secure), and no priority words, then "ie" words are introduced first.
  - Given no eligible words remain and 3 reviews are due, then the session contains those reviews (and any remediation) only.
- **FR-81**
  - Given the admin changes the backlog threshold from 80% to 70%, then the next session uses 70%, the change log shows both values, and no deployment is needed.

### 4.8 School priority words
**Description:** School vocabulary is a **scheduling constraint**, not a separate learning system. The parent can add words with an optional deadline, and the engine plans honestly within the daily budget. Realizes UJ-4.

| ID | Requirement | Priority | Realizes |
|----|-------------|----------|----------|
| FR-52 | A parent can add priority words to a child by searching the library, typing words, or pasting a list (one per line or comma-separated). Words not in the library become Drafts. The parent fills in the parent-draft minimum: spelling, Vietnamese meaning and one example sentence. Drafts appear in the Admin area's "Drafts from parents" queue, where an Admin completes the annotation and publishes. Adding a priority word assigns it to the child directly (FR-76). Each draft becomes a priority word for the child when it is published [ASSUMPTION]. | Should | UJ-4 |
| FR-53 | A parent can set an optional deadline for a set of priority words. While the deadline is ≤7 days away, the engine handles them in slot (2) of FR-47: they are exempt from the backlog freeze (FR-49), introduced first, given extra independent recall before the date, and given more time when repeatedly misspelled. All of this stays within the time budget. Priority words may go over the weekly new-word rate. | Should | UJ-4 |
| FR-54 | When priority words have a deadline, the parent sees a workload estimate computed from the child's actual practice data (attempts needed per word and time per attempt), e.g. "12 priority words remaining. Approximately 4 may need additional practice beyond the available sessions." | Should | UJ-4 |
| FR-55 | After the deadline, priority words go back to normal scheduling. Results before the deadline count as ordinary evidence. Nothing is marked Mastered because of the deadline. | Should | UJ-4 |

**Acceptance criteria**
- **FR-52**
  - Given a pasted list "friend, because, Because, xylophone ", then the input is trimmed and deduplicated case-insensitively to 3 words. Library matches are linked and *xylophone* (if new) becomes a Draft.
  - A parent can't add segments or publish a draft from the Parent area.
- **FR-53**
  - Given 12 priority words due Friday and 3 planned sessions left, then each of those sessions contains priority-word recall, and no session goes over the time budget.
  - Given a deadline 10 days away, then the words are ordered first among new words (FR-76) but aren't in slot (2) until 7 days remain.
- **FR-54**
  - Given the child has fewer than 5 sessions of history, then the estimate is labelled "rough estimate" [ASSUMPTION]. The app never promises mastery by the deadline.
- **FR-55**
  - Given all 12 words were spelled correctly the day before the deadline, then afterwards they stay in Learning or Reviewing according to FR-45, not Mastered.

### 4.9 Parent dashboard
**Description:** One screen that answers three questions: *Is he practising consistently? Is his spelling genuinely improving? What is he struggling with, and what should we do?* It uses simple bars, trends and drill-downs, with no complex analytics. Activity figures are labelled as activity, not as learning. Realizes UJ-3.

| ID | Requirement | Priority | Realizes |
|----|-------------|----------|----------|
| FR-56 | **This week (activity):** sessions completed vs. planned, total practice time, words introduced, and words that became Mastered, labelled "Activity". | Must | UJ-3 |
| FR-57 | **Lasting progress:** counts of words in each state (Unseen excluded) and the **30-day retention** figure: the share of correct independent recall first submissions on words whose most recent **exposure** before that attempt was ≥30 days earlier. An exposure is any attempt on the word in any activity, including handwriting, or any screen that showed its correct spelling [ASSUMPTION: this scope; maintenance intervals are counted from it (FR-46), so it doesn't starve this metric]. Vietnamese-meaning taps don't count. Shown as a percentage with its sample size. Below the minimum sample [ASSUMPTION: n < 10] it shows "Insufficient data". | Must | UJ-3 |
| FR-58 | **Retention trend:** Improving, Stable or Declining, from the delayed-recall accuracy of the last 30 days compared with the previous 30 days [ASSUMPTION: a change of ±5 percentage points counts as movement; "Insufficient data" if either window has n < 10]. | Should | UJ-3 |
| FR-59 | **Recurring difficulties:** up to 5 patterns whose weakness is Moderate or Strong (FR-41), strongest first, each with its error count, word count and evidence level ("ie/ei spelling — 4 errors across 3 words — Moderate evidence"). Each links to the affected words and exact attempts. A "Patterns" drill-down lists every pattern's proficiency level (FR-77). | Must | UJ-3 |
| FR-60 | **Three skills:** the typed recall, context and handwriting tracks are shown separately (counts and simple bars). No combined mastery score exists anywhere in the product. | Must | UJ-3 |
| FR-61 | **Word drill-down:** for any word, the full attempt history: date, activity, evidence type, word version, exact text submitted, error types, confidence class, scaffolding flag, current state on each track, and next scheduled review. | Must | UJ-3 |
| FR-62 | **Recommended Actions:** up to 3 optional, plain-language items, such as "Minh repeatedly struggles with double consonants. This pattern is already scheduled for extra practice." / "Five words from his school vocabulary are due for review." / "Eight words are mastered through typing but haven't been checked in handwriting." Regular learning never depends on acting on them. | Should | UJ-3 |
| FR-63 | The diagnostic report (FR-24) stays available from the dashboard. | Must | UJ-2 |
| FR-64 | **Health panel:** the system records and shows session active time, sessions abandoned before the budget is reached, parent-area active time per week, and the SM-6 and SM-7 figures. SM-6 shows words that haven't yet reached their first maintenance review as "pending", next to the rate. Once a month it asks the parent one question: "How often did Minh ask for spelling help when writing this month? Often / Sometimes / Rarely". This feeds SM-8. Answering is optional. | Must | — |

**Acceptance criteria**
- **FR-56**
  - Practice-time figures use active time (FR-27), not wall-clock time.
- **FR-57**
  - Given 30 eligible attempts with 26 correct, then it shows "30-day retention: 87% (26/30)".
  - Given 8 eligible attempts, then it shows "Insufficient data (8 checks so far)".
  - Practice recalls, Teach attempts, scaffolded attempts, transfer probes, held-out re-test attempts and retired words are left out of the denominator.
- **FR-58**
  - Given 70% (n=20) in the previous 30 days and 78% (n=25) in the last 30, then it shows "Improving".
  - Given n=8 in either window, then it shows "Insufficient data".
- **FR-59**
  - Given only Weak weaknesses exist, then the section says "No recurring difficulties with enough evidence yet."
- **FR-60**
  - No UI element combines the three tracks into one number.
- **FR-61**
  - Given a handwriting ✗ without the exact spelling, then the history shows "Handwriting: incorrect (spelling not recorded)" with no error type.
- **FR-62**
  - Given there is nothing to recommend, then the section says "Nothing needed — learning is on track."
- **FR-63**
  - Given the diagnostic finished 2 months ago, then the report opens from the dashboard and shows the same figures as when it was produced.
- **FR-64**
  - A session closed with less than 80% of its budget done and not resumed that day counts as abandoned [ASSUMPTION].
  - If the parent skips the monthly question, it isn't asked again until the next month.

### 4.10 Handwriting check
**Description:** A parent-assisted paper exercise, about 5 minutes, about once a week, outside the child's time budget. There is no OCR. Realizes UJ-3.

| ID | Requirement | Priority | Realizes |
|----|-------------|----------|----------|
| FR-65 | From the Parent area, the parent can start a Handwriting Check. The system chooses 5–10 words, putting first those Mastered or Maintained in typed recall with no handwriting verification, then words whose last handwriting result was wrong [ASSUMPTION: second criterion]. | Must | UJ-3 |
| FR-66 | During the check the app plays each word and its sentence (with replay), while the child writes on paper and doesn't see the spelling. Afterwards the parent marks each word ✓ or ✗ and can type the exact spelling written for any ✗. | Must | UJ-3 |
| FR-67 | Handwriting results update only the handwriting track [ASSUMPTION: **handwriting-verified** after 2 correct checks on separate days ≥7 days apart]. An exact misspelling entered by the parent goes through FR-38 to FR-41 like a typed attempt. It can also reclassify a matching typed error as Confirmed, which affects pattern evidence and SM-2 only (FR-40). A ✗ without a spelling is recorded as a failed attempt with no error type. Skipping or never running checks has no effect on the other tracks or on scheduling. | Must | UJ-3 |

**Acceptance criteria**
- **FR-65**
  - Given 8 words Mastered in typing and not handwriting-verified, then the check contains those 8 words.
  - Given fewer than 5 candidates, then the check uses the ones available. With none, it says no words are ready.
- **FR-66**
  - The child-facing screen during the check shows no target spelling.
  - The parent can stop partway, and the marked results are saved.
- **FR-67**
  - Given the parent enters *beutiful* for *beautiful*, then the attempt is classified (as Vowel-pattern confusion if the *eau* segment is annotated as a vowel pattern, otherwise as an Omission) and counted as Handwriting evidence.
  - Given a typed Possible input slip *frirnd* and later a handwriting *frirnd*, then the typed error is reclassified as Confirmed for pattern evidence, and the word's typed-recall state doesn't change.

### 4.11 Word Garden and session celebration
**Description:** Motivation comes from **cumulative verified learning**, not activity volume. Nothing is ever taken away. The reward logic is independent of the visual theme; the Word Garden is the first theme. Realizes UJ-1.

| ID | Requirement | Priority | Realizes |
|----|-------------|----------|----------|
| FR-68 | **Mastered-word collection:** each word that reaches Mastered (typed recall) is permanently added to the child's visible collection. Rewards are never removed for missed days, mistakes or later demotion. | Must | UJ-1 |
| FR-69 | **Word Garden:** the collection is shown as a garden. Each newly Mastered word adds a plant or flower, and each successful maintenance review makes that plant grow by a visible stage [ASSUMPTION: up to 3 stages]. Plants never wilt or die. Introducing a word grants no permanent reward. | Should | UJ-1 |
| FR-70 | **Session summary:** at the end of a session a brief, specific celebration names concrete achievements from that session, e.g. "You remembered 8 words today!", "You finally spelled 'beautiful' correctly without help!", "You strengthened 3 tricky words!". It never shows a score, grade, ranking or streak. | Must | UJ-1 |

**Acceptance criteria**
- **FR-68**
  - Given a Mastered word is demoted to Learning, then its reward is still visible.
- **FR-69**
  - Given 10 missed days, then the garden looks exactly as it did before.
  - There are no random or loot-style rewards, and nothing is time-limited.
- **FR-70**
  - Given a session with 0 correct answers, then the summary still names a real achievement (e.g. "You practised 9 words and learned 2 new ones") and never mentions falling behind.
  - The celebration animation lasts ≤3 s [ASSUMPTION] and can be skipped.

### 4.12 Data export and deletion
| ID | Requirement | Priority | Realizes |
|----|-------------|----------|----------|
| FR-71 | A parent can export one child's profile and full learning record (attempts, states, reports) as a machine-readable file [ASSUMPTION: JSON plus a CSV of attempts], after password re-authentication. | Should | — |
| FR-72 | A parent can permanently delete a child profile and all its learning records, after password re-authentication and a typed confirmation. The data is removed from the live system immediately and from backups when they rotate out (NFR-10). | Should | — |

**Acceptance criteria**
- **FR-71**
  - The export contains every attempt shown in that child's drill-downs and nothing from other profiles.
- **FR-72**
  - After deletion the profile is gone from the picker, its records can't be reached through the API, and no shared library content is affected.

### 4.13 AI-assisted content authoring
**Description:** An optional authoring aid for the admin only. AI never runs in child sessions, and nothing generated by AI reaches a child without admin review. The feature sits behind an on/off switch. **It doesn't block the v1 release:** if no AI provider has been chosen when the rest of v1 is complete, v1 ships with it switched off.

| ID | Requirement | Priority | Realizes |
|----|-------------|----------|----------|
| FR-73 | When the feature is switched on, the admin can request AI suggestions for syllables, pattern segments, example sentences, Vietnamese meanings and explanations while editing a word. Suggestions are saved as Unreviewed and must each be accepted (or edited and accepted) by the admin before they count towards publication. | Could | UJ-5 |

**Acceptance criteria**
- **FR-73**
  - A word whose only pattern segment is an unaccepted AI suggestion can't be published.
  - If the AI service is unavailable or the feature is switched off, word editing works normally. When the feature is off, the suggestion button is hidden.
  - No child-facing request triggers an AI call.

## 5. Non-goals
- **No OCR or handwriting recognition.** Paper checks are parent-recorded; recognition adds complexity without improving learning.
- **No LLM in the learning loop.** Child sessions must be fast, predictable, cheap and free of unverified spelling rules.
- **No recognition activities as mastery evidence.** Multiple choice, copying, whole-word unscrambling and spot-the-mistake are left out of v1, because they inflate apparent mastery.
- **No streaks, leaderboards, scores, grades or random rewards.** Motivation must not create anxiety or compulsive engagement.
- **No public registration, multi-family administration, teacher or classroom accounts, or payments.** v1 is for family use. The data model is ready for multiple families (FR-6), but the product isn't.
- **No native apps** and **no fully offline mode**. The product is a responsive web app. Sessions start online only (FR-37).
- **Not a fixed-length course.** There is no "program complete". The 60-word starter set is a sample, not the curriculum.
- **No ads and no third-party behavioural tracking.**

## 6. MVP scope
### 6.1 In scope (v1, single release)
Every Must, Should and Could requirement, FR-1 to FR-81, ships in v1. MoSCoW labels only set the build order. The exception is FR-73, which may ship switched off (§4.13). In summary:
- Accounts, profiles, setup and access (FR-1 to FR-6, FR-80)
- The content library and administration, including CSV import, collections and versioning (FR-7 to FR-16, FR-78)
- Pre-generated UK and US audio (FR-17 to FR-19)
- The diagnostic, its hand-off and the held-out re-test (FR-20 to FR-25, FR-75, FR-79)
- The five activities (FR-26 to FR-37)
- The error engine and pattern profile (FR-38 to FR-42, FR-77)
- States, mastery, spacing, eligibility and scheduling (FR-43 to FR-51, FR-74, FR-76, FR-81)
- School priority words (FR-52 to FR-55)
- The parent dashboard (FR-56 to FR-64)
- The handwriting check (FR-65 to FR-67)
- The Word Garden (FR-68 to FR-70)
- Export and delete (FR-71, FR-72)
- AI-assisted authoring (FR-73)

### 6.2 Later (v2+)
- Multi-family access and public onboarding: only if the owner decides to open the app to other families (revisit R-8 first).
- Optional recognition scaffolds (e.g. spot-the-mistake) as teaching aids that never count as evidence.
- OCR of handwriting, if paper checks prove valuable but slow.
- Additional garden themes, which the theme-independent reward logic allows.

## 7. Non-functional requirements
The **reference tablet** is a 10th-generation iPad or a comparable mid-range Android tablet, on home Wi-Fi [ASSUMPTION].

| ID | Category | Requirement | How measured |
|----|----------|-------------|--------------|
| NFR-1 | Performance | Feedback appears ≤0.5 s (p95) after Submit. | Timed on the reference tablet |
| NFR-2 | Performance | Audio starts ≤1 s (p95) after the play or replay tap. | Same |
| NFR-3 | Performance | The next exercise appears ≤1 s (p95) after the previous one completes, and the child home screen loads ≤2 s (p95) [ASSUMPTION]. | Same |
| NFR-4 | Resilience | Zero submitted attempts are lost or duplicated when the network drops mid-session, for any outage length (FR-37). | Scripted network-drop tests (1 min, 10 min, 24 h) |
| NFR-5 | Dependency isolation | Child sessions make no live calls to the Speech API or any AI service. The Speech API key is stored only on the server and is never sent to a browser. | Network inspection; code review |
| NFR-6 | Security | Passwords and PINs are stored with Argon2id or bcrypt. All traffic uses TLS. The PIN retry limit is enforced on the server. Every API request is authorized by role and family/child ownership (FR-6). | Security review; automated authorization tests |
| NFR-7 | Privacy | Child profiles hold only the FR-4 fields. There are no ad SDKs or third-party behavioural analytics, and no child data is sent to third parties (the Speech API and any AI service receive only library text). | Dependency audit; data-flow review |
| NFR-8 | Accessibility | Child screens use a font with clearly distinct letterforms (single-storey *a*; distinct *b/d/p/q* and *I/l/1*). Error segments are marked by colour **and** underline or outline. Text meets WCAG 2.1 AA contrast. The OS reduced-motion setting is honoured. Touch targets are ≥48×48 px and on-screen keyboard keys ≥56 px [ASSUMPTION]. | Design review; contrast checker; on-device check |
| NFR-9 | Platforms | Primary: tablet landscape on current iPadOS Safari and Android Chrome. Secondary: desktop Chrome, Edge and Safari. Phones are responsive but not optimised [ASSUMPTION: the latest 2 major versions of each browser]. | Test matrix |
| NFR-10 | Data safety | Learning records and library content are backed up daily and kept for 30 days. A restore is tested before Minh starts and then quarterly [ASSUMPTION: quarterly]. | Backup logs; restore drill |
| NFR-11 | Localization | Child UI: simple English, with Vietnamese meanings and explanations on demand. Parent UI: Vietnamese. Admin UI: Vietnamese, with English available (FR-15). All UI strings are externalised. | String audit |
| NFR-12 | Determinism | Given the same attempt history, word versions (FR-78) and engine-parameter version (FR-81), the engine produces the same classifications, states and session plan, apart from random ordering of exercises within the same priority slot [ASSUMPTION]. | Replay tests on recorded histories |
| NFR-13 | Availability | ≥99% monthly availability [ASSUMPTION]. An outage of a day costs Minh one session and nothing more. | Uptime monitor |

## 8. Constraints, dependencies and assumptions
### 8.1 Constraints
- A large development team builds it. There is no fixed date: v1 ships when FR-1 to FR-81 are complete, except that FR-73 may ship switched off.
- Responsive web app only.
- The learning loop must be deterministic (NFR-12).

### 8.2 Dependencies
- **Speech API (TTS):** the owner supplies the provider and key. It is needed before audio work (FR-17, FR-18) can be integrated. The provider isn't chosen yet (OQ-2).
- **AI service** for FR-73 only. It doesn't block release (OQ-4).
- **Seed content:** the 60-word starter list and the ~40-word diagnostic pool need to be compiled and annotated by the admin before Minh starts (OQ-1, OQ-3). The system picks the 10 held-out words from the pool automatically (FR-79).

### 8.3 Key assumptions
- Minh can use the on-screen keyboard fast enough that typing doesn't take over the 15 minutes, meaning he types a typical 5–7-letter word within about 15 s [ASSUMPTION]. *Validate:* in playtest 2 (§11).
- Rule-based alignment plus admin annotations is accurate enough to give useful pattern diagnoses. *Validate:* the owner reviews the first month of diagnosed weaknesses against the attempt history.
- The admin can sustain tiered annotation at the pace needed to keep about 5 new words a week flowing. *Validate:* library growth vs. consumption at month 2.
- The default engine thresholds (§14) are reasonable starting points. *Validate:* owner review at day 60, with tuning through FR-81.

## 9. Success metrics
Measured for Minh. Reviewed monthly by the owner; the first meaningful read is at day 60, because SM-1 needs 30 days of history. Months count from the end of the diagnostic.

| ID | Metric | Baseline | Target | When | Validates |
|----|--------|----------|--------|------|-----------|
| SM-1 | **30-day independent-recall retention** (FR-57 definition). Mostly measures words that are already Mastered, so it is read alongside SM-6. | None (new measure). The diagnostic accuracy agreed in Round 6 isn't comparable, so SM-7 provides the like-for-like baseline. | ≥80% | By month 3, sustained through month 6 | FR-29, FR-45, FR-46 |
| SM-2 | **Confirmed-error recurrence rate:** of words with a past Confirmed error from typed practice, the share with another incorrect independent recall (Possible input slips excluded [ASSUMPTION]) at a later check | Month-1 value | −50% | Month 3 vs. month 1 | FR-34, FR-38 to FR-41, FR-50 |
| SM-3 | Transfer-probe accuracy per remediated pattern | Value when remediation starts | Increases for each remediated pattern | Month 3 | FR-31, FR-77 |
| SM-4 | Handwriting accuracy on typing-Mastered words | First handwriting check | ≥75% | Month 3 | FR-65 to FR-67 |
| SM-5 | Habit: completed sessions vs. planned | — | ≥4 of 5 per week (4-week average) | Monthly | FR-26, FR-27, FR-68 to FR-70 |
| SM-6 | **Cohort retention:** of all words introduced through Teach in month 1, the share that are Mastered **and** correct at their first maintenance review. Words still pending are reported alongside. | None (new measure) | ≥70% [ASSUMPTION] | End of month 4 | FR-28 to FR-31, FR-45, FR-47, FR-74 |
| SM-7 | **Held-out re-test:** accuracy on the 10 held-out diagnostic words (FR-79) | Their diagnostic accuracy | +30 percentage points [ASSUMPTION] | Month 3 | FR-31, FR-50, FR-77 (transfer) |
| SM-8 | Independence: parent's monthly answer to "asked for spelling help" (FR-64) | Month-1 answer | Moves towards "Rarely" by month 6 | Monthly | Thesis (independence) |
| SM-C1 | **Counter:** sessions with active time over 18 min | — | <5% of sessions [ASSUMPTION] | Monthly | balances SM-1, FR-27 |
| SM-C2 | **Counter:** sessions abandoned (FR-64) | — | <10% of sessions [ASSUMPTION] | Monthly | balances SM-5 |
| SM-C3 | **Counter:** parent active time in the app per week, including handwriting checks | — | <20 min | Monthly | balances FR-52 to FR-67 |

The owner's qualitative test of success: Minh writes a paragraph on his own and correctly spells words he used to struggle with, without noticing he has overcome them.

## 10. Risks and mitigations
| ID | Risk | Likelihood | Impact | Mitigation |
|----|------|------------|--------|------------|
| R-1 | **Minh doesn't like the app.** This is made worse because he first uses it only after the full v1 is built. | Med | High | Two gated playtests with pass criteria (§11), the first before the engine is built. Five varied activities. A non-punitive tone (FR-34, FR-70). Garden rewards that are never lost. SM-5 and SM-C2 watched monthly. |
| R-2 | The engine diagnoses the wrong weakness, so practice targets the wrong pattern. | Med | Med | Evidence levels with a Moderate threshold before any weakness is shown or acted on (FR-41, FR-50). An Insufficient Evidence label (FR-23, FR-77). A full attempt drill-down so the parent can check (FR-61). Tunable thresholds (FR-81). |
| R-3 | Explanations are linguistically wrong (e.g. every final *e* called "silent e"). | Med | Med | Explanations come only from admin-written, reviewed segments. The system never auto-labels a pattern (FR-8, FR-34). AI suggestions need review (FR-73). |
| R-4 | Library growth stalls because annotation is too slow. | Med | High | Tiered metadata (FR-7), CSV import with validation (FR-9), AI suggestions (FR-73), and a library-growth check at month 2 (§8.3). |
| R-5 | The seed lists (the 60 starter words and the ~40 diagnostic words) are missing or unvalidated when Minh is ready to start. | High | High | OQ-1 and OQ-3. The Sample collection stays Draft until reviewed (FR-14). |
| R-6 | TTS mispronounces a word or uses the wrong accent. | Med | Med | Admin preview, regenerate and upload (FR-17). A missing-variety report (FR-18). |
| R-7 | Slip vs. error is misclassified, so Minh gets remediation he doesn't need or misses remediation he does. | Med | Low | Conservative three-class model (FR-40). Reclassification on recurrence or handwriting. Corrective feedback on every error regardless of class. |
| R-8 | Content copyright. The owner has decided this is not a concern for family use. If the app opens to other families, library content taken from publishers' materials could become an issue. | Low (v1) | Med (if opened) | Revisit before any multi-family release (§6.2). |
| R-9 | The Speech API provider changes price or availability. | Low | Low | Audio is pre-generated and stored, so sessions are unaffected (NFR-5). Recordings can be uploaded as a fallback. |

## 11. Rollout, stakeholders and timeline
- **Rollout:** a single v1 release to one family, gated by two playtests that DatNT runs with Minh.
  - **Playtest 1 (before the learning engine is built):** a clickable prototype of the child flow: Start Learning → Recall Dictation → correction → re-check → summary → garden.
  - **Playtest 2 (before the parent dashboard is finished):** a working child flow with real words and real feedback.
  - **Pass criteria (both):**
    - Minh completes about 10 minutes without help.
    - He doesn't ask to stop.
    - He reacts positively to the correction screen and the garden.
    - In playtest 2 only, he types a typical 5–7-letter word within about 15 s.
  - **If a playtest fails:** the child UX is redesigned and re-tested before engine work (after playtest 1) or release (after playtest 2) continues.
- **Milestones:**
  - Playtest 1: before engine build.
  - Playtest 2: before dashboard completion.
  - Seed content ready (OQ-1, OQ-3): before release.
  - v1 complete, then Minh starts the diagnostic: no fixed date.
  - First metrics review: day 60.
  - Held-out re-test and month-3 review: about day 90.
  - SM-6 cohort read: end of month 4 (about day 120).
- **Stakeholders:**
  - DatNT (owner, parent, admin): decides, approves and runs the playtests.
  - The development team: builds; consulted on feasibility.
  - Minh: user and playtester.

## 12. Glossary
- **Active time:** session time with child interaction. It pauses after 60 s idle (FR-27) and while waiting for the network (FR-37).
- **Attempt:** one submitted answer to one exercise. Only the **first submission** is recorded.
- **Backlog:** due reviews whose estimated time exceeds the threshold in FR-49.
- **Collection:** an admin-defined, publishable group of words. A word can be in many collections.
- **Confirmed spelling error / Possible input slip / Uncertain:** the three error-confidence classes (FR-40).
- **Default variety:** the English variety used when no accent preference is set. UK.
- **Diagnostic:** the first-week assessment that sets the baseline, starting states and initial queue (§4.4).
- **Draft / Published / Unpublished:** word and collection publication statuses (FR-7).
- **Eligible:** Unseen, Published, assigned to the child and not held out. Only eligible words can be introduced (FR-76).
- **Evidence type:** Instructional, Diagnostic recall, Independent recall, Practice recall, Transfer, Contextual, Handwriting or Receptive vocabulary (§4.0).
- **Evidence level:** Weak, Moderate or Strong support for a pattern weakness (FR-41).
- **Exposure:** any attempt on a word, or any screen showing its correct spelling (FR-57).
- **Family account:** the owning unit for child profiles and learning records.
- **Context-verified:** the context track's success state (FR-43).
- **Handwriting-verified:** the handwriting track's success state (FR-67).
- **Held-out words:** 10 diagnostic words, in the Held out state, kept out of all practice until the month-3 re-test (FR-79).
- **Independent recall:** the first submitted answer in Recall Dictation with no hints or scaffolding.
- **Learning state:** Held out, Unseen, New, Learning, Reviewing, Mastered or Maintained (§4.7).
- **Practice recall:** a same-session re-check or a taught word in a Pattern Family. Never qualifying (§4.0).
- **Library:** the global set of words, patterns and collections the admin manages.
- **Maintenance review:** a scheduled recall check on a Mastered or Maintained word (FR-46).
- **Mastered:** the typed-recall state reached when FR-45 holds.
- **Meaning check:** the 3-option receptive vocabulary check in the diagnostic (FR-21).
- **Pattern:** a named spelling regularity or irregularity in the pattern library, belonging to a pattern family (FR-16).
- **Pattern profile:** a child's per-pattern record, with a proficiency level and a weakness evidence level (FR-77).
- **Pattern weakness:** the weakness view of the pattern profile (FR-41). The dashboard section listing them is labelled **Recurring difficulties** (FR-59).
- **Priority word:** a word the parent adds, optionally with a deadline (§4.8).
- **Qualifying recall:** defined at the top of §4.7.
- **Retire (content error):** the admin action that withdraws a wrongly spelled word from all children (FR-78).
- **Segment:** an annotated part of a word's spelling, optionally linked to a pattern (FR-8).
- **Skill track:** typed recall, context or handwriting. Each is tracked separately (FR-43).
- **Spacing window:** the period that FR-45's span and gap rules are measured over. It starts at the first qualifying recall or the most recent Confirmed error.
- **Time budget:** the target daily active time, 15 minutes by default (FR-27, FR-51).
- **Transfer probe:** an Unseen eligible word in a Pattern Family, used to test generalisation (FR-31).
- **30-day retention:** defined in FR-57.
- **Vocabulary to Teach:** the flag on words whose meaning the child didn't know in the meaning check (FR-21).
- **Word version:** a numbered revision of a word's annotations (FR-78).
- **Word Garden:** the visual theme of the mastered-word collection (FR-68, FR-69).

## 13. Open questions
| ID | Question | Owner | Needed by | Blocking? |
|----|----------|-------|-----------|-----------|
| OQ-1 | Where is the earlier planning document with the ~60-word starter list? If it can't be found, who compiles and validates a new starter list? | DatNT | Before release (content seeding) | Yes, for Minh's start. Not for the build. |
| OQ-2 | Which Speech API provider and which UK and US voices? | DatNT | Before FR-17 integration | Yes, for audio integration |
| OQ-3 | Who compiles and annotates the ~40-word diagnostic pool, so that each pattern has enough words for FR-23's minimum (3 observations per pattern, plus the 10 that will be held out)? | DatNT | Before release | Yes, for Minh's start |
| OQ-4 | Which AI provider (if any) for FR-73, and is it acceptable to send library text (no child data) to it? | DatNT | Before FR-73 is switched on | No (FR-73 may ship switched off) |
| OQ-5 | Are the default values of the FR-81 engine parameters acceptable, or should a learning-science reviewer check them? These are the stakeholder-decided spacing (R1) and the [ASSUMPTION] thresholds. They can be tuned later through FR-81. | DatNT + dev team | Before engine build | No (defaults stand) |
| OQ-6 | Will meaning-check images be supplied? FR-21 works with text only, but pictures may suit younger children better. | DatNT | Before diagnostic content is finalised | No |

## 14. Assumptions index
- §4.1 FR-1: device session expires after 30 days, renewed on use.
- §4.1 FR-4: profiles can be archived, not only deleted.
- §4.1 FR-5: PIN is 4–6 digits. 5 failures lock it for 15 minutes. 10 minutes idle in the Parent area re-locks it.
- §4.1 roles table: parents can assign collections and words to their own children.
- §4.1 FR-80: the operator sets up accounts without a UI. The password-reset link is valid for 1 hour, single use.
- §4.2 FR-7: example sentences are at or below the word's level and at most 12 words.
- §4.2 FR-9: CSV imports of ≥1,000 rows finish within 60 s.
- §4.2 FR-12: unpublished words keep being reviewed by children who already started them.
- §4.2 FR-15: switching the admin language doesn't need a reload.
- §4.3: the default variety is UK English.
- §4.3 FR-19: slow replay is about 0.75×.
- §4.4 FR-20: the admin is warned when the diagnostic pool lacks words for a pattern family.
- §4.4 FR-21: distractors are auto-selected from the same topic by default.
- §4.4 FR-23: the diagnostic ends when every pattern is labelled, the pool runs out, after 3 sessions or after 7 days. A pattern needs at least 3 dictated words.
- §4.4 FR-75: an incorrect diagnostic dictation leaves the word Unseen (not Learning).
- §4.4 FR-79: held-out word selection (meaning-known, spread across families, mixed results).
- §4.0: Practice recall feeds the pattern profile and counts as an exposure, but never as qualifying.
- §4.5 FR-26: "Switch profile" needs no PIN.
- §4.5 FR-27: the active-time timer pauses after 60 s idle. One session per day.
- §4.5 FR-32: capitalisation and punctuation aren't scored. A missing target word gets "One word is missing".
- §4.5 FR-33: a lower-case answer on a capital-required word is correct, with a reminder.
- §4.5 FR-34: "no meaningful match" means an edit distance greater than half the target length.
- §4.5 FR-35: a missed word returns 3–6 exercises later.
- §4.5 FR-37: restarting the same day continues the remaining budget.
- §4.6 FR-38: the precedence order of primary error types.
- §4.6 FR-40: the slip window is 14 days.
- §4.6 FR-41: evidence-level thresholds (Weak 1–2; Moderate ≥3 across ≥2 words; Strong ≥5 across ≥3 words; one word alone stays Weak) over a 60-day window. Slips count at 0.25 weight.
- §4.6 FR-77: proficiency cut-offs (Secure ≥80%, Emerging 40–79%, Not Yet <40%) over 60 days, with a minimum of 3 observations.
- §4.7 transition table: the slip and Uncertain rows; re-mastery restarts maintenance at 30 days with no second reward.
- §4.7 FR-43: context-verified means 2 correct Sentence Dictations on separate days ≥7 days apart.
- §4.7 FR-46: maintenance intervals are 30/60/120/180 days.
- §4.7 FR-47: at least 40% of the budget is reserved for deadline priority words. Recent pattern = first word introduced within 14 days. 1–2 Sentence Dictations per session. Default duration estimates are used until 5 sessions are done.
- §4.7 FR-48: the new-word rate adapts ±1 per week within 2–10, at ≥85% and <60% accuracy.
- §4.7 FR-49: the backlog threshold is 80% of the budget. Due reviews (today's plus overdue) get at most 60% of a session while a deadline is active, otherwise 80%.
- §4.7 FR-50: 2 Confirmed errors in the same segment within 14 days trigger Segment Repair.
- §4.7 FR-51: the parent can set a 5–30 minute budget.
- §4.7 FR-74: planned days default to Monday–Friday. Extra pre-deadline recalls advance the spacing steps.
- §4.8 FR-52: a parent's draft becomes a priority word when it is published.
- §4.8 FR-54: estimates are labelled "rough" with fewer than 5 sessions of history.
- §4.9 FR-57: the minimum retention sample is n = 10. Exposure includes any activity, including handwriting.
- §4.9 FR-58: a trend needs a ±5 percentage-point change between two 30-day windows.
- §4.9 FR-64: a session is abandoned when less than 80% of the budget is done and it isn't resumed that day.
- §4.10 FR-65: the second handwriting-selection criterion is the last handwriting check being wrong.
- §4.10 FR-67: handwriting-verified means 2 correct checks on separate days ≥7 days apart.
- §4.11 FR-69: plants have up to 3 growth stages.
- §4.11 FR-70: the celebration lasts ≤3 s.
- §4.12 FR-71: the export is JSON plus a CSV of attempts.
- §7: the reference tablet is a 10th-generation iPad or a comparable Android tablet.
- §7 NFR-3: the home screen loads in ≤2 s.
- §7 NFR-8: touch targets ≥48 px, keyboard keys ≥56 px.
- §7 NFR-9: the latest 2 major browser versions are supported.
- §7 NFR-10: the restore drill is quarterly.
- §7 NFR-12: exercise order within a priority slot may be randomised.
- §7 NFR-13: ≥99% monthly availability.
- §8.3: the typing-speed threshold is about 15 s per 5–7-letter word.
- §9 SM-2: Possible input slips are excluded.
- §9 SM-6 and SM-7: targets of ≥70% and +30 percentage points.
- §9 SM-C1 and SM-C2: limits of <5% and <10%.
- Appendix A.3: the CSV column set is to be finalised with the admin.

---

## Appendix
### A. Technical notes
**A.1 Stakeholder-stated direction**
- Error analysis uses deterministic sequence alignment, an edit distance that supports adjacent transpositions, followed by rule-based classification against segment annotations (FR-38). No LLM is involved.
- Ownership is scoped as family → child profile → learning records, separate from the global content library, so multiple families can be supported later without a rebuild.
- The reward logic (which events earn or grow a reward) is separate from the visual theme (the Word Garden).
- TTS is generated when content is saved and stored with the content. The key is held on the server.
- FR-37 implies the client can run the preloaded exercises, including feedback, on its own (NFR-1). Session planning stays on the server.
- **Rejected alternatives:**
  - OCR, because it adds complexity without improving learning.
  - An LLM in the learning loop, because it would make sessions unpredictable and slow and could state unverified rules.
  - Letter-subset keyboards outside remediation, because they turn recall into arrangement.
  - Browser speech synthesis, because quality varies by device.

**A.2 Engine priority order (FR-47), restated for engineering**
1. Due reviews (within the backlog quota)
2. Deadline priority words (≤7 days; ≥40% reserved)
3. Remediation (Segment Repair, Pattern Family)
4. Recent-pattern reinforcement (Pattern Family)
5. New words (Teach, FR-76 order)
6. Sentence Dictation

All of these fit within the time budget.

**A.3 CSV import columns (FR-9)** [ASSUMPTION: the final format is agreed with the admin]
- `spelling`*, `variant_spelling`, `capital_required`, `meaning_vi`*, `example_sentence`*, `sentence_vi`, `syllables`* (e.g. `be|cause`)
- `segments`* (e.g. `be|cause`), `segment_patterns` (pattern names aligned to segments), `segment_explanations_en`, `segment_explanations_vi`
- `morphology`, `homophones`, `common_misspellings`, `difficulty`, `curriculum_refs`, `collections`, `related_words`

\* marks columns required for publication. Audio is generated after import.

### B. Interview record
Decisions and their reasoning are logged in `session.md` in this folder. The review is in `review.md`.

## Changelog
| Date | Change | Reason |
|------|--------|--------|
| 2026-10-11 | Initial draft | PRD interview |
| 2026-10-11 | Review fixes. Added the Unseen state, the transition table and the qualifying-recall definition (FR-44). Added pre-mastery spacing (FR-74), diagnostic hand-off (FR-75), eligibility and new-word order (FR-76), the unified pattern profile (FR-77), content versioning (FR-78), the held-out re-test (FR-79), setup and recovery (FR-80) and tunable engine parameters (FR-81). Added error precedence and the feedback message map (FR-38, FR-34), deadline-vs-backlog precedence (FR-47, FR-49, FR-53), online-start and preload behaviour (FR-37), and a non-blocking switch for AI authoring (FR-73). Added gated playtests (§11) and SM-6 to SM-8. Covered keyboard characters and case rules, the parent-draft minimum, the session-complete state, time zone, reference tablet, hash algorithm and default variety, plus glossary and terminology alignment. | prd-reviewer findings #1–#30; stakeholder accepted all fixes (R1–R9) |
| 2026-10-11 | Verification fixes. Diagnostic and priority words are now assigned automatically, and "diagnosed: misspelled" has its own introduction tier (FR-75, FR-76, FR-52). Added the Held out state, with the system picking held-out words and freezing them until the re-test (FR-79). Added Retire (content error) (FR-78). Maintenance intervals are counted from the most recent exposure (FR-46), and SM-6 is read at month 4. Added Practice recall evidence, the context-verified status, re-mastery rows, a single remediation trigger, a cap on all due reviews during deadlines, extra recalls advancing spacing, per-pattern diagnostic coverage, an explicit FR-81 parameter list, a once-per-word probe rule and a message-map order. Fixed ACs that referred to unannotated words. | Verification review findings #31–#53; stakeholder accepted all (V1, V2) |
