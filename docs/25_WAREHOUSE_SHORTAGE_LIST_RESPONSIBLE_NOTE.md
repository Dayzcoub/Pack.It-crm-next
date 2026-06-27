# 25 Warehouse — Shortage List Responsible Note

## 10.269. Responsible person in open shortage list

Decision: the open shortage list should show the assigned responsible person directly in the row.

Rules:
- assigned responsible person is visible without opening the shortage detail card;
- display must be compact and must not clutter the interface;
- if no responsible person is assigned yet, show a short empty/unassigned state;
- full assignment history remains inside the shortage detail card and action history;
- list row should still prioritize project, missing item, quantity, compact status, and responsible person.

Purpose:
- let warehouse keeper quickly understand who is handling each shortage;
- reduce unnecessary opening of detail cards;
- keep daily shortage list practical on mobile.

MVP approach:
- add compact responsible field to shortage list row;
- use short name/initials or compact label;
- keep detailed user info in the detail card.
