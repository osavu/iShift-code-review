# QA process and Jira workflow

Source: "Dev Process - QA, ABAP & Fiori Strategy" V0.1 (22 Jan 2026), slides 4-5, 9-10, 12-13.
IDs are internal; never cite them in findings.

## Phases (each is a Jira subtask of the user story)
Detailed Tech Design -> Design Tech Review -> DD Validation + TFA -> Build & UT -> Dev Tech Review -> FUT -> FUT Validation.

## Story types
Dev - Enhancement, Interface, Forms, Report, Fiori, Workflow, Conversion.

## Triggering the Design Tech Review (developer actions)
- P1. Attach the TS with the HLD chapter completed to the task.
- P2. FS SolDoc link or FS document is set on the user story.
- P3. Set the task to DONE.
- P4. Assign the Design Tech Review task to a core team QA reviewer; set it to IN PROGRESS.

## Triggering the Dev Tech Review (developer actions)
- P5. Attach the final TS version and the UTD.
- P6. Add the TR numbers in the task description; run ATC + VForge + SLIN on the TRs.
- P7. Set the task to DONE.
- P8. Assign the Dev Tech Review task to a core team QA reviewer; set it to IN PROGRESS.

## Design Tech Review checklist
- D1. TS (with HLD) is added in the Technical Design task.
- D2. Jira user story category, complexity and story points are correct.
- D3. TS has all required sections: history matrix, modification markers, header, footer, chapters.
- D4. Link to the FS from SolDoc is in "Related documents", plus other relevant links.
- D5. New implementations use the new TS template.
- D6. Existing RICEFWs use the existing TS; modifications are marked with the Jira user story number.
- D7. HLD gives enough information for a general understanding of what will be implemented. It may be modified
  after Build if it does not match the implemented solution.

## Dev Tech Review checklist
- V1. TRs are in the description of the Build & UT task (pre-loaded template); TS and UTD are attached.
- V2. ATC + VForge + SLIN were run and error findings are fixed.
- V3. Naming conventions are respected.
- V4. Header and other relevant comments are maintained in the source code.
- V5. Modified objects: modification identifier (usually the Jira US) is specified and code changes are marked with it.
- V6. Dependencies on other objects or clarifications are written as comments in the Dev Tech Review task
  (avoid back-and-forth).
- V7. Any known deviation from the development guidelines is explained in a comment.
- V8. TS is updated with the latest information; all needed sections filled in; for new implementations unnecessary
  chapters are deleted (from chapter 3 keep only relevant sub-chapters).

## Corrective review
The QA team may make code changes itself during review, limited to this "Minor Corrections" list (C1: anything else
goes back to the developer):
- Naming convention; code formatting; conditions sequence and syntax
- Simple error handling, sy-subrc checks
- Comments contents
- Method refactoring (scope to be confirmed with the user)
- Usage of constants
- Performance tuning
- Commits / rollbacks; incorrect WAIT statements
- Wrong CDS view design where the fix does not change cardinality / data flow architecture
- Table technical attributes and buffering settings
- Text elements (typos, translations, deleting unused texts, replacing texts by constants)
- Program/class attributes
- Unused workbench objects / program variables and types

## Core ABAP QA reviewers
Names are in the source deck (slide 9) and are intentionally not copied here.
