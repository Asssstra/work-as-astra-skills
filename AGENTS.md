# Working on Work Self Skills

- Preserve the user's current intent. Skills guide behavior; they do not override the user's explicit instructions.
- This is a personal workflow distillation repository. Separate observed facts, user explanations, and assistant hypotheses.
- Five authentic report samples have now been distilled. Check `skills/report/references/profile.md` for current coverage and `evidence.md` for provenance. Never invent samples, preferences, outcomes, or evidence to fill gaps; generated drafts are not user-authored samples.
- Keep each skill self-contained under `skills/<name>/`, with a valid `SKILL.md` and only references needed by its workflow.
- Store raw samples, unredacted material, holdout answers, and working notes under ignored `data-local/`. Do not upload them by default. Honor explicit authorization for a specific sanitized batch.
- Do not inspect held-out report answers while extracting rules or drafting their test outputs. If exposed, mark the evaluation as contaminated and use a new holdout for an independent test.
- Do not silently promote a one-off observation into a general preference. Record scope, supporting sample IDs, exceptions, and status.
- After changing skill instructions, run the skill creator's quick validator when available and check all relative links. Run targeted behavioral evaluation when a change affects decisions; do not claim synthetic tests prove personal style similarity.
- Report generation is drafting. It does not authorize sending a message, committing a promise, or pushing future changes unless requested in the current task scope.
- Use `pwsh.exe -NoProfile` for Windows commands. Do not modify project-mirrored `sources/` files outside this repository.
