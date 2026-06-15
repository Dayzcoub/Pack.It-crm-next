# 25 Warehouse — Inventory Report Differences and Checkpoint Note

## 10.183. Inventory report content scope

Decision: the main inventory report should show differences only, with an optional checkpoint/full checked list when needed.

Rules:
- the default report focuses on discrepancies;
- do not include the full checked list in the main report by default;
- allow adding a checkpoint/full checked list when the user needs it;
- the full list can be generated as an appendix, separate section, or separate internal checkpoint document.

Examples of discrepancies:
- expected quantity differs from counted quantity;
- missing item;
- extra item;
- item found in a wrong place;
- item requires review;
- condition/status mismatch if such detail is enabled.

Purpose:
- keep the main inventory report short and useful;
- make problems visible immediately;
- still allow a full audit trail when needed.

MVP approach:
- generate the main inventory report with discrepancies only;
- add an optional full-check checkpoint mode;
- keep both internal and without prices by default.
