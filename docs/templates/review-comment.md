# Review finding format (Jira comment)

Agreed with the user:
- Plain text, concise, numbered items, ready to copy-paste into a Jira comment (the user selects what to post).
- Each item: where (document section / object / line), what is wrong, what is expected. One or two sentences.
- No internal rule codes, no severity levels. Do not reference this repo; findings must stand on their own.
- Severe errors are highlighted to the user separately, outside the list of items.
- Screenshots are added by the user where needed; mark the item that would benefit from one with "[screenshot]".

Example:
1. TS, section 3.2: header shows the previous project name; update to the current one.
2. ZCL_XYZ, method GET_DATA: SELECT inside the loop; read the data once before the loop (FOR ALL ENTRIES / join).
