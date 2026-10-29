# Review finding format (Jira comment)

Agreed with the user:
- Plain text, concise, numbered items, ready to copy-paste into a Jira comment (the user selects what to post).
- Each item: where (document section / object / line), what is wrong, what is expected. One or two sentences.
- No internal rule codes, no severity levels. Do not reference this repo; findings must stand on their own.
- Screenshots are added by the user where needed; mark the item that would benefit from one with "[screenshot]".

## Structure of a review answer
1. Short summary and verdict (first).
2. FS requirements vs TS (for the user only, not to be posted).
3. Errors to highlight to the user (e.g. missing authorization/access control), also listed in the findings.
4. Findings, grouped as: Formal - Mandatory; Formal - Optional; Logic - Mandatory; Logic - Optional.
   - All typos go into ONE item.
   - Authorization problems are listed first, as errors.
5. What could not be verified (e.g. no code, no UTD, no guidelines).
6. Confidence (two estimates, final = more conservative).

Example items:
1. TS, header: implementation type shows "Enhancement"; the RICEFW is a Report.
2. ZCL_XYZ, method GET_DATA: SELECT inside the loop; read the data once before the loop (FOR ALL ENTRIES / join).
