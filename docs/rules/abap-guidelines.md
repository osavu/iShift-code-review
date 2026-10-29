# ABAP and Fiori guidelines (summary)

Source: QA/ABAP/Fiori strategy deck (slides 7, 18). The detailed internal ABAP development guidelines and naming
conventions will be added when the user shares them (they may be partly outdated; the user decides).

## Guiding principles
- G1. Simple, straightforward code that other developers can read and understand.
- G2. Fiori first: user-interaction functionality is delivered through Fiori apps; exceptions follow the decision tree.
- G3. Modern ABAP: obsolete statements are forbidden; use newer syntax wisely, keeping readability in mind.
- G4. Performance: use SQL / AMDP / measurement tools; analyse data volumes (e.g. ACDOCA ~2.3 billion rows in prod,
  Jan 2026); improve data selection; measure time and memory consumption.
- G5. OData services: ABAP RAP is the model of choice; classic SEGW only when RAP is not possible.
- G6. Frameworks: use existing Sanofi artefacts (parallel processing framework, Enhancement Framework, constant tables).
- G7. Documentation: diagrams help; concentrate on main ideas (no superfluous text) but give the next developer
  enough information.

## Fiori first and reports decision tree
Any user-interaction app is delivered as a Fiori Template app by default; exceptions are allowed; the decision tree
must be followed.
1. Is user interaction needed?
   - No -> ABAP report (job). Jira type: Dev - Report.
   - Yes -> 2.
2. Does it require additional UX customization?
   - Yes -> Fiori Template + Extensions (first choice) or Fiori Freestyle app. Jira type: Dev - Fiori apps.
   - No -> 3.
3. Can RAP/OData frameworks fulfil the requirements?
   - Yes -> Fiori Template. Jira type: Dev - Report.
   - No -> Fiori-enabled GUI report. Jira type: Dev - Report.

## Dev - Fiori user story structure
- F1. One Detailed Tech Design + Review task, covering backend (Dev - Report) and Fiori.
- F2. One Build & UT Report + Review task (backend side).
- F3. One Build & UT Fiori + Review task (frontend side).
- F4. The backend (Dev - Report) contains: the published OData service; the underlying model (prefer ABAP RAP over
  SEGW); all additional artefacts of the backend functionality (CDS views, classes, etc.).

## Known inconsistencies in the source deck (accepted by the user)
- Parallel processing framework is abbreviated both PAF and PPF.
- Slide 7 says Fiori-first exceptions are on "the last slide"; they are on slide 18.
