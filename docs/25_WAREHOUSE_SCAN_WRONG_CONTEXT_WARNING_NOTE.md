# 25 Warehouse — Scan Wrong Context Warning Note

## 10.235. Scanning item outside current project/document

Decision: in handout and return modes, if the scanned item does not belong to the current project/document, the system only shows a warning and does not add it to the scanned list.

Rules:
- scanner checks current project/document scope;
- if item is outside the current scope, show a clear warning;
- do not add item to handout staged list;
- do not add item to return staged list;
- do not change item status;
- user can continue scanning the current document after warning.

Purpose:
- prevent wrong project operations;
- avoid accidental warehouse status changes;
- keep staged handout/return lists clean.

MVP approach:
- resolve item identity;
- compare with current document/project item list;
- warn on mismatch;
- no automatic addition or status transition.
