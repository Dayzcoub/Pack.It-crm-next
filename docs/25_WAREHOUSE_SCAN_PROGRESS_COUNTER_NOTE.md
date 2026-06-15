# 25 Warehouse — Scan Progress Counter Note

## 10.237. Scan progress counter

Decision: handout and return scanner screens should show progress counter.

Rules:
- show how many items are scanned in the current document;
- show total expected items for the current document;
- counter should update immediately after each valid scan;
- repeated scans and out-of-scope scans should not increase progress;
- progress should be visible during continuous mobile scanning.

Purpose:
- help user understand how much of the document is already scanned;
- reduce missed items;
- make handout and return scanning easier on mobile.

MVP approach:
- display compact counter, for example: scanned 12 / 40;
- use current staged scan list for scanned count;
- use current document item list for total count.
