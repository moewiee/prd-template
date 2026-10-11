# PRD Quality Rubric

A judgment rubric, not a checklist of headings. The question is whether this PRD is *good*: could a team design, build, and measure from it without going back to the stakeholder for basics?

Calibrate to the PRD's `stakes` and shape. A hobby PRD needs a sound substance bar, not enterprise rigor. Be specific: cite sections, quote phrases, name what's missing. Vague criticism is useless.

## Dimensions

For each dimension, give a verdict (**strong / adequate / thin / broken**) backed by specifics.

### 1. Problem clarity
- Is the problem stated from the user's side, with the cost of the status quo?
- Is there evidence, or an honest admission that evidence is thin?
- Does the thesis make a falsifiable bet?
- 🚩 Red flags: the problem is really a solution ("users need a dashboard"), or the vision could be swapped into any competitor's PRD.

### 2. Decision-readiness
- Are decisions stated as decisions, with what was traded away?
- Are open questions actually open, with owners?
- Would someone pushing back find their objection acknowledged?
- 🚩 Red flags: everything "balances", every NFR is "important", every persona "loves" the product.

### 3. Substance over theater
- **Persona theater:** personas that don't drive any decision, or more than four.
- **NFR theater:** boilerplate like "must be scalable / secure / reliable" with no thresholds.
- **Feature theater:** capabilities that serve no journey or metric.
- Flag furniture even if it's well written.

### 4. Strategic coherence
- Do the features follow from the thesis, or read like a backlog with headings?
- Does MVP scope follow a clear logic (solve the core problem, test the riskiest assumption)?
- Do the success metrics validate the thesis rather than just measure activity? Are counter-metrics present?

### 5. Done-ness (be unforgiving here)
- Does every FR have at least one testable acceptance criterion?
- Flag every "gracefully", "intuitive", "fast", "user-friendly", "seamless", or "robust" that has no number or observable behavior.
- Are error, empty, and edge states covered for the Must FRs?
- Do NFRs have bounds and a measurement method?

### 6. Scope honesty
- Are non-goals explicit where readers would otherwise assume?
- Are inferences tagged `[ASSUMPTION]` and indexed in §14?
- Is anything de-scoped silently?
- Is the density of open items appropriate for the stakes? (Many blocking OQs on a "final" launch PRD is a blocker.)

### 7. Shape fit
- Consumer or multi-stakeholder product: are there UJs with named protagonists?
- Internal single-operator tool: is it over-formalized?
- Regulated: do the obligations trace to FRs/NFRs?
- Is length appropriate to stakes, with no padding?

### Mechanical checks (tail section; doesn't drive the verdict)
- IDs (UJ/FR/NFR/SM/R/OQ) are contiguous and unique; every cross-reference resolves.
- Glossary terms are used consistently, with no synonyms.
- Every inline `[ASSUMPTION]` appears in §14, and vice versa.
- Frontmatter is complete; template guidance text is removed.

## Severity
- **critical:** the PRD can't be safely used to design or build (missing problem, untestable Must FRs, contradictory scope).
- **high:** a significant gap that will cause rework or wrong decisions.
- **medium:** weakens the PRD, but a team could work around it.
- **low:** polish and mechanical issues.

Severity ranks impact, not effort to fix. A vague thesis is critical even though it's a one-line fix.

## Output format (`review.md`)

```markdown
# PRD Review: {title}
Reviewed: {YYYY-MM-DD} · Stakes: {stakes} · PRD status: {status}

## Verdict
{2–3 sentences: what holds up, what's at risk, and whether it's ready to hand to design/engineering.}

## Findings
| # | Severity | Dimension | Location | Finding | Suggested fix |
|---|----------|-----------|----------|---------|---------------|
| 1 | critical | Done-ness | §4.2 FR-5 | … | … |

## Dimension notes
### Problem clarity: {verdict}
{short judgment with specifics}
… (one per dimension)

## Mechanical notes
- …

## Questions to ask the stakeholder
{Gaps only the stakeholder can fill, phrased as interview questions.}
```
