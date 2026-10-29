# TS / FS review

Status: skeleton. To be completed when the user shares the FS and TS templates and the internal development
guidelines. Until then, only the checks below apply (from the QA deck).

## Typical problems reported by the user
- Sections maintained incorrectly (missing, wrong order, unnecessary chapters left in).
- Wrong headers and footers.
- Irrelevant or wrong text.

## Checks (from the QA process)
- Required sections present: history matrix, modification markers, header, footer, chapters.
- New implementation -> new TS template; existing RICEFW -> existing TS with modifications marked by Jira US number.
- Link to the FS (SolDoc) in "Related documents".
- HLD present and sufficient for a general understanding; consistent with the implemented solution after Build.
- For new implementations: unnecessary chapters deleted (chapter 3: only relevant sub-chapters kept).
- UTD attached at Dev Tech Review.

## To add after the templates are shared
- Section-by-section structure of FS and TS, expected header/footer content, mandatory vs optional chapters.
- Consistency checks FS <-> TS <-> code <-> UTD.
