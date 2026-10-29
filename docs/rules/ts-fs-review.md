# TS / FS review rules

Starting point defined by the user (Oct 2026); to be extended as new rules are given.
Never cite these rules by ID or mention this repo in findings (see docs/templates/review-comment.md).

## Inputs and general principles
- Documents arrive either as NEW (new RICEFW, new template) or EXISTING (modified; changes carry markers).
- Old-template documents are valid: they stay as they are and are only modified. Do NOT raise findings because a
  document uses an older template. Apply the structure checks only as far as the document's own template allows.
- Naming (RICEFW ID and files): `<type letter>FS_<STREAM>_<NNN>` for the FS and `<type letter>TS_<FS name>`-style
  for the TS (e.g. FS EFS_P2P_001, TS ETS_EFS_P2P_001). The type letter is the RICEFW type: R Report, I Interface,
  C Conversion, E Enhancement/Extension, F Form, W Workflow. The stream part must be a valid stream (see
  docs/reference/streams.md; the code and its alias, e.g. MD / MDM or PTP / P2P, are both valid). Flag a document
  name or header whose type letter, stream or ID is wrong or inconsistent with the content.
- Object names: the FS may propose object names, but this is not a rule; naming objects is the developer's
  responsibility. A name that differs between FS and TS is NOT an issue.
- New FS templates exist per RICEFW type (report, interface, conversion, enhancement, workflow) with small
  differences. The TS template is the same for all types; unwanted chapters are deleted.

## FS review (content only)
- Developers have little influence on the FS: do NOT check layout or formal rules (headers, footers, styling,
  template compliance). Only the information is relevant.
- NEW FS: assess whether the requirements are logical, make sense, and have flaws or gaps.
- CHANGED FS: (1) give the user a very short summary of the entire functionality, for context; (2) focus the
  analysis on the last change only (the requirements introduced by it; find it via the latest history entry and the
  change markers); (3) assess whether those requirements are logical, make sense, and have flaws, including
  conflicts with the existing functionality.

## Findings are split into Formal and Logic; each is further split into Mandatory and Optional
- Mandatory = sent as part of the review. Optional = proposed to the user, who decides whether to send it.
- Separately (for the user only, not part of the findings): a short "FS requirements vs TS" comparison. Do this in
  every review where an FS is available.

## TS review: Formal - MANDATORY
- Header and footer: correct stream (one of the valid streams, see docs/reference/streams.md), implementation type
  (must match the RICEFW type letter) and RICEFW ID filled in, consistent with the FS header and the file name;
  footer title filled in; no `<...>` placeholders left.
- Version history filled in. For a modified TS, each change row shows who modified, the Jira US or ServiceNow
  change number, the version, the date and a description of the main changes.
- Change markers (modified TS): every modification is visible in the text with a marker built from that US or
  change number. A begin/end pair must exist for each (Begin/End, Start/Finish or any equivalent combination),
  be closed, match a version-history entry, and every history entry has its marker(s) in the text.
- Typos: ONE finding that lists all typos found (section and word), not one finding per typo.
- Diagram and high level description: the technical flow diagram and the high level description (HLD) are present
  and meaningful. Diagrams may be images, SmartArt or shapes: check all (see "Reading documents"); never state a
  diagram is missing unless the extraction is confirmed to cover those object types; if unsure, say it could not
  be verified.
- Authorization: see "Authorization" below (critical).

## TS review: Formal - OPTIONAL (the user decides)
- Unused chapters not deleted (e.g. form design or workflow sections in a report TS; empty sections).
- Document location check (template text still present, empty section).
- Version in the version history differs from the version in the file name.
- Related Documents check (FS link present; SolDoc and SolMan are the same thing; no placeholder rows left,
  e.g. GPDDXXXX, FDXXXX; description filled in).
- Do NOT flag: text placed in a different but reasonable chapter, download-path wording, template numbering gaps.

## Authorization (critical, always check)
- Authorization is a critical point and is reported as an ERROR (mandatory, listed first, and also highlighted to
  the user). Keep an eye on it in every review, in both TS and code.
- Access Control objects (DCL) and authority checks are required for the CDS views at the TOP of the hierarchy,
  i.e. the ones consumed by the Fiori app (consumption/projection root views exposed through the service). Not
  every CDS view needs authorizations; do not flag lower-level (basic/interface) views for lacking them.
- A TS that does not mention authorizations for the consumed top-level views (empty authority-check or CDS
  access-control sections, no access control object in the object list) is an error; in a Dev Tech Review also
  verify it in the code.

## TS review: Logic
- The TS does NOT need to describe the logic in detail. Only the most important logic is needed; if the detail is
  readable from the code, it does not have to be in the TS.
- Missing detailed logic is therefore at most an OPTIONAL finding, and often not a finding at all.
- Mandatory logic findings are those where the TS is wrong, contradicts the FS/requirement or the code, or where
  an important requirement is not covered. FS vs TS differences in names of objects are not findings.
- The code is NOT described line by line; diagrams are welcome; no superfluous explanations (flag superfluous,
  wrong or irrelevant text).
- Content must match the section's purpose (see docs/reference/ts-template-structure.md).

## Reading documents
- Use `python3 tools/extract_docx.py <file.docx> [out.txt]` to extract body text, headers/footers, SmartArt text,
  the embedded-image list, and tracked changes/comments in one go (cheaper in tokens than ad-hoc reading). Images
  are not extracted; open only the ones needed (screenshots, layouts), downscaled.
- Lesson learned: plain text conversion (pandoc) silently drops SmartArt, so a SmartArt diagram looked "missing".

## Two review stages
1. Design Tech Review: focus on the HLD (section 2 "Development Overview" and the overview in section 1);
   check that it is clear, complete for a general understanding, logical and feasible, plus the formal checks.
2. Dev Tech Review: the TS is evaluated in parallel with the code. Capture the most important details:
   consistency between TS and code, completeness of the object list, authorizations, error handling, performance,
   transports, plus the formal checks. HLD may be updated after Build if it does not match the implementation.

## Output
- For TS/FS findings use docs/templates/review-comment.md. Highlight severe errors to the user separately.
