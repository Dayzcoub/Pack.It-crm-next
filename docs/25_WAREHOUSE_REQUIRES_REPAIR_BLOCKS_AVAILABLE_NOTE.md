# 25 Warehouse — Requires Repair Blocks Available Note

## 10.212. Blocking category for available status

Decision: the key blocking category for moving an item to available is requires repair.

Rules:
- if the item/problem is marked as requires repair, it cannot be moved to available;
- the item must stay in a non-available workflow status such as in_repair or quarantine until resolved;
- returned -> available is blocked while requires repair is active;
- the system should show a clear reason for the block;
- non-repair issues, such as some completeness problems, can still follow receiver judgement rules.

Purpose:
- prevent equipment needing repair from returning to active stock;
- keep availability safe and operationally reliable;
- define the blocking rule in a practical category rather than only by damage wording.

MVP approach:
- add requires repair as the primary availability-blocking problem category;
- block available transitions for this category;
- log attempted and successful status transitions where applicable.
