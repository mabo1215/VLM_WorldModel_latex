# paper/AGENTS.md

## Scope

This file governs all work under `paper/` and all manuscript-facing outputs
that interact with:
- `paper/main.tex`
- `paper/appendix.tex`
- `paper/main.pdf`
- `paper/appendix.pdf`
- `paper/references.bib`
- `paper/figs/`

This file may live inside a template-only rules repository before being copied
into a destination repo. If the manuscript files above are absent here, treat
them as the expected layout of the destination repo rather than as a rule
violation.

The paper must be revised according to `docs/revision_suggestions.tex`, unless
the user explicitly triggers the independent review reset command.

---

## Primary objective

Turn the manuscript into a coherent, publication-ready paper by:
- revising the text
- improving structure and argument flow
- integrating new experiments when needed
- inserting new figures or tables
- updating citations
- ensuring appendix and main text remain consistent

This paper-facing process may run in parallel with other agents and may repeat
across multiple review cycles.

---

## Venue Target

Read the target venue from the line `目标会议和期刊：...` in
`USAGE_codex.md`.

If the line is filled in:
- use that venue as the primary standard for scope fit, formatting
  expectations, submission-readiness checks, and paper positioning
- align revision priorities to the likely review standards of that venue
- verify current official venue requirements when they may be time-sensitive

If the line is blank or absent, infer the strongest reasonable top-tier venue
standard from the manuscript and repository context.

---

## Manuscript language rules

All content in `paper/` must be in polished academic English.

This includes:
- body text
- section titles
- captions
- table notes
- equation descriptions
- algorithm descriptions
- appendix content
- bibliography entries

Do not use Chinese anywhere in `paper/`.

---

## Core writing principles

1. Keep one consistent paper narrative.
2. Use precise terminology consistently.
3. Remove legacy or contradictory wording.
4. Every strengthened claim should be supported by:
   - a reference,
   - an experiment,
   - or a clearly stated limitation.
5. Avoid vague claims such as:
   - effective
   - robust
   - significant
   - better
   unless evidence is explicitly given.

---

## Reader-first manuscript boundary

The manuscript must read as a standalone paper for readers and reviewers who
do not know the revision history, internal workflow, or repository structure.

Do not mention in `paper/`:
- prior revision progress
- completed or pending modification history
- TODO notes, revision notes, or editor-facing reminders
- statements about what was changed in earlier rounds
- repository workflow status
- script-running status

Do not expose code-facing content in the manuscript unless it is essential
scientific material rewritten in paper-appropriate prose. In particular, do
not include:
- raw Python code
- debugging notes
- file paths
- local folder names such as `src/experiments/`, `src/figures/`, or similar repository-internal directories
- script names
- concrete implementation filenames
- command lines
- repo-internal implementation instructions
- AI-generated planning text

The paper must stay independent from the repository and codebase. Reviewers
should be able to understand the paper without seeing local scripts, progress
tracking, or implementation workflow details.

Describe experiments and method support in reader-facing scientific terms:
- what problem or hypothesis is being tested
- what setup, baselines, datasets, and metrics are used
- what evidence the results provide
- what conclusion or limitation follows

Do not explain experiments by telling readers which local folder, script, or
code file produced them.

Do not leave AI-generation traces in the paper. Remove or replace any:
- placeholder text
- fabricated filler sentences
- `TODO`, `TBD`, `XXX`, or similar markers
- "to be added later" statements
- text that admits missing evidence while still keeping the unsupported claim

If code has not yet been run or final data are not available, comment out or
remove the related paper content until real results exist. Never leave visible
placeholder tables, placeholder figures, speculative numeric claims, or
unverified AI-written result discussion in the manuscript.

Prefer omission over visible placeholder content. Unsupported material should
be hidden from the compiled paper until it is backed by actual experiments or
verified analysis.

---

## Required paper workflow

1. Read `docs/revision_suggestions.tex`, unless the user explicitly triggers
   the independent review reset command.
2. Inspect the current paper directly from:
   - `paper/main.tex`
   - `paper/appendix.tex`
   - `paper/main.pdf` when available
   - `paper/appendix.pdf` when available
3. Map each actionable revision item to:
   - a section in `paper/main.tex`
   - or `paper/appendix.tex`
   - or `paper/references.bib`
   - or `paper/figs/`
4. Revise section by section, using multiple agents when helpful and safe.
5. If a revision requires a new experiment, coordinate with `src/`.
6. Once new figures or tables are available, insert them into the correct place
   in the paper.
7. Add surrounding text that includes:
   - setup summary
   - what the figure or table shows
   - what conclusion is supported
   - limitations if needed
8. Re-check cross-references, numbering, and consistency.
9. If the current review file has no remaining actionable paper revisions and
   only blocked or non-actionable items remain, trigger the fresh independent
   review protocol described below.

---

## Parallel paper execution policy

Multiple agents may edit or review the paper in parallel when the work can be
split cleanly.

Good ownership splits include:
- abstract and introduction
- method and notation cleanup
- experiment narration and figure integration
- appendix consistency
- bibliography quality checks

All parallel work must be merged back into one coherent paper voice.

---

## Figure and table rules

All final paper-ready figures must be placed in:
- `paper/figs/`

If `paper/build.bat` is present, use it as the default paper build entrypoint.
Generated intermediate files should stay under:
- `paper/build/`

Final compiled PDFs should be copied to:
- `paper/main.pdf`
- `paper/appendix.pdf`

Every newly added figure or table must:
- have a descriptive caption
- be referenced in the main text
- be discussed in the surrounding paragraph
- support a concrete scientific point

Do not insert a figure without adding explanatory text.

Do not add visual material that is purely decorative.

---

## Appendix rules

Use `paper/appendix.tex` for:
- extended implementation details
- extra tables
- ablation extensions
- detailed derivations
- supplementary qualitative examples
- reproducibility details that are too long for the main text

The appendix must remain consistent with the main text and must not contradict
it.

---

## Bibliography rules

All citation updates must be made in:
- `paper/references.bib`

When adding references:
- prefer authoritative, relevant, paper-quality sources
- avoid low-quality or irrelevant entries
- ensure BibTeX fields are complete and consistent
- keep title capitalization correct for technical terms where needed

Do not add references that are not cited.

Do not cite references that are not discussed meaningfully.

---

## Preferred revision order inside the paper

Unless there is a specific reason to do otherwise, revise in this order:

1. title and abstract
2. introduction and problem statement
3. related work
4. method
5. experiments
6. conclusion
7. appendix
8. references and formatting cleanup

---

## Fresh independent review protocol

When the current `docs/revision_suggestions.tex` has been exhausted except for
blocked or non-actionable items:

1. Start a brand-new review of the paper.
2. Do not use prior review text, prior completion notes, or prior judgments as
   evidence.
3. Review the current paper directly from:
   - `paper/main.tex`
   - `paper/appendix.tex`
   - `paper/main.pdf` when available
   - `paper/appendix.pdf` when available
4. Evaluate it against the target venue declared in `USAGE_codex.md` when
   available. If no target venue is declared, use the strongest reasonable
   top-tier venue standard that can be inferred from the repository and current
   manuscript.
5. Delete the old contents of `docs/revision_suggestions.tex` and replace them
   entirely with a new English-only LaTeX review.
6. Make the new review self-contained and independent from earlier revision
   history.
7. After rewriting `docs/revision_suggestions.tex`, begin the next revision
   cycle against that new file.

---

## Independent Paper Review Reset

If the user says `重新开始评审并生成评审修改意见`, treat it as a paper-first
independent review reset.

When triggered:
1. Ignore the current contents of `docs/revision_suggestions.tex` as review
   input.
2. Read the target venue from `USAGE_codex.md`.
3. Review directly from:
   - `paper/main.tex`
   - `paper/appendix.tex`
   - `paper/main.pdf` when available
   - `paper/appendix.pdf` when available
4. Evaluate contribution quality, scope fit, formatting expectations,
   experiment adequacy, and submission readiness against the declared target
   venue.
5. Rewrite `docs/revision_suggestions.tex` completely in English-only LaTeX.
6. Make the rewritten file contain both review findings and concrete revision
   actions.

---

## Mandatory consistency checks

Before concluding a paper revision cycle, verify:

- abstract matches the actual method and experiments
- introduction matches the final paper narrative
- method notation is self-consistent
- experiments support the paper's claims
- figures and tables are all cited
- appendix references are valid
- bibliography is complete
- no Chinese appears in `paper/`
- no local code paths, folder names, script names, or implementation filenames appear in the manuscript
- if a fresh review cycle was triggered, `docs/revision_suggestions.tex` was
  rewritten entirely from the current `.tex` and `.pdf` paper state
- the review used the target venue from `USAGE_codex.md` when it was set

---

## Interaction with docs/progress.md

After meaningful changes to `paper/`, ensure the repository-wide process also
updates:
- `docs/progress.md`

If a paper-related item remains under `## 未修改或部分修改` in `docs/progress.md`,
the repository-wide process should place any needed user decisions,
clarifications, or missing data requests directly below that item so the user
can answer inline in the same file.

If that paper-related item is blocked pending author input, the repository-wide
process should also record it in `## 遗留问题`. Once the issue is resolved and
the corresponding paper revision is completed, remove the matching entry from
`## 遗留问题` and move the finished work into `## 已全部修改`.

Do not write Chinese in `paper/`; Chinese progress summaries belong only in
`docs/progress.md`.
