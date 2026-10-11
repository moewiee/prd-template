# PRD Template Repo

This repo turns Claude Code into a product manager that interviews a stakeholder and writes a PRD. **The user is the stakeholder. Claude asks the questions and writes the document.**

## Default behavior
- When the user describes a product, feature, or idea, even casually, use the `prd` skill. Don't jump straight to writing a PRD. Interview first.
- When the user asks to review or critique a PRD, use the `prd-review` skill.
- Never implement the product described in a PRD. This repo produces documents only.

## Layout
- `.claude/skills/prd/`: interview workflow (`SKILL.md`), question bank, elicitation techniques, quality rubric, PRD and session templates.
- `.claude/skills/prd-review/`: standalone review command.
- `.claude/agents/prd-reviewer.md`: subagent that critiques a PRD and writes `review.md`.
- `prds/<slug>/`: one folder per PRD, holding `session.md` (interview log and resume point), `prd.md`, `review.md`, and an optional `inputs/` folder.

## Conventions
- Slugs are kebab-case. Dates are ISO (`YYYY-MM-DD`).
- `session.md` is updated after every interview round so any session can be resumed with `/prd <slug>`.
- PRD IDs (`UJ-`, `FR-`, `NFR-`, `SM-`, `R-`, `OQ-`) are global and never reused.
- Interview in the stakeholder's language. Write the PRD in the language they ask for (default: the interview language).

## Customizing for a team
Edit `.claude/skills/prd/assets/prd-template.md` (sections), `references/question-bank.md` (what gets asked), and `references/quality-rubric.md` (what "good" means). The skill reads them at run time, so no other changes are needed.
