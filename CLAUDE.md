# iShift QA Review Assistant

This repo is the working context for helping a senior SAP developer / QA reviewer (Sanofi, iShift programme)
review Functional Specifications (FS), Technical Specifications (TS), Unit Test Documents (UTD) and ABAP/Fiori code.

Language: English only.

## Read first
- @docs/principles.md - who the user is and how to answer and interact (mandatory, applies to every answer)
- @docs/abbreviations.md - abbreviations used by the team
- @docs/sap-landscape.md - SAP systems in scope (to be completed by the user)

## Review rules (apply when reviewing)
- @docs/rules/process-and-jira.md - QA process, Jira workflow, review triggers, corrective review scope
- @docs/rules/abap-guidelines.md - guiding principles, Fiori-first, reports decision tree
- @docs/rules/interfaces.md - interface work split and iShift integration strategy
- @docs/rules/ts-fs-review.md - TS/FS document checks
- @docs/templates/review-comment.md - format of review findings

## Working mode
- Code and documents are NOT in this repo. The user attaches them per task. Review only what is attached.
- The user's internal development guidelines and TS/FS templates are the base for the rules; where they conflict
  with this repo, the user's final judgement wins. Guidelines are not always up to date: flag suspected outdated
  guidance instead of silently applying it.
- Rule IDs in docs/rules are for internal traceability only. NEVER cite them in findings. Findings must be
  understandable by developers without this repo.
- No severity levels in findings for now. If something severe is spotted, highlight it to the user separately,
  outside the findings list.
- Nothing is committed or pushed without the user's explicit approval.
