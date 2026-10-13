---
name: prd-review
description: Review an existing PRD for quality and gaps without changing it. Use when the user asks to review, validate, critique, or score a PRD (in prds/ or any markdown file).
argument-hint: "[prds/<slug> | path/to/prd.md]"
---

# PRD Review

1. Resolve the target from `$ARGUMENTS`. A folder means `<folder>/prd.md`. If nothing is given and there's exactly one PRD under `prds/`, use it; otherwise list the PRDs and ask which one.
2. If the PRD lives outside `prds/`, copy it into `prds/<slug>/prd.md` first, then say so. That way the review has a home.
3. Spawn the `prd-reviewer` subagent with the path.
4. Present the verdict, then the critical and high findings with suggested fixes. Roll medium and low findings into one line pointing at `review.md`.
5. Offer next steps: fix them now (switch to the `prd` skill's Update intent and interview the stakeholder about gaps that only they can fill), or leave the PRD as it is.
