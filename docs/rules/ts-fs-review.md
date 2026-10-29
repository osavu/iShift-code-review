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
  docs/reference/streams.md; the code and its alias, e.g. MD / MDM or PTP / P2P, are both valid). Flag a name whose type letter, stream or TS-to-FS link is wrong or inconsistent with
  the document header and content.
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

## TS review: formal checks (header, footer, history, markers)
- Header: correct stream (one of the valid streams, see docs/reference/streams.md), implementation type and RICEFW ID
  filled in (no `<...>` placeholders left); consistent with the FS header and the file name.
- Footer: document title filled in (no `<name of the TS>` placeholder).
- Related Documents filled in (FS link at minimum; SolDoc and SolMan are the same thing: SAP Solution Manager); no template placeholder rows left (e.g. GPDDXXXX, FDXXXX).
- Version history filled in. For a modified TS, each change row shows: who modified, the Jira US or ServiceNow
  change number that requested it, the version, the date and a description of the main changes.
- Change markers: for a modified TS every modification is visible in the text with a marker built from that US or
  change number. Check that a begin/end pair exists for each (Begin/End, Start/Finish or any equivalent
  combination), that it is closed, that its number appears in the version history, and that every history entry
  has its marker(s) in the text (confirmed by the user).
- New implementations: unnecessary chapters are deleted (section 3.2-3.4 are alternatives: keep only the one
  relevant to the implementation type); no empty or untouched template sections left; no template instruction
  text (the `[...]` guidance) left over.
- Template section numbering/numbering gaps are not to be checked (the actual TS differs from the template).
- Versioning: V0.xx intermediate, V1.0 / V2.0 final.

## TS review: content rules
- The code is NOT described line by line; only the major points are needed.
- Diagrams are welcome to explain flows.
- No superfluous explanations; the essentials only. Flag wrong, irrelevant or redundant text.
- Content must match the section's purpose (see docs/reference/ts-template-structure.md).

## Two review stages
1. Design Tech Review: focus on the HLD (section 2 "Development Overview" and the overview in section 1);
   check that it is clear, complete for a general understanding, logical and feasible, plus the formal checks.
2. Dev Tech Review: the TS is evaluated in parallel with the code. Capture the most important details:
   consistency between TS and code, completeness of the object list, authorizations, error handling, performance,
   transports, plus the formal checks. HLD may be updated after Build if it does not match the implementation.

## Output
- For TS/FS findings use docs/templates/review-comment.md. Highlight severe errors to the user separately.
