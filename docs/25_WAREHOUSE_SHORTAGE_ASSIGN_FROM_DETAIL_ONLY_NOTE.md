# 25 Warehouse — Shortage Assign From Detail Only Note

## 10.272. Responsible assignment only from shortage detail card

Decision: responsible person assignment should be available only after opening the shortage detail card, not as a quick action directly from the list row.

Rules:
- open shortage list stays compact and clean;
- list row shows responsible person or unassigned state;
- unassigned row may be subtly highlighted;
- assignment action is not shown directly in the row;
- warehouse keeper opens the shortage detail card to assign or change responsible person;
- assignment action is logged in the shortage action history.

Purpose:
- avoid cluttering the open shortage list with action buttons;
- reduce accidental assignments;
- keep assignment decision inside the full shortage context.

MVP approach:
- no inline assign button in shortage row;
- row click/open leads to shortage detail card;
- detail card contains assign/change responsible action according to permissions.
