# 25 Warehouse — Inventory Scan Out of Scope Note

## 10.232. Scanning item outside current inventory list

Decision: if an item scanned during inventory is not part of the current inventory list, the system only shows a warning. It should not automatically add the item as extra/found.

Rules:
- scanner launched from inventory checks against the current inventory session/list;
- if scanned item is not in the list, show warning: item is not included in current inventory list;
- do not mark it as checked;
- do not add it as an extra row automatically;
- user can continue scanning the planned list after warning.

Purpose:
- keep inventory scope controlled;
- avoid accidental additions during focused inventory sessions;
- make unexpected scans visible without changing report data automatically.

MVP approach:
- show clear warning for out-of-scope scan;
- no automatic report row creation;
- no automatic status change.
