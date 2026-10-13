# PRD Template for Claude Code

Describe what you want in plain words. Claude Code interviews you like a senior PM, in rounds of focused questions, then writes a structured, reviewed PRD.

```
you (stakeholder) ──idea──▶ /prd ──▶ brain dump ──▶ calibrate ──▶ interview rounds ──▶ playback ──▶ draft ──▶ review ──▶ final PRD
                                                      (stakes,       (3–5 Qs each,        (confirm     (template)   (subagent
                                                       mode)          logged to            understanding)            + rubric)
                                                                      session.md)
```

## Quick start

```bash
cd prd-template
claude
```

Then either type:

```
/prd a mobile app that lets warehouse leads assign picking tasks to their team
```

or just describe your idea. `CLAUDE.md` tells Claude to start the interview automatically.

During the interview, you can say:

| Say | Effect |
|-----|--------|
| `yes` (to a question) | Accept Claude's suggested answer |
| `skip` / `park it` | Record the question as open and move on |
| `go deeper on <topic>` | Extra rounds using elicitation techniques |
| `draft now` | Stop asking and write the PRD from what's known |
| `pause` | Save progress; resume later with `/prd <slug>` |

See **[USER_MANUAL.md](USER_MANUAL.md)** for 14 worked use cases with example conversations.

Other commands:
- `/prd <slug>`: resume an interview, or update a finished PRD.
- `/prd-review prds/<slug>`: critique any PRD against the quality rubric (works on PRDs written elsewhere too).

## Output

```
prds/<slug>/
├── session.md   # interview log: every decision + why, assumptions, open frontier
├── prd.md       # the PRD
├── review.md    # reviewer findings
└── inputs/      # (optional) material you handed over
```

## What's inside

| Path | What it does |
|------|--------------|
| `.claude/skills/prd/SKILL.md` | The interview workflow: intents (create/resume/update), rounds, question discipline, drafting, review, finalize |
| `.claude/skills/prd/references/question-bank.md` | Coverage map: 7 core areas + optional modules (B2B, regulated, payments, API, AI/ML, mobile, migration, …) |
| `.claude/skills/prd/references/elicitation-techniques.md` | Five whys, pre-mortem, forced ranking, example mapping, … |
| `.claude/skills/prd/references/quality-rubric.md` | 7-dimension rubric used by the reviewer |
| `.claude/skills/prd/assets/prd-template.md` | PRD spine (§1–14) + optional sections menu |
| `.claude/skills/prd/assets/session-template.md` | Interview log / resume file |
| `.claude/skills/prd-review/SKILL.md` | `/prd-review` command |
| `.claude/agents/prd-reviewer.md` | Independent reviewer subagent |

## Customize

- **Different PRD format** (e.g. your company's template): edit `assets/prd-template.md`.
- **Always ask about X** (e.g. legal review, analytics events): add questions to `references/question-bank.md`.
- **Stricter / looser review**: edit `references/quality-rubric.md`.
- **Use it in another repo**: copy `.claude/skills/prd`, `.claude/skills/prd-review`, and `.claude/agents/prd-reviewer.md` into that repo's `.claude/`, or into `~/.claude/` to make them available everywhere.

## Credits

Built by combining ideas from the best open-source PRD skills found in Oct 2026. See [CREDITS.md](CREDITS.md).
